---
title: "[SOLVED] Vbox error!"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-11
I keep getting this error when im trying to start my xp virtual machine

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}


```

so i ran 

```
sudo /etc/init.d/vboxdrv setup
```

in the terminal like it tells me to and then i get this:

```
dreamsofubuntu@dreamsofubuntu-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for dreamsofubuntu:
 * Stopping VirtualBox kernel module                                                                                                          *  done.
 * Removing old VirtualBox kernel module                                                                                                      *  done.
 * Recompiling VirtualBox kernel module                                                                                                       *  done.
 * Starting VirtualBox kernel module
 * Cannot change owner vboxusers for device /dev/vboxdrv
dreamsofubuntu@dreamsofubuntu-desktop:~$


```

so how do i fix this?:lolflag:


thanks in advance :)

---

### Post by bumanie on 2008-05-11
I would download the binary (free for home use) and then follow this guide and you will get usb function as well. [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

---

### Post by sdennie on 2008-05-11
Is it possible you don't have a vboxusers group setup?  You could check this by doing:

```

grep vboxusers /etc/group

```

---

### Post by kamitsukai on 2008-05-11
well it was working fine but it just stopped working a couple of days ago and this:

```
grep vboxusers /etc/group
```

Dosent do anything :(

---

### Post by sdennie on 2008-05-11
> **kamitsukai said:**
> well it was working fine but it just stopped working a couple of days ago and this:

```
grep vboxusers /etc/group
```

Dosent do anything :(

You could try:

```

sudo addgroup vboxusers
sudo adduser your_username vboxusers
sudo /etc/init.d/vboxdrv setup

```

You will likely have to logout and log back in before that will work (if it will work).

---

### Post by kamitsukai on 2008-05-11
Thankyou :)

---

### Post by mike.c on 2008-10-28
Thank You :)

I was having the same problem.

---

