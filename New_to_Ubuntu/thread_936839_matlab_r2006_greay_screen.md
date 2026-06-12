---
title: "matlab r2006 greay screen"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by antonio_ing on 2008-10-03
Hi guys

I have just installed ubuntu 8.04 in my toshiba satellite laptop. I have also installed matlab R2006a but when I start from the launcher the terminal shows this:

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5cb4767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb5cb48b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb5f801bd]
#3 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1eae26a]
#4 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1e94352]
#5 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1e94599]
#6 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa1e947a4]
#7 [0xae5b1b7a]
#8 [0xae5aba7b]
#9 [0xae5aba7b]
#10 [0xae5a9157]
#11 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb32038ec]
#12 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb32f2378]
#13 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb320371f]
#14 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb325bebb]
#15 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb37f62cd]
#16 [0xae5b142b]
#17 [0xae5ab9a4]
#18 [0xae5a9157]
#19 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb32038ec]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5cb4767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb5cb481e]
#2 /usr/lib/libX11.so.6 [0xb5f7f518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb5f760a6]
#4 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1e93227]
#5 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1e934b8]
#6 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1e946e0]
#7 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa1e947a4]
#8 [0xae5b1b7a]
#9 [0xae5aba7b]
#10 [0xae5aba7b]
#11 [0xae5a9157]
#12 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb32038ec]
#13 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb32f2378]
#14 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb320371f]
#15 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb325bebb]
#16 /usr/local/matlab72/sys/java/jre/glnx86/jre1.5.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb37f62cd]
#17 [0xae5b142b]
#18 [0xae5ab9a4]
#19 [0xae5a9157]


It is obviously a matter of java stuff but i would like to fix this issue because i did the same job in another pc and finally matlab worked fine but with some problems with the figures and surfaces.

thanks very much for each advise

---

### Post by dioltas on 2008-10-03
Are you root? The installer doesn't seem to give a lot of information about what's going wrong! Maybe you need to install some dependencies or something. Does it say anything in the README? Any troubleshooting tips or anything?

[[COLOR="Blue"]This[/COLOR]]("https://help.ubuntu.com/community/MATLAB") or maybe [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=19855") might help.

Not sure what the problem is. I recently installed r2008a. No problems, started a script in a terminal and it gave me a graphical installer.

Maybe you could try that newer version instead... *cough* pirate bay *cough* ;)

---

### Post by antonio_ing on 2008-10-03
yes. i am root. But i don't know.... it worked fine with ubuntu 7.10 too.
anyway now i have added:

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/ && matlab

at the beginning of the matlab script and it is working inside the terminal
which for me is ok too

but can you please suggest me how to get the old matlab window?

---

### Post by dioltas on 2008-10-03
Sorry, i read your origional post wrong, thought you were having trouble installing not running. I usually just type matlab in a terminal and the gui starts up for me. Not sure what could be wrong.

---

### Post by dioltas on 2008-10-03
I meant sudo matlab in the last post.

Here is the output I get in the terminal when I run it:

```
xxx@dio-ismaithliome:~$ sudo matlab
[sudo] password for xxx: 
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb53e9767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb53e98b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb56ae1bd]
#3 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaedb32be]
#4 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaed91ed7]
#5 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaed92188]
#6 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xaed9248f]
#7 [0xafa6e67e]
#8 [0xafa66e9d]
#9 [0xafa66e9d]
#10 [0xafa64207]
#11 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209a4d]
#12 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6305bc8]
#13 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x62098e0]
#14 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f77b]
#15 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb1b1096d]
#16 [0xafa6e67e]
#17 [0xafa66d37]
#18 [0xafa64207]
#19 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209a4d]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb53e9767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb53e981e]
#2 /usr/lib/libX11.so.6 [0xb56ad518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb56a40a6]
#4 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaed91189]
#5 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaed913d5]
#6 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaed92239]
#7 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xaed9248f]
#8 [0xafa6e67e]
#9 [0xafa66e9d]
#10 [0xafa66e9d]
#11 [0xafa64207]
#12 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209a4d]
#13 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6305bc8]
#14 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x62098e0]
#15 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f77b]
#16 /usr/local/matlabR2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb1b1096d]
#17 [0xafa6e67e]
#18 [0xafa66d37]
#19 [0xafa64207]

```

And it works. I don't really know what it means, but it seems fairly similar to yours. Maybe a working output will help someone else figure out what's wrong. I attached a screenshot of matlab running with simulink.
It does slow down my computer an awful though, cant have any other programs running with it or it crashes...
Sorry I can't be of more help.

---

### Post by Nepherte on 2008-10-03
I don't see why you should run matlab as root at all. This should absolutely not be necessary at all, only to install it you need root privileges.

Your output seems ok to me; I get a similar one. So from what I understand, you get a window but it turns grey? Try disabling Compiz, I've had a similar problem with matlab and maple. When compiz was enabled, it gives me a grey window, otherwise it just works fine.

---

### Post by antonio_ing on 2008-10-03
yeah nepherte you were right. But now i don't have anymore those fancy effects of ubuntu 8.04. How can i have them and matlab too?

---

### Post by Nepherte on 2008-10-04
I guess you can't. You'll have to give up some looks for productivity I suppose. You could only disable compiz for the time you're working with matlab and afterwards turn it back on. Fusion-icon is a good application for it.

---

### Post by Orange_and_Green on 2008-10-04
Ciao Antonio,

I use MATLAB on Hardy with compiz enabled and it works fine.

Have you tried ```
export AWT_TOOLKIT=MToolkit
```?

My matlab shell script is on the office computer, so if you can wait till monday I can post it here when I go back to work (sorry, I obviously don't remember it by heart... :p)

---

### Post by Orange_and_Green on 2008-10-06
OK here it is:

```
#!/bin/bash
export LIBXCB_ALLOW_SLOPPY_LOCK=1
export AWT_TOOLKIT=MToolkit
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
/usr/local/MATLAB/bin/matlab -desktop
```

---

