---
title: "Need Drivers"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by Vwpilegard on 2013-03-14
Hi,  I just installed Ubuntu 10.04 onto an old HP Compaq nc6220.  Can't make connection with Visionnet wireless M505N.  Can't load the Visionnet installation disc.  The wireless works fine on my windows based desktop and one other laptop.  I suspect I need drivers, but am not sure what to download and where to download.  Please advise. :)

---

### Post by TK999 on 2013-03-14
Hey, please run **l****susb** from a terminal (Ctrl+Alt+T) with the adapter plugged in & post the output here.

---

### Post by ManamiVixen on 2013-03-14
Currently Ubuntu 10.04 is no longer supported and all repos have been removed from Canonical's Main Servers, there is a archive repository containing all the software, but it is currently not maintained and will see no more updates. It's best to upgrade to at least 12.04. In fact, you may find 12.04 has the needed drivers and software for your wireless.

Edit: I apologize, 10.10 is no longer supported, but 10.04 support will end soon. So still upgrade though.

---

### Post by Vwpilegard on 2013-03-14
richard@richard-laptop:-$ 
Not sure I did this correctly.

---

### Post by arpanaut on 2013-03-14
> **ManamiVixen said:**
> Currently Ubuntu 10.04 is no longer supported and all repos have been removed from Canonical's Main Servers, there is a archive repository containing all the software, but it is currently not maintained and will see no more updates. It's best to upgrade to at least 12.04. In fact, you mmay find 12.04 has the needed drivers and software for your wireless.
Wrong...
10.04 is supported through April of 2013

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
Although the advice to upgrade to 12.04 is sound!

---

### Post by ManamiVixen on 2013-03-14
I made an edit before you posted that.

---

### Post by TK999 on 2013-03-14
You'd just bring up the terminal with Ctrl+Alt+T, and type **lsusb **when you see the prompt. Then, copy anything it outputs here. :)

---

### Post by carl4926 on 2013-03-14
Further info
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

12.04 might be too much for a old machine

You might want to consider either Xubuntu or Lubuntu
Or Mint 13 Mate will give you the look and feel you are familiar with

---

### Post by Vwpilegard on 2013-03-14
Thanks. 12.04 is too large for my old machine.  I'll look into Xubuntu, Lubuntu or Mint 13 Mate if you think I can find wirless drivers for these. I assume these are operating systems.

---

### Post by carl4926 on 2013-03-14
> **Vwpilegard said:**
> Thanks. 12.04 is too large for my old machine.  I'll look into Xubuntu, Lubuntu or Mint 13 Mate if you think I can find wirless drivers for these. I assume these are operating systems.
Correct they are OS's

Boot them Live the wireless may work OOTB

---

