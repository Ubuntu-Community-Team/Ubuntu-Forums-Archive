---
title: "cannot compile java program"
date: 2012-02-25
forum: Programming Talk
---

### Post by bariamtak on 2012-02-25
I hate to ask questions but I am at lost now. i have browse the forum for 1 hour without success. 
I am planning to use ubuntu to write java programs and i have installed visualVM from software centre. But when i tired to test the java program i have written it gives the following error.
******************************************************************
bariamtak@bariamtak-pc:~$ cd Desktop
bariamtak@bariamtak-pc:~/Desktop$ javac dyninit.java
dyninit.java:7: package system does not exist
system.out.println("hypotenuse is " +c);
      ^
1 error
bariamtak@bariamtak-pc:~/Desktop$ 
*******************************************************************
I am in ubuntu 11.10. Can you please tell me i need to do.
thank you.

---

### Post by greenpeace on 2012-02-25
Hi, welcome to the forums

It looks like you have an error in your java not with your Ubuntu system: 

[http://java-error-messages.blogspot.com/2009/05/package-system-does-not-exist.html](http://java-error-messages.blogspot.com/2009/05/package-system-does-not-exist.html)

Maybe using an IDE (eg. [Eclipse]("https://help.ubuntu.com/community/EclipseIDE")) with a built in compiler might help you while you're getting started?  They can help you identify where the errors are in your code

---

### Post by 23dornot23d on 2012-02-25
Try this as this appears to be one of the packages not installed 

Type these in a terminal

**sudo apt-get install javacc**

Have you tried eclipse too

**sudo apt-get install eclipse**

---

### Post by bariamtak on 2012-02-25
thank you for repying. I'll try eclipse and get back to you.

---

### Post by benson444 on 2012-02-25
Shouldn't it be System, with a capital S? Or is that just a typo in the forum post?

---

### Post by bariamtak on 2012-02-25
Thank You benson444 .
what a silly mistake ! I am new in linux so i was quick in putting the blame on it. Sorry ma bad !

---

### Post by The Cog on 2012-02-25
Yup. Follow the link that greenpeace gave in post #2.

Moved to Programming Talk.

---

