---
title: "Eclipse and Code Completion"
date: 2006-11-28
forum: Programming Talk
---

### Post by rvickers on 2006-11-28
Has anyone had success getting Eclipse to work with c++ code completion?
Thx

---

### Post by JeffS on 2006-11-28
I know I'm not being much help but ...

I've had little success with many Eclipse plug-ins.  In particular, WTP has been very problematic.  I tried the C++ plugin, and it worked OK, but it did not seem all features that are normal with the Java dev environment were fully supported.  Also, many Eclipse plug-ins can be buggy and/or poorly documented.

For me, Eclipse is good for basic Java, and Eclipse RCP development (what's installed with the standard Eclipse SDK).  Beyond that, it is a crapshoot.  That said, there are Eclipse based IDE's out there, like BEA's WebLogic Workshop, MyEclipse, etc, that are commercial, but work very well and are full featured.

Seeing as how you are attempting C++ development, I highly recommend Anjuta, since you are (presumably) doing this on Ubuntu.  Anjuta is fully supported on Ubuntu/Gnome, and it's a great C/C++/GTK/Gnome IDE (although you don't have to use it to do GTK work).

---

### Post by rvickers on 2006-11-28
Just downloaded Anjuta and it looks nice, the auto complete is what I was looking for. Very easy to configure also.
Thx:D

---

### Post by dubrict on 2007-04-27
I can't get code completion to work right in anjuta... for example if create a list a, when I start typing "a.p" I would expect it to give me a little box with possible functions to call.  It doesn't, but if I press control+enter it lists some functions that have nothing to do with the list class, but start with p.

It does work in Eclipse for me, but there's about a 5 second delay every time.

---

### Post by dori on 2007-04-27
I use Eclipse for qt4 development in c++ and it works great with code completion. It was too slow until I made Eclipse run on sun java6 not gcj. It will only get better when Trolltech will release Eclipse qt integration which will be soon.

---

### Post by dubrict on 2007-04-27
thanks for the tip.... but how do you do that?

---

### Post by dubrict on 2007-04-27
okay I figured it out, but it's still really slow for me... :(

---

### Post by dori on 2007-04-27
Are you sure your using sun java6? If you installed Eclipse from repos then you have to edit the /etc/eclipse/JAVA_HOME file to point to your java install dir

---

### Post by azntfl on 2007-06-30
Anyone able to fix the slowwwwwww Code Completion?

---

### Post by kingmanowar on 2007-07-02
Anyone tried the new CDT 4.0 ? It seems really good, it has just been released, loads of things have improved (speed of code completion is one of them).
I am planning to install it soon, but I would like to have some feedback from people who already tried it.

Thanks

---

### Post by LucioC on 2008-05-06
Hi!

2 weeks ago I updated to Ubuntu 8.04. Since that time Eclipse with CDT is running very slow. The code completion lasts about 20 seconds, for that time I can hardly use my entire system. If I try to delete a line with the backspace button, Eclipse is so slow, that if I release this button, it goes on with deleting. :confused:

Is there any recent solution to this problem? I've installed Sun's Java 6. I also edited the eclipse.ini, so Eclipse has enough memory.

Thank you,

Michael


My system: Athlon X2 3800+, 2GB Mem, Ubuntu Hardy 32bit

---

### Post by samjh on 2008-05-06
Wow, this thread has been revived... twice! :p  Talk about thread necromancy!

Check whether you're actually running Sun's Java instead of gcj.

What does```
java -version
```say?  If it says Sun Java... then you've got the right one.

If it says you're using some type of gcj, then you need to:```
sudo update-alternatives --config java
```and choose Sun Java.

Other than that, all I can suggest is to try reinstalling both Eclipse and Java. :(

---

