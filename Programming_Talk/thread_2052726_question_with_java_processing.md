---
title: "question with java processing"
date: 2012-09-03
forum: Programming Talk
---

### Post by flyingsliverfin on 2012-09-03
I was trying to run a small java program I wrote a while ago (on windows on a different computer). I have it as .java source. The problem is that it relies on processing ([www.processing.org](www.processing.org)) to do most of its work.
If i remember correctly, when I made it I had to do some mess with netbeans to get it to compile using processing. How do I compile this from bash? (I have the processing tar extracted, but I don't know how to use it)

On a side note, I just downloaded the new java 7 from java.com/downloads. Is that different from the java that gets used when I run "javac" in bash?

---

### Post by spjackson on 2012-09-04
The version of java you get when you type javac in bash depends on what you installed.
```
javac -version
```will answer the question.

What do you need to do to use Processing? Well, I don't know. Normally to compile something from bash you'd do something like this:
```

javac -cp /path/to/processing.jar:/any/other/paths/to/jars MyClass.java

```If you had the Netbeans project file, you could possibly install Netbeans and use that, except that you'd probably need to change Windows paths to Linux paths.

[Getting Started]("http://www.processing.org/learning/gettingstarted/") takes you through the Processing Development Environment. I couldn't find how to compile code from the command line within a few minutes. Ah, there's an [Eclipse tutorial]("http://www.processing.org/learning/eclipse/") and I think that you can extract from that the information you need. If I'm reading it right, it'll be:
```

javac -cp /path/to/processing/Contents/Resources/java/core.jar MyClass.java

```This all assumes, of course, that the version of Processing you used to write the application is essentially compatible with what's current.

---

### Post by Damascushead on 2012-09-09
I use both Processing and Java. I haven't done what you are talking about, but I know that Processing is just a language that is really formed from java interfaces and classes, so you are pretty much writing a higher level of java when writing Processing code. 

You should try just using **javac** to compile the Processing code, **java** to run and see what happens.

---

### Post by flyingsliverfin on 2012-09-09
thanks to both for the responses

---

