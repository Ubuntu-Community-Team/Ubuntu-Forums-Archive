---
title: "Java Security"
date: 2007-04-30
forum: Programming Talk
---

### Post by JT673 on 2007-04-30
I'm writing an application where it can deserialize a plugin from a file, but I want to run the plugin in a sandbox environment, without compensating the application's ability to read and write files.  How can I do that?  Do you think I should just resort to JavaBeans?

A side note is that I prefer the solution to be in JDK 1.4, but beggars can't be choosers...

---

### Post by Laterix on 2007-05-01
This is a difficult thing to achieve. As far as I know there is currently no mechanism in Java that can guarantee that your plug-in doesn't do anything harmful. In fact, this would require some sort of runtime monitoring, which would prevent "illegal" method calls.

This problem is considered and studied in "science world" at the moment and there are few techniques available. Those are mostly based on automaton abstraction. I suggest that you take a look at [Polymer]("http://www.cs.princeton.edu/sip/projects/polymer/"), which is designed to work in Java environment. I'm not sure does it work with 1.4 though.

Basic idea is to inject your code with aspect-like code that captures method calls. I'm not sure that is even close what you were looking for, but I think this is one of the best solutions available at the moment.

For a short preview into the subject, I recommend to read this [science article]("http://www.cs.princeton.edu/sip/pub/polymer-pldi05.pdf") about polymer.

---

### Post by jespdj on 2007-05-01
I recommend asking such advanced Java questions on a forum about Java, not on a forum about Ubuntu.

Have a look at [http://saloon.javaranch.com](http://saloon.javaranch.com) for example.

I'm not an expert at security in Java, but I do know that you can set all kinds of permissions on pieces of code etc. Look at the [Java Security Programming Guide](http://java.sun.com/javase/6/docs/technotes/guides/security/index.html).

I don't think you need really complicated techniques like Laterix describes. I think that if you control how the plugins are loaded, with a ClassLoader, then you can set the permissions on the code via the ClassLoader.

---

