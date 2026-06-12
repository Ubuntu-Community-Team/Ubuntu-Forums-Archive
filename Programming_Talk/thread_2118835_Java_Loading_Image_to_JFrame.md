---
title: "Java Loading Image to JFrame"
date: 2013-02-22
forum: Programming Talk
---

### Post by Kodeine on 2013-02-22
So I've just started playing with Java and have come to a stand still as to why such is happening. I've scoured google but still can't find any answers.

```
     Image logo1;
     try 
        {
        logo1 = ImageIO.read(new File("Images/Backdrops/Outside1.png"));
        }
     catch (IOException e) {}
     
     JLabel label = new JLabel(new ImageIcon(logo1));
     Window.getContentPane().add(label);
```
It keeps saying that 'logo1' might not have been initialized when we come to add it to the label even though it has been at the very top?

---

### Post by The Cog on 2013-02-22
I think that 'Image logo1;' declares it, without initialising it. So if the try fails, it remains ininitialised. Try 'Image logo1 = null;' at the top, and then deal with the possibility that it might still be null later.

---

### Post by Kodeine on 2013-02-22
> **The Cog said:**
> I think that 'Image logo1;' declares it, without initialising it. So if the try fails, it remains ininitialised. Try 'Image logo1 = null;' at the top, and then deal with the possibility that it might still be null later.

Ah that's it thanks!

---

### Post by Zugzwang on 2013-02-22
> **Kodeine said:**
> 
It keeps saying that 'logo1' might not have been initialized when we come to add it to the label even though it has been at the very top?

Well, what happens if image loading fails with your code? You are just gonna throw away the exception and call new ImageIcon(logo1) anyway although you are passing NULL. But what happens then? 

Exceptions are there for a reason. If you do not want to handle an Exception, at least translate it to a RuntimeException (that you do not have to declare), so it doesn't go unnoticed. Example:

```

     Image logo1;
     try 
        {
        logo1 = ImageIO.read(new File("Images/Backdrops/Outside1.png"));
        }
     catch (IOException e) {
          throw new RuntimeException("Loading of Images/Backdrops/Outside1.png failed");
     }
     
     JLabel label = new JLabel(new ImageIcon(logo1));
     Window.getContentPane().add(label);

```

You will see that the uninitialized value message will go away as well in this way.

---

### Post by slickymaster on 2013-02-22
> **Zugzwang said:**
> Well, what happens if image loading fails with your code? You are just gonna throw away the exception and call new ImageIcon(logo1) anyway although you are passing NULL. But what happens then? 

Exceptions are there for a reason. If you do not want to handle an Exception, at least translate it to a RuntimeException (that you do not have to declare), so it doesn't go unnoticed. Example:

```

     Image logo1;
     try 
        {
        logo1 = ImageIO.read(new File("Images/Backdrops/Outside1.png"));
        }
     catch (IOException e) {
          throw new RuntimeException("Loading of Images/Backdrops/Outside1.png failed");
     }
     
     JLabel label = new JLabel(new ImageIcon(logo1));
     Window.getContentPane().add(label);

```

You will see that the uninitialized value message will go away as well in this way.

In all cases the OP should always take in consideration that RuntimeExceptions identify _**programmatically recoverable problems**_ which are caused by faults in code flow.

IMHO, when developing, one should not fix them by catching them, but by writing proper code and making use of flow control statements like **if/else**, **switch**, **while**, **for**, etc.

---

### Post by Zugzwang on 2013-02-22
> **slickymaster said:**
> In all cases the OP should always take in consideration that RuntimeExceptions identify _**programmatically recoverable problems**_ which are caused by faults in code flow.


It's a sure thing that proper exception handling is the way to go in practice. Yet, the OP clearly demonstrated that he/she is unwilling of writing exception handling code in this case. Probably it's just some testing code? Throwing a RuntimeException is still a lot better than just eating up the exception, as no problem with the code will be masked that way.

