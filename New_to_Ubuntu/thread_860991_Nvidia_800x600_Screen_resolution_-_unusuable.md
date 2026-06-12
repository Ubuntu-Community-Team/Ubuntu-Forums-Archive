---
title: "Nvidia 800x600 Screen resolution - unusuable"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by philip_doherty on 2008-07-16
Hi,

I've recently installed Ubuntu (Hardy Heron, 8.04) on VirtualBox on two of my dell laptops (D430,1720) and I can not get the screen resolution to change from 800x600 on either of them.

The Dell 1720 is running Vista Business and the D430 is running Windows XP Home. 

The Dell 1720 has an Nvidia 8600 in it and the D430 has an intel mobile chipset. I've gone to the hardware driver section but theres is nothing listed there so I can't enable anything. I've tried downloading the drivers manually but as a complete newbie I cant be sure I've installed it correctly. 

I've also tried installing various packages but nothing seems to work.

When I reboot the machine now it tells me its running in low graphics mode and I can go in and pick the nvidia driver but it doesnt accept it, its driving me nuts becuase I want to use it but an 800x600 screen is unusable.

If anyone could help me out with this I'd greatly appreciate it  because it sure isn't "It just works"

---

### Post by philinux on 2008-07-16
you need to install the Guest Additions.

[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=6438](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=6438)

---

### Post by philip_doherty on 2008-07-16
Thanks, I'll let you know if that works!!

---

### Post by philinux on 2008-07-16
If you need more help there's the dedicated forum.

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

It's a bit slower there but the help is the best.

---

### Post by philip_doherty on 2008-07-16
Thanks,

That got me a bigger resolution, however its still not recognizing my nvidia card so I can't enable the desktop effects.

I even installed Envy and it doesnt detect it either. Is there an equivalent to the device manager in windows so I can check what Ubuntu is seeing?

I'm off to repost this in the other forum now.

---

### Post by philip_doherty on 2008-07-17
Thought I'd update where I am at the minute - 

I've downloaded compiz-check which is a utility that analyzes my graphics set up.

The link to the compiz-check download is [here]("http://forlong.blogage.de/article/pages/Compiz-Check"). Just download the .deb file near the bottom and double click on it whereever its been saved.

It turns out that my virtual is not seeing my nvidia card, so its using 'Innotek Systemberatung GmbH VirtualBox Graphics Adapter' instead and the driver is 'vesa'.

If anyone knows how to set this to my nvidia card that would be great, I'm going to play with VirtualBox settings to see if I can alter it that way.

---

### Post by philip_doherty on 2008-07-17
Ok,

I read a bit more - it looks like VirtualBox (or any other virtual software) will allow the virtual to access the videocard, so the only option left is a dual boot!!!

This should really be more prominent in the forums as I've read alot around this subject but its not easy to find and I'm seeing alot of other people having the same problems!!

---

### Post by philinux on 2008-07-17
> **philip_doherty said:**
> Ok,

I read a bit more - it looks like VirtualBox (or any other virtual software) will allow the virtual to access the videocard, so the only option left is a dual boot!!!

This should really be more prominent in the forums as I've read alot around this subject but its not easy to find and I'm seeing alot of other people having the same problems!!

Yes you cant have it all I'm afraid with Vbox it can only use the vesa driver. It does a lot but hardware acceleration needed for compiz is not one of them.

---

### Post by philip_doherty on 2008-07-18
Ok,

The dual boot worked fine, it can now see the NVidia card and setting up the desktop effects was pretty easy.

---

