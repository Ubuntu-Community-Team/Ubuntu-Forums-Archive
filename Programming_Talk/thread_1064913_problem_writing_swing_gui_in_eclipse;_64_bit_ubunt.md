---
title: "problem writing swing gui in eclipse; 64 bit ubuntu"
date: 2009-02-09
forum: Programming Talk
---

### Post by badperson on 2009-02-09
Hi,

I recently upgraded to the 64 bit version of ubuntu 8.10. I had heard there were some issues in Eclipse with 64 bit ubuntu. 

I did something really simple, just created a JFrame and made it visible...it opens up fine, but I have to force close it, 

If i hit the red arrow in Eclipse, it stops running ok, 
but this
```
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
```
doesn't seem to be working the way it normally does for me.

I set the compiler to 6.0.
when I launch the app from the command line, it closes ok, so I guess it's not that big of a deal, but has anyone else run into that? 


thanks, 
bp

---

### Post by Reiger on 2009-02-09
That's odd... Are you sure Eclipse is actually _using_ the Java 6 SDK of SUNs? ;)

---

### Post by badperson on 2009-02-09
how would I add this jvm

/usr/lib/jvm/java-6-openjdk/jre/lib/amd64

to my build path in eclipse?
bp

---

### Post by drubin on 2009-02-09
Install the Sun version of java.
```
sudo apt-get install sun-java6-jdk
```

Then run 
```
sudo  update-alternatives  --config java
```

I highly recommend it for 64 bit with gui.

---

### Post by myrtle1908 on 2009-02-09
You'll have a much better time with Swing if you use NetBeans.  I use Eclipse every day for my work but for Swing I'd go NetBeans every time.

$0.02

---

### Post by badperson on 2009-02-09
probably a good idea...I've never used netbeans, but I suppose I should learn. 

I use eclipse because that's what I know...but I know netbeans has a lot of drag and drop type of stuff you can do for gui's; right? 


thanks, 
bp

---

### Post by myrtle1908 on 2009-02-09
> **badperson said:**
> but I know netbeans has a lot of drag and drop type of stuff you can do for gui's; right?

Correct.  It makes creating Swing GUIs very easy.  There's also some wizards that start you off with menus, status bar etc.

---

### Post by jespdj on 2009-02-10
> **badperson said:**
> ... I had heard there were some issues in Eclipse with 64 bit ubuntu.
Do you have more information about what issues there are with Eclipse on 64-bit Ubuntu?

I'm using Eclipse 3.4 on 64-bit Ubuntu 8.04 and I've never encountered any strange issues; it works normally. I'm using the Eclipse 3.4 for 64-bit Linux package that I've downloaded from the Eclipse website (I'm not using Eclipse from the Ubuntu repository, because that's an old version).

NetBeans is also a very nice IDE, especially for Swing applications; it has a good [GUI builder](http://www.netbeans.org/features/java/swing.html) which Eclipse unfortunately lacks (out-of-the-box). Download NetBeans 6.5 from the [NetBeans website](http://www.netbeans.org), because like with Eclipse, the version in the Ubuntu repo's is unfortunately outdated.

---

### Post by drubin on 2009-02-10
> **jespdj said:**
> 
I'm using Eclipse 3.4 on 64-bit Ubuntu 8.04 and I've never encountered any strange issues; it works normally. I'm using the Eclipse 3.4 for 64-bit Linux package that I've downloaded from the Eclipse website (I'm not using Eclipse from the Ubuntu repository, because that's an old version).


Is this with openjdk or sun java?

---

### Post by jespdj on 2009-02-10
It runs fine with both OpenJDK and with Sun Java.

---

