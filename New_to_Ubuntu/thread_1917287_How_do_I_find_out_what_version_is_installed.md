---
title: "How do I find out what version is installed?"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by Airycat on 2012-01-29
I had problems installing the 64 bit Ubuntu. What happened is that it deleted the 32 bit and ran to the end and then gave me a messages saying I needed to burn the CD more slowly. (I didn't see any option to choose speed.) Then it opened to a new Ubuntu with everything I had added, except the trash, removed and there was a link to install Ubuntu on the desktop... So I clicked. I did a complete overwrite again and it didn't give me any error messages this time, but I want to verify that I have the 64 bit version. 

In windows I'd just right click on the "My Computer and get properties. I have no idea how to do this in Ubuntu.

TIA
~Faith

---

### Post by oldfred on 2012-01-29
From terminal:

32 or 64 bit
```
uname -a
```
i386 or i686 = 32-bit
x86_64 = 64-bit

You get some info from System, Administration, System Monitor but in the new versions with Unity I do not know where system monitor is or if it is installed as standard.

---

### Post by Airycat on 2012-01-29
> **oldfred said:**
> From terminal:

32 or 64 bit
```
uname -a
```
i386 or i686 = 32-bit
x86_64 = 64-bit

You get some info from System, Administration, System Monitor but in the new versions with Unity I do not know where system monitor is or if it is installed as standard.

Thank you!! It installed correctly and is very clear to see with that bit of code. Thank you!
~Faith

---

