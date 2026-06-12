---
title: "[SOLVED] Installing SUSE"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Krishna_81 on 2008-08-13
I like Ubuntu for sure but wanted to know if we can install open SUSE too.
Can I have two distros of linux on the same computer?Can we dual-boot them?

---

### Post by pparks1 on 2008-08-13
Yes, you certainly can dual boot them.

---

### Post by pparks1 on 2008-08-13
You may also want to look into some virtualization software, like VMWare or VirtualBox.  This would allow you to learn and play without risking anything on your machine.  Plus, it lets you still have access to the web from the host computer (Ubuntu), while you work on getting the other distro working (for example, if you cannot get the network working).

---

### Post by Krishna_81 on 2008-08-13
Thanx.
How to partition the disk then?
Do we need to have two swap,'/' partitions?

---

### Post by Krishna_81 on 2008-08-13
anyone there!

---

### Post by overdrank on 2008-08-13
> **Krishna_81 said:**
> anyone there!

Hi and as for partitioning, yes you will have to direct suse to your root directory, and it should detect the existing swap. DO not quote me on this as it has been a while since I used Suse. The installation is a little more in depth then the ubuntu installation. 
Here is a link on partitioning basics
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by meindian523 on 2008-08-13
Might help,though it's my blog post:
[http://stardustinmybones.wordpress.com/2008/06/30/triple-boot/](http://stardustinmybones.wordpress.com/2008/06/30/triple-boot/)

---

### Post by Elfy on 2008-08-13
When I installed it the swap was recognised.

---

### Post by Krishna_81 on 2008-08-13
What you mean to say is that..
we should have two swap partitions for both?
Dont mind my que's.They might seem too basic:)

---

### Post by meindian523 on 2008-08-13
Nopes,you need one swap partition which will be used by whichever system you have booted into at the moment.

---

### Post by SuperSonic4 on 2008-08-13
I'd imagine you'd only need one swap, particularly if you have a lot of ram or unless you hibernate

---

### Post by Krishna_81 on 2008-08-13
Thanx a lot for your replies.
Last one plz.
You said that swap partition is to be shared by different distros.That's clear.
What about '/' partition?
Finally,tell me the partitions that ive to make,say on a 20 GB free space

---

### Post by M-Theory on 2008-08-13
You will have a separate '/' partition for each distro. If you plan on dual-booting, you will need to create this partition prior to installing SUSE or during it's installation process.

The size of the partition should be about 7-8 GB, if you don't use a seperate home partition you may want to add some space to this.

---

### Post by ajgreeny on 2008-08-13
No, you most definitely need separate / partitions and if you run a separate /home partition, you need that separate from ubuntu as well, or you will end up with all sorts of configuration clashes.  One swap for both is no problem.

I have done exactly what you are asking about with the OpenSuse 11 kde4 version, but quickly decided that kde4 was not for me so am now trying other distros, which I do all the time.  I have at one time had windows XP and three separate distros on the same machine with no problems, or at least no problems related to the fact that I had the four OSs.

I would suggest that you make a 10GB partition for / and 10 GB partition for /home and make sure the original swap is allocated for swap in Suse.  The / partition is probably bigger than it needs to be but just for now, go with that and you will be able to change things later if you need to.

---

### Post by Krishna_81 on 2008-08-13
You mean to say except for swap area everything else should be separate for both the distros.Is that all?

Thanks for all your replies!

---

### Post by Flyingjester on 2008-08-13
yup, except, swap everything should be separate.

---

### Post by meindian523 on 2008-08-13
Not necessarily,I'm using a common /home,only with different usernames.If you don't want the hassle of remembering two usernames and two passwords,by all means,keep you /home for Ubuntu and /home for openSUSE separate.

---

### Post by Krishna_81 on 2008-08-13
Thanx to all!

---

