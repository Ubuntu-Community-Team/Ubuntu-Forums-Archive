---
title: "Nvidia dual screen problem with Xserver"
date: 2015-01-27
forum: New to Ubuntu
---

### Post by super kim on 2015-01-27
I am trying to set up an old machine with dual screens, but I've come to a problem that I cant solve on my own.

When I go to the nvidia settings I get this message:[INDENT]Unable to load X Server Display Configuration page:


The NVIDIA X driver is not new
enough to support the nvidia-settings Display Configuration page.[/INDENT]



```
lsb_release -rcd ; uname -r
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
3.13.0-44-generic

```
```
dpkg -l | grep -i nvidia
ii  nvidia-173                                            173.14.39-0ubuntu3                                  amd64        NVIDIA legacy binary driver - version 173.14.39
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver

```

```
lspci -nnk | grep -iA2 vga
03:02.0 VGA compatible controller [0300]: NVIDIA Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)
    Kernel driver in use: nvidia
03:08.0 Ethernet controller [0200]: Intel Corporation NM10/ICH7 Family LAN Controller [8086:27dc] (rev 01)

```

I would be happy to install a newer driver but when I use the additional drivers tab on software updates it only displays:
[LIST]
[*]NVIDIA legacy binary driver - version 173.14.39
[*]X.Org X server - Nouveau display driver
[/LIST]
I had used this graphics card before with an older ubuntu, but I quite like the new ubuntu. Should I use an older version of ubuntu?

---

### Post by mansonfan78 on 2015-01-27
Try this: [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)  It says it's for 13.04, but it will still work for newer versions.  It shows several different methods.  But you definitely need a newer driver.

---

### Post by super kim on 2015-02-04
I looked on the Nvidia website and couldn't find a newer driver than this:[TABLE="width: 100%"]
[TR]
[TD="class: gridItem"]173.1438[/TD]
[TD="class: gridItem"]October 1, 2013[/TD]
[/TR]
[/TABLE]

I tried downloading a different driver (NVIDIA-Linux-x86_64-331.113) but when I try to install it I'm told that the GPU doesn't support it.

---

### Post by mansonfan78 on 2015-02-04
It might be possible to install a driver older than the one you downloaded but still newer than the one you have.  Nvidia should have a section called "beta and older drivers" in the links halfway down the page.

---

### Post by mansonfan78 on 2015-02-04
Now that I think about it - you're problem might be simply with the nvidia-settings program that's installed isn't the right one for your driver.

---

