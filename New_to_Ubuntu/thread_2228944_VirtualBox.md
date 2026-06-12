---
title: "VirtualBox"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by Toni_Vines on 2014-06-10
OK, I've done just about everything I think I should and I thought I'd cracked it but no chance! When I try to load my xp.iso I get the following error message.

RTR3Init failed with rc=-1912 (rc=-1912)

The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

may correct this. Make sure that you do not mix the OSE version and the PUEL version of VirtualBox.

I have absolutely no idea what on earth this is all about. Can anyone help me please? I'm running Ubuntu 12.04 LTS 64 bit. 
Thanking you,
Toni.

---

### Post by papibe on 2014-06-10
Hi Toni_Vines.

How did you install VB?
Did you install the version on the software center or did you downloaded and installed a version from VB site?
One on top of the other?

Regards.

---

### Post by monkeybrain20122 on 2014-06-10
It tells you exactly what to do :), well almost.
Close VB, open a terminal and type
```
sudo /etc/init.d/vboxdrv setup
```

This usually happens after kernel update.

---

### Post by Toni_Vines on 2014-06-10
OK, I've done that and now I'm getting the following:

toni@toni-HP-xw6400-Workstation:~$ sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules/etc/init.d/vboxdrv: 302: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...done.
Trying to register the VirtualBox kernel modules using DKMS/etc/init.d/vboxdrv: 327: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

Anyone help me please?
Cheers,
Toni.

---

### Post by Bijan_Yusefi on 2014-06-10
The Error is saying, RTreaInit with RC=-1912 in other words RC shouldnt be -1912

---

### Post by Bijan_Yusefi on 2014-06-10
I have yet to go that far lol

---

### Post by SeijiSensei on 2014-06-10
You need to install the **dkms** package so you can compile the kernel driver for VirtualBox.
```

sudo apt-get update
sudo apt-get install dkms

```
That will bring in a variety of other packages like the gcc compiler.

I prefer to install VB from Oracle's repository following the method described here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by Vladlenin5000 on 2014-06-10
> **SeijiSensei said:**
> I prefer to install VB from Oracle's repository following the method described here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

+1

---

