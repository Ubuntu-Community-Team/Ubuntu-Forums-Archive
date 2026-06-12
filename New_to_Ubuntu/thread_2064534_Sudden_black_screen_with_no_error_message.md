---
title: "Sudden black screen with no error message"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by kaylaKT on 2012-09-29
Hi!  I'm running 11.10 on a 32 bit, 2 year old Lenovo thinkpad.  About once ever 10 hours of usage, my screen becomes black with no error message, but the computer and monitor are still on.  Hitting various keys, CTRL-ALT-DEL, mouse buttons, etc. don't do anything.  When I pull the plug, it reboots fine.  I have a dual boot system and didn't run into this problem on Windows 7 for over two weeks, so I assume it's a linux issue.  I also had the same issue using 12.04, also dual-boot, so I downgraded to 11.10, with no luck.  The last time this happened, I was running IDLE for python development and maybe Firefox in the background.  I don't remember what was running the previous times, but I wasn't running CPU-intensive programs or more than three applications at a time.

Any ideas on how to prevent the black screen?  I see similar "black screen" posts, but usually there's an error message.  Thanks in advance.

---

### Post by karat on 2012-09-30
> **kaylaKT said:**
> Hi!  I'm running 11.10 on a 32 bit, 2 year old Lenovo thinkpad.  About once ever 10 hours of usage, my screen becomes black with no error message, but the computer and monitor are still on.  Hitting various keys, CTRL-ALT-DEL, mouse buttons, etc. don't do anything.  When I pull the plug, it reboots fine.  I have a dual boot system and didn't run into this problem on Windows 7 for over two weeks, so I assume it's a linux issue.  I also had the same issue using 12.04, also dual-boot, so I downgraded to 11.10, with no luck.  The last time this happened, I was running IDLE for python development and maybe Firefox in the background.  I don't remember what was running the previous times, but I wasn't running CPU-intensive programs or more than three applications at a time.

Any ideas on how to prevent the black screen?  I see similar "black screen" posts, but usually there's an error message.  Thanks in advance.

I have a similar problem, but if my screen is clean and I look *really* closely, I can see outlines of windows, as if the brightness is turned way down.  However, I deal by putting the laptop in sleep mode (FN-1 on my system), and the brightness is back when I wake it up again.  However, it's likely to fail again before too long.  After this happened, I tried rebooting into Windows and had it happen again, so I decided it was a hardware failure (for a laptop over 5 years old).

So, my suggestions include:
1) Putting the computer to sleep and waking it up again when it happens.

2) *If* it recurs soon after waking up, try rebooting into Windows *after* a failure to see if it happens to Windows then. (I know you haven't seen it with Windows so far, but it can be hard to tell with an intermittent problem.)

---

### Post by Bashing-om on 2012-09-30
when you "black screen" can you ctl+alt+t to get a terminal ? Look in your logs for indicators ?

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by kaylaKT on 2012-10-01
Thanks, Karat and Bashing-om.  I'll try your solutions next time it happens.

---

