---
title: "This java method is misterious can somebody explain it please."
date: 2010-12-03
forum: Programming Talk
---

### Post by hoboy on 2010-12-03
was reading  this code:
context.addRoutes(new RouteBuilder() {
     public void configure() {
          from("test-jms:queue:test.queue").to("file://test");
            // set up a listener on the file component
           from("file://test").process(new Processor() {
               public void process(Exchange e) {
                   System.out.println("Received exchange: " + e.getIn());
                 }
              });
           }
         });
at [http://camel.apache.org/manual/camel-manual-2.5.0.pdf](http://camel.apache.org/manual/camel-manual-2.5.0.pdf)
my confusion is that context.addRoute() is a method call on the object context, how is it posible to declare public void configure() method inside method call ?

---

### Post by endotherm on 2010-12-03
its an inline method declaration. this syntax is most commonly used for ["Anonymous Classes / Methods"]("http://www.developer.com/java/other/article.php/3300881"). anonymous members are useful when you will never want to refer to a member outside of the current context, but need to provide dynamic evaluation of an expression. this is particular useful for event based programming.

---

### Post by TennTux on 2010-12-03
I'm not sure how new to Java you are so here is a simplified breakdown of what hoboy was saying. :)

I java you can write a class as
```
class DoIt {
  public void run() { System.out.println("I am here") ; }
}
```

You can also extend a class or implement an interface as in the following
```
class DoIt implements Runnable {
  public void run() { System.out.println("I am now here") ; }
}
```

There is a method "EventQueue.invokeLater(yyy);" that takes an instance of a class that implements Runnable. Rather than go to the full effort of writing a completely separate class it is possible to provide the class at the point you use it provided you don't need any other references to it.

Hence the final example.
```
EventQueue.invokeLater(new Runnable() {
  public void run() { System.out.println("This is it.") ; }
}
```

---

### Post by hoboy on 2010-12-03
> **TennTux said:**
> I'm not sure how new to Java you are so here is a simplified breakdown of what hoboy was saying. :)

I java you can write a class as
```
class DoIt {
  public void run() { System.out.println("I am here") ; }
}
```

You can also extend a class or implement an interface as in the following
```
class DoIt implements Runnable {
  public void run() { System.out.println("I am now here") ; }
}
```

There is a method "EventQueue.invokeLater(yyy);" that takes an instance of a class that implements Runnable. Rather than go to the full effort of writing a completely separate class it is possible to provide the class at the point you use it provided you don't need any other references to it.

Hence the final example.
```
EventQueue.invokeLater(new Runnable() {
  public void run() { System.out.println("This is it.") ; }
}
```

Thanks to all of you who try to explain it.

---

### Post by endotherm on 2010-12-03
> **hoboy said:**
> Thanks to all of you who try to explain it.
it's an advanced concept. I'd recommend you just use it for now, and worry about understanding the details a little later. someday soon, you'll see somthing like it, and the concept will just "click" for you. I had the same experience a dozen times over.

---

### Post by CptPicard on 2010-12-03
Anonymous inner classes are about the best feature Java has.

They allow  you to just provide an ad hoc implementation of whichever type is required at the given location. Modern IDEs will then allow you to crack out these implementations into actual classes as needed.

A further implication of them is that they can almost act the way lambdas in functional languages do -- with a certain wrapper-reference trick you can make them behave as closures, which Java does not natively have (due to a stupid comittee decision, there is no REAL reason).

From this, it follows that they can nearly serve as constructors as per the functional-programmming OOP paradigm. In this case it is of course senseful to consider whether it actually *is* a class you should be constructing explicitly.

---

