---
title: "Which to install - 32 or 64 bit"
date: 2012-08-05
forum: Recurring Discussions
---

### Post by RogerDavis on 2012-08-05
I just got a new high power computer and want to confirm which to install of 12.04 - 32 or 64 bit?

Specs:
Intel DZ77BH-55K motherboard
Intel i7 3770 Ivy Bridge CPU at 3.4 GHz
Radeon 7750 1 Gig 800 MHz display card
16 Gig memory
1T hard drive for Ubuntu only

I thought this might be a common question, but a search turned up nothing definitive. 

I simply assumed that 64 bit would be the answer, but I see that 32 bit is recommended, and if I select 64 bit, it appears that I'm still only offered 32 bit even though 64 bit is selected - so WHERE can I get a for sure 64 bit version for normal desktop use?

Last, but not least, which is the preferred installation method for this machine?

Thanks!

---

### Post by darkod on 2012-08-05
To fully use the 16GB of ram I would say 64bit definitely.

You have all images of Lubuntu 12.04 LTS here:
[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)

Just download the one saying desktop-amd64, that covers all 64bit CPUs including Intel of course.

As for preferred installation method, I think all of them should work and it depends on you. I always install the manual way (Something Else option) because I am using separate /home partition and I want full control of the partitioning.

With the automated methods you can't have separate /home and the installer decides on the partition sizes.

---

### Post by jackyboy633 on 2012-08-05
Darkod beat me to it! Here is my view, though

The choice of 32 or 64 bit depends on what you are doing with your computer. Here are the pros and cons of each:

**32-bit**
***Pros***
[LIST]
[*]Has better compatibility with some applications (Flash Player only has a 32-bit stable edition, for example.
[*]More stable and well-tested than 64-bit
[/LIST]
***Cons***
[LIST]
[*]Will not take advantage of powerful new hardware, like yours. (will only use 3.5GB of the 16GB RAM you specified, for instance.)
[*]Applications will not run as well compared to 64-bit Linux.
[/LIST]
**64bit**
***Pros***
[LIST]
[*]Will take advantage of newer hardware (using the full 16GB RAM for instance)
[*]Applications will run faster as more and more software is designed to take advantage of 64-bit
[/LIST]
***Cons***
[LIST]
[*]Lacks compatiblity with some applications
[*]Not as stable or as well tested as 32-bit.
[/LIST]

I would go with 64-bit, because 32-bit would be a bit of a waste on this hardware. You could always run 32-bit on VirtualBox/KVM, so it is not a big loss to go with 64-bit.

From what I can see, this page gives you the right version (for sure) when you click on the link: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu) If it is 64 bit, it will have 'amd64' in the filename, or for 32-bit, it should have 'i386' in the filename.

I would just try installing Ubuntu normally. Here is my recommended partitioning scheme:

/boot = 100 MB
/ = 15-20 GB
Swap = 32GB
/home = The rest.

Hope this helps,
Jackyboy633

PS: Sorry about the essay, by the way! :)

---

### Post by RogerDavis on 2012-08-05
I'll use the entire 1T disk for Ubuntu.  I switch them with a hardware switch, so the Windoze disk is just for Windoze, and the Ubuntu disk is just for Ubuntu.  

I understand that the file marked AMD64 is also for Intel64 ?!?!?!  Why the goofy naming if it also works for Intel?  I guess that's just a rhetorical question, unless one of the "movers and shakers" happens by.  It seems REALLY confusing, and I NEVER would have used this file without additional info.

Anyway, all good info, and would appreciate more from whoever can provide it.

Thanks!

---

### Post by darkod on 2012-08-05
AMD came up with the first 64bit CPU and amd64 remained trademarked. It applies to all 64bit CPUs these days but I guess the trademark remains.

---

### Post by Ubun2to on 2012-08-05
> **RogerDavis said:**
> I understand that the file marked AMD64 is also for Intel64 ?!?!?!  Why the goofy naming if it also works for Intel?

AMD originally came up with the 64 bit architecture, so it's basically a shoutout to AMD. Less common these days, but it's still around.

---

### Post by oldfred on 2012-08-05
Moved to recurring discussions as we get this daily.

[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

I think jackyboy633 comparison was valid a few years ago, but not now. 
I used 32bit in 2006, but converted to 64bit with 9.10 and cannot say I have had any issues (other than all the usually issues :) ).

---

### Post by Ubun2to on 2012-08-06
I should add that, regardless of the RAM you have, most new computers have x64 processors. Like the [System76 Meerkat Ion NetTop]("https://www.system76.com/desktops/model/ment5")-it comes with a 64 bit OS regardless of whether you have 2 GB of RAM or 4 GB.
It used to be that the amount of RAM determined whether you had a 32 bit or 64 bit processor. Now, that's not a very reliable measurement.

---

