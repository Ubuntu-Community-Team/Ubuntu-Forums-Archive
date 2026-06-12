---
title: "Bootchart Analysis/Diagnosis. Any Suggestions?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by kestal on 2008-11-15
So I managed to take out my old laptop and install Ubuntu 8.10 on it. Its quite nice. Problem is I am still 'pretty new' to Linux and although I have a general understanding of the things mentioned in the bootchart, some of the data (like CPU/IO spikes, among other things that take a good chunk to load) worries me. There is an attachment provided at the bottom.


**[COLOR="DarkRed"]My Specs: [/COLOR]**
> 
Laptop: Gateway 7422gx. 2.2ghz Single Core. (seems to clock down to 800ghz a lot, plugged in or battery).
Ram: 1gb
HDD: 80gb
Video: ATI 9600/9700 Mobility. (64mb)


I turned off all the services I do not think I need.

**[COLOR="DarkRed"]The Services that are Left:[/COLOR]**
> AT SPI Registry Wrapper
Gnome Keyring Daemon Wrapper
Gnome Settings Daemon
GNOME Settings Daemon Helper
Gnome Splash Screen (is this the uSplash that you see with load bar, or GDM?)
Network Manager
Power Manager
Pulse Audio
Window Manager

[COLOR="RoyalBlue"]**Q1:**[/COLOR] Is there a way to turn off hardware? (or at least, not load it up via a config file?) Would this help decrease the time it takes to boot?

**[COLOR="RoyalBlue"]Q2:[/COLOR]** Which is better for a general use user? Readahead, Preload, sReadahead? etc? are these even related?

**Extra Information:**
- I only use 1 USB out of 4. No exceptions really. I rarely use the 1. I do not use a printer with this laptop.
- I only connect through wireless.
- I do not use my card reader, my VGA connector, or my Mic.
- I only use my main account, I do not log onto root. (GDM changes, possibly?)

I also installed Preload. Though Readahead is still running.
I am using Wine 1.1.8.
I did not use BUM (or a program related) to remove anything from boot yet.
I will not be using a printer or accessing remote files from another computer within a wireless network.
I wish to keep my usplash, even though I am only stuck using the default one.

Any Suggestions? I tried a few times to get lower than 29s but each time I tried it stopped working.

[CENTER]**>> Attachment Provided Below <<**[/CENTER]

---

