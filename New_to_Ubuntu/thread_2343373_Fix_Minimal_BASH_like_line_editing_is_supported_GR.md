---
title: "Fix Minimal BASH like line editing is supported GRUB Error In Linux"
date: 2016-11-15
forum: New to Ubuntu
---

### Post by dewilas on 2016-11-15
Hello,

I have dell inspiron 15 7000 (7537). I bought laptop with Ubuntu OS. Firstly, I installed windows 8.1 to other partition. After instalation I lost dual boot. Then I boot live ubuntu session from usb with Ubuntu OS. Tried to repair boot but all crashes and I lostt booting menu. Now then i starting my computer on the black screen I see this text:  [http://2.bp.blogspot.com/--hE36ZRrX7s/VB4YpSVB2SI/AAAAAAAAAXc/kanBU_fLCqM/s1600/dsc00227edit0.jpg](http://2.bp.blogspot.com/--hE36ZRrX7s/VB4YpSVB2SI/AAAAAAAAAXc/kanBU_fLCqM/s1600/dsc00227edit0.jpg).

Then my steps was:

1. Boot live CD and repair boot one more time
2. Then i do steps by this tutorial [https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/)
On popup I click recomended repair. When to terminal I write command sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -a drom popup but I got at the end errors: 

```
dpkg: error processing package iwlwifi-firmware (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of iwlwifi-dkms:
 iwlwifi-dkms depends on iwlwifi-firmware; however:
  Package iwlwifi-firmware is not configured yet.

dpkg: error processing package iwlwifi-dkms (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 iwlwifi-firmware
 iwlwifi-dkms
```


How to fix that? I need to repair Grub booter and repair dual boot - ubuntu and windows 8.1. Please help. Thank you guys for the help.


Ps.: sorry for my english

---

### Post by Impavidus on 2016-11-16
Boot-repair gives you a link to a boot info summary. Could you post that link, so we can see why your computer doesn't boot? I don't know about iwlwifi-* packages. Proprietary firmware maybe? But that shouldn't keep your computer from booting.

Which version of Ubuntu?

---

