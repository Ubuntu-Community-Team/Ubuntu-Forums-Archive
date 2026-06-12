---
title: "How to install on a second internal HD?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by slocks on 2008-04-28
I don't have room on C: to install Ubuntu (8.04), so I'd like to put it my second internal hard drive. However after installing to a second drive and then selecting Ubuntu on boot up I get error 15. From other posts it seems that this is due to grub looking at the wrong drive. 

So what should I do and *exactly* how do I do it?:confused:

Please feel free to assume I know nothing other than how to read and type!

Thanks for any help!

---

### Post by zvacet on 2008-04-28
Maybe [this]("http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot") can help you.

---

### Post by slocks on 2008-04-29
Thanks for the link.

I had looked through that before but with some dismay as it runs to 11 pages of technical detail with links and is mostly from 2006 to 2007. Near the end of page 11 someone asks if this is appropriate to 8.04, but without a direct reply that I can see.

So is there anything simpler and are the instructions correct for 8.04?

Thanks

---

### Post by slocks on 2008-04-30
When 8.04 is installed via windows one of the options is which drive letter to install to. Given the option is more than the drive c: I would be suprised if those who wrote this did not intend installation to other than c: to be common. So I presumed there might be standard documentation to tell users what to do if not installing to c: with 8.04. That's why it is odd that all I can find is complex conversations from 2006-7. What I am hoping for is something like: "Once installed on a secondary drive, open this file... and change the text to this..." 

Are there simple instruction like that out there anywhere? 

Thanks for any help!

---

### Post by yamawho on 2008-04-30
I installed using the entire 2nd hdd and used advanced to install Grub to the MBR of the 2nd hdd.

I had Grub issues and was getting error 17 Cannot mount partition.

I tried to figure out what was going on but being more of a hardware guy, I started playing around with the sata cables to see if I could get it to actually boot.

I unplugged the windows hdd and restarted the system, then replugged the 2nd hdd ... same thing.

I decided to reinstall and noticed that the order of the hdd's had changed because of my tinkering. So I installed 8.04 again as above and it works

I can booth directly to XP by f11 to access the boot menu.
I can access XP from grub doing a normal boot.
I can boot into ubuntu doing a normal boot.

I know my changing the order in which the system see the hdd's was the key to solving this.

---

### Post by inferiorwang on 2008-04-30
It's because ubuntu put the boot loader on the second hard drive.  You need to set up the mbr on the primary drive.

---

### Post by yamawho on 2008-04-30
> **inferiorwang said:**
> It's because ubuntu put the boot loader on the second hard drive.  You need to set up the mbr on the primary drive.

I figured as much ...

However, installing on the 2nd gives me the option to remove it without effecting the XP install.

I did it this way on my kid's system, she saw me playing with ubuntu and thought it was cool and asked me to put it on her computer.

---

### Post by slocks on 2008-04-30
> **inferiorwang said:**
> It's because ubuntu put the boot loader on the second hard drive.  You need to set up the mbr on the primary drive.

How do you do that?

Thanks

---

