---
title: "Hi, noob here...is it safe to dual boot?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by brjones80 on 2008-08-20
I'm a complete linux noob, but I've just started experimenting with Ubuntu and I love it so far (currently I have it running in VMware loaded on an XP machine).

I'd like to learn more and thus, would like to install it on actual hardware (instead of virtually), that way I can get a sense for how it interacts with physical hardware, drivers, and such.

So, I'm thinking about creating a dual boot XP/Ubuntu system.  It seems this is very common, and I've already read the manuals on how to set it up, but my question is, are there any dangers?

I've heard stories (not sure how true they are) about people losing their Windows partition when they have a dual-boot setup.  Any truth to this?

Thanks guys, I look forward to becoming a real Ubuntu user.

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by sandysandy on 2008-08-20
how many partitions do u have. 

if u need to resize ur XP partition to make room for creating ubuntu partitions, do defragment XP before resizing.

take backup!

see these links on dual boot

[http://apcmag.com/how_to_dual_boot_w...lled_first.htm](http://apcmag.com/how_to_dual_boot_w...lled_first.htm)

[http://www.howtoforge.com/dual_boot_..._ubuntu_feisty](http://www.howtoforge.com/dual_boot_..._ubuntu_feisty)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


regards

---

### Post by alecz20 on 2008-08-20
Hi there,

I have setup a few dual-boot systems. Also I know a few people that did the same. None of us had any problems with losing the Windows partition.

**However**, you can destroy your Windows partition if you don't so it right.

In Ubuntu 7.10 (which I installed on dual boot systems), you have to resize the Windows partition and create a new one on which you install Ubuntu. If you choose "use the entire disk" you will obviously lose you Windows.

Here's a guide:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Alternatively you can use WUBI to install Ubuntu 8.04.1 side by side with Windows on the same partition. (For some reason I don't feel comfortable doing that).

Since you've never done this before you might screw up, so I suggest you back-up important documents on an external HDD or DVD or something. Also defrag Windows before resizing the partition.

Good luck!

Edit:
you might also want to check this out:
[http://www.google.ca/search?hl=en&q=Ubuntu+Windows+XP+dual+boot&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=Ubuntu+Windows+XP+dual+boot&btnG=Google+Search&meta=)

---

### Post by timcredible on 2008-08-20
the only way you'd lose your windows partition is if you erase it when installing ubuntu.  the installer does give you the option of using the entire disk for ubuntu, which WILL erase windows.

---

### Post by brjones80 on 2008-08-20
Okay...so assuming I install it correctly, and barring any future USER error, there's not much danger in doing this?

For instance, file corruption due to a glitchy system (outside of any usual glitches experienced by a single-boot system)?

---

### Post by alecz20 on 2008-08-20
> **brjones80 said:**
> Okay...so assuming I install it correctly, and barring any future USER error, there's not much danger in doing this?

For instance, file corruption due to a glitchy system?

Never happened to me, and never heard of it.

Note that Windows partitions will be accessible from Linux, so you can still destroy your Windows if you want to (again depends on USER)

---

### Post by brjones80 on 2008-08-20
> **alecz20 said:**
> Never happened to me, and never heard of it.

Note that Windows partitions will be accessible from Linux, so you can still destroy your Windows if you want to (again depends on USER)

okay, well that makes me feel better.  I'm pretty competent when it comes to computers in general, I'm just new to linux.  I understand partitioning, and general hardware stuff, so I think I'm gonna go for it.

Thanks for the links and advice guys :)

---

### Post by alecz20 on 2008-08-20
Don't forget it's wise to backup important stuff!

(Think of term papers, compositions, your parents files, whatever)

---

### Post by brjones80 on 2008-08-20
> **alecz20 said:**
> Don't forget it's wise to backup important stuff!

(Think of term papers, compositions, your parents files, whatever)

That was going to be my first step...I think I'm just going to take a ghost image of my drive.

Also, would it be advantageous for me to just forget partitioning and put in a second HDD to put Ubuntu on?  Would it work better/worse that way?

---

### Post by sandysandy on 2008-08-20
dual booting on same hard disk is not an issue.

but i recommend u read up before u do that.

see the links i have posted above in post #3.

regards

---

### Post by alecz20 on 2008-08-20
That way you get more total HDD space, and if one HDD fails you can still use your computer from the other HDD.

Apart from that, I don't see other advantages, but I might be wrong.

Well, I guess you have less chances of damaging your Windows. Also, you probably should keep the Windows disk in there (since it's primary and has the MBR)

---

### Post by brjones80 on 2008-08-20
> **alecz20 said:**
> That way you get more total HDD space, and if one HDD fails you can still use your computer from the other HDD.

Apart from that, I don't see other advantages, but I might be wrong.

Well, I guess you have less chances of damaging your Windows. Also, you probably should keep the Windows disk in there (since it's primary and has the MBR)

I would keep both of them, and dedicate one for Windows and the other for Linux.  Is it harder/easier to set up a dual-boot system that way?

---

### Post by alecz20 on 2008-08-20
> **brjones80 said:**
> I would keep both of them, and dedicate one for Windows and the other for Linux.  Is it harder/easier to set up a dual-boot system that way?

It is probably a bit easier, since you don't have to resize the Windows partition.

Still, I would manually create 1 ext3 partition and 1 swap (both)on the 2nd HDD.

This advantage, however is only  applicable when you install. Once you successfully installed and have dual-boot you won't notice it that much.

If you have the extra HDD, you should probably go for it.

Edit: Also follow up on sandysandy's links for some tutorials. You can also browse the Internet from the live CD, so that's a plus.

---

### Post by cybrsaylr on 2008-08-21
Make sure to read the setup instructions for a dual boot till you understand them.
Get familiar because it can be confusing if you are only used to Windows. 
When I did my first setup I overwrote part of XP and only Ubuntu would boot because of setting up the wrong size partition. I lost XP. Had to format and start all over. Now my two dual boot systems run fine.

---

### Post by brjones80 on 2008-08-21
> **cybrsaylr said:**
> Make sure to read the setup instructions for a dual boot till you understand them.
Get familiar because it can be confusing if you are only used to Windows. 
When I did my first setup I overwrote part of XP and only Ubuntu would boot because of setting up the wrong size partition. I lost XP. Had to format and start all over. Now my two dual boot systems run fine.

It must've been that sort of flub I was reading about...I'm glad to hear that merely running the two on one computer doesn't cause a problem.

I'm definitely going to create a Ghost backup then, before I begin :)

---

### Post by sharks on 2008-08-21
I have been dual booting . i havent had a problem with it.

---

### Post by stalkingwolf on 2008-08-21
One advantage of using a seperate drive for linux is not
having to mess with partitioning.  You can just select
use entire drive and it sets up your swap and / automatically.

I would suggest if you are going to do it this way that you run
gparted from the live CD and make note of how your drives are named.  This will help to insure you select the proper drive. Then just close gparted and hit install.

When I do it this way the second drive is greyed out until I select it.   tick  the box then the options for that drive are available

---

### Post by brjones80 on 2008-08-21
> **stalkingwolf said:**
> One advantage of using a seperate drive for linux is not
having to mess with partitioning.  You can just select
use entire drive and it sets up your swap and / automatically.

[B]I would suggest if you are going to do it this way that you run
gparted from the live CD and make note of how your drives are named.  This will help to insure you select the proper drive. Then just close gparted and hit install.[/B]

When I do it this way the second drive is greyed out until I select it.   tick  the box then the options for that drive are available

Understood, thanks for the tip :)

Edit:  One other question.  If I have XP and Ubuntu loaded (in a dual-boot setup), is my XP partition vulnerable to viruses while I'm using the Linux part?  Say, a windows virus or something, which would be harmless to the linux side?

---

### Post by alecz20 on 2008-08-21
> **brjones80 said:**
> Understood, thanks for the tip :)

Edit:  One other question.  If I have XP and Ubuntu loaded (in a dual-boot setup), is my XP partition vulnerable to viruses while I'm using the Linux part?  Say, a windows virus or something, which would be harmless to the linux side?

Yes and No.

You may still get an infected file, but it should not spread the infection under Linux.

So let's say you download some .exe file. Even if you run it in WINE it should not infect the Windows system. If you run it from Windows, then it will infect the Windows system.

You can also run and Anti-virus in Linux, and scan for both Windows and Linux viruses. The most popular one is included in the repos. ClamAV I think.

Hope this helps

---

### Post by Kyle1981 on 2008-08-21
I think it will be safe. but it may lead to some troubles if you reinstall your system. so I recommend you to install a single system. you can backup your data to another device. I can use ubuntu to do most things I would like.

---

### Post by alecz20 on 2008-08-21
> **Kyle1981 said:**
> I think it will be safe. but it may lead to some troubles if you reinstall your system. so I recommend you to install a single system. you can backup your data to another device. I can use ubuntu to do most things I would like.

While I generally agree with you (thinking myself about removing Windows from the Dual Boot. The fact of life is some people will still need Windows somewhere handy.

If one has both a laptop and a desktop, they should probably have Linux on laptop and Windows or Dual-boot on Desktop.

If I go to a LAN party with my friends... I need Windows...:(

---

### Post by tarps87 on 2008-08-21
One advantage of using two hard drives is if you need to reinstall windows you can set it a the master drive and remove the Ubuntu one, once you've reinstalled you can put the Ubuntu drive back in and you won't have to mess about with the bootloader. This is assuming when you install Ubuntu the drive you are installing it onto is set to master, this way the grub will stay with the Ubuntu drive.

---

### Post by alecz20 on 2008-08-21
> **tarps87 said:**
> One advantage of using two hard drives is if you need to reinstall windows you can set it a the master drive and remove the Ubuntu one, once you've reinstalled you can put the Ubuntu drive back in and you won't have to mess about with the bootloader. This is assuming when you install Ubuntu the drive you are installing it onto is set to master, this way the grub will stay with the Ubuntu drive.

I think this would complicate things. The system will read the MBR on the master and will read the available OS's from there. If you have to HDD's and you installed an OS on each individually, I think you need to change the master from BIOS everytime you want to boot in a different OS.

---

### Post by tarps87 on 2008-08-21
> **alecz20 said:**
> I think this would complicate things. The system will read the MBR on the master and will read the available OS's from there. If you have to HDD's and you installed an OS on each individually, I think you need to change the master from BIOS everytime you want to boot in a different OS.

If Ubuntu is the master drive and the windows one connect when installed Ubuntu is installed it will add the windows to the boot list, I have it set up this way which paid off when I got a virus and had to reinstall xp. I removed the Ubuntu drive set the xp one to master reinstalled, set the Ubuntu on back to master and reconnected it. It then ran a normal without having to reinstall the grub to the MBR, I can boot Ubuntu or XP just as you could if it was on the same drive. I only done this as I was to lazy to mess about with the MBR and the side of my tended to be open at that time.

---

### Post by brjones80 on 2008-08-21
> **tarps87 said:**
> One advantage of using two hard drives is if you need to reinstall windows you can set it a the master drive and remove the Ubuntu one, once you've reinstalled you can put the Ubuntu drive back in and you won't have to mess about with the bootloader. This is assuming when you install Ubuntu the drive you are installing it onto is set to master, this way the grub will stay with the Ubuntu drive.


Interesting...I think my computer right now has an IDE drive in it.  I set master and slave using the jump switches right?  Are SATA drives configured using BIOS then?

---

### Post by linuxguymarshall on 2008-08-21
I think on the new Ubuntu Live CDs it is all automated. Once you get to the partitioning you just drag the bar around and select how much space you want each to have.

---

### Post by tarps87 on 2008-08-22
> **brjones80 said:**
> Interesting...I think my computer right now has an IDE drive in it.  I set master and slave using the jump switches right?  Are SATA drives configured using BIOS then?

I use two IDE drives, I only have to change the jump switches when I'm using just the xp drive, when I'm dual booting the Ubuntu drive is master the xp is slave and I just use the grub/ bootloader to select Ubuntu or xp. I don't need to change any master/ slave or bios settings under normal use, it behaves like any other dual boot system. I assume it is possible with SATA drives but have not tried it.

---

### Post by Briped on 2008-08-22
Another piece of advice is - if you download and burn your own ISO image, do check the MD5 sum of the download. Clever me didn't. 'oh no, it's probably fine', so went ahead and screwed up my first dual boot install = in the end a lost windows partition.
My second dual boot install (different desktop)? lost my windows partition too, but that was because I found out my HD had bad sectors, so I chose to invest in a new. So yes, loosing a windows partition will happen for different reasons.](*,)

Britta

---

### Post by cometa2k7 on 2008-08-22
> **brjones80 said:**
> Okay...so assuming I install it correctly, and barring any future USER error, there's not much danger in doing this?

For instance, file corruption due to a glitchy system (outside of any usual glitches experienced by a single-boot system)?

If you install Hardy 8.04 you have to type an administrator password in when you try to open another internal partition (ie. your Windows partition). This should stop anyone else from messing up Windows while using your Ubuntu install.

I have Hardy dual-booting with Vista at the moment, and I have only one problem. If I boot into Windows, then hibernate, boot Linux, and reboot into Windows again, I lose my internet connection. It's annoying, but it's more a hardware issue than anything else I think.

You shouldn't encounter any real problems, and corruption of a drive shouldn't happen. You are more likely to mess up your Windows partition by using Windows than by using Linux. :lolflag:

---

