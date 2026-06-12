---
title: "memory card reader"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by antisocialist on 2008-04-28
i have a built in mem card reader and recently acquired a camera that uses sd cards, and already have a couple psp's that use mspd cards, both of which are readable by my built in card reader, so i figured i would set it up

i found time to do it and so here i am. i used the cmds
sudo modprobe tifm_core
sudo modprobe tifm_sd
and then (minus the sudo part) put them in /etc/modules

i then ran dmesg and it showed that the memory stick is in socket 0:3
[ 1320.732042] tifm_core: MMC/SD card detected in socket 0:3

i want to know how i can mount this, and any other card i put in it (which would be one of my 2 2gb mspd sticks

---

### Post by antisocialist on 2008-04-28
bump

---

