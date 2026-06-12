---
title: "Installing to a laptop from scratch"
date: 2012-08-18
forum: New to Ubuntu
---

### Post by Frank O on 2012-08-18
I have an x86_64 laptop running Windows 7 whose disk got corrupted beyond repair. I'd like to buy a new hard drive for the laptop and install a flavor of Unix to practice on. I used FreeBSD some years ago, but it's been a while.

I asked a system admin friend for recommendations of free versions of Unix, and he suggested I check out Ubuntu and CentOS.  He thought Ubuntu might be a little more user-friendly.

I guess I'll need to download to a DVD, then use that to partition and format the drive and install the OS.  Is this a fairly straightforward process with Ubuntu?

---

### Post by darkapec on 2012-08-19
yep, just as easy, if not easier then windows

Download ISO from ubuntu
burn ISO to disk
place disk into computer you want to install ubuntu on
reboot target computer and boot from cd
the gui will guide you the rest of the way.

---

### Post by Frank O on 2012-08-19
Thanks. I see on ubuntu.com that the 32-bit version is marked as "Recommended." Can there be complications with installing the 64-bit version?

---

### Post by bodhi.zazen on 2012-08-19
I suggest you use the 64 bit version of Ubuntu if you have a 64 bit processor.

I also suggest you download the Ubuntu CD rather then the DVD. The Ubuntu DVD contains language packages.

With Centos you would use the DVD.

---

### Post by 681ankit on 2012-08-19
> **bodhi.zazen said:**
> I suggest you use the 64 bit version of Ubuntu if you have a 64 bit processor.

I also suggest you download the Ubuntu CD rather then the DVD. The Ubuntu DVD contains language packages.

With Centos you would use the DVD.

Why to download 64 bits...Is it better than 32..???I thought that.. there is no performance change if you have 4 gb or less ram...Rather processor will have to work with 64 bits of registers which is not required by general user as user is not concern with high calculation for great accuracy..64 bit os will be for next generation ...I think... ;-)....

---

### Post by sid0972 on 2012-08-19
> **681ankit said:**
> Why to download 64 bits...Is it better than 32..??? there is no performance change if you have 4 gb or less ram...Rather processor will have to work with 64 bits of registers which is not required by general user as user is not concern with high calculation for great accuracy..64 bit os will be for next generation ...I think... ;-)....

why not to download 64 bit OS?
i have 64 bit version of ubuntu, and works flawlessly
and its not like working with 64 bit os slows down the computer.

and OP, installing it is very easy, you can follow some guide if you have problems, and the best part is you can access internet while installing it side by side

---

### Post by anewguy on 2012-08-19
Should be faster than 32-bit.  All transfers, not just calculations, will be done on that boundary.

---

### Post by 681ankit on 2012-08-19
> **sid0972 said:**
> why not to download 64 bit OS?
i have 64 bit version of ubuntu, and works flawlessly
and its not like working with 64 bit os slows down the computer.

and OP, installing it is very easy, you can follow some guide if you have problems, and the best part is you can access internet while installing it side by side

okey .. i'm not saying 64 bit is not good...But i say that 32 bit can also be downloaded..and i know 64 bit processes 64bits in 1 cycle

---

### Post by Jakin on 2012-08-19
Considering Ubuntu is now Multi-arch, there is no good reason not to choose the 64bit version. Anything you can do on x86, you can do on x86_64 *PLUS*, this includes installing dual versions of libraries, if needed.
 There is the added speed everyone has mentioned too. Also if you ever do go above 4gb with the ram, then your system can take full advantage; 32bit cannot- if it EVEN recognizes the full 4gb or ram you have.

---

### Post by mastablasta on 2012-08-19
> **Frank O said:**
> I have an x86_64 laptop running Windows 7 whose disk got corrupted beyond repair. I'd like to buy a new hard drive for the laptop and install a flavor of Unix to practice on.

you can just boot from the media (CD/DVD or USB - use unetbooting or linux live usb creator) and select try it from that. linux has a live OS environment (everything loads into RAM and so no changes are done to computer). install process is easy. this is how it looks like: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

you can also put it in a virtualbox. it's quite easy&fast: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

for testing and playing arround an 8 gb key is enough. those are cheap. no need for hard disk here... if you just want to run it live (maybe even with some persistance) then 1 Gb USB key  is enough.

---

### Post by anewguy on 2012-08-22
+1 to what bodhi.zazen and mastablasta have said.  If you have a 64-bit processor, use 64-bit.  Many more optimizations, etc., in it.  Do try as mastablasta suggested to see what you like.

Yes, the 32-bit will run on a 64-bit processor, but use the 64-bit version and you'll be happy.

As far as your existing hard disk goes, you mention it got corrupted beyond repair and that you wanted to replace it with a new drive.  First off, when you say corrupted do you mean the disk and/or drive is physically damaged?  If not, and it's a "logical" corruption that stopped Windows from booting, do try installing to it first to see if it will work - if so, you've saved some money.

---

