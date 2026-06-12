---
title: "Cannot setup ADSL because no eth is recognised"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by ronbarak on 2008-05-17
Hi,
I'm trying to set an IBM Thinkpad T43 laptop with Ubuntu 7.10
The machine can connect to an ASDL modem from Windows XP, but when I run "[FONT="Courier New"]sudo ppoeconf[/FONT]", none of the three eth's in the system are recognised, and I cannot get connected.
Any suggestions ?
Thanks,
Ron.

---

### Post by jbrown96 on 2008-05-18
A couple of things to see if your card is working. Can you find your card in the output of ```
lspci
```? Does ```
ifconfig
``` return anything for eth0 (usually your wired connection but it may be something else). If the card is found in lspci, but not in ifconfig, try to run ```
sudo ifconfig eth0 up
```, which will bring the interface up. It may be worth trying to substitute eth1 also.

---

### Post by ronbarak on 2008-05-19
> **jbrown96 said:**
> A couple of things to see if your card is working. Can you find your card in the output of ```
lspci
```? Does ```
ifconfig
``` return anything for eth0 (usually your wired connection but it may be something else). If the card is found in lspci, but not in ifconfig, try to run ```
sudo ifconfig eth0 up
```, which will bring the interface up. It may be worth trying to substitute eth1 also.

Thanks for the suggestions, JB.
My LAN cards are seen by ubunto (see the attached 'script' output file).
I found that my MTU was not to ubuntu's liking, and I changed it to 1500, so there're no complints of wrong mtu now.
However, still no luck in configing ADSL :-(

Bye,
Ron.

---

