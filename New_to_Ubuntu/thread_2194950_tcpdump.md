---
title: "tcpdump"
date: 2013-12-21
forum: New to Ubuntu
---

### Post by memon_saifullah on 2013-12-21
Is TCPDUMP comes with Ubuntu 13, if yes then how do I use it?

---

### Post by bashiergui on 2013-12-21
Simple enough to find out by typing in a terminal```
tcpdump
```If it's not installed type in ```
sudo apt-get install tcpdump
``` To learn how to use it type ```
man tcpdump
``` or go to this link [http://manpages.ubuntu.com/manpages/lucid/man8/tcpdump.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/tcpdump.8.html)

---

### Post by memon_saifullah on 2013-12-21
How do I install TCPDUMP in Ubuntu? or does it come with Ubuntu already, if yes then where can I find it?

---

### Post by sisco311 on 2013-12-21
Please don't start multiple threads on the same subject.

---

### Post by Lars Noodén on 2013-12-21
It is easy to use once you get the syntax, which is simple.  Here is a basic tutorial:

[http://www.danielmiessler.com/study/tcpdump/?ModPagespeed=noscript#basics](http://www.danielmiessler.com/study/tcpdump/?ModPagespeed=noscript#basics)

However, maybe you want something graphical like Wireshark?

---

### Post by memon_saifullah on 2013-12-21
when I install tcpdum I receive this message "You need to be root to perform this command", I don't know why this I happens

---

### Post by memon_saifullah on 2013-12-21
Ok, I've Installed it as you suggested, but when I write tcpdump in terminal following message appears
"tcpdump: no suitable device found"
how do use access it

---

### Post by memon_saifullah on 2013-12-21
but when i use it this is displayed in response "tcpdump: no suitable device found"

---

### Post by Lars Noodén on 2013-12-21
tcpdump needs to be run as root.  The tutorial mentions it indirectly, but does not come out and say it explicitly.  

```

sudo tcpdump

```

Same for wireshark, except use gksudo instead of sudo.

---

### Post by raja.genupula on 2013-12-21
> sudo apt-get install < pkg_name>

Thats the command to install any package in ubuntu.

you have to be root to install any package.

---

### Post by memon_saifullah on 2013-12-22
What does it meant by "being a root"?

---

### Post by overdrank on 2013-12-22
> **memon_saifullah said:**
> What does it meant by "being a root"?

[_RootSudo_]("https://help.ubuntu.com/community/RootSudo")

---

