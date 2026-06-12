---
title: "Free -h too low"
date: 2017-03-28
forum: New to Ubuntu
---

### Post by karentutor1 on 2017-03-28
have reinstalled ubuntu 3x looking to see how to increase the Mem option.

My free - h output is

/dev/sda1 521m efi
/dev/sda2 488m Linux file system 
/dev/sda3 464g Linux lvm

My free -h is

Mem 3.5 g
Swap 3.6 g

So there should be lots there.  I can follow instructions to increase using a lvm but am not sure what exactly to increase.

Any input as to how to increase mem fresh ubuntu 16.04 install?

Thanks!
Karen

---

### Post by sp40140 on 2017-03-28
Could you please post the pic of: launch system monitor -> file system?
Also, are you talking about RAM memory or HDD disk space?

---

### Post by ajgreeny on 2017-03-28
Hi karentutor1

The output you show from command **free -h** is not normal in any way; it should look more like ```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:           7.5G        1.1G        4.2G        173M        2.2G        5.9G
Swap:          4.0G          0B        4.0G
```
Are you sure that is the command you actually used because the output appears to be showing partition sizes not memory amount.

---

### Post by oldos2er on 2017-03-28
What exactly do you mean by ubuntu 3x?

---

### Post by ajgreeny on 2017-03-28
> **oldos2er said:**
> What exactly do you mean by ubuntu 3x?
I presumed that meant she(?) had reinstalled Ubuntu "three times" and was not a version number, but it would be good to know for sure what is the situation.

---

### Post by Habitual on 2017-03-28
> **ajgreeny said:**
> Are you sure that is the command you actually used because the output appears to be showing partition sizes not memory amount.

Looks like 
```
df -h 
```
from here. :)

---

### Post by karentutor1 on 2017-03-28
Sorry I I was unclear.

Yes, I reinstalled 3 times Ubuntu Server Xenial 16.04.

The first output  is a fdisk and the other is free -h.

I need to have 4 g of mem but keep ending up with 3.5g as per the free-h output.

I am guessing it is part of the partition when you install ubuntu.

I am just at loss how to set up to increase the mem.

My best guess is that it would be done here per online installation instructions 16.04

My hard drive has 500g available so I know there is space.

 It is just allocating it correctly.

 But that is only a guess.  The objective is just to ensure the correct amount of mem.

I followed the tecmint install guide.

You can see step 12 link 

[http://www.tecmint.com/installation-of-ubuntu-16-04-server-edition/2/](http://www.tecmint.com/installation-of-ubuntu-16-04-server-edition/2/)

Quote :
For a general purpose server you can stick to Guided with LVM method as illustrated below, which automatically creates the partitions on your behalf


but again I am only guessing.

What is the. Way way to get the 4g mem? Reinstall how? Alter partition with lvm?

Thanks!
Karen

---

### Post by cariboo on 2017-03-28
About the only way you are going to get the ram amount you need, is to add more ram. Some of your ram is used by the system for shared devices built into the motherboard. In older systems you could set the amount of ram used by shared devices in the bios, but I haven't seen a setting in the bios for quite some time.

BTW I'm running Ubuntu server on a system with only 2GiB of ram and so far I haven't run out of ram.

Services running:

[LIST]
[*]apache
[*]mysql
[*]Serviio
[*]NFS
[*]Samba
[*]ssh
[*]Calibre Server
[*]Logitech Media Server
[*]Owncloud
[/LIST]

---

### Post by sp40140 on 2017-03-28
There is a BIG difference between RAM (usually called memory). and disk space (hard disk). These are two different hardware components on computer. So, please be clear about it. 
You can not take from one and put into other. Doesn't work that way. "free" command gives you information about RAM while "df" command provides information about hard disk(s) and/or partitions created on hard drives.
Also, you mention "I NEED 4 GB but only 3.5 GB available". I am curious as to what problem is caused by the difference of 500MB. (just curiosity).

---

### Post by karentutor1 on 2017-03-28
Oh goodness!!

Apologies for my stunning display of confusion.

So mem == RAM == manufacturerd or purchased and installed hardware?

It was a complete misunderstanding :(

Do I need to purchase a new computer or can I plug in some components to upgrade?

---

### Post by sp40140 on 2017-03-28
No worries. All good as long as confusion is cleared up.

"mem == RAM == manufacturerd or purchased and installed hardware?"
Yes, It is.

"Do I need to purchase a new computer or can I plug in some components to upgrade?"
It depends on your computer. Sometimes you can add more RAM chips and sometimes you can't. You can look this information up online based on make and model of the computer.

---

### Post by karentutor1 on 2017-03-28
Hi 

I don't know what caused the difference.  I just have a clean ubuntu install.  The specs suggest 4g for some software, but I only have 3.5.

I assume the shortfall is just due to low quality laptop.

---

### Post by sp40140 on 2017-03-28
Do not worry about 3.5 GB. Your computer has 4GB RAM. It's just the operating system is reporting 3.5 as usable. My desktop has 8GB ram, but Ubuntu shows only 7.7. It happens. No big deal. Unless you have some application which needs at least 4GB. (that's why I asked initially, Why do you need 4GB?)

---

