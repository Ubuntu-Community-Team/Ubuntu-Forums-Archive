---
title: "Nvidia GeForce GTX 550 Ti: Stuck at a 800x600 resolution on a 1680x1050 monitor"
date: 2014-01-03
forum: New to Ubuntu
---

### Post by xinghua31 on 2014-01-03
Hi,
   I've tried to install Ubuntu 12.04 a few times over the past few months, but I always find myself defeated by the same problem! Whenever I install the Nvidia binary driver through the Driver thing in the System Settings, I'm always greeted and stuck in a 800x600 resolution after I've reset to activate the driver. Oddly however, the default 'Nouveau' drivers detects my monitor's resolution just fine, but it's pretty unstable & unusable. 
   
   My PC Specs are:
   
   Zalman T4 Micro ATX Case
   430W Corsair Modular PSU
   MSI FM2-A55M-E33 Motherboard
   AMD Athlon X4 760K CPU
   4GB 1600MHZ Kingston HyperX DDR3 RAM
   320GB SATA HDD (recycled from an old netbook)
   KFA2 GeForce GTX 550 Ti 1GB GDDR5 GPU
   Hanns.G HG216D monitor (connected with HDMI cable.
   
   Sorry for the overload of info, but it's just for the sake of completeness.
   
   I'm trying to install Ubuntu 12.04.3 64bit currently. It's odd that the default 'Nouveau' driver has no resolution problems, but the official Nvidia driver does!
   
   Thanks!

---

### Post by dannyboy79 on 2014-01-03
i'm guessing that you're stuck in the 800x600 window because you have the propritary drivers AND nouveau installed at the same time and they are conflicting with each other. you can always take a look at /var/log/Xorg.0.log and read it line by line and see where the problem may lay.  i believe you have to blacklist nouveau in order to use the propritary drivers. check this out [http://www.linuxers.org/howto/how-remove-nouveau-drivers-ubuntu](http://www.linuxers.org/howto/how-remove-nouveau-drivers-ubuntu)

---

### Post by xinghua31 on 2014-01-03
I don't think so. I installed it via 'Additional Drivers', and from what I've read, that disables the Nouveau driver.

---

### Post by egeezer on 2014-01-03
WHICH Nvidia are you installing?  I found that the only one that works for me on 12.04 was the 304 version, not the newer 319.  But my card is a lesser one (GeForce 210), so that may not be a fair test.

---

