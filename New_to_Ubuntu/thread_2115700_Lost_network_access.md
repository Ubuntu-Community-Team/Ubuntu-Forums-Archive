---
title: "Lost network access"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by tcnm on 2013-02-13
I have ubuntu 12.10, which until today was working correctly.  In particular, I could use Firefox to access the Internet (and my mail) through my wireless router.

Today I received a notice advising me that additional software was available.  I chose to download the software.  At the completion of the download I was asked to reboot the computer, which I did.  When the reboot finished, I received the message "Network Disconnected". and I can no longer access the Internet with Firefox.

When I select the "Network" icon, the option "Wireless" has disappeared, I and I can find no way to reconnect via my wireless router.

Can anyone help?  Thank you very much.

TCNM

---

### Post by Mark_in_Hollywood on 2013-02-13
Please explain what you did to 

1 - Download

2 - Install

the additional software. 

Let us begin there.

---

### Post by tcnm on 2013-02-13
I clicked "Download" to download the new software.

When the download was complete, I clicked "Reboot now" to reboot the computer

---

### Post by Mark_in_Hollywood on 2013-02-14
try:

sudo apt-get update
sudo apt-get install aptitude

from the terminal type

sudo aptitude install -f

the

 -f  

will try to resolve problems. After it runs, if you still are w/o network, re-boot. Let me know. If this solves it, please mark this thread as solved under Thread Tools near top of posting window.

---

### Post by DuckHook on 2013-02-14
aptitude -f is not such a good idea right away-- at least, not until we do some tests. Also, aptitude is redundant. Let's try to stick with apt to avoid confusion and system bloat.

@OP

We need much more info about your system. Otherwise, fumbling around in the dark. Were you describing a system update? If your wireless stopped working after an update, it is possible that the update loaded conflicting wireless modules that are now competing for your wireless chip. Please open a terminal using <Ctrl>+<Alt>+<t> and do:```
sudo lshw -C network
``````
sudo lspci -vk | grep -iA13 net
``````
ifconfig
``````
iwconfig
``````
cat /etc/modules
``````
grep blacklist /etc/modprobe.d/blacklist.conf
```The output will be considerable, so for easier reading, highlight each set of outputs and wrap it in a "code" box just like I have by using the hash (#) character at the top of the posting box. Please give each output its own hash tags.

---

### Post by Mark_in_Hollywood on 2013-02-15
Yea, follow the Duckster.

---

