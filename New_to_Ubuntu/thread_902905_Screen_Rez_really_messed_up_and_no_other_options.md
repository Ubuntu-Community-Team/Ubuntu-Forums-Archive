---
title: "Screen Rez really messed up and no other options"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by SlingerXL on 2008-08-27
I tried to plug in an svideo to my ubuntu machine and after it didn't work and I restarted my computer all of a sudden everything was stretched wider. Not much wider, like just barely enough to notice but it was wider and annoying. So I restarted again and before it even booted up it said ubuntu was in low graphics mode and gave me a bunch of options. I messed with the monitor output or something and now when the machine boots up the desktop is horribly small resolution now. Like, worse than 600x400. When I go to preferences>screen resolution it doesn't give me any other options other than 640x480 in resolution.

So what do I do?

---

### Post by tuxxy on 2008-08-27
Is your video driver at fault? try reinstall it maybe

---

### Post by rockerphil on 2008-08-27
i know this works for me when screen resolution goes awry, try running this from the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

if that doesn't work you may try booting to the recovery mode in GRUB and allowing it to fix the X server. hope it helps,

Phil

---

### Post by SlingerXL on 2008-08-27
How do I boot in recovery mode?

---

### Post by SlingerXL on 2008-08-27
And how do I reinstall the video drivers?

---

### Post by SlingerXL on 2008-08-27
> **rockerphil said:**
> i know this works for me when screen resolution goes awry, try running this from the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

if that doesn't work you may try booting to the recovery mode in GRUB and allowing it to fix the X server. hope it helps,

Phil

Oh that did it!! Thanks a lot. What does that command mean?

---

### Post by rockerphil on 2008-08-27
if you went with a standard install when you boot the machine you should see a short countdown (typically 3 seconds) durning this time you can press Esc. to get to the GRUB menu, you should see a recovery mode right under the default boot option. hope it helps,

Phil

---

### Post by rockerphil on 2008-08-27
> **SlingerXL said:**
> Oh that did it!! Thanks a lot. What does that command mean?

that is the command to reconfigure your X server, which is the program that runs underneath your window manager. basically without the X server you can't create any windows thus leaving you with nothing but a command prompt. i'm glad it helped though, and remember to be sure to mark your thread as solved if you've gotten your problem sorted.

Phil

---

### Post by hrvoje-sl on 2009-01-19
I wish I have read these posts before trying to enable tv-out. Well just to say that I reinstalled ubuntu 8.10 twice bacause it switched in low graphics mode and did not know what to do.

---

