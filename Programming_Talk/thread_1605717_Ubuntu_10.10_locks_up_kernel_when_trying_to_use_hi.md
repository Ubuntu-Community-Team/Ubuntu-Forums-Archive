---
title: "Ubuntu 10.10 locks up kernel when trying to use hidapi in X-Plane Plugin"
date: 2010-10-25
forum: Programming Talk
---

### Post by sparker256 on 2010-10-25
I am a X-Plane plugin developer for Saitek panels running Linux. My plugin worked great in previous versions (9.04, 9.10) until when alpha and beta testing Ubuntu 10.10 my led displays did not look right. Saitek panels use feature report for the led display and I was using write report on previous versions but does not work correctly now with 10.10. To get around this problem I found a lib called hidapi [http://github.com/signal11/hidapi](http://github.com/signal11/hidapi) by Alan Ott.

This is my problem, when I use this lib in my plugin I will get a kernel lock-up in Ubuntu soon after I start X-Plane other times many minutes after I start X-Plane.

I am using the NVIDIA driver as packaged by Ubuntu and it appears like the system log stack dumps in the NVIDIA driver. I have included my system logs and wondered if some one has a idea as to why this is happening.

Thanks Bill

---

