---
title: "Ubuntu 14.04 crashes frequently"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by davoudi on 2014-05-03
Hi Folk,

 I recently installed Ubuntu 14.04 which unfortunately crashes when it is in locked mode (I haven't observe the otherwise). The background has a random shapes, mouse is active and I can move it around, and sound also crashes. I guess it is a problem with Unity. This problem happenes every other day so it is not very frequent.

 Any help to resolve the problem is greatly appreciated.

Best wishes,
Bahman.

---

### Post by LastDino on 2014-05-03
System info? Especially GPU? Was that a fresh install?

---

### Post by davoudi on 2014-05-04
My Laptop is sony vaio with the following specifications:

Four CPU
Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
4 GB RAM
NVIDIA Corporation GT218M [GEForce310]

And yes the instalation was fresh.

---

### Post by Ubi_one_2014 on 2014-05-04
what kernel version do you run?

uname -r[enter]

---

### Post by davoudi on 2014-05-04
It is 3.13.0-24-generic.

---

### Post by BBQdave on 2014-05-04
> **davoudi said:**
> My Laptop is sony vaio with the following specifications:

Four CPU
Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
4 GB RAM
[COLOR=#ff0000]NVIDIA[/COLOR] Corporation GT218M [GEForce310]

My thought would be video issues with the hybrid hardware (NVIDIA graphics).

No problems with Ubuntu 14.04 (Unity) and Lenovo Thinkpad T400 - Intel processor with Intel graphics.

Maybe not a complete fix, but a work around - you could disable auto lock when screen sleeps. Again, funky background images, makes me think video driver issues.

---

### Post by davoudi on 2014-05-04
> **BBQdave said:**
> My thought would be video issues with the hybrid hardware (NVIDIA graphics).

No problems with Ubuntu 14.04 (Unity) and Lenovo Thinkpad T400 - Intel processor with Intel graphics.

Maybe not a complete fix, but a work around - you could disable auto lock when screen sleeps. Again, funky background images, makes me think video driver issues.

So how I could resolve the issue? Is there any better driver I can use?

---

### Post by LastDino on 2014-05-04
Look for supported Nvdia driver released for ''Linux'' on their site. By default Ubuntu installs open source drivers. My first thought was GPU too but you mentioned you have this problem periodically and sound issues as well, so I'm in two minds. It wouldn't hurt to try though.

---

### Post by davoudi on 2014-05-07
Thanks a lot. That resolve the problem using the commands in this link [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/).

---

### Post by LastDino on 2014-05-07
I generally recommend to install directly from site and not through unknown (At least I didn't know about that site) PPA sources, but I'm glad it worked out for you.

---

### Post by sandyd on 2014-05-07
xorg-edgers/ubuntu-x-swat is not a unknown ppa

---

### Post by LastDino on 2014-05-07
Like the original post said: I did not knew about it, but thanks! Now I know  ;D

---

