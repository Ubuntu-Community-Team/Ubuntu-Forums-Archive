---
title: "I get lost at theJava API"
date: 2008-06-08
forum: Programming Talk
---

### Post by babacan on 2008-06-08
Hello,
As a beginner/intermediate level Java developer, I find the java API pretty confusing, I simply get lost at the left frame when I enter the [java api website]("http://java.sun.com/j2se/1.5.0/docs/api/") and try to find whatever I want. For instance when I want to find the related API for manipulating a string, I really cant see anything.


How do you experienced java developers handle in order to find whatever you want to find ? Any related source that helps ? I really need some enlightment :)

Cheers

---

### Post by Shin_Gouki2501 on 2008-06-08
Well since Java is Object oriented all Objects exist in a certain Hierarchy.

If you look for a "certain" problem you have to find the class which relates to the Problem.

For "String"-Manipulation that would be java.lang.String.
You will find that class in the left sided Frame after searching like 5-6 times. (only as "String" described)

Hope that helps :)

---

### Post by mike_g on 2008-06-08
Personally, I would create an instance of a string then put a dot after it and see what methods the netbeans code completion comes up with and read the docs on anything that looks like what I am trying to do. Netbeans rocks :)

---

### Post by Shin_Gouki2501 on 2008-06-08
i guess ... he don't use an IDE :P
I prefer eclipse but i heard good stuff about netbeans 6.1

---

### Post by Quikee on 2008-06-08
Also.. if you vaguely know in which category the searching item belongs you can just select in the top left. Most useful basic stuff is in java.lang, java.util and maybe also java.io / java.nio and java.text so you can quickly shrink to only a few classes.

As already said.. in a IDE such as Eclipse or NetBeans searching through class libraries is much easier.

---

### Post by NormR2 on 2008-06-08
I found "The Java Class Libraries" by Chan, Lee and Kramer an excellent reference book for understanding how to use classes and methods. its full or examples for ALL the classes and most of the methods.
Once you know what class to use, then using the API doc is much easier.

---

### Post by babacan on 2008-06-08
Thanks for all the suggestions :)
> **NormR2 said:**
> I found "The Java Class Libraries" by Chan, Lee and Kramer an excellent reference book for understanding how to use classes and methods. its full or examples for ALL the classes and most of the methods.
Once you know what class to use, then using the API doc is much easier.

Do you refer to [this]("http://www.amazon.com/Java-Class-Libraries-java-applet-java-beans/dp/0201310031") book? , it looks abit old (1997)

---

### Post by NormR2 on 2008-06-08
Yes, that's about when I learned java. I still use it for the non-GUI classes. The book you linked to is Volume 2, I was refering to Volume 1.
Before you try to use Sun's java API for reference, you should read a good textbook or the tutorial so you have some ideas on what packages and classes to use to write a program. The API is for looking up syntax and a little usage, but it expects that you already know something about the package and classes.

---

### Post by descendency on 2008-06-08
I'm not a java programmer. I have java programmed in the past, but the advise seems to be universal.

Often what I do when I need to know or be reminded of a class that does something I type what I want into google followed by "Java" or whatever language I need. 

When browsing the results, I tend to go towards API listings (such as the one provided) if there are any.

---

