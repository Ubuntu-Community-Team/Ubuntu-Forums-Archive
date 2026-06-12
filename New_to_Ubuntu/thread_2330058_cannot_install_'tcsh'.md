---
title: "cannot install 'tcsh'"
date: 2016-07-07
forum: New to Ubuntu
---

### Post by jim-anderson on 2016-07-07
I'm new to ubuntu, but not new to Linux. I have used apt, and it has worked well for me.

I just installed ubuntu 14.02, then brought up an xterm and tried to install 'tcsh' with


> jja@furillo:~$ sudo apt-get install tcsh
[sudo] password for jja: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tcsh


Can someone help?

Jim A.

---

### Post by &amp;KyT$0P# on 2016-07-07
Have you run [FONT=Courier New]sudo apt-get update[/FONT] on this system yet?
If not, it won't have any package information other than the locally installed packages, so it won't know what all packages are available.

---

### Post by steeldriver on 2016-07-07
I believe that tcsh is in the 'universe' repository, which may not be enabled by default - you can enable it from Software Sources or from a terminal using

```

sudo apt-add-repository universe

sudo apt-get update

```

---

### Post by jim-anderson on 2016-07-07
I can't believe I forgot to run apt-get update. This is done and I'm good not. Thank you both!

Jim A.

---

### Post by &amp;KyT$0P# on 2016-07-07
You're welcome! :KS

---

### Post by ajgreeny on 2016-07-07
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

