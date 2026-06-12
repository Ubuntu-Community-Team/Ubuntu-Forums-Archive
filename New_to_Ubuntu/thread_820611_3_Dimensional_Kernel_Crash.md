---
title: "3 Dimensional Kernel Crash"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by markekeller on 2008-06-06
I use Linux Mint, a varient of Ubuntu based on Gutsy.  A few weeks ago I installed the proprietary ATI graphics drivers, so as to get good 3D acceleration, from [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html").   The first thing I tried to test whether acceleration worked was *Blob and Conquer*, a 3D game.  It did work, so I played it for a while - and then it crashed.  Not just the game, because [FONT="Monospace"]Ctrl-Alt-Backspace[/FONT] did nothing, and not just X, either, because [FONT="Monospace"]Alt-SysRq-B[/FONT] did nothing either: the whole kernel went down, I think.  At first I thought this was something with the graphics driver, but after a while I decided it was merely a bug in *Blob and Conquer*, because it didn't happen with other 3D games, and even in *Blob*, it only seemed to happen when I had other programs open at the same time.

But then I downloaded the new version of Blender - and it does the same thing!  Not only when I run other programs at the same time as it, either, and much more often than with *Blob*.

This is, I think now, some problem related to my graphics driver/kernel/whatever.  The whole computer freezes, at seemingly random times, while running either *Blob and Conquer* or Blender.  I have a Radeon 9600 card, with kernel version 2.6.22 and Gnome 2.20.

Does anyone have any idea what could be causing this?  And does anyone know how I can fix it?  I'd really like to be able to use Blender in Linux.

---

### Post by markekeller on 2008-06-06
Anyone?

---

### Post by markekeller on 2008-06-06
So . . . have you ever encountered something like this before?

---

### Post by Xerp on 2008-06-06
Not me. Try installing the ATI driver again using Envy. Also, check /var/log/messages and /var/log/syslog.

---

### Post by markekeller on 2008-06-07
Good tip.  I looked through both those files, and in /var/log/messages, I found this:

```
Jun  5 03:02:41 kellerboys -- MARK --
Jun  5 03:16:15 kellerboys kernel: [33240.447426] [fglrx] interrupt source 10000000 successfully disabled!
Jun  5 03:16:15 kellerboys kernel: [33240.447436] [fglrx] enable ID = 0x00000000
Jun  5 03:16:15 kellerboys kernel: [33240.447440] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000005
Jun  5 03:16:15 kellerboys kernel: [33240.447760] [fglrx] interrupt source 20008000 successfully disabled!
Jun  5 03:16:15 kellerboys kernel: [33240.447763] [fglrx] enable ID = 0x00000000
Jun  5 03:16:15 kellerboys kernel: [33240.447766] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000004
Jun  5 03:16:20 kellerboys exiting on signal 15
Jun  5 09:16:41 kellerboys syslogd 1.4.1#21ubuntu3: restart.
```

That must be it.  I'll do a little searching around and see if I can find what's causing this . . .

---

