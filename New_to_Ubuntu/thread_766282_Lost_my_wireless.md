---
title: "Lost my wireless"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by 3dgimp on 2008-04-25
Hey all

After putting on Hardy, it found my netgear wg111 no problem. MAnaged to get online and even download new packages. After restarting the pc it now doesn't work. It doesn't list any networks. I tried manually pointing it to the network, and that failed.

What can I do to fix this? Are there any commands I can type to give you guys more background info on my predicament.

Big thanks in advance, Ed

---

### Post by NiklasV on 2008-04-25
Try to connect and then post the output of the iwconfig and dmesg commands.

---

### Post by fabrice79 on 2008-04-25
The WG111 dongle is known to have problems with native support; depending on the chipset, it usually works for some time (some hour, or less) than it stops.

Refer to [this post]("http://ubuntuforums.org/showthread.php?t=329299&highlight=wg111") for more informations and a guide on how to use ndiswrapper for it.

---

