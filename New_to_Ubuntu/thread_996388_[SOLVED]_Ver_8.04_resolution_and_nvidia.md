---
title: "[SOLVED] Ver 8.04 resolution and nvidia"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by thadacto on 2008-11-28
I have just upgraded from version 7.10 which was working fine to 8.04 (after some 6 hours of downloading.Now my screen resolution is stuck on 640 x 480.
When I try to install restricted drivers I get a message that 
nvidia-glx 1:96.43.05 +2.6.24.14-22.53 failed to install or upgrade.
This resolution is useless to me, I'm not that blind that I need things so big. In the previous version (7.10) I was using 1024 x 768 (I think it was).
What do I do now??

---

### Post by cariboo on 2008-11-28
Have you gone to System-->Administration-->Hardware Drivers to see if there are new drivers available for your graphics adapter?

Jim

---

### Post by Coreigh on 2008-11-28
After an upgrade you will certainly need to re-enable the restricted and multiverse sources and re-enable that video driver as cariboo907 suggests.

I know its an upgrade but they still make you re-set some settings.

---

### Post by thadacto on 2008-11-28
When I go to the device drivers, it is marked:
nvidia accelarated graphic driver -  Not enabled

If I enable it I then get:
Installing and removing software.

This then fails and I get
E:nvidia-glx subprocess post removal script returned error exit status 2.
Changes not applied.
I have tried several times to no avail.

When I start the computer I am offered various alternatives for loading:
Ubuntu 8.04.1 Kernel 2.6.24-22-generic
Ubuntu 8.04.1 Kernel 2.6.24-22   recovery
Ubuntu 8.04.1 Kernel 2.6.24 -16 generic
         Ditto                   recovery
Ubuntu 8.04.1 Kernel 2.6.20 -17 generic
         Ditto                   recovery
Ubuntu 8.04.1, memtest 86+                  // obviously a memory test

Does it matter which generic kernel I select?
I have tried them all (except the recovery versions) but there seem to be no difference?
More problems.  I think I should have stuck with version 7.10 - at leat I eventually got most things working there.
It's three days now, that I've been trying to upgrade, and I'm getting somewhat exasperated to say the least.

---

### Post by thadacto on 2008-11-29
Sorry, but I am trying to bump this to the top again as I have had no joy in resolving the problem - still stuck on resolution of 640x480

I did manage to get it to 800x600 but I lost the sound but when I rebooted resolution was back to 640x480

Any one any ideas????????????
I have no idea on the use of code though I do remember using DOS code back in the old days.  REM = # ..... yes?

---

### Post by lswest on 2008-11-29
I would try running ```
sudo apt-get remove nvidia-glx
``` in the terminal then re-enabling the restricted driver modules.  Seems it can't upgrade or uninstall the old driver.

---

### Post by thadacto on 2008-11-29
Just done that but it seem it didn't work; copy from terminal reads:
(Reading database ... 126307 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

Where do I go from here??

---

### Post by hanchung on 2008-11-29
You can try this in a terminal:

```
sudo apt-get install nvidia-glx --reinstall
```

---

### Post by Dai Bando on 2008-11-29
I had the same problem and ended up re installing 7.10 and I am staying with that.

---

### Post by thadacto on 2008-11-29
Got a resolution of 800x600 so atleast things get on the screen without scrolling up and down and left and right.

For anyone witrh this type of problem here's how I got over it - afet some 30 hours of mucking about and reading other people's problems:
For me, the problem seems to have been that during the upgrade from 7.10 to 8.04 (I can't remember their names!!) the upgrade system couldn't identify my monitor. I eventually found a program: Screen and Graphics, which should be in the applications menu (but for me this is more of a system program and shouldn't be in the main Applications menu).
The program can be found by going:
Places>Computer>File System/usr/share/application/screen and graphics.
Here you can set the made and model of the monitor and select the graphics card and its driver. 
However, with nVidia, there are other problems which I have to sort out.

I hope this is of some help to someone.

---

