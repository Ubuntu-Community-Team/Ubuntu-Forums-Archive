---
title: "Java 1.6 swing events freeze during debug"
date: 2009-02-11
forum: Programming Talk
---

### Post by Tanked on 2009-02-11
I was just wondering if anyone is having issues debugging java swing applications.  With java 1.5 I had no problems, now that we are in 1.6_11, when I debug a swing application the X display completely freezes and I have to kill the debugging app (intellij or eclipse).  I did hear something about 1.6_12 that fixed a combo box issue but 1.6_12 has issues as well.  Has anyone else had issues with the X display freezing?


NOTE: these are the sun jvms.

---

### Post by cl333r on 2009-02-11
The X display? Or you just mean the window?
Are you sure you tested your code enough with and without separate threads like the following?
```

final JFrame win = ...;
SwingUtilities.invokeLater( new Runnable() {
public void run() {
win.setVisible(true);
}
});

```

---

### Post by Tanked on 2009-02-11
No, it does not have anything to do with a java window, its not an internal design/coding flaw. Its freezing the X display completely, can't click on another window (i.e. terminal, mail application, etc.).  I take the jar I am using, launch it with java 1.5 and debug it, fine.  I take the jar I am using, launch it with java 1.6 and debug it, to get access to any application on my desktop I have to kill the process I am debugging then my desktop can be used.

---

### Post by cl333r on 2009-02-11
Since you're sure it must be Java's fault I can only suggest you report this issue as a bug to Sun Microsystems.
Since Sun cares a lot more about its own IDE (NetBeans) try also testing your code on NetBeans 6.5

---

### Post by Tanked on 2009-02-11
I would agree, but it doesn't happen on other platforms, just ubuntu.  Thought I would check here first in case anyone else has had this issue.

---

### Post by tfasanga on 2009-02-20
I have the same issue with java 6 (from update 7 to 12) and Ubuntu (Gnome, 64-bit, 8.04).

---

### Post by mebigfatguy on 2009-12-22
this just happened to me with 1.6.0_17 on Karmic setting break points in an JComboBox ItemListener. Everything locked up

maybe related to this: [http://bugs.sun.com/view_bug.do?bug_id=6384219](http://bugs.sun.com/view_bug.do?bug_id=6384219)

also see

[http://wiki.netbeans.org/wiki/view/FaqDebuggingAWTXWindows](http://wiki.netbeans.org/wiki/view/FaqDebuggingAWTXWindows)


i am using eclipse 3.5

---

### Post by cawo on 2010-04-29
Found a workaround:  Add the following to your VM parameters:

 [FONT=Courier New]-Dsun.awt.disablegrab=true[/FONT]

found here: [http://bugs.sun.com/view_bug.do?bug_id=6714678](http://bugs.sun.com/view_bug.do?bug_id=6714678)

Works for me.

---

### Post by alanmehio on 2011-01-16
> **cawo said:**
> Found a workaround:  Add the following to your VM parameters:

 [FONT=Courier New]-Dsun.awt.disablegrab=true[/FONT]

found here: [http://bugs.sun.com/view_bug.do?bug_id=6714678](http://bugs.sun.com/view_bug.do?bug_id=6714678)

Works for me.

Actually I tried debug the a simple Swing application with event handling for JComboBox with the above jvm paramteter. Still the same problem 

The desktop freezes just dead. the  the following  java version 
OpenJDK Runtime Environment (IcedTea6 1.9.2) (6b20-1.9.2-0ubuntu1~10.04.1)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)

Hope there is a solution for this problem

---

### Post by clpineda on 2011-03-23
The same behavior with:
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)
Ubuntu 10.10

---

### Post by yurx cherio on 2011-03-31
I am getting the same problem. It freezes as soon as it stops at a breakpoint.
Java 1.6.0.24
Eclipse 3.6
Ubuntu 10.10 amd64

Update: using "-Dsun.awt.disablegrab=true" did the trick. I added this argument to my project launch configuration and the debugging is back. Feels like voodoo.

---

### Post by valenajarro on 2011-06-10
Thanks pals! The workaround solved the problem for me on 32-bit Ubuntu 11.04 & NetBeans 6.9

---

### Post by alanmehio on 2011-08-05
adding [FONT=Courier New]-Dsun.awt.disablegrab=true  to the JVM argument; it works very nice and fine now.   

:KS
[/FONT]

---

### Post by svaens on 2013-01-18
> **cawo said:**
> Found a workaround:  Add the following to your VM parameters:

 [FONT=Courier New]-Dsun.awt.disablegrab=true[/FONT]

found here: [http://bugs.sun.com/view_bug.do?bug_id=6714678](http://bugs.sun.com/view_bug.do?bug_id=6714678)

Works for me.
fixed it for me! 
Thanks very much. 

Though, I would have thought this is somehow a 'linux' bug, as it apparently doesn't happen on any other platforms (and Java or any other program shouldn't be able to freeze X so thoroughly, for any reason). Would be nice to know if one of the developers are taking this seriously...

---

