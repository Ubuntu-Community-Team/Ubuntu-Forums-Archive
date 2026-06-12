---
title: "Slow scrolling/laggy typing in Geany/Gedit"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mrkennie on 2011-09-24
Has anyone experienced slow performance in Geany/Gedit? CPU reaches 100% while scrolling. The experience is like running the application over a slow network.

I've read there was a similar issue in Maverick which was somehow related to sub-pixel font rendering but I can't see anyway to configure this in Oneiric to try.

I was going to raise a bug but I use the Nvidia restricted drivers and I get the feeling it's going to be a NOP.

---

### Post by ventrical on 2011-09-24
> **mrkennie said:**
> Has anyone experienced slow performance in Geany/Gedit? CPU reaches 100% while scrolling. The experience is like running the application over a slow network.

I've read there was a similar issue in Maverick which was somehow related to sub-pixel font rendering but I can't see anyway to configure this in Oneiric to try.

I was going to raise a bug but I use the Nvidia restricted drivers and I get the feeling it's going to be a NOP.


 Gedit is working beautifully here. I have the GT218, 2.66GHZ dual core on an Intel Desktop MoB. The last kernel update really fixed any  processor issues. Running now really cool.

---

### Post by mrkennie on 2011-09-24
My hardware isn't great but it's not bad either. I have an AMD 64 X2 5600+, 4GB ram and onboard Geforce 8200 which handles most things pretty well, outside of gaming at least (from what little of that I do). 

We are on the same kernel I assume?

uname -a gives:

```
Linux jacob 3.0.0-11-generic #18-Ubuntu SMP Tue Sep 13 23:38:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

apt-cache policy linux-image-generic gives:

```
linux-image-generic:
  Installed: 3.0.0.11.12
  Candidate: 3.0.0.11.12
  Version table:
 *** 3.0.0.11.12 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by cariboo on 2011-09-24
I'd suggest opening a terminal and running top, when you run into the problem with gedit, to see if there is anything using up cpu cycles.

---

### Post by mrkennie on 2011-09-25
> **cariboo907 said:**
> I'd suggest opening a terminal and running top, when you run into the problem with gedit, to see if there is anything using up cpu cycles.

Xorg CPU usage jumps straight to ~60% and beyond with Gedit and Compiz coming second and third with ~5%. I can't see anything else significant. It doesn't happen straight away either, it seems to degrade over a short period of time. 

I've installed kernel 3.0.0-12 as announced on the forums but no change as far as this issue goes.

I think I'll report this as a bug anyway and see what comes of it.

---

