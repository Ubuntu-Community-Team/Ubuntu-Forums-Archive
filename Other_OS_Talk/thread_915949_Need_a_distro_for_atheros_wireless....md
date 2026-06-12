---
title: "Need a distro for atheros wireless..."
date: 2008-09-10
forum: Other OS Talk
---

### Post by Fzang on 2008-09-10
Seems like atheros is pretty hateful against linux, so older versions of linux will have pretty bad support for atheros...

[http://forum.mandriva.com/viewtopic.php?t=93921](http://forum.mandriva.com/viewtopic.php?t=93921)

This seems like a kernel issue or something... pretty dam annoying, I can't use ANY new distro. I've tried using gutsy gibbon and mandriva 2007.1, which worked well though...(older kernel? :O)

But the old mandriva doesn't even detect my wireless card.. which basically means I'm screwed, since it's a laptop...

Is there any "old" (that date back to gutsy or mandriva 2007'ish kernels) which will support my hardware without too much hassle...

Specs:

Atheros AR5007EG (I'm pretty sure, but I always forget)
AMD Turion 64bit Mobile technology
ATI Radeon Xpress 1100
Realtek HD Audio (that's what my laptop calls it)


Help! I really wanna be able to use linux without having to buy a new computer

---

### Post by tdrusk on 2008-09-10
> **Fzang said:**
> Seems like atheros is pretty hateful against linux, so older versions of linux will have pretty bad support for atheros...

[http://forum.mandriva.com/viewtopic.php?t=93921](http://forum.mandriva.com/viewtopic.php?t=93921)

This seems like a kernel issue or something... pretty dam annoying, I can't use ANY new distro. I've tried using gutsy gibbon and mandriva 2007.1, which worked well though...(older kernel? :O)

But the old mandriva doesn't even detect my wireless card.. which basically means I'm screwed, since it's a laptop...

Is there any "old" (that date back to gutsy or mandriva 2007'ish kernels) which will support my hardware without too much hassle...

Specs:

Atheros AR5007EG (I'm pretty sure, but I always forget)
AMD Turion 64bit Mobile technology
ATI Radeon Xpress 1100
Realtek HD Audio (that's what my laptop calls it)


Help! I really wanna be able to use Linux without having to buy a new computer

I have that card. The new Mandriva works with it out of the box.. They use the madwifi patch. I am using this in Ubuntu just fine. 

If you want it working in Ubuntu use [this]("http://ubuntuforums.org/showthread.php?t=792158") guide.

To check to make sure you are talking about the right card use ```
lspci
``` and look for 
```
Atheros Unknown device 001c (rev 01)
```

---

### Post by cmat on 2008-09-10
Atheros is actually making an honest effort to get support going. A good percentage of the time it's the computer's hardware interfaces which are the problem (proprietary configuration not adhering to the ACPI standard).

---

### Post by Fzang on 2008-09-10
> **tdrusk said:**
> I have that card. The new Mandriva works with it out of the box.. They use the madwifi patch. I am using this in Ubuntu just fine. 

If you want it working in Ubuntu use [this]("http://ubuntuforums.org/showthread.php?t=792158") guide.

To check to make sure you are talking about the right card use ```
lspci
``` and look for 
```
Atheros Unknown device 001c (rev 01)
```

That's what I'm saying, I can't use mandriva older than 2007, otherwise it won't boot

Also, gutsy gibbon has no support for my graphics card, so that's one problem traded in for another..

Is it possible to install mandriva 2007, then install a newer version of madwifi or something else and use my atheros card?

---

### Post by 67GTA on 2008-09-10
Since madwifi has made a patch, most of the upcoming distros will work out of the box. I just tried the Mepis 8 beta on my laptop with ar5007eg, and it was connected as soon as the desktop loaded with no configuring needed. I assume Intrepid will also. I don't know of any current distros that work out of the box with the ar5007eg at the moment. Mint 5 has the drivers on the CD, but that is as close as you are going to get right now.

---

### Post by wolfen69 on 2008-09-10
next months ubuntu release should work fine. if you can't wait, just run Ibex alpha 5.

---

### Post by 67GTA on 2008-09-10
I just tried alpha 5 64bit on my laptop, and wireless doesn't work. It is loading the ath5k module, so not sure what is up with that. The 32bit version may work though.

---

### Post by ffi on 2008-09-10
> **Fzang said:**
> Seems like atheros is pretty hateful against linux, so older versions of linux will have pretty bad support for atheros...

[http://forum.mandriva.com/viewtopic.php?t=93921](http://forum.mandriva.com/viewtopic.php?t=93921)

This seems like a kernel issue or something... pretty dam annoying, I can't use ANY new distro. I've tried using gutsy gibbon and mandriva 2007.1, which worked well though...(older kernel? :O)

But the old mandriva doesn't even detect my wireless card.. which basically means I'm screwed, since it's a laptop...

Is there any "old" (that date back to gutsy or mandriva 2007'ish kernels) which will support my hardware without too much hassle...

Specs:

Atheros AR5007EG (I'm pretty sure, but I always forget)
AMD Turion 64bit Mobile technology
ATI Radeon Xpress 1100
Realtek HD Audio (that's what my laptop calls it)


Help! I really wanna be able to use linux without having to buy a new computer

If you get to udev you have made it into the kernel already, there was major change though around that time with ide drivers, try to boot with either one or both of these options appended to your boot option:

all-generic-ide 
irqpoll

(ie like: kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=d9409e54-697c-4de8-ad50-bc43d6c883c5splash=silent vga=791 all-generic-ide irqpoll)

---

