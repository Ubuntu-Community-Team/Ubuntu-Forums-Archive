---
title: "Unit testing in Java"
date: 2012-02-17
forum: Programming Talk
---

### Post by abraxas334 on 2012-02-17
Hi,
I would like to learn about unit testing in java. What is the best way of doing this?
Let's assume I have a class with 3 individual functions, where each is relying on each other for a correct output, so they can only be called consecutively. I want to make sure each of them work individually though. So I would like to set up a unit test for each of the functions, to be sure that they work before testing them with real data. How is this best done in terms of class structure. Of course i can just add thre other functions to the class testing those? But then i would have to set that particular class as a main class, which i don't want to do? So basically I am wondering how does unit testing really work. Can you either give me pointers, or a link, which is helpful?

Any help is greatly appreciated. Thanks!

---

### Post by Azdour on 2012-02-17
Hi,

I'm a Java Developer and I would suggest you use JUnit to write unit tests:

[http://www.junit.org/](http://www.junit.org/)

---

### Post by muteXe on 2012-02-17
+1 for junit. using it all the time at the moment.

---

### Post by r-senior on 2012-02-17
+1 for JUnit.

As far as structure is concerned, the usual approach is to create a test class for the class that you want to test. So if you have a class called Service, you'd create a class called something like ServiceTest and put your tests in there. You don't want to pollute your real classes with tests.

So, for example, if you have:

*Service.java*
```

package mypackage;

public class Service {

    public int doSomething() {
        ...
    }

}

```

You'd have a test class:

*ServiceTest.java*
```

package mypackage;

public class ServiceTest {

    @Test
    public void testDoSomething() {
        Service service = new Service();
        int actual = service.doSomething();
        int expected = 42;
        assertEquals(expected, actual);
    }

}

```

If you use Maven, it assumes your sources are under src/main/java and the corresponding tests are under src/test/java. Maven will run unit tests automatically during a build. In case you forget. ;)

Note that JUnit doesn't order tests. If your functions are dependent on each other, you would need to test them as a single process. Or use mock results from the previous phase to test each function in isolation. Mockito is a nice framework for doing that sort of thing.

Lots of cool things you can do with JUnit though, like expected exceptions, timeouts, setup/teardown methods. Great framework.

For your next project, once you've got into JUnit, consider writing a comprehensive test class *first*, based on the requirement. Test-driven development can be a very productive approach to certain types of development. Search for "junit test driven development".

---

### Post by ofnuts on 2012-02-17
> **abraxas334 said:**
> Hi,
I would like to learn about unit testing in java. What is the best way of doing this?
Let's assume I have a class with 3 individual functions, where each is relying on each other for a correct output, so they can only be called consecutively. I want to make sure each of them work individually though. So I would like to set up a unit test for each of the functions, to be sure that they work before testing them with real data. How is this best done in terms of class structure. Of course i can just add thre other functions to the class testing those? But then i would have to set that particular class as a main class, which i don't want to do? So basically I am wondering how does unit testing really work. Can you either give me pointers, or a link, which is helpful?

Any help is greatly appreciated. Thanks!
+1 for Junit. Theres is also a variant called DBUnit if your Java code interacts with a DB. 

If you use Eclipse there are plugins to integrate them.

---

### Post by hoboy on 2012-02-17
I use [http://code.google.com/p/mockito/](http://code.google.com/p/mockito/)
it is great

---

### Post by doobrie on 2012-02-17
> **hoboy said:**
> I use [http://code.google.com/p/mockito/](http://code.google.com/p/mockito/)
it is great
Mockito is great when used in conjunction with JUnit.

If you're using Eclipse or NetBeans, then you can use the wizards to create stub unit tests for you to help you get started.

Another useful tool is EclEmma ([http://www.eclemma.org/](http://www.eclemma.org/)) which allows you to see exactly what parts of your application get tested during your unit tests.

If you're interested in some JUnit tutorials have a look at these.  [http://www.mkyong.com/tutorials/junit-tutorials/](http://www.mkyong.com/tutorials/junit-tutorials/)

---

### Post by r-senior on 2012-02-17
> **doobrie said:**
> Another useful tool is EclEmma ([http://www.eclemma.org/](http://www.eclemma.org/)) which allows you to see exactly what parts of your application get tested during your unit tests.
Looks like a nice tool, I've used Cobertura, which integrates well with Maven, but it generates HTML reports. Never tried the [eCobertura](http://ecobertura.johoop.de/) plugin but I guess that's a similar deal.

---

