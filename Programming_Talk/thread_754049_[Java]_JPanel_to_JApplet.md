---
title: "[Java] JPanel to JApplet"
date: 2008-04-13
forum: Programming Talk
---

### Post by TreeFinger on 2008-04-13
Another java question from me. What a surprise.

I am working on a program that is suppose to be a Java Applet. Currently I have 3 files that are part of the program and none of them are Applets. 

Is there an easy way to make my program into an applet? I utilize a JPanel in the program.. I don't know if that is a problem.

---

### Post by bovus on 2008-04-13
To use an applet, dont use a main function (thats the main difference I've noticed).  instread, have your class extend JApplet and implement the functuion 'public void init()'. In there you put all the components needed (buttons, textboxes, ect.)

---

### Post by bovus on 2008-04-13
oh yea, and to display the applet in a web page, use the hml tag <applet>, like:
```

<applet
	code	= "MyClass.class"
	width	= "800"
	height	= "700"
	>
</applet>

```

---

### Post by TreeFinger on 2008-04-13
I've created an applet before but I am wondering if there is an easy way to convert a program to an applet? I'm using multiple classes and a JPanel to draw some graphic objects..

I guess I'm just going to re-write the program in applet form without utilizing objects..

---

### Post by Zugzwang on 2008-04-14
> **TreeFinger said:**
> I guess I'm just going to re-write the program in applet form without utilizing objects..

No, no! Just separate your program logic:
[LIST]
[*]Have one starting class using "void main(String[] args)" and a window class
[*]Additionally, derive an Applet class for applet loading
[*]Both will do nothing but instantiate a derived JPanel (which contains the rest of your application) and add it to the applet or window .
[/LIST]

In both cases, you can use objects in the same way.

This way you get two versions of your program: One as classical program and one as applet.

---

