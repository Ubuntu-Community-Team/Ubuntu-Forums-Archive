---
title: "Fresh install of Ubuntu from Ubuntu"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by kerryhall on 2012-01-07
I have a netbook that doesn't have a cd drive. I used a usb->ide cable to connect to a cd drive, but I no longer have a burner that is working (old one crapped out on me) Also: upgrading this release did not go well. I do not have a jump drive, and I think making a bootable jump drive did not go well. (back when i had a jump drive) Long story short:

Is there a binary I can download that will start a fresh install of Ubuntu, from Ubuntu? 

Thanks!!

---

### Post by Basher101 on 2012-01-07
you can make a bootable USB with ubuntu. There is a tool inside the system settings, all you will need is a .iso of the version you want to install and a USB pendrive that is at least 1 GB big.

---

### Post by bluexrider on 2012-01-07
Take a look at this [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Note: copy the .iso files to a separate partition that is not going to be used as ROOT otherwise the installation will fail.

---

### Post by kerryhall on 2012-01-12
> **Basher101 said:**
> you can make a bootable USB with ubuntu. There is a tool inside the system settings, all you will need is a .iso of the version you want to install and a USB pendrive that is at least 1 GB big.

I have two computers that need a fresh install of Ubuntu. I tried my USB drive on both, BIOS detects it on both, but it won't boot on either. One just hangs, the other just boots the HD. Do some USB drives boot better than others? What is a good USB key to get? Used Lili usb creator from windows to make the bootable USB drive.

Thanks!

---

### Post by kerryhall on 2012-03-01
Still wondering about this. BIOS on both machines can boot to an external hard drive using a USB to IDE adapter, so it is possible.

However, tried two different USB sticks and still can't boot. 

Any ideas?

(I might consider a PXE boot if I can't get USB to work.)

---

### Post by Foxheadz on 2012-03-01
I would try using something other then lili. I've had issues with it when it came to booting ubuntu, try unetbootin.

---

