---
title: "System crash 12.04 LTS"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by Rlange289 on 2012-12-22
Hi
I am new to Ubuntu. Less than a year. I have a desktop system. Mostly use it for E-mail and web browsing. Running a dual boot with win 7. (needed for work) After upgrading to 12.04 I started to have problem with the system crashing. It's been getting progressively worse, about 3-5 times a day now. First thing is that the system will freeze and a couple of seconds later the screen goes dark and I get the screen that attached. nothing seems to work. I have to do a hard reset to reboot and it will work fine for a while again.
Running an Intel DH57DD MB, i7, 8Gb

Any suggestions on what might be causing this or how to fix it?

Thanks

---

### Post by squakie on 2012-12-22
What are the specs on your PC?  Make, model, cpu, memory, etc., etc., etc..

---

### Post by Rlange289 on 2012-12-22
I built the system. Always wanted to try it.
 
Motherboard Intel DH57DD
CPU  Intel i7
8Gb ram Corsair
Apevia case with Power supply
1Tb Western digital HD

Win 7 seems to run fine. Only use it for work.

---

### Post by sandyd on 2012-12-23
> **Rlange289 said:**
> Hi
I am new to Ubuntu. Less than a year. I have a desktop system. Mostly use it for E-mail and web browsing. Running a dual boot with win 7. (needed for work) After upgrading to 12.04 I started to have problem with the system crashing. It's been getting progressively worse, about 3-5 times a day now. First thing is that the system will freeze and a couple of seconds later the screen goes dark and I get the screen that attached. nothing seems to work. I have to do a hard reset to reboot and it will work fine for a while again.
Running an Intel DH57DD MB, i7, 8Gb

Any suggestions on what might be causing this or how to fix it?

Thanks

You have an encrypted partition? If you do, its probably [http://www.saout.de/pipermail/dm-crypt/2012-January/002275.html](http://www.saout.de/pipermail/dm-crypt/2012-January/002275.html)

btw, just for reference (i had to crane my neck to see this)
```

paging request at fffffffffffffff8
kthread_data+0x11/0x20
```

Merry Christmas! (or soon to be)

---

### Post by Rlange289 on 2012-12-23
How do I check if I have an encrypted partition? When I did the install I followed the instructions. 

One thing I tried to do was change the partitions, I had it set up 550Gb for Win 7 and 500 for Ubuntu. I wanted to allocate more space to Ubuntu. I ended up with 225Gb of unallocated space. Not sure how to get it reallocated.

Not sure why the attachment was turned on its side. It comes up correctly on my system. I'll see if I can fix it.

Thanks

---

### Post by grahammechanical on 2012-12-23
Did you use the Windows partitioning tools for shrinking the Windows partition? That is the recommended procedure. 

We, here, are assuming that it is Ubuntu that is switching out of the desktop environment to a Linux command line screen. But if you have not altered the Ubuntu partition,  then what has happened to Ubuntu to cause it to do this?

Do you have a true dual boot. Some people install Ubuntu inside Windows (a Wubi install) and call it dual booting but it does make a difference to know if it is a Wubi install or not. Because then the issue might be with Windows and not Ubuntu.

Does this happen when you are running Windows 7? If so, it could be a hardware problem.

Regards.

---

### Post by Rlange289 on 2012-12-23
No, I did not use the Windows partitioning tool to change partition size. I made the change in Gparted. Now I have 3 partitions. 244Gb for windows, 225 Gb unallocated and 461 Gb for Ubuntu

I believe I have a true dual boot. When the machine boots up I have to select Windows if I want to use it, otherwise it will boot into Ubuntu in 10 seconds.

I have no problems with Windows 7. Seems to run fine. All I use it for is to log into my work network. I can't seem to get Citrix XenApp to work in Ubuntu. Other wise I would completely remove Windows if I could.

---

