---
title: "Problem with 8.04 sound"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by leehouse on 2008-05-16
So, I've read through some of the comprehensive sound problem solution guide and nothing seems to work.  I'm running on a Dell Inspiron 1420 laptop, which prior to upgrading to 8.04 had no issues with sound.  Now the sound card isn't detected at all.  

My sound card is listed as Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) when I use lspci -v

I am unsure which alsa driver to use and all in all am quite lost.  If it isn't obvious I'm rather new to ubuntu.


Thanks for any help you can offer.

I also googled the sound card which came up with some instructions that didn't seem to work, as I recieved

---

### Post by almabeck on 2008-05-16
> **leehouse said:**
> So, I've read through some of the comprehensive sound problem solution guide and nothing seems to work.  I'm running on a Dell Inspiron 1420 laptop, which prior to upgrading to 8.04 had no issues with sound.  Now the sound card isn't detected at all.  

My sound card is listed as Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) when I use lspci -v

I am unsure which alsa driver to use and all in all am quite lost.  If it isn't obvious I'm rather new to ubuntu.


Thanks for any help you can offer.

I also googled the sound card which came up with some instructions that didn't seem to work, as I recieved

I've got the exact same computer, same sound card (although I don't know how to tell if the sound card is detected). I've tried every suggestion on this forum (I have a list of what I've tried if it would be helpful)--all to no avail. So if anyone out there can solve this problem, you'll be helping two folks (if not more).

---

### Post by almabeck on 2008-05-16
Addendum to above post: I run Windows using VBox. When I go into that to see if I have sound (Sounds & Audio Devices, Properties, Volume) it says, "No Audo Device".

---

### Post by leehouse on 2008-05-16
Just for a bit of further clarification aplay -l is listing that I have no sound card.

---

### Post by lswest on 2008-05-16
i'm not sure if this is similar to what you are experiencing but there's a bug report on launchpad that says there was a fix released (for gutsy) for the card: [https://bugs.launchpad.net/ubuntu/+bug/122560](https://bugs.launchpad.net/ubuntu/+bug/122560) have a look there.

also maybe look at this: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/197394](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/197394) or [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192005](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192005)

---

### Post by leehouse on 2008-05-16
I have looked through those bug reports and none of the solutions seem to work.  Alsa still doesn't seem to register my sound card at all.

---

### Post by joseardzm on 2008-05-21
my sound do works, but not as in xp, i remember that in xp it was also somehow tricky to get the sound working, because the 1420s comes with Vista mostly (except for 1420n) , I dont know how to help you , i think i also have ICH8 audio, and I have hardy with kernel 2.6.24-16 generic. 

The problem I have is that my audio output is pretty low, and sometimes distorted , also in the volume; i dont hear anything until it goes beyond the half of the bar (i m not deaf), very weird but at least is better than nothing.

---

