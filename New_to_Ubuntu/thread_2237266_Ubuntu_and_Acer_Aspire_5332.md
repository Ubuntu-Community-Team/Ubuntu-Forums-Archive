---
title: "Ubuntu and Acer Aspire 5332"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by sunnycreatives on 2014-07-31
Hi all...have googled how to install Ubuntu on my laptop but the 5332 isn't listed any place I have looked.

Does this mean I can't do this or have I missed something?

I no longer have a desktop and only have this laptop so am suffering Ubuntu withdrawal...lol

---

### Post by yancek on 2014-07-31
You need to post some information on your laptop rather than expecting others to look up that information.  Processor, RAM, graphics card, other operating system(s) if any.

---

### Post by sunnycreatives on 2014-07-31
> **yancek said:**
> You need to post some information on your laptop rather than expecting others to look up that information.  Processor, RAM, graphics card, other operating system(s) if any.

Not meaning to be awkward...but I posted this in the absolute beginners section because I am an absolute beginner re: laptops in combination with Ubuntu having only ever used a desktop and an Ubuntu disc in the past.

I googled how to install Ubuntu on an Aspire laptop and found a list of model instructions but not for my laptop 

Will go off and google how to find the info you would have liked to have seen.

---

### Post by sunnycreatives on 2014-07-31
Ok...OS is Windows 7 home edition

Processor: Celeron (R) Dual Core CPO T3000 @ 1.80 GHz 1.79 GHz

RAM 3.00 GB

System type 64 bit Operating System

---

### Post by kira-yamato-2008 on 2014-07-31
Go for Lubuntu, or Xubuntu. I have three gigs on a Turion X2 @2.00 ghz also with 3 gigs ram and Ubuntu can be a bit problematic in such a low ram environment. But I know that Lubuntu is blazingly fast and multitasks like a pro on about 3 gigs.

---

### Post by sunnycreatives on 2014-07-31
> **kira-yamato-2008 said:**
> Go for Lubuntu, or Xubuntu. I have three gigs on a Turion X2 @2.00 ghz also with 3 gigs ram and Ubuntu can be a bit problematic in such a low ram environment. But I know that Lubuntu is blazingly fast and multitasks like a pro on about 3 gigs.

Many thanks for your reply....I am just missing the Ubuntu right now.

Might run an Ubuntu disc as an experiment but will look at Lubuntu as well ...just want to feel at home on the laptop...just got used to the ease of use after  years of faffing about with Windows and then going back to it with this laptop that was given to me recently.

---

### Post by Rob Sayer on 2014-08-03
If you've used ubuntu in the past, just burn the iso file to cd or USB stick preferably, boot, open a terminal, enter the commands to find out what the hardware adapters are (esp. graphics and wireless), search for "ubuntu <whatever adapter>" .  No different than with a desktop.

You can do this in windows with system information or whatever it was but I find linux gives you better, more specific info on hardware.

---

### Post by 3rdalbum on 2014-08-03
> **kira-yamato-2008 said:**
> Go for Lubuntu, or Xubuntu. I have three gigs on a Turion X2 @2.00 ghz also with 3 gigs ram and Ubuntu can be a bit problematic in such a low ram environment. But I know that Lubuntu is blazingly fast and multitasks like a pro on about 3 gigs.

Dude, what? 3 gigs of RAM is NOT a "low-RAM environment".

Ubuntu will run very well with 3 gigs RAM. It even runs alright on 1 gig.

OP: The general instructions for installation on the Ubuntu site should work just fine on your computer. Ubuntu usually sets itself up to your computer automatically.

---

### Post by sandyd on 2014-08-03
> **3rdalbum said:**
> Dude, what? 3 gigs of RAM is NOT a "low-RAM environment".

Ubuntu will run very well with 3 gigs RAM. It even runs alright on 1 gig.

OP: The general instructions for installation on the Ubuntu site should work just fine on your computer. Ubuntu usually sets itself up to your computer automatically.

This.

I have chrome with a bazillion tabs open, along with hexchat, and a few other apps in KDE (Kubuntu), and my RAM usage still comes up to
```

resurrectedstar@PrincessSophie:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7838       4400       3437        203        124       2274
-/+ buffers/cache:       2001       5837
Swap:        10239          0      10239

```

---

### Post by yancek on 2014-08-03
```
I googled how to install Ubuntu on an Aspire laptop and found a list of model instructions but not for my laptop 

```

Installing to a specific brand name computer or whether it is a desktop or laptop usually doesn't matter that much.  Things people usually have trouble with are wireless cards and some graphics cards.  The specs you posted should enable you to run any version of Ubuntu with the above caveats, won't know until you try.  There is a tutorial on the Ubuntu site for install alongside and the second link below is an extremely detailed explanation of it with a lot of other very useful information:

 [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Jin_Long on 2014-08-04
> **sunnycreatives said:**
> Hi all...have googled how to install Ubuntu on my laptop but the 5332 isn't listed any place I have looked.

Does this mean I can't do this or have I missed something?

I no longer have a desktop and only have this laptop so am suffering Ubuntu withdrawal...lol

wow... so, @sunnycreatives ... i'm just gonna say that these people are not explaining things at a basic level for the beginner. i say this because... i'm a beginner, and i get where you're coming from. just because a couple of people have souped up laptops doesn't mean they need to go posting their own specs as a pissing contest in a forum where a new guy is asking wth he should do.

here's the basic, broken down answer. it helps to print the instructions, view them on a smart phone as you're doing it, or write them down if you have to:

1. download the ".iso" file. since you have a 64bit computer, then you'll want the 64bit version of ubuntu. to download the 64bit version, go to [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) , make sure "64-bit" is selected on the list (it should be the default option), and click "Download". 64bit ubuntu will download - save it to your desktop for easy access. it says "ubuntu desktop". that's okay - it's also the same one used for laptops.

2. burn the ".iso" file to a dvd. keep the dvd in your disk drive.

3. turn off your computer. turn it back on, and at the initial boot screen, click [F11], [F12], or whatever button your computer requires in order to "change boot sequence". that button varies from computer to computer, but it should say at the bottom of the screen.

4. a list should appear, saying "e-sata" (or "sata"), "hdd", "lan", "cd/dvd rom", "usb", etc. use the arrows to go down to "cd/dvd rom" and click [Enter]. don't worry about changing the boot sequence, because sometimes computers don't listen, and you'll just have to change it back anyway. just click [Enter] to boot from the disk.

5. 64bit ubuntu will load up. it will ask you if you want to "Try Ubuntu" or "Install to Hard Drive". you're wanting to install to the drive, so just go for it. i recommend wiping the drive and installing ubuntu over it. no sense in keeping windows 7.

and you should be good. pm me if you need any more help and i'll give it to you straight.

---

### Post by gordintoronto on 2014-08-04
Hi Sunny,

You describe yourself as a beginner, so there are two things you might need to learn about:
 - how to boot your laptop from a DVD or USB stick,
 - how partitions work. For starters, you need to know what partitions are on your computer now. I assume there is a single drive for Windows and all its files, so you will need to use Windows to shrink that to make some space for Ubuntu.

You don't need specific instructions for your computer.

---