Can you give a reference to the idea that a RuntimeException should represent a programmatically recoverable problem?
The Java Tutorial states that "Runtime exceptions represent problems that are the result of a programming problem, and as such, the API client code cannot reasonably be expected to recover from them or to handle them in any way." ([http://docs.oracle.com/javase/tutorial/essential/exceptions/runtime.html](http://docs.oracle.com/javase/tutorial/essential/exceptions/runtime.html)). One could easily argue that the absense of proper exception handling is a programming problem.

---

### Post by slickymaster on 2013-02-25
> **Zugzwang said:**
> Probably it's just some testing code? Throwing a RuntimeException is still a lot better than just eating up the exception, as no problem with the code will be masked that way.

Completely agree with you.

> **Zugzwang said:**
> Can you give a reference to the idea that a RuntimeException should represent a programmatically recoverable problem?
The Java Tutorial states that "Runtime exceptions represent problems that are the result of a programming problem, and as such, the API client code cannot reasonably be expected to recover from them or to handle them in any way." ([http://docs.oracle.com/javase/tutorial/essential/exceptions/runtime.html](http://docs.oracle.com/javase/tutorial/essential/exceptions/runtime.html)). One could easily argue that the absense of proper exception handling is a programming problem.

**RuntimeExceptions** are a special kind of exceptions, they are unchecked exceptions.
Referencing [javapractices.com]("http://www.javapractices.com/topic/TopicAction.do?Id=129"):
> _Unchecked exceptions:_
[LIST]
[*]represent defects in the program (bugs) - often invalid arguments passed to a non-private method. To quote from The Java Programming Language, by Gosling, Arnold, and Holmes : "Unchecked runtime exceptions represent conditions that, generally speaking, reflect errors in your program's logic and cannot be reasonably recovered from at run time."
[*]are subclasses of *RuntimeException*, and are usually implemented using *IllegalArgumentException*, *NullPointerException*, or *IllegalStateException*
[*]a method is not obliged to establish a policy for the unchecked exceptions thrown by its implementation (and they almost always do not do so)
[/LIST]
_Checked exceptions:_
[LIST]
[*]represent invalid conditions in areas outside the immediate control of the program (invalid user input, database problems, network outages, absent files)
[*]are subclasses of *Exception*
[*]a method is obliged to establish a policy for all checked exceptions thrown by its implementation (either pass the checked exception further up the stack, or handle it somehow)
[/LIST]

Basically what I was saying is that RuntimeExceptions should identify programmatically recoverable problems which are caused by faults in code flow or configuration (read: developer's faults) contrary to  Checked Exceptions that should identify programmatically recoverable problems which are caused by unexpected conditions outside control of code (e.g. database down, file I/O error, wrong enduser input, etc).

---

### Post by r-senior on 2013-02-25
The original intent was that unchecked exceptions would represent unexpected conditions, often programming errors, that should ripple up to the top of the application and cause an abort and stack trace, e.g. ClassCastException. Checked exceptions, on the other hand, were designed to represent more specific conditions that the calling code could reasonably be expected recover from. e.g. by displaying an error message for a FileNotFoundException.

In practice, checked exceptions can cause problems in a multi-tiered application architecture, e.g. a web application or web service. While they can be caught and re-thrown inside a wrapping exception, there is a great temptation in mid layers to log and consume or consume silently because it's not clear what the response to the condition should be at that level. Even if catch and rewrap is done properly, it creates coupling between layers because the enforced try-catch blocks reference specific exception classes from the lower tier.

The alternative approach of re-throwing checked exceptions in an unchecked wrapper (as illustrated above by Zugzwang) provides a choice in the mid layers of a multi-tiered application with regard to catching exceptions. Apart from reducing non-value-adding clutter it has the added benefit of reducing coupling between those layers.

The Spring framework for example, ignores the original guidance on the use of the different types of exception and converts all checked exceptions to unchecked in the lower layers of an application, e.g. DAO template classes wrap SQLException and HibernateException with unchecked DataAccessException subclasses. Mid layers then have the choice of whether to catch or silently ignore exceptions. A typical mid layer service class in a Spring application doesn't have any try-catch blocks and therefore no dependency on exceptions coming from lower tiers. Spring transactions automatically roll back on unchecked exceptions and the exception itself ripples up to the web tier or web service which can choose to handle it and report the error or let the container deal with it.

The way I see it is that the original guidance on exceptions was written without a crystal ball to see how they would work in practical situations. Checked exceptions have their place and work well in smaller applications, but expanding the use of unchecked has its advantages in tiered applications. What's important is to understand the differences and apply them as required to a particular architecture.

---

