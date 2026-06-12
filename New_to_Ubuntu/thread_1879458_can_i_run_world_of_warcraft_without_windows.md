---
title: "can i run world of warcraft without windows?"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by laserkitties on 2011-11-11
i am relatively new to ubuntu, currently running version 11.10.  when i originally installed it, i got rid of windows completely, having decided that i would only use this laptop for light use; internet, e-mail, and so forth.  but i miss being able to play WoW, and based on what i have read so far i think that i can never play it on this computer without windows being on another partition.

i'm not very computer savvy, although i know enough to learn quickly by doing a little research.  with this problem though, i'm at a loss.  so i was wondering if someone could please answer my question- can i run WoW, or any windows-based game for that matter, without windows?

thank you ; )

~sara

---

### Post by anewguy on 2011-11-11
You can probably get a lot of help by posting and reading in the Ubuntu Gaming and Leisure forum:

[http://ubuntuforums.org/forumdisplay.php?f=93]("http://ubuntuforums.org/forumdisplay.php?f=93")

Best of luck, and welcome to Ubuntu!

Dave ;)

---

### Post by Mark Phelps on 2011-11-12
Most Windows games rely on DirectX for fast frame rates.

To have that, you need both a video card/chip that supports it and video drivers that support it.

The problem is not going to be Wine; instead, the problem is going to be the video driver support in Ubuntu.

Wine won't let you install any drivers, so if even if your current video card supports the DirectX version needed in the game, unless there are Restricted Drivers available for your card that ALSO support that DirectX version, your game performance is going to be very slow -- possibly to the point of being unusable.

If you don't know the make and model video card/chip in your PC, then open a terminal, enter "lspci" and look for the line containing "VGA".  Post that result back here.

We can then tell you whether or not current Restricted Drivers are available for that video card/chip.

---

### Post by Paqman on 2011-11-12
> **Mark Phelps said:**
> Most Windows games rely on DirectX for fast frame rates.


Luckily WoW has pretty low hardware requirements. Give Wine a go, I'd suggest installing [PlayOnLinux]("apt:playonlinux"), which is a front-end for Wine that bundles some of the tweaks that games need to run well with the installation process for that game.

---

### Post by laserkitties on 2011-11-12
so far, i have installed wine and attempted to install wow with it.  everything goes well until the newish launch screen/installation bar starts, and then i get a vague error message.  as of this moment i am installing playonlinux, and reading some of the gaming forum generously posted (ty!)  as far as the video thingy you asked about, here's what i found:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)

this laptop never ran all the expansions incredibly well when i had windows, and since i've become such a casual player over the years, i currently don't care to install anything other than the so-called "vanilla" version of the game.  so, i think that if i keep it simple, as long as it installs properly, it should run well enough for me to get my fix before returning to my ps3.  playonlinux is finished, so i'm going to explore that for a bit and then i'll post my findings.  thanks so much for all the help!  you've all been very informative ; ) xoxox

---

### Post by haqking on 2011-11-12
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

and a ton of threads on WoW [http://ubuntuforums.org/tags.php?tag=wow](http://ubuntuforums.org/tags.php?tag=wow)

Enjoy

---

