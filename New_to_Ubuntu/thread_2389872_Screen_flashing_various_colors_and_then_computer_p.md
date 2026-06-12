---
title: "Screen flashing various colors and then computer powering off"
date: 2018-04-22
forum: New to Ubuntu
---

### Post by gladstone2 on 2018-04-22
Hi everyone,

Sorry for the bother, but I'm running into an odd problem at a rather inopportune time. For the past three or four days, whenever I power on my laptop, the screen starts flashing a bunch of different colors rapidly. This doesn't happen until I get to the login screen or after I log in. Eventually, the colors stop flashing and it settles on a single color, typically a black band around the center. I can't do anything at this point. For example, REISUB doesn't work. I have some keys on my keyboard that let me power on/off the screen, and those still work. The laptop then powers itself off after what seems to be a few minutes. If I keep turning the computer back on, eventually things pan out and I can use the computer normally, say for hours without any problem. But today, things got worse and it happened after working fine for about 30 minutes.

I'm somewhat pressed for time at the moment as I need to finish my dissertation by the 30th. I'd greatly appreciate any advice. I have my data backed up, but I don't have another computer. I'm weighing running out and just buying the cheapest thing I can get to try and finish my work, but it'd be great if I could keep working on this one and save the time/money as I'm already pressed for time as it is.

I looked around on the forum, and the most similar post seems to be this one: [HTML]https://ubuntuforums.org/showthread.php?t=2061180[/HTML].

The results I'm getting from the same terminal commands suggested there are:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"

```

```

Linux Patch 3.13.0-144-generic #193-Ubuntu SMP Thu Mar 15 17:03:53 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device [1558:2702]
    Kernel driver in use: i915

```

```

DESKTOP_SESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=Unity

```

Needless to say, I'd appreciate any input on the matter. Thanks a bunch.

---

### Post by Autodave on 2018-04-23
Not sure if this is a software or hardware problem. Can you try booting the machine up to either a USB stick or CD/DVD and try it that way?

This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

