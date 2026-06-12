---
title: "New installation - Read error"
date: 2015-08-13
forum: New to Ubuntu
---

### Post by duncan9 on 2015-08-13
Hi, I'm hoping someone can help me. Please excuse my ignorance.

I have a laptop and have wiped XP from it with the 'erase and install' function whilst installing 14.04.3 LTS. I got a short error message at the end about a grub error and now when I boot it just goes to 'read error'.

I have tried to download a couple of tools but I can't connect to Wifi at the moment (on this laptop - I can download anything I need to a key and try that). I will fix the wifi when I have Ubuntu fully installed. 

The live CD works fine.

Any help would be gratefully received!!

Best,

Duncan

---

### Post by nerdtron on 2015-08-13
> I have a laptop and have wiped XP from it with the 'erase and install'  function whilst installing 14.04.3 LTS. I got a short error message at  the end about a grub error and now when I boot it just goes to 'read  error'

You can try to install again. Choosing "Erase and Install". See if there is improvement.

Have you tried to check the CD for defects? Like when the Live CD boots, press the shift key, instead of choosing Try Ubuntu, choose "Check CD for defects".

By the way, what is the model/specs of the laptop? Maybe Xubuntu will have better performance if it's an old machine.

---

### Post by Geoffrey_Arndt on 2015-08-13
Duncan,

We need to know the basic specs of your laptop:

>  make/model
>  what video chipset . . . nvidia ??, ati ??, intel  ?? (e.g., Intel 3100, 4000,
>  what wifi chipset . . . broadcom, intel, atheros, realtek 
>  how much ram (2 GiB is minimum for Ubuntu with Unity desktop)
>  what cpu and speed
>  how much free hdd space
>  am assuming no other OS on laptop per your info

---

### Post by sammiev on 2015-08-13
Have you checked your ISO download for errors?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Just a thought.

Then you have all the above post.

---

### Post by duncan9 on 2015-08-14
Hi all, many thanks for the replies. It is a Compaq Presario 2100. I've had a quick look at the requirements for Ubuntu and it appears that it only has 456Mb of RAM which appears to be below the minimum requirement for Ubuntu (although it seems to be running from the Live CD and previously ran Windows XP fine).

Reading through the above, would I be better to try Xubuntu?

---

### Post by Geoffrey_Arndt on 2015-08-15
Yikes . . . that's a salty old dog all right!

But, we might still "kick some life into it" by trying to install "Lubuntu" . . . it's even lighter than Xubuntu (although Xubuntu is an excellent distro and worth a try). 

Another alternative would be "AntiX" . . . . using the "FLuxbox" desktop.   It's probably the lightest Linux distro that still has all the functionality needed.   You can get it from the usual sources such as [http://www.distrowatch.com](http://www.distrowatch.com) (scroll down to the distro listing on right side.).

EDIT:   just looking a bit further at your options, I think unless you can bump memory up to 2 GiB ram, AntiX is your best bet (Lubuntu & Xubuntu really want 1 GiB minimum to run all normal web services at above a snails pace).

---

### Post by duncan9 on 2015-08-15
Thanks for all the replies. I've tried Ubuntu, Xubuntu and Lubuntu. I've tried each ISO on a separate DVD/CD but am getting the same error with each one. 

Unable to install GRUB in /dev/sda
Executing 'grub-install /dev/sda failed.

This is a fatal error.

I've checked the hard disk for errors each time and each time it has reported that there are no errors. I've 'tried' Ubuntu and Xbuntu (no option to do this with Lubuntu) and it seems to work fine even with the limited amount of RAM. 

There was XP on this machine before I started and I think this may be causing the problem. Maybe?

---

### Post by Geoffrey_Arndt on 2015-08-15
No, XP not the issue but the hard drive partitioning scheme may give a clue as to what's going on.

Suggest you use Xubuntu to load the live version (Try Xub . .), and then find the program "gparted".    Start it and when the partition schematic displays, take a screenshot and post here so we can see your PC's layout.

(note - - an easy way to do this is using Imgur or similar web hostiing service)

---

### Post by duncan9 on 2015-08-15
Many thanks for your help. Far from perfect image but hopefully it works........

[IMG][IMG]http://i.imgur.com/dlGio6k.png?1[/IMG][/IMG]

---

### Post by Geoffrey_Arndt on 2015-08-16
> **duncan9 said:**
> Many thanks for your help. Far from perfect image but hopefully it works........

[IMG][IMG]http://i.imgur.com/dlGio6k.png?1[/IMG][/I
MG]

