---
title: "Hardware upgrade, some advice......"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by techno-mole on 2008-08-21
Hello.
i want some advice on a hardware upgrade, i have a system that duals boots kubuntu with xp (on different hard drives) now i want to upgrade the cpu, graphics, and most likely i will be putting in a new main board, so would it be best to do the upgrade and then just re-install kubuntu (and xp obviously)
or could i get away with doing the upgrade, but using the kubuntu install i already have ?
i assume that if i dont re-install i will have to do some re-configuring of drivers etc ?
cheers

---

### Post by WRDN on 2008-08-21
Before offering advice, some information may be needed. For example, what do you use your PC for, and what is your budget?

After you get the new PC, you could use the old HDD so you don't need to reinstall Ubuntu. However, Windows will need to be reinstalled, or reactivated.

---

### Post by techno-mole on 2008-08-23
i already have the hardware, nothing special, just better than whats there already, eg - 1.6ghz sempron to a 2.2ghz athalon, more ram etc etc, better agp card.

it was more a question as to whether i could get away with not having to re-install kubuntu, as i am most likely going to have to re-install xp on the other hard drive, i dont mind re-installing kubuntu, but if i can get away with not then its a bonus :-) as i will only have to re-install one os and not both.

---

### Post by mellowd on 2008-08-23
It depends on the chipsets being used on the old and new boards. You could certainly try it.

I'd create full backups of both, install the new hardware and see what happens. If it refuses to boot reinstall and restore your data.


If it was just a cpu and gpu upgrade, you wouldn't need to do it. The motherboard is another story though.

It might just work ;)

---

### Post by coffeecat on 2008-08-23
Don't forget that if you find Kubuntu works fine with your new hardware but that you have to reinstall Windows, it will overwrite the mbr and, until you repair grub, you will only be able to boot into Windows.

Repairing grub is easy enough. It's just a matter of reinstalling stage 1 to the mbr. If you don't know how, just post.

---

### Post by techno-mole on 2008-08-24
thanks for all the help, i may play it safe and just do a fresh install of everything.
cheers

---

