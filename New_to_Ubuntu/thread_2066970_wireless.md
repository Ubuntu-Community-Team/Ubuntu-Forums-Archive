---
title: "wireless"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by pancho45 on 2012-10-05
Hello

Dell Inspiron 1501
 I just installed Ubuntu 12.04 on this laptop but i cant connect
wirelessly.Cant see any wireless network.Is there a way to fix
this issue yo can help me with.Thanks

---

### Post by sandyd on 2012-10-05
Hi, many cards today are powered by the Broadcom Propreitary drivers which are not included with your Ubuntu install by default.

1. Connect your computer to your router via an ethernet cable
2. Open Hardware Drivers (Unity dash (thats the ubuntu logo in the top-left) -> Type in "Jockey"
3. If you see any hardware drivers that say "broadcom", enable them.

If not, post with screenshot.

---

### Post by pancho45 on 2012-10-06
> **sandyd said:**
> Hi, many cards today are powered by the Broadcom Propreitary drivers which are not included with your Ubuntu install by default.

1. Connect your computer to your router via an ethernet cable
2. Open Hardware Drivers (Unity dash (thats the ubuntu logo in the top-left) -> Type in "Jockey"
3. If you see any hardware drivers that say "broadcom", enable them.

If not, post with screenshot.
Thank you for help.
Found this thread
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install b43-fwcutter firmware-b43-installer.
That fixed the problem

---

