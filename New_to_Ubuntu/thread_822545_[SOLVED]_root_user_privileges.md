---
title: "[SOLVED] root user privileges"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by ghostier on 2008-06-08
Hi, I'm new to ubuntu. The problem I'm having is that a lot of the times when I try to do something, I can't because of insufficient privileges. I would have to use the terminal in order to get it done. This is frustrating because I would rather use the GUI instead. Is there anyway of my user account having root privileges?

---

### Post by Joeb454 on 2008-06-08
It does have root privileges. If you want to run nautilus as root for example, hit Alt+F2 and type (or copy/paste) ```
gksudo nautilus
``` Hope this helps :)

---

### Post by The Cosmic Hobo on 2008-06-08
Joeb454 is right. Ubuntu doesn't let you be root for safety and security reasons. I've not used Ubuntu much so I can't tell you about the gksudo command, but you can also use the sudo command for single tasks (eg sudo apt-get install) on the command line, which in any single shell session will prompt you for the admin password once.

I suspect gksudo might be more what you need - sounds like it gives root privs to Nautilus, which would let you do what you want in the GUI rather than in the shell.

---

### Post by omi291 on 2008-06-08
You can check out this site for some more information if you want:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by meindian523 on 2008-06-08
gksudo is graphical sudo.It's better used with graphical apps.Look here for why:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by bruce89 on 2008-06-08
Be aware that removing files in Nautilus doesn't actually delete them, it just moves them to the root user's "bin".

Why do you need to poke about with non-home files?

---

### Post by ghostier on 2008-06-08
To install new skins for some apps. Also, I wanted to put the java runtime folder in that place instead of desktop. 

Thanks alot. gksudo's great.

---

### Post by bruce89 on 2008-06-08
> **ghostier said:**
> To install new skins for some apps. Also, I wanted to put the java runtime folder in that place instead of desktop. 

Thanks alot. gksudo's great.

Adding / removing files outside your home directory is a bad idea.

You ought to install java the proper way through some kind of package manager. [apt:openjdk-6-jre]("apt:openjdk-6-jre") will do it.

What do you mean by skins, and for which programs?

---

