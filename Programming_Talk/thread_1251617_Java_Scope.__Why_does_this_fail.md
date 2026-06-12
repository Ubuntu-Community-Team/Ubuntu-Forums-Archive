---
title: "Java Scope.  Why does this fail?"
date: 2009-08-27
forum: Programming Talk
---

### Post by mcla0203 on 2009-08-27
I've been working with java for a while, and I'm a bit baffled at this scenario.  I created a simple test case to depict it.  My question is, why doesn't the value of "wtf" carry over to the testScopeTest_run2 method?  Of course, assume that run1 is run first, and run2 is run second.

```

import junit.framework.TestCase;

public class ScopeTest extends TestCase {

	private String wtf = null;

	public void testScopeTest_run1() {
		wtf = "TEST";
		assertEquals(wtf, "TEST");   //SUCCESS
	}
	
	public void testScopeTest_run2() {
		assertEquals(wtf, "TEST");     //FAILED (wtf = null)
	}

	
}
```

---

### Post by kpkeerthi on 2009-08-28
Are you running a junit testcase? Can you post a code that compiles?

---

### Post by Fallen_Demon on 2009-08-28
Show us your run code as well. It's entirely possible that you're accidentally creating a new instance of the class

---

### Post by mcla0203 on 2009-08-28
This compiles assuming you add the junit framework to your classpath.  I'm not sure what is meant by run class.  This is just a simple test case meant to depict the scenario.  Just assume that testScopeTest_run1() runs first, then assume testScopeTest_run2() runs second.  I expected that the string "wtf" was still defined since it is a member variable.  I don't understand why it would make a new instance if it is refering to the instance created in the class.

```

import junit.framework.TestCase;

public class ScopeTest extends TestCase {

	private String wtf = null;

	public void testScopeTest_run1() {
		wtf = "TEST";
		assertEquals(wtf, "TEST");   //SUCCESS
	}
	
	public void testScopeTest_run2() {
		assertEquals(wtf, "TEST");     //FAILED (wtf = null)
	}

	
}
```

---

### Post by spupy on 2009-08-28
JUnit test don't run one after the other in the sense that you first execute method1 and then immediately method2. First the test object is created (set-up method for the test case, if you have any), method1 is run, test object is torn down (tear-down method, if you wrote one); test object is created again, method2 is executed, test is torn down.

In short, for the execution of each test method, the test class is instantiated anew. That is way 'wtf' is null in the method2 - method1 is not run so the var is not initialized.

EDIT: If you want to have the var initialized, you need a set-up method. In JUnit 4 you do this with @Before, but I have no idea how to do that in junit version 3.

---

### Post by mcla0203 on 2009-08-28
> **spupy said:**
> JUnit test don't run one after the other in the sense that you first execute method1 and then immediately method2. First the test object is created (set-up method for the test case, if you have any), method1 is run, test object is torn down (tear-down method, if you wrote one); test object is created again, method2 is executed, test is torn down.

In short, for the execution of each test method, the test class is instantiated anew. That is way 'wtf' is null in the method2 - method1 is not run so the var is not initialized.

EDIT: If you want to have the var initialized, you need a set-up method. In JUnit 4 you do this with @Before, but I have no idea how to do that in junit version 3.

I agree with you here regarding JUnit, but it does not explain why this happened with a Java class.  My original issue was that this happens in a regular old SomeClass.java.  A method is called that instantiates a member var.  The method that instantiates the member var is not a constructor.  And then another method calls the member variable that was instantiated and it is null all of a sudden.  The same thing occurs independent of the JUnit functionality, although you are completely right about JUnit.

Any other ideas why this would happen in a regular old java class?  I made the unit test to help depict the problem at a simple level, and I guess it has not helped.  My mistake.

---

### Post by spupy on 2009-08-28
> **mcla0203 said:**
> I've been working with java for a while, and I'm a bit baffled at this scenario.  I created a simple test case to depict it.  My question is, why doesn't the value of "wtf" carry over to the testScopeTest_run2 method?  Of course, assume that run1 is run first, and run2 is run second.

```

public void testCase() {
	
	private String wtf = null;

	public void testScopeTest_run1() {
		wtf = "TEST";
		assertEquals(wtf, "TEST");   //SUCCESS
	}
	
	public void testScopeTest_run2() {
		assertEquals(wtf, "TEST");     //FAILED (wtf = null)
	}
	
}
```

Wait, I just now looked closely at your code and noticed that the two methods are not in a class, but in a method? How does this even work? I put the two methods in a class and they run as expected ('wtf' is initialized).

---

### Post by mcla0203 on 2009-08-28
> **spupy said:**
> Wait, I just now looked closely at your code and noticed that the two methods are not in a class, but in a method? How does this even work? I put the two methods in a class and they run as expected ('wtf' is initialized).

That was a typo.. Refer to the second block of code that I posted.  Sorry.... I also edited the first one.  It should be a class, for sure =P

---

### Post by gmclachl on 2009-08-28
I doubt it would pass. There is no way of guaranteeing the order in which tests are runs. So I would move any initialisation of wtf to a setUp() method, this will be called before each test is executed. 

George

---

