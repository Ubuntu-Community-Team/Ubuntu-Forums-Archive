---
title: "Must set up dual boot on 11.10 machine"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by Newbuntu2011 on 2012-04-24
Having used ubuntu for over a year and absolutely loving it, I have run into two issues (unable to play flash video - been working on it for 3 weeks & HPLIP will not allow me to utilize my scanner on hp AIO) that are going to force me to reinstall windows xp pro as a dual boot. 

I have 11.10 installed as my only operating system, and have no intention of leaving ubuntu, hopefully the new LTS will fix my problems, however, in order to keep my job I am going to have to reinstall windows in dual boot, & don't know how. can anyone help me?

---

### Post by audiomick on 2012-04-24
Read about it here
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by oldfred on 2012-04-24
Welcome to the forums.

You can use gparted to create a primary NTFS partition with the boot flag. XP will then install to that.

It does not have to be sda1 although most installs are that way as Windows is normally installed first. Windows will only boot from primary partitions, so do not attempt to install to a logical partition. Second installs of Windows can be in logical partitions as long as Windows can move its boot files to a primary NTFS partition to use for booting.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

You will have to reinstall grub2's boot loader to the MBR so have a current version liveCD available.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by Newbuntu2011 on 2012-04-24
Thanks for your quick replies! Just another reason to love ubuntu!  I will work through the tutorials to solve my problem, thanks again!

---

### Post by skiingisbelieving on 2012-04-24
Here is a wonderful tutorial. I used it about a year ago.

[http://m.lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://m.lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by Newbuntu2011 on 2012-04-25
Thanks everyone, your "let me help you" attitudes are exactly why I love Ubuntu so much!  It also made me think, why am I trying to reload windows with all of it's problems?  It's like going BACK into an abusive relationship!  SOOOOOO... with that being said, maybe someone on this forum can help me with the issues that have forced me to think of going back to the overlord Bill Gates!

My two problems are -

       1.  After running an update in 10.04 LTS I could no longer play flash content - I use logmein.com to get to my office computer so this is a really big deal to me!  My job depends on it!


In trying to fix this issue, I upgraded to 11.10, now still have the same problem AND NOW...


       2.  I have a HP OfficePro 8600 AIO and when I  a) try to print it slows the machine to the point that I think it has locked up and then *finally *begins printing, and b) xSane doesn't even recognize the scanner any more.  Again, I must scan docs for my job, and this is also a really big deal!

Thanks in advance for your kindness in helping some who's spirit is strong, yet their computing abilities are weak!

You guys are the best!!!!!!!!!!!

---

### Post by Bartender on 2012-04-25
Can't help you with the flash content thingie.

But I may be able to help with the printer.  Maybe.  Here's a [thread]("http://ubuntuforums.org/showthread.php?t=1910222") I started a few weeks ago.

The HPLIP toolbox available through the repos is older than the one you can install manually from HP.  Getting the latest version of HPLPIP may not solve anything.  But it's worth mentioning.

---

### Post by Curtis6767 on 2012-04-25
If you've been trying to fix Flash, then you've probably seen this:

[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

It's a pretty long thread but if you've haven't been following it then maybe you can find a solution in there.

I have the flash version that ends with .233 and I'm not having any problems with Flash. Maybe I'm lucky.

To find your current version: [http://helpx.adobe.com/flash-player.html](http://helpx.adobe.com/flash-player.html)

---

