---
title: "How to update LTS of ubuntu?"
date: 2020-08-11
forum: New to Ubuntu
---

### Post by ferfykins on 2020-08-11
Using XUbuntu
Wondering how i update it to the latest LTS version of XUbuntu? Thanks guys.

---

### Post by grahammechanical on 2020-08-11
What version do you wish to upgrade from?

One of the first things we do is to update the existing installation using the usual method. I do not use Xubuntu so I cannot give specific directions but Xubuntu should have a utility to give you control over Software & Updates. That utility will let you set Xubuntu to inform you of the availability of the next LTS release of Xubuntu. When that upgrade dialog appears you just click Install or Upgrade or something like that. I am still waiting to get that message on my install of Ubuntu 18.04. I am in no hurry.

Sometimes things get delayed. It is possible to start the upgrade process using terminal commands.

Regards.

---

### Post by Impavidus on 2020-08-12
I use Xubuntu. Go to Settings&#8594;Software & Updates -> Updates, set Give notification of a new version of Ubuntu to LTS releases only and click close. Then run the Update manager, install all available upgrades and if you're running Xubuntu 18.04, it should offer an upgrade to 20.04. Or it will in a few days. I don't know if the upgrade is already released.

The only currently supported releases of Xubuntu are 18.04 and 20.04.

---

### Post by Autodave on 2020-08-12
But, BACK UP everything first!  (You do do that already, don't you?)

---

### Post by ferfykins on 2020-08-12
Thanks guys!

---

### Post by ferfykins on 2020-08-12
Just curious, why do i need to back up everything before updating LTS?

---

### Post by MartyBuntu on 2020-08-12
> **ferfykins said:**
> Just curious, why do i need to back up everything before updating LTS?

Just in case something, *anything*, goes wrong.
Because accidents happen.

---

### Post by ferfykins on 2020-08-12
> **MartyBuntu said:**
> Just in case something, *anything*, goes wrong. Because accidents happen.  gotchya thanks!!

---

### Post by mastablasta on 2020-08-13
updates are safe it's upgrades (from one version to another) that often don't go as planned.

to upgrade kernel to latest LTS version you use HWE stack: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
once you use HWE (or if you install xx.04.2 LTS) it will then always upgrade kernel automatically. you can always boot from older version and remove the new version, if something goes wrong.

upgrade from 16.04 --> 18.04
or form 18.04 ---> 20.04 (and so on)

always has some risks involved, so it is good to either backup data or at least keep user data (e.g. family photos etc)  on separate partition. sometimes upgrades fail and require a format and reinstall or at least a reinstall

---

