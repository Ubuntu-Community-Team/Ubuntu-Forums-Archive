---
title: "&quot;No system tray detected&quot;"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Primus1 on 2012-08-28
Hi, Got my new HP all-in-one printer/scanner working in 10.04 using the 12.04 HPLIP :p. However when starting my computer, this error box shows:-

"No system Tray detected on this system. Unable to start, exiting"

Is this a serious problem or small bug and how can I rectify it please?
Thanks

---

### Post by Ms. Daisy on 2012-08-29
Why can't you use the hplip for 10.04?

I believe the "system tray" refers to the unity dash which you obviously don't have in 10.04.

---

### Post by Primus1 on 2012-08-30
> **Ms. Daisy said:**
> Why can't you use the hplip for 10.04?

I believe the "system tray" refers to the unity dash which you obviously don't have in 10.04.

The hplip that comes with 10.04 does not support my all-in-one printer, the newer one which comes with 12 does. hplip is constantly updated to include more hardware.

My system tray problem had nothing to do with Unity and has been corrected.

---

### Post by cmcanulty on 2012-08-30
Please post the fix. I have that issue with 10 library laptops

---

### Post by Chrison999 on 2013-01-15
Did you ever get this fixed?  I'm having the same issue and I'd sure like to fix it, so if anyone knows the solution please post it here.

Thanks!

Regards,

Chris

---

### Post by cmcanulty on 2013-01-15
no even with hplip installed and put in startup applications I still get it

---

### Post by Chrison999 on 2013-01-15
Don't know if this will help you, but I found this by searching with Yahoo:

[https://bugs.launchpad.net/hplip/+bug/335662/comments/31](https://bugs.launchpad.net/hplip/+bug/335662/comments/31)

Seems that when Update Manager did it's thing awhile back it removed the Notification Area from my panel, and when I put it back then hp-systray came back again when I ran it from a terminal command prompt.  Haven't done a reboot, yet, but I don't see why it won't work now.

Silly me!  I hadn't noticed that the Notification Area was gone!  (Slapping head....)

Anyway, hope this helps you...

Regards,

Chris

---

### Post by Joentokyo on 2013-01-31
> **Chrison999 said:**
> Don't know if this will help you, but I found this by searching with Yahoo:

[https://bugs.launchpad.net/hplip/+bug/335662/comments/31](https://bugs.launchpad.net/hplip/+bug/335662/comments/31)

Seems that when Update Manager did it's thing awhile back it removed the Notification Area from my panel, and when I put it back then hp-systray came back again when I ran it from a terminal command prompt.  Haven't done a reboot, yet, but I don't see why it won't work now.

Silly me!  I hadn't noticed that the Notification Area was gone!  (Slapping head....)

Anyway, hope this helps you...

Regards,




Chris

Whoa :oops:, I had the same problem maybe this is the reason.

---