OK, as Ubuntu is the only OS, it would be simpler to have just two partitions (sda1 for ubuntu and another system id'd partition for swap.   Swap could also be bumped up to a 1 or 1.5 GiB)

On my PC's, the mount points are /media/user1, user2, user3 etc.   Is "ubuntu" the name and ID of your home directory?   Did you create a user - - am wondering if you have a write permissions issue on sda1 so grub couldn't be written there.

I would suggest a total or new reinstall after you've merged your  partitions.

When you do the install, be sure to use a standard mount point of just root (/), and be sure when prompted, you point grub to be written to sda.

Even if this cleans things up - - you may still have issues on this old device, especially if you have a proprietary graphics chipset (nvidia or ati).   

And - - if it was my machine, I wouldn't even mess with any Ubuntu (including Xubuntu or Lubuntu) - - just too much.   Antix with it's much lower requirements is a much better fit.

Good luck and let us know how it goes.

---

### Post by duncan9 on 2015-08-18
Thanks so much for your help Geoffrey. I'll take your advice and try Antix. Should I try and partition the drives using Gparted first? Excuse my ignorance - I may need some step by step guidance!!

---

### Post by Geoffrey_Arndt on 2015-08-19
I think the AntiX installer also has an option to install AntiX using the "whole disk" . . . in which case it should overwrite your existing data and partitions.   So, using gparted ahead of the install may be unneeded.  But, it wouldn't hurt either to use gparted to simplify your partiteoning on that smallish hard drive.

Perhaps the easiest way to learn gparted is to head over to "youtube" and search for gparted.   Watch 4 or 5 videos (some are kind of old) . . however the basic operations remain pretty much the same.   IF you don't already have critical or important data on the PC, treat this PC as your "sandbox" or learning PC.   Have a lot of fun!

---

### Post by oldrocker99 on 2015-08-19
It's also a very good idea to create a small root partition (64 GB is hard to fill up with programs) and use the rest of the drive as a separate /home partition, which can be created with the "Something Else" option in the installer. If you ever have to reinstall, you reformat the / partition and mount the second partition as /home, but don't reformat it, so all your settings, music, photos, videos, etc will be preserved.

Here's the official Ubuntu skinny on how to do it:[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving).

---

### Post by duncan9 on 2015-08-20
Thanks everyone.

I've installed AntiX and it went swimmingly. I have one problem now and that is the network connecting and then dropping a few second later but have enquired on the AntiX forum.

Many thanks again!!

Best,

Duncan

---

### Post by Geoffrey_Arndt on 2015-08-20
Good to know Duncan!.    I think it's a good idea to backup your networking hardware . . . I like to use a nano size dongle like the "panda ultra wireless n usb adapter 150mbps - 802.11n 2.4ghz".   It's available on Amazon and similar sites (newEgg) for about $10. and is just "plug & play" on most all linux distros (and AntiX is based on Debian stable* I believe).

[http://www.amazon.com/Panda-Ultra-150Mbps-Wireless-Adapter/dp/B00762YNMG/ref=sr_1_1?ie=UTF8&qid=1440088674&sr=8-1&keywords=panda+ultra+wireless+n+usb+adapter+150mbps+-+802.11n+2.4ghz](http://www.amazon.com/Panda-Ultra-150Mbps-Wireless-Adapter/dp/B00762YNMG/ref=sr_1_1?ie=UTF8&qid=1440088674&sr=8-1&keywords=panda+ultra+wireless+n+usb+adapter+150mbps+-+802.11n+2.4ghz)

* Edit:  based on Debian "Testing" (like Ubuntu)

---

