---
title: "Help with running vmware player"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nikhilbhardwaj on 2011-10-02
I installed vmware player, upon running it it asks for compiling modules.
That step fails, here's the output of the log file.
 I'm running 11.10 beta2
```
Oct 02 19:39:28.117: app-140027678226208| Your GCC version: 4.6
Oct 02 19:39:28.175: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.178: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.180: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.182: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.184: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.665: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.666: app-140027678226208| Building module vmmon.
Oct 02 19:39:28.666: app-140027678226208| Extracting the sources of the vmmon module.
Oct 02 19:39:28.686: app-140027678226208| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.0.0-11-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6.1
Oct 02 19:39:29.800: app-140027678226208| Failed to compile module vmmon!
```

---

### Post by RikoW on 2011-10-02
Hi :)

it seems like there is a vmplayer4.0 which should work out of the box with the Kernel 3.x.

However, I have VMware Workstation and had the same problem. There is a patch, which fixes VMware up. I don have the exact link anymore of what I followed, but this looks like what I did and it worked:

[http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&p=12078]("http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&p=12078")

Good luck,
     Riko

---

### Post by nikhilbhardwaj on 2011-10-04
thanks will give that a shot.

---

### Post by nikhilbhardwaj on 2011-10-11
works!!

---

