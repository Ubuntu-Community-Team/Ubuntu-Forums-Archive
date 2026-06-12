---
title: "JDK 1.4.2 and JML"
date: 2007-04-23
forum: Programming Talk
---

### Post by oled on 2007-04-23
I'm taking a curse where we are learning specifications techniques. We are using JML([http://www.cs.iastate.edu/~leavens/JML/](http://www.cs.iastate.edu/~leavens/JML/)) to test the specifications so I need to set it up on my own pc. 

The JML package requires JDK 1.4.2 and some of the scripts needs it to be installed in /usr/local/jdk1.4 

I'm new to java, (I know pascal/delphi/some .net) so I have no experience in setting up a java enviroment. Could someone help me get this working with feisty?

I trieded seaching the forums, but all jdk posts I found was how to install java 5 or 6. 

/Ole

---

### Post by phossal on 2007-04-23
You can use a tutorial like the one in my signature for manually installing Java, but instead of grabbing JDK 5 or 6, get a previous version. The only trouble with those is that they require an additional sym link to a .so library that has been upgraded. When you get that far, ask for help.

---

### Post by oled on 2007-04-23
Ok so far so good!

I think I've got it installed. 

tried to run JML without the .so sym link. And got a couple of errors! Don't know if it is related. When I launch the JML gui. I get a "Specs missing" box. "The Sourcepath or classpath set .... does not contain an existing specs directory. And then it list class and sourcepath and sourcepath is null.

Also when I try to run an java file from the console I get an "Exception in thread "main" java.lang.NoClassDefFoundError: SqrtMain/java"

/Ole

---

### Post by phossal on 2007-04-23
Post your errors, if possible.

---

### Post by oled on 2007-04-23
The errors were the specs missing and the noClassDefFound.....

The noClassDefFound errors was described in the documentation, either the classpath isn't set correct or else it contains redundant declerations of fx string. 

Where can I see/set my classpath? And where do I set the sourcepath and what shold they be? Are they global or specific for each project?

/Ole

---

