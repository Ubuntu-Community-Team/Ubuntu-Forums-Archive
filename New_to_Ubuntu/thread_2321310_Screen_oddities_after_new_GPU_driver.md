---
title: "Screen oddities after new GPU driver"
date: 2016-04-21
forum: New to Ubuntu
---

### Post by Noah_Babineau on 2016-04-21
[IMG]http://imgur.com/sSZVqeI[/IMG]

So I recently went into the additional drivers thing, and selected a driver from a binary nvidia source (I have Nvidia Quadro M1000M). After installing this and restarting, strange things happen. First, I get a grey screen with a dark grey background, which lasts for about a minute. then it goes black, and for a 3 second period, a screen shows up with this logo [pic related]. At this point it goes to another black screen, and remains there. I assume that something went wrong with driver install, but I cant figure out how to fix it. When I hold down shift when booting, I get the same thing.

Additionally, the only OS on my computer is Ubuntu, and GRUB doesn't normally appear, it just boots to ubuntu.

How do I fix this?

---

### Post by Geoffrey_Arndt on 2016-04-21
> **Noah_Babineau said:**
> [IMG]http://imgur.com/sSZVqeI[/IMG]

So I recently went into the additional drivers thing, and selected a driver from a binary nvidia source (I have Nvidia Quadro M1000M). After installing this and restarting, strange things happen. First, I get a grey screen with a dark grey background, which lasts for about a minute. then it goes black, and for a 3 second period, a screen shows up with this logo [pic related]. At this point it goes to another black screen, and remains there. I assume that something went wrong with driver install, but I cant figure out how to fix it. When I hold down shift when booting, I get the same thing.

Additionally, the only OS on my computer is Ubuntu, and GRUB doesn't normally appear, it just boots to ubuntu.

How do I fix this?

Must uninstall the driver you selected - to get past black screens, do:

 For a PC with no other operating system - the Grub2 menu will NOT be displayed by default, so:

>     Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu.  

> At the grub menu highlight the kernel you want to use and click 'e' to edit 

> Find the line that ends in 'quiet splash' and after a space, add 'nomodeset'.     Save changes.

The end of the line should look like this: [U]quiet splash nomodeset


[/U]
This should give a working display, whereupon you can go back to Additional Drivers and reverse your update (also can use the Synaptic package manager to completely remove the nvidia drivers).

---

### Post by grahammechanical on 2016-04-21
Does Ubuntu load to a login screen and a desktop user interface? If so, then what is the problem?

If I use an open source video driver I get a purple Ubuntu splash screen. If I use an Nvidia driver I do not get the purple splash screen. And like you a black screen appears for a few seconds and then the background to the login screen appears. Sometimes during this process the digital monitor will produce a "no signal" message.

Regards.

---

