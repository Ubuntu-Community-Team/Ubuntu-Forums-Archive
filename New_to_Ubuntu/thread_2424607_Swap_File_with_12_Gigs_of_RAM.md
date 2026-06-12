---
title: "Swap File with 12 Gigs of RAM?"
date: 2019-08-11
forum: New to Ubuntu
---

### Post by white-chocolate on 2019-08-11
I moved to Ubuntu from Linux Mint. My machine has 12 Gigs of RAM. Swappiness is set to 1. Any idea why System Monitor shows a swap file and that it is using space? I know watching YouTube didn't consume all of my available memory. When using Mint (itself a Ubuntu derivative) when my swappiness was set to 1, my swap file would be 0. Any ideas why Ubuntu 19.04 is creating a swap file?

---

### Post by Bashing-om on 2019-08-11
white-chocolate; Hello

Even with 12 Gigs of ram a bit of swap is a good thing - the system does look for swap space in any event :)
In new installs a swap file is now prefered rather than a partition. Disk space is cheap :)
Too know "swap":
```

swapon -s
free -m

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by TheFu on 2019-08-11
Seems that all Linux desktops need *some* amount of swap.  
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-Does-Bad-Low-RAM](https://www.phoronix.com/scan.php?page=news_item&px=Linux-Does-Bad-Low-RAM)

I've had issues where swap wasn't large enough and the GUI appeared to lock up for 10+ minutes.  By ssh'ing in, I could see it was just the GUI and not the OS.  Checked the swap and the default created by the installer was a little under 1GB, which doesn't make sense to me.  Swap is there to provide feedback to end-users when RAM is becoming less and less available.  The entire system gets a little slower, but doesn't stop.  I've had 2G, 4G, 6G, 8G and 16G desktops and in my considered opinion, 4.1G of swap is the correct amount for any of these RAM amounts.  For low-RAM systems, I still want to use the RAM hog browsers and not have the OS crash.  For systems with more RAM, I want the slowness that using swap provides as feedback.  This is only for desktops.  If you use hibernation, the amount of swap matters in a different way.  I don't hibernate, but I do go into standby on a laptop every night and a few times daily.

I run a very light desktop setup.  No DE.  fvwm as my window manager, which is extremely light on RAM. I can only imagine that people using DEs that suck an extra GB of RAM for their overhead would have the issues much quicker and more often if they don't have swap.

For servers, often, almost always, we can tune the available RAM to match what is needed to perform all necessary tasks of the server so no swap is necessary.  Almost all of my servers are configured without any swap, though a few can need swap to fill in for very high transaction periods that happen just a few times a month.

---

