---
title: "Touchpad not working on Lenovo Ideapad FLex 5 14ARE05 Ubuntu 20.04 Kernel 5.8.x"
date: 2021-01-31
forum: New to Ubuntu
---

### Post by 0x54 on 2021-01-31
Well, yet another post about the touchpad.

I have tried to dual boot Ubuntu 20.04 on my laptop and the touchpad has not been functioning since day one.
Im fairly certain it is an MSFT touchpad, although lenovo appears to be using some kind of undetectable black market touchpad-tech here. The touchpad does not get detected at all. No entry in xinput, lshw, lspci, etc. 
So far I have tried many fixes involvig grub falgs, modprobe reloading of i2c and hid modules, installing synaptics drivers.

In case you need more information, here is a bug I submitted:

[https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-5.8/+bug/1912880](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-5.8/+bug/1912880)

So far there does not seem to be an existing solution excpet waiting two more moths until april when 21.04 gets released, although I have no hopes for a fix there.
Also, I would like to avoid messing woth the kernel to much beause I would likely break more than I coud fix.

If you have an idea, I would be thankful for any help.

Edit: I installed Ubuntu with kernel 4.5.x and then upgraded later with OEM kernel.

---

### Post by ActionParsnip on 2021-01-31
Try the boot option:
```

i8024.reset

```

---

### Post by 0x54 on 2021-01-31
Unfortunately that does not work.

---

