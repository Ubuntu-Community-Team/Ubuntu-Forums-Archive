---
title: "Applications in ubuntu work at a slow pace"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by zedlinkus on 2012-05-19
I av ubuntu linux installed in my virtual box as a guest os, the host os is window 7, the issue is dat my linux environment is very slow, what do I do to make my applications work faster than they do now?

---

### Post by Redblade20XX on 2012-05-19
Look in the virtualbox settings to change number of cpus and memory available to the virtual os and other video settings. Also what are the specs of the host computer?

-Red

---

### Post by neofreud on 2012-05-19
Unless you have a decent proessor and lots of ram you may be better off using a light weight distro like Xubuntu or Lubuntu since it is less resource hungry and works much faster in a VM. 

Virtualization is great, but requires a signifcant amount of processing power and memory.

---

### Post by zedlinkus on 2012-05-19
My processor is intel core 2 duo, 3g of ram size and I assigned 617mb of ram to my vm, is dat not gud enof?

---

### Post by uRock on 2012-05-19
> **zedlinkus said:**
> My processor is intel core 2 duo, 3g of ram size and I assigned 617mb of ram to my vm, is dat not gud enof?
Anything less than 2 GB is going to slow the OS down. You may see a large improvement by upping the VBox memory to 1.5GB. Windows may slow down a bit while the VM is running.

---

### Post by matt_symes on 2012-05-19
Hi

> My processor is intel core 2 duo, 3g of ram size and I assigned 617mb of ram to my vm, is dat not gud enof?

You may get more replies to if type using full English spelling. People will take you more seriously.

U no wut i mean ?

Anyway, give the virtual machine more memory to start with. 

Install htop or use system monitor to see what is using system resources.

EDIT: Did it really take me 11 minutes to type this reply ? :D

Kind regards

---

### Post by HermanAB on 2012-05-20
Also, as said above, install LXDE, XFCE or even IceWM, log out, select the new DE and log in again.

---

