---
title: "[SOLVED] I'd like a little help installing Avast! for Linux on Ubuntu Hardy 64-bit"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Zieg30CT on 2008-09-20
I have the program downloaded from their site and I also have the necessary product key. However when I attempt to install the file I get the following:
adrian1@Dracula:~$ sudo dpkg -i '/home/adrian1/Desktop/avast4workstation_1.0.8-2_i386.deb' 
[sudo] password for adrian1: 
dpkg: error processing /home/adrian1/Desktop/avast4workstation_1.0.8-2_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 /home/adrian1/Desktop/avast4workstation_1.0.8-2_i386.deb

Is there a way to make it recognize the 64-bit architecture?

---

### Post by jamesrfla on 2008-09-20
You don't need anti virus protections unless you are sharing files with Windows computers.

---

### Post by Zieg30CT on 2008-09-20
I am dual-booting my computer with Vista Ultimate and I'd just like to make sure nothing can wreak havoc on it.

---

### Post by Dr Small on 2008-09-20
> **Zieg30CT said:**
> I am dual-booting my computer with Vista Ultimate and I'd just like to make sure nothing can wreak havoc on it.
Nothing will. Windows viruses will not install themselves on your Ubuntu partition. Don't sweat it.

---

### Post by Zieg30CT on 2008-09-20
Alrighty then, thank you :popcorn:

---

