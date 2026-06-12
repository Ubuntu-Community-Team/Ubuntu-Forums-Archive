---
title: "how to load kernel with grub2"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by rauloid on 2013-10-06
Just installed Lubuntu 12.10 alternate install on an old PC (Celeron, 318MB RAM), and after the install all I get is a CLI with a "grub> "
How do I load a kernel?
(I'm a newbie, if you cannot tell.. :)

---

### Post by whitesmith on 2013-10-06
What choices does Grub offer you?

---

### Post by DuckHook on 2013-10-06
Welcome to the forums and Lubuntu!

You are stuck at the grub bootloader. Because you did not get a black screen, chances are this is not a video driver issue but a kernel issue. Please describe your system just a little more... some Celerons are 32-bit and some are 64-bit. Do you know which yours is? If not, Google make/model of old PC. The CPU speed is also an indicator of the model of Celeron. What MHz does it run at?

Did you install 32-bit Lubuntu or 64-bit? It is also possible that your install disk is corrupted. Did you download it using torrent or one of the mirror sites?

318 MB RAM is severely limiting. The only 'buntu distro that it will run at all would be Lubuntu. You may actually have better luck running another distro altogether like Puppy, CrunchBang or SliTaz.

Did you try running Lubuntu as a LiveDVD before installing it? If not, please try to do so now. If it cannot run as a LiveDVD, then it won't run when installed either and we would need to do some detective work to make it work.

Please answer all above questions and we can see where to go from there.

---

### Post by rauloid on 2013-10-06
No GUI. just the grub> cursor

---

### Post by rauloid on 2013-10-06
Single core 667MHz, 32bit; I know it's low on power, it's why I chose Lubuntu 32bit. Used a mirror to get the ISO. Did not try LiveCD, since I tried it a while ago on a similarly low powered laptop and it worked ok there.

---

### Post by cody1233 on 2013-10-06
How did you install?

---

### Post by DuckHook on 2013-10-06
> **rauloid said:**
> Single core 667MHz, 32bit; I know it's low on power, it's why I chose Lubuntu 32bit. Used a mirror to get the ISO. Did not try LiveCD, since I tried it a while ago on a similarly low powered laptop and it worked ok there.Torrent downloads are more reliable due to concurrent dynamic error-checking. Try LiveCD now and let us know if it works.

---

### Post by rauloid on 2013-10-06
tried LiveCD and it works.
should I try to repair the install or ..?

---

### Post by rauloid on 2013-10-06
does anyone know how to load the kernel from my grub> CLI?

---

### Post by DuckHook on 2013-10-06
It is possible to search for your /boot, but by the time we walk you through this, you may as well have installed a new Lubuntu. I suspect that a problem occurred during your initial install and GRUB was not pointed properly to your /boot. Rather than trying to figure out your partitioning scheme, find /boot and edit your various config files from a LiveCD, it will save you time and unnecessary effort to just install Lubuntu again, but this time, *from the LiveCD*. Alternate installs are fine if you are more versed in installations, but for new users, LiveCD is most intuitive.

---

### Post by mörgæs on 2013-10-06
You could try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), but even if you get it to boot it will only barely be usable. Sorry to be blunt, but I would not spend time on this old iron when you can pick better computers up from a dumpster.

If you really want it to work I recommend a [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") of Lubuntu 13.04.

On such limited hardware the 'install from a live session' approach is not likely to work.

---

### Post by DuckHook on 2013-10-06
> **mörgæs said:**
> I would not spend time on this old iron when you can pick better computers up from a dumpster....but some of us *like* sticking pins in our eyes. :lolflag:

Seriously though, it's a rewarding experience to resurrect old HW. There's something about taking an old derelict, spiffing it up, tinkering with it in some way, and magically making it relevant again. It's probably the same impulse that made the film Wall-E such a touching story.

@OP

Of course, if you desire some sort of production machine, then mörgæs is absolutely correct and you are wasting your time. This "old iron" (love that phrase!) is really nothing more than a personal challenge at this point. However, if you are in it to learn, then I can't imagine a more effective way to understand Linux than to wrestle with an obsolete underpowered cussed jalopy that you have to fight every step of the way.

---

