---
title: "[SOLVED] Help! accidently uninstalled network manager."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by bhadotia on 2008-04-28
I was browsing the new hardy repositries and decided to install some packages in "new in repositries section" namely eagle usb and dhcp client (I don't actually know what these packages are meant for).

After the installation I found that the network manager was automatically uninstalled . May I did not read the dependcy notification that comes when one installs a package. It might have uninstalled the network manager.


Now even after uninstalling the packages , I find that synaptics is not installing the network manager . It says that they might be "not uploaded,obsolete"  and some things like that.


I NEED HELP.  PLEASE , I AM NOT ABLE TO BROWSE THE NET.

---

### Post by szymon_g on 2008-04-28
do you have a wired or wireless connection?

---

### Post by bhadotia on 2008-04-28
Yes, I have wireless connection.

---

### Post by szymon_g on 2008-04-28
the easiest way wyould be to connect your hub/router with your comp by a cable (if its possible- it would be great) than put into your

/etc/network/interfaces

lines like that

# The primary network interface
auto eth0
iface eth0 inet dhcp

(assuming that eth0 is your ethernet card) - you may check it by typing 

sudo iwconfig

than you may run

sudo dhclient
(or
sudo /etc/init.d/networking restart
)
and check connection (eg. ping [www.google.com](www.google.com))

if wired connection isnt possible- could you give me some information: is this connection encrypted (wpa, wep etc) or not?
if yes, than, i'm afraid, i may not be able to help you :/

---

### Post by bhadotia on 2008-04-28
Is there no way in which we can reinstall the gnome network manager?

---

### Post by onero on 2008-04-28
If you have the CD, I believe you can install it from there. Disable the other repositories in Synaptic and enable installation from CD (it's a checkbox there, forgot what exactly as I'm not on my Ubuntu box right now), and then install as usual.

---

### Post by Tom--d on 2008-04-28
do.. 

```
sudo apt-get install network-manager-gnome
```

---

### Post by gardara on 2008-04-28
I would recommend you to try wicd instead of network-manager... I just tried it few days ago and I just love it... 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by bhadotia on 2008-04-28
Thanks I have installed the network manager fromthe cd.

---

### Post by quill3033 on 2009-10-26
/etc/network/interfaces

lines like that

# The primary network interface
auto eth0
iface eth0 inet dhcp


sudo /etc/init.d/networking restart
=====================
thank you! that worked for me - mine was eth1 and now I can go to synaptic and download network manager from there :-):guitar:

---

