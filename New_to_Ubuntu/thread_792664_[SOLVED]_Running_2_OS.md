---
title: "[SOLVED] Running 2 OS"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by kovankerckhoven on 2008-05-13
Hello, I might be making a complete fool of myself here :D
But I was wondering if I could run (temporary only) Windows
& Ubuntu on the same computer (desktop)?

If there are any ppl that think they can help me, plz respond,
as I would really like to become part of this growing and
actually amazing community. :)

thx in advance

---

### Post by teamkiller87 on 2008-05-13
You can achieve this without installing anything for the moment. Just download the LiveCD from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) . Burn the image to a CD and boot from it... You will be able to use Ubuntu without installing. As for dual-booting there are dozens of guides and how-to's on the net... You can start with this one [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by kovankerckhoven on 2008-05-13
I've already downloaded the liveCD, So I'm supposed to burn it onto a CD and boot from it? Won't I be missing out on some functions if I do that then?

---

### Post by meech on 2008-05-13
This is pretty common and is called dual booting. With windows and Ubuntu, windows needs to be installed on an earlier, faster part of your hdd. Before attempting any installs, make sure you give consideration to how much space you have and can allocate to necessary partitions you will be making. For example, will you need a disk partition that can be accessed by both os's, which os will be the one you're using the most and need more space for, etc. 

It's been awhile but I can help you with some more information. Don't hesitate to google your questions; there is a wealth of information both there and in these forums. Don't hesitate to ask! :)

---

### Post by Dani Filth on 2008-05-13
> **kovankerckhoven said:**
> Hello, I might be making a complete fool of myself here :D
But I was wondering if I could run **_(temporary only)**_ Windows
& Ubuntu on the same computer (desktop)?

If there are any ppl that think they can help me, plz respond,
as I would really like to become part of this growing and
actually amazing community. :)

thx in advance

If you meant temporary then you can try virtual machine, VMWare perhaps :popcorn:
Otherwise, follow the Dual Boot guide which can be searched in the forum :D

---

### Post by kesman on 2008-05-13
> **kovankerckhoven said:**
> I've already downloaded the liveCD, So I'm supposed to burn it onto a CD and boot from it? Won't I be missing out on some functions if I do that then?

It will be a little slow since it reads the CD all the time, and you can't save anything, it's all gone after you reboot. Otherwise, you can do almost everything you would with an installed system, browse net, play games, create documents, irc, msn etc...

---

### Post by kovankerckhoven on 2008-05-13
You mean I will need to have a part of my HD to run Ubuntu, and another part for Windows?

---

### Post by kesman on 2008-05-13
> **kovankerckhoven said:**
> You mean I will need to have a part of my HD to run Ubuntu, and another part for Windows?

Yeah, partitions. You need one for windows and two/three for ubuntu. The LiveCD contains a partition editor under system-menu that you can use to view your current partitions. If you decide to install ubuntu, it will guide you to partition your hard disk.

Be careful to use unpartitioned space and learn to remember the names of partitions. I guess your windows partition will be names as hda1/sda1 depending of the type of your HD, and linux partitions will be hda2/sda2, hda3/sda3 and hda4/sda4

---

### Post by kovankerckhoven on 2008-05-13
> **kesman said:**
> It will be a little slow since it reads the CD all the time, and you can't save anything, it's all gone after you reboot. Otherwise, you can do almost everything you would with an installed system, browse net, play games, create documents, irc, msn etc...

Can I actually use Windows Live Messenger on Ubuntu?

---

### Post by kesman on 2008-05-13
If you must, I think wine(windows "emulator") can run it, but a much better way to MSN is use Pidgin, a linux instant messenger which also supports msn accounts.
It's a bit different from windows live messenger, but everything in linux is different from windows. It's up to you if you decide to like it and give it a try or not.

---

### Post by hyper_ch on 2008-05-13
> **kovankerckhoven said:**
> Can I actually use Windows Live Messenger on Ubuntu?

NO, but there are replacement programs like aMSN..

