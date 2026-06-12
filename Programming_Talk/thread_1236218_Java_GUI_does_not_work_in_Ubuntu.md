---
title: "Java GUI does not work in Ubuntu"
date: 2009-08-10
forum: Programming Talk
---

### Post by casta2k on 2009-08-10
Hello everybody,

I made an application in Eclipse in Windows, which worked perfectly until I tried to use the same source code in Ubuntu. When I run it in Ubuntu, the GUI shows up, and the program works until I place the pointer on top of the program's window. When I do so, the program freezes and after a couple of seconds I get a message telling me that the program is not responding. 

The weirdest thing is that I can run it without problem by using only the keyboard, by tabbing between the buttons of the GUI. If I do so, it works without any problems, and the output is exactly what I expect it to be.

I also tried to compile it outside of Eclipse with gcj and I get the same result: It works perfectly until I place the pointer on top of the window. 

Does anybody know what the problem may be? I will post the files as .txt, because they are quite large to post here. The comments, method and variable names are in spanish, but I think that understanding how the program works is not very important to realize what the problem is. The problem should be in the class Interfaz (Interface in spanish, quite different, isn't it?).

I would appreciate if anybody could help me, thanks!

---

### Post by kpkeerthi on 2009-08-10
Try with Sun's JRE. Instructions: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

To check if Sun's JRE is configured as the default JVM for your machine, run this command:
```
java -version
```

---

### Post by casta2k on 2009-08-16
I tried running a very simple "Hello World" program and it did not work either. The problem is the same: once I place the pointer on top of the window, it freezes and then an error message appears. I will post the code so you can see the simple code. Does anybody know any similar case? Thanks

---

### Post by The Cog on 2009-08-19
It works for me. 
Maybe you forgot to put the file in the directory **start** ?
The notes in the file say it belongs in package start, so you must put HelloWorldSwing.java in a directory called start. Then compile it like this:
> javac start/HelloWorldSwing.java
and run it like this:
> java start/HelloWorldSwing

---

