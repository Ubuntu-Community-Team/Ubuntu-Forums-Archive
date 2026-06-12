---
title: "Startup and Shutdown Screens show verbose text (Kub.13.4) - how2cleanup?"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by GregA on 2013-05-13
Hi,

This weekend I installed Kubuntu 13.4 on a friends laptop (HP tx1210us w/nvidia GeForce Go 6150 gpu, broadcom wireless and 2 gig ram).   Overall, the install went smoothly, I downloaded & installed the proprietary wireless and video drivers.  The active driver is Nvidia v304.88.

Starup and shutdown screens display a few lines of text scattered across the screen, and then showing the normal graphical start/shutdown screens.   This looks kinda tacky and detracts from an otherwise very acceptable gui experience.

Is there any way to tweak and clean up that verbose text?

---

### Post by 2F4U on 2013-05-14
Did you already try to add "quiet" (without quotes) to the grub command line? It is supposed to suppress these kind of messages.

---

### Post by GregA on 2013-05-14
I haven't tried that as I wasn't aware of how & where to change that.  Also, how do I bring up Grub to do that edit?   This laptop is running only Kubuntu 13.4, . . . no other OS's.

Thanks.

---

### Post by GregA on 2013-05-15
Well Ok, I went back to some notes I took about grub many moons ago, and figured out how to access grub in /etc, and to edit via Kate with su.   But the grub file already shows quiet in a couple lines, so I'm not sure what line or syntax to enter.   This isn't a critical issue, as the laptop will start and shut down just fine.  It just looks a little tacky (imho) and I'm working with someone new to linux and want a good experience all around.

---

### Post by 2F4U on 2013-05-16
Looks like a similar problem I found here:

[http://ubuntuforums.org/showthread.php?t=2066656](http://ubuntuforums.org/showthread.php?t=2066656)

---

### Post by GregA on 2013-05-17
Thanks for the update.  All things considered, I'll probably just leave the laptop setup as is, rather than risk breaking something (on another persons machine).   The Kubuntu install has really improved the speed and functionality of the system overall.

---

