---
title: "Can I just install Oneiric daily build just once?"
date: 2011-06-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-06-06
Hi,

Can I download and install the daily build just once and keep updating so that I automatically get alpha 2, alpha 3...beta 1, beta2, etc. toward the final release?

Or do I need to download the daily build every day?

Just want to confirm.  Thanks for your help.

---

### Post by wojox on 2011-06-06
Just once and then keep it updated.

---

### Post by iClouseau88 on 2011-06-06
Hi wojox,

That's what I thought, but just want to make sure.  Thanks for your reply.

---

### Post by arpanaut on 2011-06-06
[http://ubuntuforums.org/showthread.php?t=1751289](http://ubuntuforums.org/showthread.php?t=1751289)

---

### Post by jerrylamos on 2011-06-06
> **iClouseau88 said:**
> Hi,

Can I download and install the daily build just once and keep updating so that I automatically get alpha 2, alpha 3...beta 1, beta2, etc. toward the final release?

Or do I need to download the daily build every day?


My experience over last several Ubuntu's is that updates work for a while then:
1.  Wham! "Dread Update" borks my install.  Now I have at least two if not three partitions with previous release that works (!) plus the test partitions so I just do an install from daily build.  For a couple months on Natty that didn't even work because install itself was borked.
2.  Any number of times I'll have a partition which has been updated for weeks and do a fresh install in another partition.  Despite claims to the contrary they are different, desktop, etc. etc.

What I'm doing now is I have a Ocelot install on a USB hard drive.  I didn't put it on the main drive because installing Natty with Grub 2 kept screwing up the Grub boot menus.  I had to scramble to find another bootable partition and do update-grub grub-install to get going.

Right now at this early stage I'm booting the .iso from a folder on the hard drive, in persistent mode.  It's easy and quick to do a zsync to try the next daily build.  Directions for doing this are in this forum.

On Alpha 1 and the last few daily builds there are a number of things that are busted on the desktop on two of my three test pc's.  When I find one that seems to be pretty solid I'll try another install on the USB hard drive.  The hard drive was a left over laptop drive and the USB and adapter case cost me $10.

Anyway if you like running Alpha's and Beta's and new things, it's really handy to be used to doing installs.  This entry is from an Acer Aspire one netbook with Windoze 7, Meerkat, and Narwhal installed and am testing the latest Ocelot booting .iso persistent from a folder on Meerkat.

Have fun, and do remember pre releases do break.  I learn a lot of linux that way, and sometimes the bugs I find are useful to the developers.

Jerry

---

### Post by jerrylamos on 2011-06-06
Example today's daily build the "Applications" launcher does not, the BFB does not show a menu, Home launcher does work, and the Firefox launcher did.  Not ready for an install for me.

Now I can get to System Settings with the Power applet since the BFB doesn't work, and I can get a terminal session with Ctrl-Alt-t so I can use the daily build by working around what's busted.

One improvement, the exit-minimize-maximize buttons are back.  They've been missing the last couple days. 

Jerry

---

### Post by sparker256 on 2011-06-06
> **jerrylamos said:**
> Example today's daily build the "Applications" launcher does not, the BFB does not show a menu, Home launcher does work, and the Firefox launcher did.  Not ready for an install for me.

Now I can get to System Settings with the Power applet since the BFB doesn't work, and I can get a terminal session with Ctrl-Alt-t so I can use the daily build by working around what's busted.

One improvement, the exit-minimize-maximize buttons are back.  They've been missing the last couple days. 

Jerry
Are the buttons back in unity-2d or unity? I have always had them working in unity-2d.

Bill

---

### Post by floydsp on 2011-06-06
Thanks Jerry will try and do that

pbfloyd

---