Before you start installing Ubuntu do:

(1) BACKUP of your important data

(2) DEFRAG your windows drive 2-3 times

the following steps I recommend but aren't required

(3) Get a windows partitioning tool

(4) Resize the windows partition

(5) Leave the freed space unpartitioned

----------------

During the install you can then choose something ilke "select largest continouuse empty space".

Make sure it says "EMPTY" there, otherwise you might overwrite the whole disk.

---

### Post by kovankerckhoven on 2008-05-13
> **kesman said:**
> Yeah, partitions. You need one for windows and two/three for ubuntu. The LiveCD contains a partition editor under system-menu that you can use to view your current partitions. If you decide to install ubuntu, it will guide you to partition your hard disk.

Be careful to use unpartitioned space and learn to remember the names of partitions. I guess your windows partition will be names as hda1/sda1 depending of the type of your HD, and linux partitions will be hda2/sda2, hda3/sda3 and hda4/sda4

So if i had a 300 gig Hd it would be 100 gig for windows, and 200 for Ubuntu?

---

### Post by kesman on 2008-05-13
It's up to you how much you'd like to give ubuntu. With that space, I would start with ~50gig for ubuntu and later on resize the partitions if you ever need more than that.

---

### Post by kovankerckhoven on 2008-05-13
> **kesman said:**
> It's up to you how much you'd like to give ubuntu. With that space, I would start with ~50gig for ubuntu and later on resize the partitions if you ever need more than that.

What if I only had a 80Gig HD (which I can clear to almost 20Gig for files left by burning dvd's) so i have 60gig ... Do u think I would be able to give Ubuntu 50 and Windows would have enough with 30?

---

### Post by kesman on 2008-05-13
Yeah, it's all up to you, how much you got data on the drive. If you can free up at least 5gb for ubuntu, it will work perfectly.

---

### Post by kovankerckhoven on 2008-05-13
> **kesman said:**
> Yeah, it's all up to you, how much you got data on the drive. If you can free up at least 5gb for ubuntu, it will work perfectly.

5Gig would be no problem at all :D

do I need to backup my data to run Ubuntu from boot cd?

---

### Post by kesman on 2008-05-13
> **kovankerckhoven said:**
> 5Gig would be no problem at all :D

do I need to backup my data to run Ubuntu from boot cd?

If you aren't planning to install it yet, you don't need to back anything up. Just insert the cd and reboot your computer. There's an icon on the ubuntu desktop with "install" text on it. Clicking it will start the install wizard which will guide you. It will also recommend backing up your data.

To sum up: for liveCD use, don't backup. For faster use(installed system), backup.

---

### Post by kovankerckhoven on 2008-05-13
K guys thank y'all, I'ma go and try the liveCD boot now, be back in a few mins to c if I got any other questions ;)

---

### Post by kovankerckhoven on 2008-05-13
Hi Guys, I installed Ubuntu as a windows application, and although it took a while before my hardware was configured (i had to get a keyboard with ps2 from the attic), I am quite satisfied with it.(I am even writing this reply in ubuntu right now!)

I will be considering making Ubuntu my only OS as soon as I get the 500Gig HD i ordered :) Thx u guys for helping me out

---

### Post by kesman on 2008-05-13
Great job! The windows installer was a good choice. For applications, check out add/remove applications, they're all there :D

---

### Post by kovankerckhoven on 2008-05-14
> **kesman said:**
> Great job! The windows installer was a good choice. For applications, check out add/remove applications, they're all there :D

I got a problem guys; having Ubuntu installed as a component of Windows, I have been busy transferring all my files to see how everything works, but I cannot seem to install Java :S I have to install it through the terminal window, and as I press 'su', it asks me for my root password. What is this password? (It isnt my Ubuntu login password or username, and I even tried my MySQL root password, which didn't work :S) help plz !

---

### Post by kesman on 2008-05-14
You can install Java from synaptic package manager.
For su, you don't use it in Ubuntu. Use sudo in front of a command instead.

---

