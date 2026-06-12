---
title: "no longer can adjust brigthness, contrast and gamma on nvidia"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by forgetton_nick on 2013-04-20
Hi,
Got an old laptop with a 8400M, used to use nvidia-settings all the time to adjust the screen when watching movies.
Now under xserver settings I get the error :
**[SIZE=4][The NVIDIA X driver is not new enough to support the nvidia-settings Display Configuration page]("http://askubuntu.com/questions/205628/the-nvidia-x-driver-is-not-new-enough-to-support-the-nvidia-settings-display-con")[/SIZE]**


I've done nothing to the set up except allow system updates that ubuntu has been bugging me for weeks about, nothing else has changed by me.
Removing and reinstalling nvidia drivers or nvidia-settings has not helped.

Any ideas to go back to how it was before I updated the system?
The system update did not include new nvidia drivers, still on driver version 173; but some software ubuntu wanted to install stuffed something up (Xorg?)

Edit:  for some reason, Driver Version 173.14.36 and NV-Control version: 1.16 stopped working.  I had the same problem with Driver Version 295.40 and NV-Control version: 1.27
Maybe that update triggered it all, but removing them and going back to Driver Version 173.14.36 and NV-Control version: 1.16 didn't even fix the problem for some reason.


Problem solved upgrading to Driver Version 304.88 and NV-Control version: 1.28

---

