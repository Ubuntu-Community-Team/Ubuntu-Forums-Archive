---
title: "I need some advice"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by tenshou on 2012-03-19
Hi everyone!! I am a new Linux user! So... I have had some trouble with ubuntu 11.04, and im still using windows, but i definitely want to switch to Linux.

I work with PHP and MySQL a lot (and sometimes C++) and i was wondering which distro fits better for me, i did some research and found out that almost all dristo are good for that kind of job, and i also want to learn more about Linux, my friends told me to install Gentoo and i know that Gentoo is good for learning but it is way too hard for me, i spent all day trying to install this beast but i couldn't get it to work after all.

So i decided to try Ubuntu again, i'm pretty sure that i did something wrong when i was trying to install Ubuntu for the first time, maybe my installation file was corrupt or something like that. 

So besides my work with webdevlopment i just surf the web, watch videos on youtube and i play Dofus which is built in Java so... What do you guys think?

---

### Post by snowpine on 2012-03-19
Welcome to the forums! If you'd like to tell us about "some trouble with ubuntu" then maybe we can help. :)

---

### Post by dmouck on 2012-03-19
Welcome to the forum, and welcome to Ubuntu!

As you probably know, there are several linux distros available. Fortunately, most offer a "live mode" where you can boot into and use linux right from the CD. Give a few a try and see how you like the looks of them. Some of the more popular ones are Ubuntu (or course), Linux Mint (based off of Ubuntu), or Fedora. These are just a few of them.

What exactly went wrong when you tried to install Ubuntu? Can you provide more details so that the community can help you through it? If you are used to Windows, any flavor of linux can be new and intimidating, but with some patience and a desire to learn a new operating system, you will do fine. Most of us started using Windows before linux, so we know where you are coming from :).

---

### Post by sudodus on 2012-03-19
Welcome :-)

I suggest that you describe you computer (you have already described what you want to do), cpu, ram, graphics chip or card, wifi or wired internet...

There are several versions of Ubuntu (time-wise) and flavours (desktop-environment-wise), and I suggest that you try several of them live. Download the iso files and make boot CD/USB drives to test before installing!

---

### Post by tenshou on 2012-03-19
Thank you guys!! I just tried the "live mode" but it didn't work, it keeps loading forever, i didn't try the live mode before so i guess my DVD is not working! I don't remember which versions it is, maybe 10.10. So this time i downloaded the 11.10 32bit version and burned it and the live mode is working fine now.

My PC configuration is:
Pentium(R) 4   2.8GHZ
2048MB RAM DDR2
Motherboard: PW-945GCX
Videocard: NVIDIA GeForce 9400 GT 1024MB
wired internet

I have 2 HD's:
SANSUMG HD 80GB
ST 80GB

Kinda old but still good for me!

What is the best way to partition my HD's?
Will i need a SWAP?

Thanks!

---

### Post by snowpine on 2012-03-19
Glad that 11.10 is working OK for you!

The default partitioning scheme is:

swap partition equal to or greater than your RAM
/ partition ("root" partition not to be confused with "root user") with the ext4 format using the rest of the space.

If you have different partitioning needs (for example: you want to dual-boot with Windows, or you want a separate /home partition, or ____) then please be specific. :)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by madjr on 2012-03-19
yeap Ubuntu should be good for you.

I also dev with mysql/php and played dofus for a few years (good memories!) in ubuntu.

cant play anymore because of work. But yeap you're great candidate for linux. :p

ubuntu has the biggest community, so you will always find help much easier.

also this here guide should help:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

and check some resources like 

-the full circle ubuntu magazine (free)
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

-and ubuntu updates here:
[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)

---

### Post by Gleichsnerd on 2012-03-19
I have an old Dell Dimension with specs like that, and I've come to find that Ubuntu (Natty Narwhal, specifically) works best really on that kind of hardware.

Alas, if you want to shoot for a more recent version (or even alpha), feel free; it's your dinosaur! Beware too much Unity, though, as it has a dirty habit of making your life heck on old computers.

Live Disk is generally slow just because your CD/DVD drive isn't nearly as efficient with reading data as a hard drive is. If you're shooting for a hard install straight to HD, I'd recommend keeping your Windows and Ubuntu partitions on separate drives, that way if one drive completely crashes or whatnot, you still have a functional OS (after you fixboot and fixmbr accordingly, but that's for later years :) )

