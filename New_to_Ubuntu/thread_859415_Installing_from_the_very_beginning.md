---
title: "Installing from the very beginning"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Taero on 2008-07-14
Hi there, new user here :) I've ran a check for the title and nothing came back so here goes.

I'm about to nuke my laptop in order to start from the very beginning, windows annoys the bejeezus out of me and I want it to die.  I'm using DBAN at it's highest setting, I have some personal pictures, scanned payslips, finance documents, account details saved and I can't afford to take any chances as I'm also debating whether or not to just sell this crappy thing, get what I can and put it towards my new desktop.

Right, so once I've nuked the laptop it'll be 100% wiped, all that will be left is the BIOS as obv. that's motherboard based.  My question is this, if I alter the BIOS to check for the DVD drive before the Harddrive on bootup will the Ubuntu installation DVD (the .iso) automatically start?  And if not how do I boot it, plus does it come with the basic drivers etc.  I can get wireless drivers etc. from my manufacturer but that's no good if it won't recognise my mouse etc :P Will I need to get the graphics card drivers again as well :P?

Any help would be much appreciated I don't feel like hitting GO then thinking...oh dear :)

My laptop currently:
Windows XP
Aspire 5024 WLMI with upgraded RAM

---

### Post by TSS on 2008-07-14
First, the BIOS question.  The boot order will have to be set so your computer boots from the CD drive before the hard disk.  I think most computers are like that now anyway, but it wouldn't hurt to check.  When you start up your computer, you press F10 or the equivilent to access the BIOS.  

Ubuntu has a wide range of drivers and a ton of hardware is supported.  Here is something I dug up with a quick google: [http://ubuntuhcl.org/browse/product+Acer_Aspire_5024_WLMi?id=687](http://ubuntuhcl.org/browse/product+Acer_Aspire_5024_WLMi?id=687)

---

### Post by philinux on 2008-07-14
Make sure you back up all your stuff first.

---

### Post by AnLGP on 2008-07-14
it should boot right away if you have your bios set to boot from cdrom first.

you may or may not have to configure it so things work for you (ie sound etc).  there's good support here, though.

as stated already back up your stuff and good luck!

---

### Post by Taero on 2008-07-14
Thanks for the quick replies :) Yeah I'm going to back everything up to my external HD (Well what there is left of it, my laptop went meltdown, shut down and corrupted itself and had to be reinstalled anyway)  Hopefully I can do this and come out with a fully functioning laptop :P I won't be able to install it until tomorrow or the day after as DBAN takes a LONG time.  Ah well the price of safety.

By the way, what exactly is the difference between Ubuntu and all the others like kubuntu etc.?  I like the look of this one a lot but are there any major differences?

Also would you recommend creating a ghost image of how it is now in case things don't work?  I mean I'm sure they will but my recovery CD won't work after this as the wipe will remove the partition that all the data's stored in.

---

### Post by snowpine on 2008-07-14
Hi Taero, don't worry, booting from the CD should be really easy. Depending on your bios, it might just boot from the CD no problem, otherwise, you'll have to press a F key, like F10 or F12, but no big deal. Spend a little time with the Live CD to make sure Ubuntu works with your hardware, and then just run the Installer to make it permanent. Definitely back up all your important data from the hard drive first!

In terms of the difference between Ubuntu, Xubuntu, Kubuntu, etc. you can read all about it if you do a little research. :) They all have the same kernel, but have a) different desktop user interfaces, and b) different applications. Ubuntu is certainly a good one to start with, if you like the look. You can always add more applications if the default Ubuntu is missing something you need/want.

Good luck!

---

### Post by Taero on 2008-07-14
> **snowpine said:**
> Hi Taero, don't worry, booting from the CD should be really easy. Depending on your bios, it might just boot from the CD no problem, otherwise, you'll have to press a F key, like F10 or F12, but no big deal. Spend a little time with the Live CD to make sure Ubuntu works with your hardware, and then just run the Installer to make it permanent. Definitely back up all your important data from the hard drive first!

In terms of the difference between Ubuntu, Xubuntu, Kubuntu, etc. you can read all about it if you do a little research. :) They all have the same kernel, but have a) different desktop user interfaces, and b) different applications. Ubuntu is certainly a good one to start with, if you like the look. You can always add more applications if the default Ubuntu is missing something you need/want.

Good luck!

Thank's that was helpful :) I read about the live CD and it's a great idea, I'd better be sure as I'll be installing from absolute scratch on a laptop with no OS.

I'm being paranoid now :P Here's how it's going to go in my head :P

1 DBAN runs, my entire HD get's wiped, no drivers, no nothing, nothing recoverable.
2 The laptop is now a box with a Bios and no OS
3 I put the CD/DVD in with Ubuntu on
4 Ubuntu Installs
5 Profit

Stop me if I'm missing something obvious ^_^; I really don't want to screw up.

---

### Post by appi2012 on 2008-07-14
most bios's have something like press ESC for Boot Menu, or something similar. That will let you select your dvd drive.

---

### Post by canthus13 on 2008-07-14
You might want to search the forum for your particular model.  There seem to be a few issues that make getting it up and running a bit more involved than most laptops, but at first glance, it looks like the issues are resolved.  In particular, I saw some references to acpi and wireless.  Make sure it's something you want to mess with before you jump in.

--Me

p.s.  You could just buy a new laptop from someone like [ZaReason]("http://www.zareason.com/shop/home.php") and have Ubuntu preinstalled and working perfectly.

---

