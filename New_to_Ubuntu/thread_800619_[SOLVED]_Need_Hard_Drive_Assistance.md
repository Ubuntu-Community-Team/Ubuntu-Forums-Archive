---
title: "[SOLVED] Need Hard Drive Assistance"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-05-20
ok, I'm running a Seagate Barracuda IV (single platter) 7200rpm 2mb cache HDD. Runs super quiet (platter spin) but sounds like a muffled teletype when the heads are moving. What's the quietest drive (platter spin & head seek) in the 80GB range (SATA) ? Thanks

---

### Post by HotShotDJ on 2008-05-20
> **Samurai Penguin said:**
> What's the quietest drive (platter spin & head seek) in the 80GB range (SATA) Honestly, I've found the Seagate Barracuda series (7200.10 series) to be the quietest, although I know what you mean about the "muffled teletype" sound during read/writes. They are available in an 80GB model.

---

### Post by Samurai Penguin on 2008-05-20
I was just looking at the Seagate Barracuda 7200.10  250GB SATA at Newegg ... it has a 16mb buffer compared to an 8mb buffer on the 80GB SATA. Will that make that much of a difference?

---

### Post by sdennie on 2008-05-20
You could see if the drive supports acoustic management.  It may make the drive run slower but, it should be quieter.  Assuming the disk is /dev/sda:

```

sudo hdparm -M 128 /dev/sda

```

That value will reset on reboot but, if it makes the disk quieter, you should be able to make it permanent using /etc/hdparm.conf.

---

### Post by nowshining on 2008-05-20
or if u can - set-it thru ur BIOS, I  know my dell 4600i allows this thru the BIOS.

---