### Post by Jimmay on 2008-06-08
I just use the java tutorial ([http://java.sun.com/docs/books/tutorial/index.html](http://java.sun.com/docs/books/tutorial/index.html)) when I want to use something I'm not sure on. I've also got two reference books from O'Reilly (Java in a nutshell & Java foundation classes in a nutshell) which really help; they've got examples showing how to do stuff (java in a nutshell has some good stuff on string manipulation) and a reference at the back showing the methods of classes and stuff. Together they cover pretty much everything I use.

---

### Post by pmasiar on 2008-06-09
Java API is so vast and byzantine complex (why we need 60+ file-like classes?) that IMHO it is impossible to "know" by mere humans. Everyone I know uses some printed reference - and a lot of googling around. After 10 years, maybe, but not any sooner.

[http://www.java2s.com](http://www.java2s.com) is excellent website with examples of code - we need more of those. There are many forums like [http://www.javaranch.com/](http://www.javaranch.com/) - because they are needed. Problem with those forums is, many times Google can find you someone who asked same question like you have, and it is without the answer. People who know the answers do not waste time there...

Also, Apache Commons has good tools which should have in Java from the very beginning if API was designed by someone more skilled than cheap summer interns - but it is too late now. :-( So what you need is some local Java guru you can ask for help - or beg online. IDE could help you when you know the class name, but how to find that name? 

I am slowly getting used to idea that being lost in Java API is normal status for first 10 years of using Java, sadly. And creating my own library of snippets of solutions which worked for me.

---

### Post by Shin_Gouki2501 on 2008-06-09
I like Java2s, especially regarding SWT or Jface resources!

---

### Post by Woei on 2008-06-09
I recommend you install an IDE like NetBeans, Eclipse, or (my favorite) IntelliJ IDEA. Make sure that in each IDE you attach the sources and the Javadoc documentation to the rt.jar file, which contains the standard java.* and javax.* API. After you've done you can read the JavaDoc documentation about every method that's available on a certain variable.

Say you have something like this:

```

JFrame f = new JFrame("foo");
f.

```

After typing f., your IDE should open up a scrolldown list of possible method and member completions. Take your time to look at each method, reading its documentation if you're not 100% sure what they're supposed to do and making little test programs to find out what the common way is to achieve feature X or Y. Inline documentation for each method in your IDE is a **great** way to quickly learn an API.

Also, you haven't said *what* part of the Java API you're having trouble with grokking. One user responded about why there are lots of classes to do file I/O. Yes, for the uninitiated, it's pretty confusing on why there's InputReaders and Writers, BufferedReaders, OutputStreams, PipedReaders, etc. But once you understand that one should chain these classes together to achieve a goal none of these classes can attain on its own you see the beauty of the system. The I/O classes are an example of the [decorator design pattern]("http://en.wikipedia.org/wiki/Decorator_pattern").

Similarly, in graphical development, it's important you understand the base classes: Component and JComponent and their properties.  They're the top classes in the Swing system from which all GUI components are derived. They're also generic handles one can use to traverse and compose a part-whole relationship frequently used in Swing GUIs (again, an implementation of the [Composite pattern]("http://en.wikipedia.org/wiki/Composite_pattern")). The way Event dispatching is performed in Swing is also something you just have to grok. For any event, say an event that encapsulates a mouse click, there are at least three and sometimes more objects cooperating. You attach a MouseListener to a Component. Said Component *fires* a MouseEvent whenever it detects a click.  Listeners are attached with addXYZListener(XYZListener) and removed with removeXYZListener(XYZListener). This is an implementation of the [observer pattern](http://en.wikipedia.org/wiki/Observer_pattern).

The way JTables, JLists and JComboBoxes work is also something you just have to see in action in someone else's code to appreciate. A JComboBox is actually a fairly dumb class that only strings its model, renderers (and if it were editable, editors) together. You could see an implementation of the [mediator pattern](http://en.wikipedia.org/wiki/Mediator_pattern) in it. The model stores some information (strings, ints, complex user-defined objects) and a renderer you write to interpret said model items is supplied with it to your JComboBox.  That way, JComboBox can be reused, whether you have a model containing books with pictures or just plain ints. Similarly, the way a model is visualized is easily changed without touching the model or the JComboBox by supplying a different renderer (which implements ListCellRenderer). The latter is an example of the [Strategy pattern](http://en.wikipedia.org/wiki/Strategy_pattern).

For EJB development, you should also look at the general compositions of the classes rather than looking at all the different methods in isolation. When tackling EJB, you should understand what it's trying to solve: fixing the object/relational impedance mismatch. It does this through something called Entity Beans, which are usually kept at the server and fronted by a Session Facade, which, for any given method, can span operations on one or more tables and table rows ([Facade](http://en.wikipedia.org/wiki/Facade_pattern)). In a Java web-application, you'd have some view technology (plain JSPs, Velocity, or a component framework like Swing with JSF) that talks to a Controller (the Session Facades) which does some magic to the underlying Model (the Entity Beans). The EJB standard and all of its companion standards is huge. You only need to understand the key parts to get going, however. Once you run into something you can't fix with the core pieces, you can sit back and look in all of the other APIs for a way that can help you achieve your goal.

I hope it's clear by now that to learn an OO-API, you should invest in learning the classic design patterns (google for the Gang of Four book). Once you have some programming experience and while learning an API, you can readily apply these patterns to the classes you're studying: "Oh, this listener, event object and these methods on this class are just infrastructure to implement the observer pattern. I should treat them as one whole." "Hmm, there should be a way to add behavior to an Object without having to subclass it. Great, it implements an interface. I can implement that interface too, compose the object being enhanced inside of me and just delegate the calls I'm not interested in to said object while doing my thing on the methods I am interested in."

You should also understand that Java is a type-safe language. Yes, there are lots of classes and interfaces, but all these classes and interfaces allow you to better describe your intent to fellow programmers and work with them in a team. If it's just you alone behind your computer banging out code, then yes, Java's API is a bit verbose. However, verbosity, type safety and clean, extensible architecture helps tenfold once you're in a group of programmers trying to achieve a certain goal.

Finally, there are lots of great books about the various APIs used in Java. I can highly recommend the 'monkey' O'reilly book "Java Swing" if you're interested in understanding just how that huge Swing API *fits together*. Of course one doesn't know all the minute details about a method or field of a certain class in this API. Such "freak" knowledge comes over time when using an API daily. The important bit is that you understand how everything relates to each other: for example, how you can do custom painting or even go wild by implementing your own UI delegates through composition.

So, to summarize my rant: learn the classic design patterns, look for them in an API you're studying, install an IDE which allows you to view documentation inline for each method and class and allows you to view the source of the core Java APIs. Don't be shy to search for and buy a book about an API you're confused about. If you're cheap, just look the net for articles describing common practices on how to achieve something. Quick answers can be great, but it's far better if you find articles describing the composition and the intent of an API rather than just how to achieve feature X or Y.

---

