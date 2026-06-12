---
title: "madwifi"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by grumpylad77 on 2008-07-01
I have a compaq Presario F700, I got the wireless working with this guide [//http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html]("//http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html")

I followed this guide and it worked, but the next time I rebooted my wireless disappeared. 
So I did
sudo iwlist scan... wlan0 doesn't even show up anymore.
Any ideas?

---

### Post by avtolle on 2008-07-01
If you updated the kernel between the time you got it working and when you restarted, you're going to need to redo the installation process I think.

---

### Post by stchman on 2008-07-01
> **grumpylad77 said:**
> I have a compaq Presario F700, I got the wireless working with this guide [//http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html")

I followed this guide and it worked, but the next time I rebooted my wireless disappeared. 
So I did
sudo iwlist scan... wlan0 doesn't even show up anymore.
Any ideas?

When you install drivers via the method listed above they are only going to work on a certain kernel.  If you try another kernel then your drivers will not work.

Pressing ESC during bootup will give you a list of kernels to choose.  The latest is the -19.

---

### Post by grumpylad77 on 2008-07-01
That worked... thanks.

---

