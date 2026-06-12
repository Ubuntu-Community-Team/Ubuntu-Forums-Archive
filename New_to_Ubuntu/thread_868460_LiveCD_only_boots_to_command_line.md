---
title: "LiveCD only boots to command line"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-07-23
I was briefly discussing this in a thread earlier, but that thread was made to address a different problem, so I figured I'd make a new one for this problem.

I built my first desktop earlier today, and want to install Ubuntu on it.  The liveCD loads correctly, but when I select either 'install ubuntu' or 'try ubuntu without making changes to your computer' it always ends up at a command line.

The liveCD I am using is for 64-bit Ubuntu (which the computer is more than capable of handling), but the 32-bit cd does the same thing.  So it's not the liveCD.

Hitting F4 at the menu for 'modes' and choosing 'safe graphics mode' does the same thing.

I have a disk for the video card driver, but it's not installed since I don't have an OS to install from.  The motherboard does not have on-board video, so this could be part of the problem.

Thanks in advance.

---

### Post by Yuki_Nagato on 2008-07-23
See what the command:

```
startx
```

spits back out at you.

---

### Post by Dark_Stang on 2008-07-23
Do any errors pop up? When happens when you run "startx" at the command line?

---

### Post by ConMan318 on 2008-07-23
```

(initramfs) startx
startx
/bin/sh: startx: not found
(initramfs)

```

Doesn't recognize the command.  "(initramfs)" is the command prompt for some reason.

Same thing whether in 'safe graphics' mode or not.

And no errors (well, besides that one), it just goes from the orange bar that goes back and forth to that command line.

---

### Post by Dark_Stang on 2008-07-23
The livecd may not work for you. Try installing with the alternace cd. That will be a text based install, so feel free to ask questions.

---

### Post by Yuki_Nagato on 2008-07-23
> **Dark_Stang said:**
> The livecd may not work for you. Try installing with the alternace cd. That will be a text based install, so feel free to ask questions.

Sounds as if the XWindow system is not even found.  It might be fixed by  installing that separately.  And yes, try the alternative CD.  That may be easier.

---

### Post by superprash2003 on 2008-07-24
there could be a possibility of a corrupt cd or you may be having less RAM on your machine

---

