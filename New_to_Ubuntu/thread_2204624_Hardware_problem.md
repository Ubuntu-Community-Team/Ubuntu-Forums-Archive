---
title: "Hardware problem"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by h_piper on 2014-02-09
I just got a new usb dac that I use for listening to music on my computer. It works fine under Win7. When I boot into Ubuntu 12.4 I get a very sluggish OS. If I run 'top' I see a process called 'pulseaudio' running and taking up 35-50% of my cpu. I am not running any applications at all at this point so I kind of wonder why pulseaudio is running at all. However, if I unplug the USB connector on my dac evrything goes back to normal, pulse audio is nowhere to be seen on 'top' and all my appliocations run normally. Is there any fix for this other than get a different dac that gets along with Linux better? I tried killing pulseadio but it just pops back up in a few seconds.

---

### Post by UltimateCat on 2014-02-09
PulseAudio is a sound system for POSIX OSes, meaning that it is a proxy  for your sound applications. It allows you to do advanced operations on  your sound data as it passes between your application and your hardware.

 PulseAudio is designed for Linux systems. It has also been ported to  and tested on Solaris, FreeBSD, NetBSD, MacOS X, Windows 2000 and  Windows XP.
  PulseAudio is an integral part of all relevant modern Linux  distributions and used in various mobile devices by multiple vendors.

> Is there any fix for this other than get a different dac that gets along with Linux better? 


Sorry I don't know a fix for it but other members might know.

This might help:
[http://ubuntuforums.org/showthread.php?t=1921650](http://ubuntuforums.org/showthread.php?t=1921650)

---

