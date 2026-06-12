---
title: "no network devices available"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by GazaIan on 2012-03-31
I'm running Ubuntu on my Galaxy Tab 10.1 but WiFi shows "No network devices available", what could be the problem? is it kernel related?

---

### Post by wildmanne39 on 2012-03-31
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
 by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by GazaIan on 2012-03-31
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
 by clicking on new reply and click # and paste the information between the brackets.
Thank you


Entering "cat /etc/lsb-release; uname -a" returns:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10
Linux gazaian-laptop 2.6.36.4-zefie+ #2 SMP PREEMPT Mon Mar 26 09:48:55 EDT 2012 armv7l armv7l armv7l GNU/Linux
```

Entering "lspci -nnk | grep -iA2 net" returns

```
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
```

Entering "lsusb" returns

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
```

Entering "iwconfig" Returns

```

lo         no wireless extensions.

dummy0     no wireless extensions.

sit0       no wireless extensions.

ip6tnl0    no wireless extensions.


```

Entering rfkill list all returned a "permission denied, so I ran it with sudo, which returned:

```

0: bcm4330 Bluetooth: Bluetooth
         Soft Blocked: yes
         Hard Blocked: no
```

entering lsmod returns:

```


Module         Size       Used by
brcmfmac       114913     0
cfd80211       126257     1 brcmfmac
brcmutil       3192       1 brcmfmac
scsi_wait_scan 0          0
```

---

### Post by wildmanne39 on 2012-04-01
Hi, did you edit the information you posted like lsmod?

Where did this kernel come from Linux gazaian-laptop 2.6.36.4?

Try:
```
lspci -nn
```
```
uname -a
```
Thanks

---

### Post by GazaIan on 2012-04-01
> **wildmanne39 said:**
> Hi, did you edit the information you posted like lsmod?

Where did this kernel come from Linux gazaian-laptop 2.6.36.4?

Try:
```
lspci -nn
```
```
uname -a
```
Thanks
lspci -nn returns

```
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.
```

uname -a returns

```
Linux gazaian-laptop 2.6.36.4-zefie+ #2 SMP PREEMPT Mon Mar 26 09:48:55 EDT 2012 armv7l armv7l armv7l GNU/Linux
```

The kernel is a custom built kernel since at the time, Android drivers were removed from Linux kernel sources, and the current linux kernel source from Samsung was half baked and could hardly support linux.

Also it turns out that WiFi really was broken, the thread where I downloaded Linux for my tab said WiFi was working but I guess it was written falsely.

Lastly; if this helps, there is another Linux distro available for my tablet, Gentoo, which I know has working WiFi (and working sound as well). Thing is, Gentoo its all command line so I don't even know how to set up WiFi with just a shell and no GUI. Is there a way I can 'extract' the kernel from Gentoo and install it for use with Ubuntu? if not, is there a way to set up Gnome in Gentoo?

---

### Post by wildmanne39 on 2012-04-01
Hi, you can install gnome gui but setting up gentoo is a pretty hard thing to do, here is a link for it, then you would need to get help from the gentoo forums however most of the time they refer you back to there documentation because it covers everything but it is a long read and hard to understand for a new person.
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml)

---

