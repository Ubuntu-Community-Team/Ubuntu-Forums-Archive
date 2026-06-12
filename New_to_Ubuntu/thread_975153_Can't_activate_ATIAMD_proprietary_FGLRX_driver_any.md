---
title: "Can't activate ATI/AMD proprietary FGLRX driver anymore"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by a_rojilla on 2008-11-08
Hello to all and excuse me for my poor english,

I have found this bug that pretty much describes what happened to me:

[#277361]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/277361")

Like this (C&P):

> Enabled ati restricted driver for my xxx card":
-had to enter my password then I saw an icon next to driver indicating I should reboot to enable driver.
-shut down computer
-on reboot instead of seeing the login window was automatically taken to a safe login mode stating that my driver fialed to load.
-chose to save log file and switch to a generic driver ..

This is exactly what happened to me, but the problem is that it is marked as a duplicated of this other bug:

[247376]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376")

But this bug seems to be solved, and **it is not**. That or they are different bugs because things doesn't work for me.

So this is the whole story and what I was trying to do:

- I upgraded from 8.10 from 8.04.

- When I first logged in, the drivers manager 'told' me that restricted drivers where activated and in use.

- I want to play movies in my TV (mostly some kids movies -Winnie the Pooh, Sesame Street...- for my daughter) while I can use the PC for other things.

- I could see my desktop in the TV, BUT and this is a big but, with a wrong resolution and as a clone of my desktop (what is of no use for me).

- And I couldn't see any option to change all this in the Screen Resolution Settings and Detect Displays didn't work either, so I said to me: well, they still didn't solve this...

- Then, seeing what was new in the new version, I found under Applications/Accesories the ATI Catalyst Control Center.

- I launched it and saw it was properly detecting both monitors (my monitor and the TV) and that the resolution for the TV was higher that what it really is.

- I picked a lower resolution in the select list, clicked Apply (or OK, whatever) and...

- **Something crashed**.

- I got a message saying the Ubuntu was running in safe graphic mode or something like that, and I was given the option to restore xserver and other things, but no matter what I did it was like being in a loop, allways trhought the same options again and again. So clicking cancel was the only way to go out.

- Then I restarted Ubuntu and... the restricted driver was not activated, so I couldn't see my desktop in the TV anymore (with or without a correct resolution, just nothing).

- So I thought I had to activate the restricted driver again and so I did.

- But as explained in the bug, whenever I try to do this something crashes and I'm sent back to save graphics mode with all that options. Another loop. Another restart. And the restricted driver is still deactivated. And so on...

Any idea on what to do? Why is the bug seen as a duplicated (and a solved one) when all this happens in a just upgraded system?

Well, I guess ATI is to blame for all this (and believe me, I will never buy ATI again), but what I want to do is something I've been easily doing with OpenSUSE for years.

No, I don't want to go back to OpenSUSE since I like Ubuntu more, but I just hope that all this is solved sooner than later.

Thanks for your time.

Regards.

---

### Post by bscbrit on 2008-11-08
You don't have to apologise for your English - I understood you just fine.

When a bug is marked as duplicate, I think that it doesn't necessarily mean that the symptoms are identical (although they might be) but, after some investigation, they both seem to be caused by the same fault.

Was your system working fine under 8.04?  If yes, I would recommend that you revert to 8.04 for a couple of weeks.  There are a few display bugs that need to be sorted out and you seem to have found one of them!  There is nothing that is vital in 8.10 which is not in 8.04, and 8.04 will be stable and supported until at least 2011.  If the driver didn't work under 8.04 either then come back and we will try to find out why.

Although it is easy to blame ATI - and if their drivers were FOSS we could probably fix them ourselves - but I suspect they worked fine under 8.04.  The kernel and xorg have been changed giving the users many additional benefits but it seems that the upgrade has broken compatibility with the ATI driver.  Perhaps ATI will issue a new driver for latest kernel.

---

### Post by bscbrit on 2008-11-08
I've checked, and the bug that you have found is still under investigation.  Don't worry, I don't believe that it is being ignored. But if you want to add your comments to the original bug report, or raise your own report, it might provide useful information to those doing the investigation.

---

### Post by a_rojilla on 2008-11-11
Thank you so much for your reply, and sorry my late response!

It's nice to know (because I didn't know this before) that even being tagged as duplicated the bug is still open (not that I'm happy that there is bug, you know).

I still have Ubuntu 8.04 in my "production" PC (a really old laptop -old by PC standards anyway, because it still works great for my needs, even with only 256 MB of RAM and no dedicated GPU) and I don't plan to upgrade it to 8.10. If is still alive then, I will just upgrade it to the next LTS.

The PC where I upgraded to 8.10 is more powerful but it has become in sort of a TV and DVD player (mostly for my daughter) and I'd like to use it for other things so that's why I want to be able to display movies in the TV while I can do those other things.

BTW, and as others are reporting, this new version is slower (some programs run slower than before), and it automatically upgraded Flash to version 10, which it is giving me worse results than version 9 (I have version 9 in Ubuntu 8.04).

Oh, why did they romove displayconfig-gtk? Well, let's be patient and wait.

Again, thank you so much for your time and to all Ubuntu developers for such a great software. Even with its bugs!

:wink:

Regards.

---

### Post by bscbrit on 2008-11-11
No problems, I hope you enjoy using Ubuntu.  See you around the forums!

bscbrit

---

### Post by Raymond Petit on 2009-01-22
Dear Guys,

I am having the same problem.  I just upgraded from 8.04 because all of the instructions to get my Pinnacle pctv HD card working were to 'vague' and not 'step-by-step' enough for someone who is not good in the terminal.  Anyway, I found out that the drivers for it were to be included in the newest linux kernel, thus the upgrade from 8.04. (I finally did install the drivers in 8.04, but all I could get was a white screen, no desktop, not tv, no nothing)  After installing 8.10, my desktop is not only the wrong resolution but is off to the left, leaving a black margin on the right side of the screen.  The proprietary driver for the ATI/AMD, which installed with no problem in 8.04, will not install.  Already had one crash.  Don't want to go back to 8.04 because I want some hope of watching tv.  Can anyone help, please?!

---

### Post by Raymond Petit on 2009-01-22
Dear Guys,

I was wrong, I have two problems.  The first is the problem with the ATI/AMD driver not loading, so I took that card out and rebooted.  The resolution and offset to the left of my desktop was still there (black band down right side of screen).  I played around with the resolutions in 'Screen Resolutions' and 1152 x 864 placed the desktop centered as it should be although I do not like this resolution.  I'll try to post a bug report tomorrow but hope this info helps.  I would like to go back to the higher resolution.  After my fresh install it was at 1400 x 1050 even when the installation disk was in before I clicked "Install".  As I said, or not, 1280 x 1024 is offset to the left.

---

