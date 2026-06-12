---
title: "PowerEdge R630"
date: 2023-11-26
forum: New to Ubuntu
---

### Post by fenux1977 on 2023-11-26
I have purchased 

[COLOR=#333333][FONT=Montserrat]Dell PowerEdge R630 Server | 2x E5-2660 V4 2.0Ghz 28 Cores | 16GB | S130 | 2x HDD Trays

Do I need to put the server version or can I install the standard?

Or will it work at all?


Thanks,

John Coleman[/FONT][/COLOR]

---

### Post by deadflowr on 2023-11-26
Properly you would install the server version.


I'm not sure what the Standard version is.

I would think the server version is the standard version.

There is a desktop version, but it exists the same as the server version.

In fact, an argument could be made that the desktop version is the niche version as the server version has hundreds of millions (maybe billions) of installs.
Whereas the desktop version has tens of millions, at best.

---

### Post by MAFoElffen on 2023-11-26
It will work with either Server Edition and Desktop Edition, with some caveats...

Storage: The PERC RAID does not support JBOD, so for Ubuntu to see the drives, they either need to be setup as RAID Arrays on the PERC, or just set the individual drives as single RAID 0 ararays (work-around for JBOD).

It has a Matrox onboard GPU. It will not support a GPU card on that server... 

If you use Desktop, you may not have problems with graphics = Matrox released the driver as opensurce after kernel 5.10. But some users still had problems with that... 
RE: 
[https://ubuntuforums.org/showthread.php?t=2329585&p=13512765#post13512765](https://ubuntuforums.org/showthread.php?t=2329585&p=13512765#post13512765)



If so, then use 'nomodeset' as a boot parameter until you get the graphics driver setup. On Server with Matrox G200 to G400 variants, for graphics, I use X11 (Xorg) and use driver 'xserver-xorg-video-mga'... I post some instructions on how to do that during and install. Let's set if I can find that for you...

This post and the post before it: [https://ubuntuforums.org/showthread.php?t=2492127&p=14163640#post14163640](https://ubuntuforums.org/showthread.php?t=2492127&p=14163640#post14163640)

Also here is more info I posted on that GPU: [https://ubuntuforums.org/showthread.php?t=2477375&p=14105529#post14105529](https://ubuntuforums.org/showthread.php?t=2477375&p=14105529#post14105529)

---

