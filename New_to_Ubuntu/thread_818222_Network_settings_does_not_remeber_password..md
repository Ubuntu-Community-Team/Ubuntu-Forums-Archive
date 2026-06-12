---
title: "Network settings does not remeber password."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-06-04
Need a little help here, I have just changed my broadband provider, and reset my setting in network manager. The problem is that when I re-boot the computer the password is not saved. If I log out and in again it is fine, the prob only happens when I re-boot. Any Ideas ??

The key is type WPA Personal.

---

### Post by celticbhoy on 2008-06-04
I know its a little early for a bump but the wife is giving me a headache!!

---

### Post by cjv8888 on 2008-06-04
I had this problem too with Hardy with wireless.
Had to change to WICD and it worked fine.

---

### Post by celticbhoy on 2008-06-04
Trying not to sound stupid but what is WICD ??

---

### Post by iaculallad on 2008-06-04
Try configuring your Wireless password using the Gnome-Keyring-Manager.
The application to be configured with the password is /usr/bin/nm-applet

---

### Post by celticbhoy on 2008-06-04
Where do I get access to the keyring manager

---

### Post by cjv8888 on 2008-06-04
WICD is a replacement for the network manager . If you Google it, you will find a website with all the info about how to add it to the repositories and then you can just install it by Synaptic.
Good luck. :)

---

### Post by iaculallad on 2008-06-04
> **celticbhoy said:**
> Where do I get access to the keyring manager

Navigate to System->Administration->Keyring Manager

---

### Post by celticbhoy on 2008-06-04
sEEMS TO BE WORKING - tHNX.

---

### Post by Unix_Slayer on 2008-06-04
> **celticbhoy said:**
> sEEMS TO BE WORKING - tHNX.

It's in a config somewhere. knetworkmanager works fine for me.

---

