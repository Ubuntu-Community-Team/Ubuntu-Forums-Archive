---
title: "network manager on xfce"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by AVStudio on 2012-10-03
I do all my ubuntu installs from the server iso and then install a window manager on top.  i did this with xfce and 12.04 and duriing the install i setup wireless network access.   i don't know what service is connecting me?  as long as i boot up in range of my network i'm connected on wlan0.  network manager isn't running according to the nm-applet.  how do i configure network manager properly?

---

### Post by cway00 on 2012-10-03
> **AVStudio said:**
> I do all my ubuntu installs from the server iso and then install a window manager on top.  i did this with xfce and 12.04 and duriing the install i setup wireless network access.   i don't know what service is connecting me?  as long as i boot up in range of my network i'm connected on wlan0.  network manager isn't running according to the nm-applet.  how do i configure network manager properly?

Open a terminal and press for admin access

```

sudo su 

``` 

then press 
```

service network-manager start

```

This starts network manager if it still does not start ...reply

---

### Post by 2F4U on 2012-10-03
There are more than one method to connect to a network, and NetworkManager is only one of them. Ubuntu server, as far as I rember, doesn't ship with NetworkManager by default, but instead uses the more traditional configuration through /etc/network/interfaces and shell scripts (ifconfig, ifup, ifdown).

---

### Post by AVStudio on 2012-10-03
thanks for the info!  i see now how the /etc/network/interface file was connecting me.  as for network-manager whats the best way to start the service at boot?  how do i set wlan0 to be managed? (applet shows eth0 manged but not wlan0) i would guess because the interface file has it as default.  and finally if network-manager is configured corectly will the part of the boot sequence when it looks for a network take forever?  i mean is there a way to adjust the time out or remove it? thanks again for the quick reply!!

---

