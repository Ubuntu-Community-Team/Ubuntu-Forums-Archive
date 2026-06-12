---
title: "Kernel Upgrade"
date: 2005-02-02
forum: Repositories &amp; Backports
---

### Post by sully748 on 2005-02-02
i just installed ubuntu 64 4.10 and im liking it very much 
when i try to run the updates ... it wants to upgrade to the newer kernel 
ok so when i do this // reboot/// then x will not launch 
this is the same problem i have when i first install 
what i have to do is apt-get nvidia-glx and nvidia-glx-config enable and then it works 
but after the upgrades it won't work 
any help pls .,,, im lost

---

### Post by flyfishin on 2005-02-03
The binary Nvidia drivers, nvidia-glx, are kernel specific.  So every time you upgrade your kernel you will need to upgrade the nvidia-glx package to a version that is specific for your new kernel. If the nvidia-glx packages are not recompiled to match your kernel version you are out of luck using those.  Assuming you didn't wipe out your old kernel during the install you can boot into your old kernel and you should get your X server back.

---

### Post by sully748 on 2005-02-03
ok thx very much 
any news on the release on the new nvidia drivers to match the newer kernel ?

---

