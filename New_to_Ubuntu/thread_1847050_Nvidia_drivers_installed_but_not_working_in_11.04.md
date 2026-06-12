---
title: "Nvidia drivers installed but not working in 11.04"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by MashedUp on 2011-09-20
Hi all, I hope this is the right sub-forum...

I know there are heaps of posts on this (I've read most of them, and tried the solutions from many) but since going from 10.04, where everything worked perfectly, to 11.04 (also tried 10.10 - same) I can't get the drivers for my nvidia video card to work.


- I install the current driver (through Jockey or the terminal) which seems to go ok, and gives me a tiny little xorg.conf file without a "Driver" line.

- I reboot, but everything looks the same as before, and Jockey says the drivers are installed but not being used.  

- I run nvidia-settings but because xorg.conf doesn't say I'm using the nvidia driver it tells me to run nvidia-xconfig and reboot.

- I run nvidia-xconfig (well I do in 10.10 at least - 11.04 doesn't appear to have it!!) and get a nice looking xorg.conf.

- I reboot, and just get the CLI. The only way to boot back into the GUI is to remove the "Driver nvidia" line from xorg.conf (or to delete xorg.conf completely).


I've tried many, many variations on the above, but that's the basic story: install the drivers but see no change, and only get CLI if xorg.conf has the driver line.

Does anyone know how to fix this?  Anything....?

---

### Post by realzippy on 2011-09-20
```
sudo nvidia-bug-report.sh
```

..creates a file in your user's home directory.
Attach it..
..and welcome to UF!

---

### Post by technosysind on 2011-09-20
Give me details of your Nvidia Card? Have you tried the experimental 3d drivers. I think they work the best.

---

### Post by realzippy on 2011-09-20
All "details" will be in the bug-report file.
The "experimental" driver has the "worst" performance.

---

### Post by MashedUp on 2011-09-20
Thanks guys...

My card is a GT240, I just tried the experimental drivers (I assume they're the nouveau drivers?) now but no luck, and I'd rather not anyway.

My nvidia bug report is attached.

EDIT: just realised the bug report will depend on my current setup.  This one is with the experimental drivers installed, and no xorg.conf.  Will create some more in a minute.

---

### Post by MashedUp on 2011-09-20
Here is an nvidia bug report after reinstalling the nvidia-current drivers (strangely this time it didn't produce an xorg.conf, and so booted through to GUI - but it's not working).

BTW this is currently on the latest version on Mint - I was at my whit's end, thought (incorrectly: same results as Ubuntu, unsurprisingly) maybe there might be some trivial difference in my favour ;)

EDIT: more possibly relevant info: have two cards: a GT240 that currently has 1 screen plugged in, and an old 9300 with nothing plugged in. They both use the same driver (I checked with nvidia when I bought the 9300) and I've had them both working perfectly in 10.04 with 3 screens attached (2 in the GT240).  Right now I'd just be happy (very happy) to get just one screen working properly on the GT240.

---

