---
title: "Swap UbuntuOS Hard Drives Between Computers"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by afterfostercare on 2012-02-22
I want to physically swap hard drives between my two home computers.

I have **Ubuntu 11.10** installed and running on one PC and **Ubuntu 11.04** installed and running on the other PC.

Both are home computers (not laptops)

Both are different home computers
[INDENT]Ubuntu 11.10 installed on an IBMNetVista 1GB RAM[/INDENT]
[INDENT]Ubuntu 11.04 installed on a (different computer can't recall) with 4 Gigs RAM[/INDENT]

If I take the hard drives out of each computer, and swap them, will the OS be ok and like MS Windows would, just install necessary drivers as it boots or could I be causing myself a world of pain?

---

### Post by roelforg on 2012-02-22
Just make sure you use the 32-bit version,
the system shouldn't mind in that case.

Did a lot, always worked.

---

### Post by blazemore on 2012-02-22
Assuming they are both the same type of CPU (Intel x86 or x64) you should be fine, but it will try to mount hard-disks that aren't there.

Your best bet is probably to back up the entire /home/your_username folder (including any hidden files, which begin with a dot), install Ubuntu from scratch on the new computer, then copy the folder back across which will restore all your settings and files.

---

### Post by afterfostercare on 2012-02-22
That is great. I did not mention that they are both 32-Bit installs and architechture thanks for reminding me. I learned how to find out if my hardware is 32-Bit or 64-Bit at this page:

[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/](http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/)

---

### Post by roelforg on 2012-02-22
> **afterfostercare said:**
> That is great. I did not mention that they are both 32-Bit installs and architechture thanks for reminding me. I learned how to find out if my hardware is 32-Bit or 64-Bit at this page:

[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/](http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/)


I said to use the 32-bit version because then you don't have to mind the difference,
unlike windows; with linux the benefits from 64-bit over 32-bit are small; very small.

---

### Post by blazemore on 2012-02-22
> **roelforg said:**
> I said to use the 32-bit version because then you don't have to mind the difference,
unlike windows; with linux the benefits from 64-bit over 32-bit are small; very small.

I have 16Gib RAM, so using 32 bit would be stupid.

---

### Post by roelforg on 2012-02-22
> **blazemore said:**
> I have 16Gib RAM, so using 32 bit would be stupid.
32-bit linux can handle 64gb;
See: [http://www.cyberciti.biz/tips/maximum-memory-and-cpu-limitations-for-linux-server.html](http://www.cyberciti.biz/tips/maximum-memory-and-cpu-limitations-for-linux-server.html)

---

