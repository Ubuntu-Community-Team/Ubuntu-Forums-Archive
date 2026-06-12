---
title: "Installation Question"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by OregonGuy on 2008-06-09
I have an old PC that my daughter left in my garage.

Athlon 750MHz
64M RAM
14GB hard drive

Can I install ubuntu or xubuntu on this computer with only 64Meg of RAM?

I tried installing from the i386 Alternate CD, everything goes fine until the Partitioning step.  Then the system just stops.

Thanks

---

### Post by iaculallad on 2008-06-09
With that RAM, try installing lighter distro instead. User either [Puppy]("http://www.puppylinux.org/") or [DSL]("http://www.damnsmalllinux.org/").

---

### Post by Joeb454 on 2008-06-09
You could try doing a minimal install of Ubuntu, that way you can add only the packages you need. Though adding some more RAM would do WONDERS for that machine :)

---

### Post by gr4nf on 2008-06-09
Use debian for the install, as the installer for that distro is not gui.

If you ever do get ubuntu installed, and it still runs slow, try making it CLI only, like this:

```

sudo mv /etc/rc3.d/S10xserver-xorg-input-wacom /etc/rc3.d/K80xserver-xorg-input-wacom

```

Simply reverse the command to revert it back to starting up in gui.

---

### Post by Joeb454 on 2008-06-09
The Ubuntu alternate install disc isn't a GUI either - it's text based :)

---

### Post by OregonGuy on 2008-06-09
Thanks 
I'll try a smaller version first before upgrading the RAM

---

### Post by gr4nf on 2008-06-09
If you do get more RAM, remember to get very low speed cards. The high speed stuff will be wasted on your old, slow motherboard, and will cost more. Aim for less than 800 mhz.

---

