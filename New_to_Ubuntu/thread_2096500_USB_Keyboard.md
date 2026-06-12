---
title: "USB Keyboard"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by yajnamurti on 2012-12-20
I have a problem with my keyboard. I use a USB keyboard attached to my netbook. It works fine but after suspend it does not work. I have to reboot, them I can use the USB keyboard again. I opened one terminal and typed lsusb when the USB key board was not working after a Suspend:

```

yajnamurti@yajnamurti-AO725:~$ lsusb
Bus 002 Device 002: ID 064e:e330 Suyin Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 1bcf:0005 Sunplus Innovation Technology Inc. 
yajnamurti@yajnamurti-AO725:~$ 
```



And after rebooting here it is:

```
yajnamurti@yajnamurti-AO725:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. 
Bus 002 Device 002: ID 064e:e330 Suyin Corp. 
Bus 005 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
yajnamurti@yajnamurti-AO725:~$ 
```

Can someone help me to solve this problem, please?

---

### Post by Pjotr123 on 2012-12-20
Hibernate and suspend are sometimes unreliable. I advise this workaround: [https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)

---

### Post by yajnamurti on 2012-12-20
> **Pjotr123 said:**
> Hibernate and suspend are sometimes unreliable. I advise this workaround: [https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)

Is there a way without turning off suspend?

My usb mouse works fine even after I suspend Ubuntu. Why only the keyboard has this problem?

---

### Post by yajnamurti on 2012-12-21
> **yajnamurti said:**
> Is there a way without turning off suspend?

My usb mouse works fine even after I suspend Ubuntu. Why only the keyboard has this problem?

Any Ubuntu Kung fu there??? 

Please Help!

---

### Post by cwsnyder on 2012-12-21
I can explain why the mouse works but the keyboard doesn't.  The mouse and the synaptic keypad both connect through a USB interface, but the built-in keyboard does not.  Why should the (waking) operating system check for an 'extra' keyboard when it has a pointing device and a working keyboard?  You might look into disabling the built-in keyboard, but that may cause problems down the road where you may not be able to re-enable it.

[:irony:]Of course, if you want to specifically change the code to meet your requirements, the source code is available.[/:irony:]

---

