---
title: "Waking from suspend using keyboard (not mouse)"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by codell on 2008-05-18
Is there a way to make it so that the computer only wakes from suspend if you hit keys on the keyboard i.e. not mouse movement. :-k I don't want accidental mouse movement to wake up my computer.

---

### Post by EXCiD3 on 2008-05-18
Check this out: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199006](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199006) and [https://lists.linux-foundation.org/pipermail/linux-pm/2007-November/015551.html](https://lists.linux-foundation.org/pipermail/linux-pm/2007-November/015551.html)

---

### Post by codell on 2008-05-18
When I type in 
```
cat /proc/acpi/wakeup
```
into the terminal, it comes up saying that all of the devices are disabled except the power button. My mouse/keyboard are both PS/2 devices, so then how can I disable the mouse from being a wakeup event?

I'm using Feisty and GNOME 2.18.1.

---

### Post by EXCiD3 on 2008-05-18
I cant seem to find anything about disabling the mouse, but i would check the contents of /proc/acpi/wakeup. Unfortunately im not sure if mouse and keyboard are separate entries or what. Post your wakeup file and ill take a look at it. (I'm on a windows box right now...AND dialup :()

---

### Post by codell on 2008-05-19
```

Device	S-state	  Status   Sysfs node
PCE2	  S4	 disabled  
PCE3	  S4	 disabled  
PCE4	  S4	 disabled  
PCE5	  S4	 disabled  
PCE6	  S4	 disabled  
PCE7	  S4	 disabled  
SBAZ	  S4	 disabled  pci:0000:00:14.2
PS2K	  S3	 disabled  pnp:00:06
PS2M	  S3	 disabled  pnp:00:07
P0PC	  S4	 disabled  pci:0000:00:14.4
AC97	  S4	 disabled  
MC97	  S4	 disabled  
USB1	  S3	 disabled  pci:0000:00:13.0
USB2	  S3	 disabled  pci:0000:00:13.1
USB3	  S3	 disabled  pci:0000:00:13.2
USB4	  S3	 disabled  pci:0000:00:13.3
USB5	  S3	 disabled  pci:0000:00:13.4
EUSB	  S3	 disabled  pci:0000:00:13.5
PWRB	  S3	*enabled 

```

Once again, my keyboard and mouse are both PS/2 devices.

---

### Post by EXCiD3 on 2008-05-19
I can't seem to find anything about disabling PS/2 devices, there isnt a whole lot of information on this. Maybe post a bug on [http://launchpad.net](http://launchpad.net) and see what the developers have to say.

---

