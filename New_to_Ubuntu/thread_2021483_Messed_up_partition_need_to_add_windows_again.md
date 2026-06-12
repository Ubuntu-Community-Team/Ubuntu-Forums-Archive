---
title: "Messed up partition need to add windows again"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by scottau74 on 2012-07-09
I am extremely new to ubuntu and to linux as a whole. sadly there are many programs that i wish i could use but am unable because they are not supported on ubuntu. The person that did the partition messed everything up so there is only the unallocated and ext4 and i am unable to do anything. i have a copy of windows but my drive need reformatted to ntfs. i am very new to things such as this so i will need it to be dumbed down as far as possible.

---

### Post by AlbertJB on 2012-07-09
First of all, take it easy.

Secondly, almost every application in Windows have its counterpart or equivalent in Ubuntu.. maybe not as user-friendly some of them, but at least are open source.

Third point is: there's an app called Wine which allows you to run Windows apps under Ubuntu. If you are still interested, there are many tutorials on how to configure it.

Finally, if you really don't want to migrate to Ubuntu or Linux in general and keep to Microsoft products, you have also the option of get your copy of Windows (a DVD maybe) and follow the steps in order to format the hard drive to NTFS or whatever the filesystem you want to work with on Windows.

I think nowadays it's not that hard to install Ubuntu, and plus you could have a dual boot Ubuntu - Windows with 2 different physical partitions, or even run Ubuntu inside Windows with a virtual machine to test it. 

It's just my humble point of view of course, I am a newbie too.

---

### Post by SirWhy on 2012-07-09
> **Gosset Inofensiu said:**
> 
I think nowadays it's not that hard to install Ubuntu, and plus you could have a dual boot Ubuntu - Windows with 2 different physical partitions, or even run Ubuntu inside Windows with a virtual machine to test it. 


I highly recommend creating a virtual machine to test out Ubuntu first on windows. See if you like the thing.

I also highly recommend Dual Booting Ubuntu with Windows, Wine can be a bit tricky and doesn't always work so it would be nice to have both operating systems installed, so that you don't need to choose one or the other.

---

### Post by AlbertJB on 2012-07-09
I had Dual Booting Ubuntu and Windows for a year and was a pain in the.. each time I wanted to switched OS I had to reboot the machine.. I completely agree it's better one only OS as host and as many guest OS using your virtual machine engine (Virtual Box, for example...). 

> **SirWhy said:**
> I highly recommend creating a virtual machine to test out Ubuntu first on windows. See if you like the thing.

I also highly recommend Dual Booting Ubuntu with Windows, Wine can be a bit tricky and doesn't always work so it would be nice to have both operating systems installed, so that you don't need to choose one or the other.

---

### Post by SirWhy on 2012-07-10
> **AlbertJB said:**
> I had Dual Booting Ubuntu and Windows for a year and was a pain in the.. each time I wanted to switched OS I had to reboot the machine.. I completely agree it's better one only OS as host and as many guest OS using your virtual machine engine (Virtual Box, for example...).

I never really had a problem with rebooting to use a different OS. I use Ubuntu 90% of the time and Windows only for certain programs (I don't really like wine, for Steam stuff). 

I also have desktops with dedicated OSes so definitely not a problem. Virtual Machines basically mean an OS running off another OS which on a meh laptop with few resources is a problem (for me)

Guess it depends on your situation.

---

### Post by critin on 2012-07-10
> **scottau74 said:**
> I am extremely new to ubuntu and to linux as a whole. sadly there are many programs that i wish i could use but am unable because they are not supported on ubuntu. The person that did the partition messed everything up so there is only the unallocated and ext4 **and i am unable to do anything**. i have a copy of windows but my drive need reformatted to ntfs. i am very new to things such as this so i will need it to be dumbed down as far as possible.

Welcome to ubuntu, scottau74,
What is the specific problem?

How is the partition/disk messed up?  Do you mean you're unable to use the machine?  Does ubuntu work?

* Use gparted (get it in Software Center--open it and go to the disk and ask it to format the unallocated to ntfs.

Did you attempt to install windows on the unformatted partition and it refused or what?  

Use a live cd or a live partition manage, these are on a separate disk,  divide the disk into partitions,  format part of the disk (or how much you choose) in ntfs,  **install Windows first**, then install ubuntu into another partition.  

I haven't seen many windows programs that can't be found in open source (free).  Games aren't easy to find, but if you still have windows...and who uses games all the time anyway? 

> The person that did the partition messed everything up so there is only the unallocated and ext4 **and i am unable to do anything**.

Take it back and ask him to do it right this time, or get your money back.  Be sure and tell him you wanted to install Windows too.

Ubuntu isn't for everyone, but it's a good system.

Good luck!

---

