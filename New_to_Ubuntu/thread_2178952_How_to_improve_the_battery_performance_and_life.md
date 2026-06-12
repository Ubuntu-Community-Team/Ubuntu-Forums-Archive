---
title: "How to improve the battery performance and life"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by adithya2 on 2013-10-05
I am new to Ubuntu.I find that the power consumption in Ubuntu is more compared to the battery charge consumed in Windows 7(dual boot).Is there any way to improve the battery performance.
Thanks and regards in advance.

---

### Post by Kevin McCready on 2013-10-06
I use Lubuntu and it seems heaps better on the battery than Windows ever was. Possibly turning off a lot of logging processes may help. If you do ctrl-alt-del you can also see what is eating up your cpu.

---

### Post by _birdman on 2013-10-06
Does your laptop have a discrete graphics card?  I know that if it is an Nvidia optimus card (I don't own an AMD laptop so I cannot comment about them) then Ubuntu will power them both up in a vanilla installation.  Have a look at :  [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) I had a huge battery improvement after this.

Also take a look at: [http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)

---

### Post by grahammechanical on 2013-10-06
Use the Network Manager Icon to disable Wi-Fi until you need it. In fact going into Edit connections and untick Automatically Connect.

Regards.

---

### Post by Linuxisfast on 2013-10-06
Install TLP and you need latest kernel with pstate enabled, also compile Intel Thermal Daemon, I get same life and a cooler than Windows 8 i7 with nvidia here.

---

