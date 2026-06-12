---
title: "Intermittent lock-ups during boot-up..."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by mingle on 2008-07-08
Hi,

I have Ubuntu 8.04 installed on my HP D530 desktop (P4, 512MB, i845 GFX) and I have a problem with it locking-up during the boot process.

The orange Ubuntu progress-bar completes, then the "X" mouse cursor appears (for about 1 second), then it changes to the Gnome pointer/cursor for a split second. Then the pointer graphics corrupt, the screen goes blank (my LCD monitor reports "Input Signal Out of Range") and the system freezes.

So it appears to be happening just before the login screen appears...

Then I have to power off the PC, as nothing else will break out of the lock-up.

This only seems to happen about 30% of the time, which is strange (and bloody annoying!)

Where should I look (log files, etc) to see where it's bombing out?

Cheers,

Mike.

---

### Post by ZabiGG on 2008-07-08
There are two outputs that could help you figure how where the problem lies.

enter these commands in a terminal right after boot, or log in directly to a terminal before the gnome desktop manager loads (CTRL-ALT_F1)

```
dmesg > dmesg_txt
```

```
less /var/log/Xorg.0.log
```

that's a zero, not a capital o.

You'll find the text documents in /home/yourusername.

Hope this helps,

Z.

---

