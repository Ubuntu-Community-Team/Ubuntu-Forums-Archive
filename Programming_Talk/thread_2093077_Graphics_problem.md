---
title: "Graphics problem"
date: 2012-12-09
forum: Programming Talk
---

### Post by seeker.k3 on 2012-12-09
Hi,
I'd really appreciate it if someone could give me some advice here: I have a graphics problem. For example, I'm running a dual boot system, but I've never seen the boot menu, even though it works and I use it, it just doesn't display. Normal usage (Internet and docs) all seem fine.

Now, I'm trying to write a program---a project for psychology (using Psychtoolbox). When run a Screen() function to make a screen to start my project (I guess you would say it loads a graphics device), it does a sync test. Unfortunately, it reports synchronization failure.

[HTML]VBL Calibration run No. 1 failed. Couldn't even collect one single valid flip interval sample! Sanity range checks failed!  Couldn't compute a reliable estimate of monitor refresh interval! Trouble with VBL syncing?!?
[/HTML]

I really don't know anything about this sort of stuff. 

I've installed nvidia-current-updates from Synaptic. I'm running 64-bit Xubuntu Precise.

Here's some more info:
[HTML]GeForce 6150SE nForce 430/integrated/SSE2 :: 2.1.2 NVIDIA 295.40
Also,
Kernel modules: nvidia_current, nvidia_current_updates, nouveau, nvidiafb
[/HTML]

I'd be very grateful for any help with this.

---

### Post by Bashing-om on 2012-12-09
seeker.k3; Hi !

Can't help ya on the screen() function, but for the boot display, try this: From xubuntu terminal:
```
sudo update-grub
``` will regenerate the config files and I expect pick up the other operating system(chainloading).

[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by seeker.k3 on 2012-12-09
Thanks for your comments. Just to keep things on track, I have to say that the problem is with the display, not the grub.

BTW, I downloaded a driver, file name: NVIDIA-Linux-x86_64-177.82-pkg2.run

I think it's what I need, but I'm not sure what to do with it.

---

### Post by Bucky Ball on 2012-12-09
*Thread moved to **Programming*** ***Talk***

> **seeker.k3 said:**
> Hi,
I'd really appreciate it if someone could give me some advice here: I have a graphics problem. For example, I'm running a dual boot system, but I've never seen the boot menu, even though it works and I use it, it just doesn't display. Normal usage (Internet and docs) all seem fine.

This is confusing. You use the boot menu but you can't see it???

Okay, after the bios screen hit shift. That will take you to the menu list where you can see all operating systems and select one. Can't quite work out where the graphics problem comes in. Have you done an update and checked 'Additional Drivers' for a graphics driver that is disabled?

Secondly, you seem to be asking about two issues in the one thread. Your chances would be much better if you edited your post and put the 'graphics issue' as a separate thread and leave the rest as it is. I have moved this thread to the **Programming Talk **sub-forum, as that is what it is mostly about. 

Good luck, but be aware, there is a line (and don't get me wrong, not saying you've crossed it, just a heads up). From the Code of Conduct:

> While we are happy to serve as a resource for hints and for asking  questions when you get stuck and need a little help, the Ubuntu Forums  is not a homework service. Please do not post your homework assignments  expecting someone else to do it for you. Any such threads will be taken  offline and warnings or infractions may be issued.People generally consider this to be aimed at high school assignments. It is not. It applies to all assignments, regardless.

---

### Post by seeker.k3 on 2012-12-10
I don't seem to be getting my message across. 

It's a graphics problem!

Nothing to do with grub, nothing to do with assignments or programming. My screen doesn't display anything when I hit shift---it's blank. Nor does it display anything when it should display the boot menu, and it doesn't display anything when I hit ctl + alt + F1. When I tried to write an application, it won't work because of a graphics problem---synchronization failure. I think the problem relates to the driver, but I don't know how to fix it.

---

### Post by Bashing-om on 2012-12-10
graphics problem: boot up with the "nomodeset" parameter by editing the booting kernel's boot line. This boots with kernel mode setting disabled, if you boot to some kind of a GUI, (12.04: launcher->System Settings-> Additional Drivers; Install the recommended driver.

[INDENT]still try'n to help < == BDQ

[/INDENT]

---

### Post by seeker.k3 on 2012-12-10
OK. Thank you. I'll definittely look into that.

---