Here's a link to how you can automount your other hard drive once you install:
[http://ubuntuforums.org/showthread.php?t=1927504&highlight=Automount+fstab](http://ubuntuforums.org/showthread.php?t=1927504&highlight=Automount+fstab)


Happy Ubuntu!

---

### Post by madjr on 2012-03-19
unity 2d should fair ok

---

### Post by BertN45 on 2012-03-19
I have a 3.2 gHz Pentium IV with 1.5 GB and I run Ubuntu 12.04 Beta. I am happy with it and in my opinion it is already better (faster and more reliable) then Ubuntu 11.

---

### Post by IWantFroyo on 2012-03-19
Ubuntu 10.10 had some ACPI issues for me. If you ever decide to try it again, I would recommend using the pci=noacpi boot command.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

This doesn't have pci=noacpi, but if acpi=off works, you can add in pci=noacpi later on in your /etc/default/grub.

---

### Post by cortman on 2012-03-19
11.04 and 11.10 have both worked perfectly for me.

---

### Post by sidzen on 2012-03-19
OP said, "I have 2 HD's:  SANSUMG HD 80GB (and) ST 80GB"

Recommend keeping the dominant distro on one and Linux distro on the other;  try Xubuntu 11.04 and partition 15-20Gb for /, a 2GB swap, and the remainder of one hdd for /home; use ext4 for / and /home.

Best wishes with the P4!

BTW, couldn't find specs on that mobo -- where'd you get it?

---

### Post by tenshou on 2012-03-20
I really don't need a fancy desktop, i like performance, so i think Xubuntu will be better, Xubuntu uses Xfce right? So.. Do i install it on Ubuntu?
Do i need to download and install Xubuntu? I got confused :confused:
I found out that i can install Xfce on Ubuntu so what's the point of Xubuntu?

By the way, i don't want to dual-boot my HD's, i will create a separate partition for my /home like sidzen said, i'm not sure yet. Could you guys give me more examples?

Thanks!

---

### Post by mraandtux on 2012-03-20
> **tenshou said:**
> I really don't need a fancy desktop, i like performance, so i think Xubuntu will be better, Xubuntu uses Xfce right? So.. Do i install it on Ubuntu?
Do i need to download and install Xubuntu? I got confused.
I found out that i can install Xfce on Ubuntu so what's the point of Xubuntu?
1: You can install Xubuntu in Ubuntu by Seaching xubuntu-desktop on Software Centre or Synaptic, or just type "sudo apt-get install xubuntu-desktop" on terminal.
What's the point of Xubuntu? See Wikipedia: [http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu)

---

### Post by MG&amp;TL on 2012-03-20
Each *buntu has its own package, xu/lu/ku/ubuntu-desktop, which you can install on any of the versions. You could say that there's no advantage to installing a *buntu other than Ubuntu, but if you only want one sort of *buntu, you save quite a lot of disk space and internet time.

You said php and mysql? [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) might be a good link, if you haven't seen it already.

---

### Post by sudodus on 2012-03-20
> **tenshou said:**
> I really don't need a fancy desktop, i like performance, so i think Xubuntu will be better, Xubuntu uses Xfce right? So.. Do i install it on Ubuntu?
Do i need to download and install Xubuntu? I got confused :confused:
I found out that i can install Xfce on Ubuntu so what's the point of Xubuntu?

By the way, i don't want to dual-boot my HD's, i will create a separate partition for my /home like sidzen said, i'm not sure yet. Could you guys give me more examples?

Thanks!
There are 'flavours' of Ubuntu, that are delivered with different desktop environments, DEs. So instead of getting 'vanilla' Ubuntu and installing another DE, you can download the iso file of

Kubuntu with KDE
Xubuntu with XFCE
Lubuntu with LXDE

Several flavours are described in the following link
[[COLOR="Red"]_http://www.psychocats.net/ubuntu/whichbuntu_[/COLOR]]("http://www.psychocats.net/ubuntu/whichbuntu")

---

### Post by mikaere66 on 2012-03-20
I too am new to Linux ... I first tried Linux Mint 11 but once I discovered Ubuntu, I was hooked. I'm using version 11.10 and find it very stable & customizable. I have a Compaq laptop with 1.73 GHz Duo, 2 Gb RAM, and 120 Gb HDD.

---

### Post by tenshou on 2012-03-20
I just installed xubuntu-desktop here, it's working fine, i like it!! Thanks you guys for all the messages and all the links!

By the way, i am reading this -> [http://wiki.xfce.org/tips](http://wiki.xfce.org/tips) , if you guys have any other suggestions i will appreciate it.

Thanks for the support.

---

