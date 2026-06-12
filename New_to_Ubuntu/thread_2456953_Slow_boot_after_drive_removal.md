---
title: "Slow boot after drive removal"
date: 2021-01-22
forum: New to Ubuntu
---

### Post by xxx5 on 2021-01-22
Hello I'm on Ubuntu 20.04 had Ubuntu 16.04 on another drive that I disconnected from the computer. It use to take max of 1 minute to boot into Ubuntu 20.04. After I removed Ubuntu 16.04 from the other hard drive it now takes over 5 minutes to boot. I thought it was grub so I updated it and still has the slow boot time. What else can I do in order to get it to boot regularly? I can always but back the Ubuntu 16.04 and redo grub, but I rather not have to do that. Thanks for any help.

---

### Post by CelticWarrior on 2021-01-22
Check the fstab. It may have an entry for the old drive and it stalls while trying to mount it.

---

### Post by grahammechanical on 2021-01-22
+ 1 for the above post

If the 16.04 drive had a swap partition and 20.04 was set to use the swap partition on the 16.04 drive, then 20.04 would spend time trying to mount the swap partition. I hit a problem recently that slowed the boot time. I installed Debian and allowed it to format the swap Partition. This gave the swap partition a new unique identifier which was different from that listed in /etc/fstab. And so, loading my installs of Ubuntu took much longer.

Regards

---

