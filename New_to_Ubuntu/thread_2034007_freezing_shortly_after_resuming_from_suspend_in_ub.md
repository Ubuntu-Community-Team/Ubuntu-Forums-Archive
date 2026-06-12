---
title: "freezing shortly after resuming from suspend in ubuntu 12.04"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by ziggutas on 2012-07-27
I'm a beginner in ubuntu and the forum; will need simple instructions for technical stuff and using commands. 

I have ubuntu 12.04 with kernel version recently updated to 3.2.0.27.29 dual booting with windows xp on a new custom pc. Standby in windows works fine. Motherboard is ASROCK 61M,Intel® Core™ i3-2120 CPU @ 3.30GHz × 4 ,Intel Sandybridge desktop graphics, 8GB memory and 1TB hard disk. Ubuntu partition 500GB.

This problem is a bit erratic but the constant part of it is that I will always get a freeze up after using suspend where I can see no alternative to a hard restart to get back in. Sometimes I get a black screen when pc wakes up, with no mouse or keyboard input possible. Sometimes it wakes to the locked screen display and i can resume a session only for the screen and keyboard to freeze sooner (most often) or later. I have just tried suspend from the terminal and it woke up to a resumed session with terminal open etc, but froze almost immediately. The pc is only a few weeks old, working fine apart from this, and has had this problem  issue all along.

Things I have tried:
After latest kernel update problem still persists so I tried the fix suggested in post#6 of this;  [http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290) but later realised perhaps I shouldn't have, as the fix was intended for kernel 3.2.0.24. But it did seem to get me past the black screen stage, only to freeze later.

In the ASROCK Set Up utility I have disabled CPU C3 , C6 and Package C State Support support; leaving C1E State enabled. This doesn't appear to make any difference.

Anybody have any ideas?

---

### Post by ziggutas on 2012-07-31
Since posting this problem I have re-enabled C3, C6 and Package C State Support in the UEFI Setup Utility. Resuming from suspend is udually possible - the pc wakes up and shows screen login - but everything will still freeze up every time.

I have contacted ASROCK to see if they have any advice about how to set things.

---

### Post by ka91 on 2012-07-31
suggest to test your pc on windows. standby it or hibernate it on windows. do you see same problem?

---

### Post by ziggutas on 2012-08-01
Standby in windows xp (this is a dual boot set up) works flawlessly.

---

### Post by ziggutas on 2012-08-04
Can anybody help me with this?

In addition to the above: I tried swapping keyboards and mouse - but this made things worse (maybe coincidentally, who knows?). Resume from suspend and get black screen and immediate freeze.

Updated to kernel 3.4.0-030400-generic-pae. Resume from suspend gets as far as screen login. One occasion black screen with tty1 and login prompt at top left of screen; but keyboard/mouse frozen.

I notice opinion is divided on whether one should suspend a desktop pc in the first place, but I find it to be a core requirement and miss it a lot!

---

### Post by ziggutas on 2012-08-15
Anybody?

Still cannot resume from *suspend*. PC will wake up but mouse keyboard and monitor nearly always unresponsive, i.e. monitor still in low power mode and unlit, keyboard no caps lock or any other input possible. Sometimes PC wakes from suspend normally to a login screen, but mouse pointer and keyboard will always freeze at some point; either in the process of logging in or very soon into a session. What little hair I have left is being torn out!!

Automatic updates issued kernel 3.2.0-29-generic pae, which I am using now. Problem persists.

---

### Post by nothingspecial on 2012-08-16
Thread closed at OP's request.

---

