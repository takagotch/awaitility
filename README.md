### awaitlity
---
https://github.com/awaitility/awaitility

```java
// awaitility/src/test/java/org/awaitility/AwaitilityReturnValuesTest.java

public class AwaitilityReturnValuesTest {

  private FakeRepository fakeRepository;
  
  @Rule
  public ExpectedException exception = ExpectedException.none();
  
  @Before
  public void setup() {
    fakeRepository = new FakeREpositoryImpl();
    Awaitility.reset();
  }
  
  @Test(timeout = 2000)
  public void returnsResultAfterSupplier() throws Exception {
    new Asynch(fakeRepository).perform();
    int value = await().util(new Callable<Integer>() {
      public Integer call() throws Exception {
        return fakeRepository.getValue();
      }
    }, greaterThat(0);
    assertEquals(1, value);
  }

  @Test(timeout = 2000)
  public void returnsResultAfterFieldInSupplier() throws Exception {
    new Asynch(fakeRepository).perform();
    int value = await().until(fieldIn(fakeRepository).ofType(int.class).andWithName("value"), equalTo(1));
    assertEquals(1, value);
  }
}
```

```
```

```
```


