---
title: "network driver"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by tsucol11 on 2011-10-14
Motherboard M2N-sli (Asus).

Home network works flawlessly in ubuntu 10.04. In windows using the Nvidia ethernet drivers, the 2 onboard lans transfers data very slowly when connecting to my home network (both XP Pro).

I would like to see what drivers Ubuntu installed by default for the onboard lan(s). What do I type in terminal to get this info.

Thanks


Brian

---

### Post by jtarin on 2011-10-14
The command for listing drivers (known in Linux as modules) would be ```
lsmod
```post the output and we can take a look.

or the command ```
lspci -v
```which gives more specific output.

---

### Post by tsucol11 on 2011-10-15
Thank you jtarin

The driver is Forcedeth, an open source driver as compared to Nvidias proprietary driver for windows.  I was kind of hoping I could get a similar driver for windows. All is not lost, I will get a new nic for windows & use the on board nic's for Ubuntu.

Your help was greatly appreciated.

Brian

> **jtarin said:**
> The command for listing drivers (known in Linux as modules) would be ```
lsmod
```post the output and we can take a look.

or the command ```
lspci -v
```which gives more specific output.

---

