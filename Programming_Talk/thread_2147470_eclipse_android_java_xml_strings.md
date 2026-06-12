---
title: "eclipse android java xml strings"
date: 2013-05-22
forum: Programming Talk
---

### Post by aspidistra on 2013-05-22
in just a simple "hello world" example

the string "hello world" is contained in an xml file "strings"

this seems overly complex .. why isn't "hello world" in the program code (say main is it?)

I just don't understand why.  Is it because strings may be different (unicode) between devices?

also anyone know any fast track tutorials for java/eclipse/android .... many tutorials out
there are far too ponderous for my tastes -- need stuff that gets right to core issues fast

---

### Post by kunal00731 on 2013-05-22
That's just how the android frame work is organized. I understand you have gone through the android developers forum stated "Hello World" tutorial. The String.xml as you have mentioned is the one which contains all the strings to be used by your main class. You can add a lot of things here, like button-id etc.

> [COLOR=#000000]also anyone know any fast track tutorials for java/eclipse/android .... many tutorials out[/COLOR]
[COLOR=#000000]there are far too ponderous for my tastes -- need stuff that gets right to core issues fast[/COLOR]

I had gone through some tutorials for android, but the one which was most effective was the one which MyKong publishes. His blog contains chapter by chapter explanations with a how to do approach.

Probably, you can give that a twirl : [http://www.mkyong.com/tutorials/android-tutorial/](http://www.mkyong.com/tutorials/android-tutorial/)

---

### Post by aspidistra on 2013-05-22
thanks

right away I see a plainer "hello world" than other tutorials
it's not just a few lines of code with android

---

### Post by KdotJ on 2013-05-22
> **aspidistra said:**
> 
this seems overly complex .. why isn't "hello world" in the program code (say main is it?)



If you think about it, it's actually a very good idea.

What happens if you want to release this app in another country which speaks a different language? If your Strings are hard coded in the Java classes, then you would have to change them all and rebuild your app specifically for each country. 

By using an xml file with the Strings in, you can have a different xml for each language. You can now easily deploy your app in different languages without ever having to change the Java code.

---

### Post by ofnuts on 2013-05-23
Because in the real world people speak different languages... If you put strings in the code you need a version of the program for each language, by "externalizing" them you just need to have the program pick the right file (or part of file) when it starts.  This also lets you get the string produced/edited by a translator who isn't a programmer.

---

### Post by fct on 2013-05-23
Consider also that it is always better to have "Continue" written once in an XML file than dozens of times in several .java files, possibly with different typos. What if you want to change it to "Skip"? Edit the XML entry once vs. search and edit through the java code.

---

