---
title: "[SOLVED] JOptionPanes always crash"
date: 2008-09-18
forum: Programming Talk
---

### Post by semitone36 on 2008-09-18
:)Hi!

This is a bit of a strange question.  Im a freshman CompSci major and Im learning Java in a programming class.  I use gedit on my laptop to write my programs.  The problem is that whenever I write a program that invoves the methods (not sure if thats the right terminology but whatever) JOptionPane.showInputDialog or JOptionPane.showMessageDialog the window that this produces always freezes and get an error message that says "**** is not responding" and I have to force quit the window to get it off my screen.

I know that there is nothing wrong with my source code because I can compile and run it just fine on other computers (using Kate)but for some reason it wont work on my laptop.  Has anyone had problems with this before? Is it a gedit bug? Any help is appreciated.:)

---

### Post by rlzyoner on 2008-09-18
Are you compiling and running from the command line ?

---

### Post by semitone36 on 2008-09-18
Yup.  I use the javac and java commands to compile/execute it.

---

### Post by xlinuks on 2008-09-18
rlzyoner probably means to post the error stack trace if any, or file a bug report.

---

### Post by semitone36 on 2008-09-18
> **xlinuks said:**
> post the error stack trace if any, or file a bug report.

Haha Ill have to remind you that Im a freshman CompSci major.  How do I do that?

---

### Post by Reiger on 2008-09-18
Running from a commandline should make it dump all errors to the shell, so just select that and copy it from your shell?

Anywho: you sure you have a JDK by SUN installed and not the GNU version (only). Because the latter one isn't fully compatible with Swing (seen other users try the same and see it break on the GNU interpreter), and at any rate it isn't nowhere near Sun's in terms of supported Java constructs.

---

### Post by semitone36 on 2008-09-18
Sorry I should have been more clear.  The error message I get doesnt appear through the terminal.  I get it when I click the close button on the window that is run from my program.  Much like when Internet Explorer freezes and when you try to x-out of it you get a message saying "internet explorer is not responding..." So i dont have a specific error to refer to. (if I understand what you are asking for)

As for my compiler I am 99% positive I am running JDK for I had specifically downloaded and installed it for my class.  Is there a command I could use to prove that JDK is my default program?

---

### Post by drubin on 2008-09-18
Post the out put of this please.
```
java -version
javac -version
```

I have never had an issue with java/JoptionPanes on linux/windows. do any other components cause issues?

**EDIT:** Highly recommend using the SUN version as well!

---

### Post by semitone36 on 2008-09-18
> **rubinboy said:**
> do any other components cause issues?

Not that I am aware of as of yet but Ive only been a "programmer" for about 3 weeks so there is plenty of time for me to find out.  Im not at my laptop at the moment but Ill post the output as soon as I get to it.

---

### Post by semitone36 on 2008-09-18
Okay so i ran the commands and you may have been right Reiger, I think Im using the GNU JDK:

***********************************************************************
travis@travis-laptop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

travis@travis-laptop:~$ javac -version
javac 1.6.0_06
***********************************************************************

How can I fix this?

---

### Post by semitone36 on 2008-09-21
Anybody?

---

### Post by drubin on 2008-09-21
Sorry for the late answer been a busy week end. 

Try this
[https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)

---

### Post by semitone36 on 2008-09-22
> **rubinboy said:**
> Sorry for the late answer been a busy week end. 


Haha same here.

Thanks so much for the link everything works just fine now!  God I love these forums!
:guitar:

---

