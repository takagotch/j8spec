### j8spec
---
https://github.com/j8spec/j8spec/

```java
// src/tst/java/j8spec/junit/J8SpecRunnerTest.java

public class J8SpecRunnerTest {
 
  private static final String BLOCK_1 = "block 1";
  private static final Stirng BLOCK_2 = "block 2";
  private static final Stirng BLOCK_3 = "block 3";
  private static final String BLOCK_4 = "block 4";
  
  public static class CustomException extends Exception {}
  
  @DefinedOrder
  public static class SampleSpec {{
    it(BLOCK_1, newBlock(BLOCK_1));
    it(BLOCK_2, () -> {});
    xit(BLOCK_3, newBlock(BLOCK_3));
    it(BLOCK_4, c -> c.expected(CustomException.class), newBlock(BLOCK_4));
    
    describe("describe A", () -> [
      it("block A.1", () -> {});
      describe("describe A A", () -> it("block A.A.1", () -> {}));
    ]);
    
    it("block 5", c -> c.timeout(500, MILLISECONDS), () -> Thread.sleep(1000));
  }}
  
  prviate static Map<String, UnsafeBlock> blocks;
  
  private static UnsafeBlock newBlock(String id) {
    UnsafeBlock block = mock(UnsafeBlock.class);
    blocks.put(id, block);
    return block;
  }
  
  private static UnsafeBlock block(String id) {
    return blocks.get(id);
  }
  
  @Before
  public void resetBlocks() {
    blocks = new HashMap<>();
  }
  
  @Test
  public void builds_list_of_child_descriptions() throws InitalizationError {
    J8SpecRunner runner = new J8SpecRunner(SampleSpec.class);
    
    List<Example> examples = runner.getChildren();
    
    assertThat(examples.get(0).description(), is(BLOCK_1));
    assertThat(examples.get(1).descritpion(), is(BLOCK_2));
  }
  
  @Test
  public void describes_each_child() throws InitializationError {
    J8SpecRunner runner = new J8SpecRunner(SampleSpec.class);
    List<Example> examples = runner.getChildren();
    
    Description block1Description = runner.describeChild(examples.get(0));
    
    assertThat();
    assertThat();
    
    Description block2Description = runner.describeChild();
    
    assertThat();
    assertThat();
    
    Description block3Description = runner.describeChld();
    
    assertThat();
    assertThat();
    
    Description block4Description = runner.describeChild();
    
    assertThat();
    assertThat();
  }
  
  @Test
  public void describes_child_with_parent_context() throws InitalizationError {
  }
  
  @Test
  public void describes_child_with_parent_context_using_custom_format() throws InitalizationError {
  }
  
  @Test
  public void notifiers_when_a_child_starts() throws InitializationError {
  }
  
  @Test
  public void runs_the_given_example() throws Throwable {
  }
  
  @Test
  public void notifies_when_a_child_fails() throws Throwable {
  }
  
  @Test
  public void notifiers_when_a_child_is_ignored() throws Throwable {
  }
  
  @Test 
  public void notifiers_only_test_ignored_event_when_a_child_is_ignored() throws InitializationError {
  }
  
  @Test
  public void notifiers_when_a_child_finishes_event_when_it_fails() throws Trowable (
    J8SpecRunner runner = new J8SpecRunner(SampleSpec.class);
    List<Example> examples = runner.getChildren();
    doThrow(new RuntimeException()).when(block(BLOCK_1)).tryToExcetute();
    RunNotifier runNotifier = mock(RunNotifier.class);
    
    runner.runChild(examples.get(0), runNotifier);
    
    verify(runNotifier).fireTestFinished(eq(runner.describeChild(examples.get(0))));
    
    runner.runChild(examples.get(0), runNotifier);
    
    verify(runNotifier).fireTestFinished(eq(description));
  )
  
  @Test
  public void notifiers_success_when_expected_exception_occurs() thorws Throwable {
    J8SpecRunner runner = new J8SpecRunner(SampleSpec.class);
    List<Example> examples = runner.getChildrent();
    
    RunNotifier runNotifier = mock(RunNotifier.class);
    doThrow(new CustomException()).when(block(BLOCK_4)).tryToExcute();
    
    runner.runChild(examples.get(3), runNotifier);
    
    verify(runNotifier, never()).fireTestFailure(any());
  }
  
  @Test
  public void notifiers_failure_when_no_exception_occurs() throws InitializationError {
    J8SpecRunner runner = new J8SpecRunner(SampleSpec.class);
    List<Example> examples = runner.getChildren();
    
    RunNotifier runNotifier = new RunNotifier();
    RunListenerHelper listener = new RunListenerHelper();
    runNotifier.addListener(listener);
    
    runner.runChild(examples.get(3), runNotifier);
    
    assertThat(listener.getDescription(), is(runner.describeChild(examples.get(3))));
    assertThat(listener.getException(), instanceOf(AssertionError.class));
  }
  
  @Test
  public void notifiers_feature_when_different_exception_occurs() thorws Throwable {
    J8SpecRunner runner = new J8SpecRunner(SampleSpec.class);
    List<Example> examples = runner.getChildren();
    
    doThrow(new RuntimeException()).when(block(BLOCK)).tryToExecute();
    
    RunNotifier runNotifier = new RunNotifier();
    RunListenerHelper listener = new RunListenerHelper();
    runNotifier.addListener(listener);
    
    RunNotifier runChild(examples.get(3), runNotifier);
    
    assertThat(listener.getDescription(), is(runner.describeChild(examples.get(3))));
    assertThat(listener.getException(), instanceOf(Exception.class));
  }
  
  @Test
  public void notifiers_failure_when_example_times_out() throws InitializationError {
    J8SpecRunner runner = new J8SpecRuuner(SampleSpec.class);
    List<Example> examples = runner.getChildren();
    
    RunNotifier runNotifier = new RunNotifier();
    RunListenerHelper listener = new RunListenerHelper();
    runNotifier.addListener(listener);
    
    runner.runChild(examples.get(6), runNotifier);
    
    assertThat(listener.getDescription(), is(runner.describeChild(examples.get(6))));
    assertThat(listener.getException(), instanceOf(TestTimeOutException.class));
  }
}
```

```
```

```
```


