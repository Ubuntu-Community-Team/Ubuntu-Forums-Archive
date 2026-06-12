---
title: "Ubuntu 14.04 - I am afraid of constant crashes"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by marius5 on 2014-07-08
I gave ubuntu ~5 chances to completely replace my OS and use it daily and yet it constantly keeps letting me down.
This time, I completely formatted my SSD and installed 14.04 as main OS. I configured it to make sure that it runs as smoothly as possible when it comes to SSD and yet it crashed completely and I was unable to recover it (it went into low graphics mode and I tried various methods to fix it) so I gave up and installed Windows 7 again... But still, Ubuntu feels more like home for me, even though I never used for more then a month.
I guess my question is, can ubuntu be rock solid without any crashes? I own MSI FX600 laptop which has Intel HD graphics and nvidia 325m graphics card and this seems to be the biggest conflict for ubuntu of them all.
When I install propriatery drivers for ubuntu (the first ones from the list) - desktop after n amount of minutes simply freezes and you have to reboot laptop. Then I tried installing the second propriatery drivers and it froze my desktop again and after rebooting I was unable to get into my desktop...
Is it possible to make sure that my system runs ubuntu without any issues and nvidia doesnt spit in my mouth constantly and intel graphics works as it should?

---

### Post by bapoumba on 2014-07-08
*Thread moved to **Absolute Beginners Section**.*

---

### Post by Richard_Romick on 2014-07-08
Ubuntu is typically very stable.

I think your problem may be the nvidia graphics card.  Do some research to find out if it uses optimus, like mine.  If it does, you need to install bumblebee before installing nvidia drivers.

---

### Post by Mark Phelps on 2014-07-08
Unfortunately, Hybrid Graphics, like the setup you have, is extremely unreliable in Linux -- due entirely to the lack of specialized drivers, which come preinstalled in Windows when you buy a machine already configured that way.  Sorry, but it's unlikely you're going to match the Windows graphics performance on that machine while running Linux.

---

### Post by buzzingrobot on 2014-07-08
Any chance the Nvidia can be disabled in the BIOS, so you could run on the Intel?

---

### Post by Bucky Ball on 2014-07-08
Bumblebee is in the repositories (Software Centre or Synaptics or a terminal). As suggested, fresh install and try that if you are using an Optimus nvidia card. That would certainly be your problem by what you've described.

---

### Post by monkeybrain20122 on 2014-07-09
> **buzzingrobot said:**
> Any chance the Nvidia can be disabled in the BIOS, so you could run on the Intel?

But why would one want to do that? A laptop with just an intel integrated card would be a lot cheaper. If there is a BIOS option to turn off Optimus (only some Lenovo laptops have it  apparently) then I would instead use Nvidia only whenever it is plugged in. :)

@OP

+1 to bumblebee.

bumblebee ppa [https://launchpad.net/~bumblebee/+archive/ubuntu/stable](https://launchpad.net/~bumblebee/+archive/ubuntu/stable)

I wouldn't install things that are under active development  and a bit of hit and miss like bumblebee from Ubuntu's repositories, chances are the repo version is very outdated and contains bugs that have been fixed upstream a century ago :). Disable the ppa once things are working so they won't break with updates.

---

### Post by buzzingrobot on 2014-07-09
> **monkeybrain20122 said:**
> But why would one want to do that? A laptop with just an intel integrated card would be a lot cheaper. If there is a BIOS option to turn off Optimus (only some Lenovo laptops have it  apparently) then I would instead use Nvidia only whenever it is plugged in. :)



To get video that works out of the box without the flaky hassle of Nvidia, Bumblebee, Prime and all that. It's the easy fix.

 For myself, unless the video card switch happens automatically in response to demand, I can't be bothered with it.

I use a Lenovo with three video options: Intel, Nvidia, Optimus. I don't see a reason to use Optimus, so it's disabled.  The current Nvidia drivers work acceptably, but run a bit warmer than the Intel, but I seldom really need them. In any case, my results with Nvidia's drivers have been spectacularly variable across kernel, driver, and distro versions.  The Intel HD4000 in this thing easily handles Unity and Gnome Shell,, and less demanding interfaces like Mate and XFCE are even better, especially with compositing turned off.

---

### Post by grier-devon on 2014-07-09
Are you gaming on this notebook still? I am asking as 300 series graphics from Nvidia are pretty old. If not it sounds like the problem happens when you install the proprietary drivers, have you ever tried to just run the open source drivers and see how the reliability is?

---

### Post by monkeybrain20122 on 2014-07-09
> **buzzingrobot said:**
> To get video that works out of the box without the flaky hassle of Nvidia, Bumblebee, Prime and all that. It's the easy fix.

 For myself, unless the video card switch happens automatically in response to demand, I can't be bothered with it.

I use a Lenovo with three video options: Intel, Nvidia, Optimus. I don't see a reason to use Optimus, so it's disabled.  The current Nvidia drivers work acceptably, but run a bit warmer than the Intel, but I seldom really need them. In any case, my results with Nvidia's drivers have been spectacularly variable across kernel, driver, and distro versions.  The Intel HD4000 in this thing easily handles Unity and Gnome Shell,, and less demanding interfaces like Mate and XFCE are even better, especially with compositing turned off.

Well anything nowadays pretty much handles Unity and gnome shell (even my roommate's 8 year old laptop that came with XP and a crappy old ati card with stock  driver. but it doesn't have enough ram to run them smoothly, that is a different story) so it is not much of a benchmark like it was a few years ago. :) But if you pay the money to get a Nvidia card supposedly for performance you may as well use it. :)

I think video card switching on demand like bumblebee may actually be better than automatic switching. I have heard Windows users complaining that automatic switching doesn't always switch when they think it should.

---

### Post by buzzingrobot on 2014-07-09
> **monkeybrain20122 said:**
> Well anything nowadays pretty much handles Unity and gnome shell (even my roommate's 8 year old laptop that came with XP and a crappy old ati card. but it doesn't have enough ram to run them smoothly, that is a different story) so it is no big deal. But if you pay the money to get a Nvidia card supposedly for performance you may as well use it. :)

I think video card switching on demand like bumblebee may actually be better than automatic switching. I have heard Windows users complaining that automatic switching doesn't always switch when they think it should.

Well, I paid my money for the Nvidia card in this Lenovo, but I find myself disabling it most of the time. C'est la vie. 

My experience with automatic switching was on MacBooks, which have hardware that handles it. You don't know that it's happening unless the fans perk up.

---

### Post by BBQdave on 2014-07-09
Just to add to what has already been said, no troubles with Ubunutu Unity (64-bit) 14.04LTS and Lenovo T400 Thinkpad. Intel Centrino 2 with Intel graphics, 2GB of RAM and SSD. I stay away from hybrid graphics with Linux.

Even with only 2 gigs of RAM, Unity functions smoothly, with multiple applications going: Firefox Web Browser, Thunderbird email client, Rhythmbox, GIMP and Scribus. I am amazed at how stable 14.04 is (for just being released) and how well it performs on this old hardware :)

---

