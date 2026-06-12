---
title: "Ubuntu 14.04 Freezes Randomly &amp; Internal Error Popups: Newly Built PC"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by alex234 on 2014-07-31
Hello, I mounted Ubuntu off a USB Stick I made bootable onto my new PC I built.  It has been working fine the past few weeks with the occasional crash at the login screen, but after downloading Wine and a handful of other programs (Steam, mostly games), I notice that when accessing the desktop, random "System Error" pop-ups occur for various folders/files.  Eventually, the screen freezes completely and I have to hit the reset button on my tower.  

I realize this is rather general, but this has happened regardless of what I'm doing (although usually happens after watching a livestream, not just idling on the desktop), and multiple times I've seen the details of the error report referring to a CPU freeze.  When checking the System Monitor, the resources don't seem especially burdened and I recently played a game on Wine at over 60 FPS.  Perhaps it is an installation problem, but overall the first impression of Ubuntu is a very sleek OS.

Specs:
GPU: EVGA GTX 660
CPU: i5-4460k
MOBO: Z97-A
HDD: 2TB WD
RAM: 2x 8GB DDR3 Ripjaws
I'm using HDMI, and I also recently installed new NVIDIA drivers to see if that was causing the errors.

---

### Post by QIII on 2014-07-31
Hello!

If you could post one or two of those random system error messages it would be very helpful.

---

### Post by alex234 on 2014-07-31
I can't seem to replicate it at desktop startup, is there perhaps a place these are stored?

EDIT: Nevermind:

Package: linux-image-3.13.0-32-generic 3.13.0-32.57
Problem Type: KernelOops
Title: BUG: soft lockup-CPU#2 stuck for 23s! [chrome:4352]
Annotation: Your System might become unstable now and might need to be restarted
ApportVersion: 2.14.1-0ubuntu3.2
Architecture: amd64

...And many more smaller descriptions like the date and time.  I was watching a livestream and a shockwave player crashed and this shortly followed.  I wouldn't be surprised if this is one of the problems.  I can't vouch for any varying reports yet, but I will post them if they come.

---

### Post by alex234 on 2014-08-01
So after more of the previous logs showed up, I decided to check System Monitor.  I did not realize CPU (Core) 3 was being run to 100%, while the others were hovering around 10-20%.
I tried disabling a few chrome extensions, so only PDF Reader and Google Docs is enabled, neither should interfere with daily use.

My PC then soon froze and I had to restart, obtaining the internal errors much like the one above.

My thoughts:
-The CPU driver somehow needs to be updated
-Just don't use chrome.  Firefox was installed originally for a reason. :KS

---

### Post by Vladlenin5000 on 2014-08-01
[http://ubuntuforums.org/showthread.php?t=2205211](http://ubuntuforums.org/showthread.php?t=2205211)

---

### Post by Impavidus on 2014-08-01
Sounds like a hardware issue. Maybe the power supply, but I was thinking of RAM.

---

### Post by alex234 on 2014-08-01
Hello, I am currently running a memtest, I'll leave it on overnight.  I forgot to mention something I obliviously overlooked: a beep code frequently at startup.  I didn't think anything of it after the initial beep, but 1 long and 3 short beeps most likely means memory failure.  I will see if any errors come up before reseating the RAM, but I may have to RMA.  Any further suggestions is always welcome though in the meantime.

---

### Post by terrykiwi83 on 2014-08-02
One Long and Three Short beeps can backup your statement about the memory (RAM). I would see how you go with memtest and RMA them if you get any errors.

Source: [http://www.computerhope.com/issues/ch000996.htm](http://www.computerhope.com/issues/ch000996.htm)

---

### Post by alex234 on 2014-08-02
13 passes and absolutely no errors...I could've ran it longer I guess.  I'm considering updating my BIOS firmware, or maybe considering drivers that are bad (although I recently reinstalled Nvidia drivers to see if that made a difference).  My Ubuntu install could also be bad, I wouldn't be surprised if that caused freezing.  Also, sometimes when booting the beep code does not play.  Or better still, recheck my MOBO documentation to see what RAM slots should be used first.  I currently have mine staggered, first one closest to CPU and second one in the third from the CPU.

---

### Post by terrykiwi83 on 2014-08-02
Maybe check the manufacturers recommendation for RAM [here]("http://dlcdnet.asus.com/pub/ASUS/mb/LGA1150/Z97-A/Z97_A_DIMM_QVL.pdf"), see if yours is there and change the settings to those recommended by ASUS. See if that makes any difference.

---

### Post by alex234 on 2014-08-03
Interesting...the exact model number is not listed.  However, one very close to it is (8GB, DDR3 1600).  Would CAS/latency actually throw off the MOBO that much?
Also I booted up the computer again today after the memtest and no beep codes occurred, so far has been running smoothly, even playing a game on Wine.

---

### Post by alex234 on 2014-08-13
We'll call it solved.  Haven't had a problem and I think simply running that memtest, doing some boot repairs and updates seemed to help somehow. Thanks for the replies, I'll be vigilant about it.

---

