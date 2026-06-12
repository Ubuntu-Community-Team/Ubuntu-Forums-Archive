---
title: "Sound not working all the time."
date: 2008-06-08
forum: New to Ubuntu
---

### Post by dwhitney67 on 2008-06-08
I have a Dell Inspiron E1505 with Ubuntu 8.04 that is suffering from a mysterious problem with the sound chip-set.

Initially when I boot the system, the sound card works (I hear the Ubuntu drum-roll).  When I use an application like Amarok, I am able to play/listen to music.

Then for no apparent/obvious reason, the sound card stops working.  From that point I cannot use any media application that uses the sound card.

If I test with the Gnome for configuring "Sound Preferences", I cannot get any of the tests to work.  When the system is first booted, the tests do work.

What's going on?  Why would the sound card stop working at some random point?

Here's the sound card (chip-set) that I have as listed by running 'lspci':
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

If you have a similar sound chip-set, can you please post the following files from your system?
[INDENT]1) /etc/modules
2) /etc/modprobe.d/alsa-base
3) /etc/modprobe.d/options[/INDENT]

Perhaps a recent system update affected one or more of these files.

Thank you!

---

### Post by faktorqm on 2008-06-10
Hello!

try to press fn + f5. bye!

---

### Post by dwhitney67 on 2008-06-10
What?  Que???

---

### Post by faktorqm on 2008-06-11
[en]
Do you speak spanish?

I read this in one user blog, by pressing fn + f5 the system automatically auto correct the problem. 

This solve your problem? I'm glad to be of help.
[/en]

[es]
Entendés castellano?

Lei eso en el blog de un usuario, que presionando Fn + F5 el sistema automaticamente autocorregia el problema. 

Esto resuelve el problema? Me alegro de ser de ayuda. 
[/es]

---

### Post by dwhitney67 on 2008-06-12
Pressing Fn-F5 does nothing on my system.  That series of keystrokes is not mapped to anything... at least not on my system.  On another system I have, striking Fn-F5 would in theory (if running Windoze) place the system into the "hibernate" mode.

Anyhow, the problem is caused by a bug in the **gstreamer-plugins-good** package.  Fedora has issued an update for this package; I can only hope that Ubuntu does it as well (or have they??)

For more information:  [https://bugzilla.redhat.com/show_bug.cgi?id=449268](https://bugzilla.redhat.com/show_bug.cgi?id=449268)

---

