---
title: "Upgrading kernel from a CD"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by MisterA on 2008-11-01
I have installed Ubuntu 8.04.1 server onto an Intel Atom system with the Intel D945GCLF chipset. There is a known problem with the onboard LAN driver not working and from looking at the forums the best solution is to upgrade the Kernel. I have downloaded the  package linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb and blown it onto a CD but when I try apt-get install it keeps trying to access the package from the network. How can I persuade it to install the package from the CD or do I need to do something else altogether? All the posts I see assume network connectivity.

---

### Post by phidia on 2008-11-01
You can edit your repos in /etc/apt/sources.list by placing a "#" in front of all of those except the cdrom and that should do it.
Opening System > Admin > Software sources will let you do that in an easier gui way.

---

### Post by taurus on 2008-11-01
> **phidia said:**
> You can edit your repos in /etc/apt/sources.list by placing a "#" in front of all of those except the cdrom and that should do it.
Opening System > Admin > Software sources will let you do that in an easier gui way.

I thought the server has no GUI UNLESS he installed it by hand after.  Therefore, he has to use either vi or pico from a prompt to do any editing.

```
sudo pico -Bw /etc/apt/sources.list
```

---

### Post by phidia on 2008-11-01
You're right taurus, while I was composing my response I forgot the OP had a server install.

---

### Post by MisterA on 2008-11-03
Thanks guys that was what I needed and thanks Phidia for suggesting Pico I find VI very frustrating. Just one more thing after trying so many different commands I'm not sure how I picked up the package. Do I use (I know about sudo) apt-get install <package name> or does it pick it up automatically? I will get this working for the benefit of my experience and then try 8.10

---

