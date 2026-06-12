---
title: "xubuntu on 8 gb usb key, cannot install VirtualBox and &quot;failed to execute web browser"
date: 2015-10-31
forum: New to Ubuntu
---

### Post by andrew266 on 2015-10-31
Hi, I cannot install VirtualBox. I get "new softare can't be installed because there is a problem with software currently installed. Do you want to repair it?" I put Repair but next I get "package operation failed". " IN the details I get "...failed to create directory: no space left  dpkg-deb: error: subprocess tar returned error exit status 2....".
I was following an accurate guide to put virtual box in xubuntu partitioning a usb of 8 gb. I do not know if this help but in desktop I have as directories the second partition of my usb, my pc hard drive, then 272 MB volume, then File sytem and home.

---

### Post by Bucky Ball on 2015-10-31
Welcome. Please provide a link to the guide you are using.

---

### Post by andrew266 on 2015-11-01
it is a guide found in the deep web. I wounder, maybe i get that error cause 8 gb are not enough?

---

### Post by mastablasta on 2015-11-02
> **andrew266 said:**
> ...failed to create directory: no space left 


there you go.

check the disk space 

```
df -h

```

---

### Post by Vladlenin5000 on 2015-11-02
> **andrew266 said:**
> it is a guide found in the deep web. I wounder, maybe i get that error cause 8 gb are not enough?

By all means, feel free to post it. We all know how to use TOR :popcorn:

---

