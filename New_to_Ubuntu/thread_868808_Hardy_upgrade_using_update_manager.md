---
title: "Hardy upgrade using update manager"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by JohnnyC44 on 2008-07-24
After any updates I have the box to check if I want to upgrade from Gutsy to Hardy automatically.  The text says this is 8.04 LTS.  Question: will I be downloading the base Hardy released in April, or will this be 8.04.1 released earlier this month, which includes all the bug fixes?

---

### Post by Hospadar on 2008-07-24
When you do it that way, I believe it just downloads and installs all the packages currently in the repos for hardy (i.e. the most current packages).  there may be some things you have to update afterwords (kernels, other biggies) but even then I don't think you will really.

Also, be sure to back up all your important data or at least have a livecd on hand should things go awry.  The update managers are much better today than they were a year or two ago, but they still dead machines every now and then.  It's a tricky thing to push a new OS through a network upgrade.

---

### Post by Flyingjester on 2008-07-24
> **Hospadar said:**
> When you do it that way, I believe it just downloads and installs all the packages currently in the repos for hardy (i.e. the most current packages).  there may be some things you have to update afterwords (kernels, other biggies) but even then I don't think you will really.

Also, be sure to back up all your important data or at least have a livecd on hand should things go awry.  The update managers are much better today than they were a year or two ago, but they still dead machines every now and then.  It's a tricky thing to push a new OS through a network upgrade.

+1 it also gets rid of obsolete packages for you

---

### Post by philinux on 2008-07-24
It will update to the latest kernel automatically as part of the upgrade process.

---

### Post by Troll_the_Great on 2008-07-24
If it's not too much trouble, I would suggest to back up all your important data, make a list of your installed applications and make a clean install.It's always best to make a fresh install rather than an upgrade.From the forums, I saw that many peoples had problem, during or after the upgrade.So is up to you but my advice would be a clean install of Hardy.
Cheers!

---

### Post by kansasnoob on 2008-07-24
My luck with upgrades is about 50/50, half the time it works with little trouble, the other half I end up having to delete the whole partition and start from scratch.

For that reason, and especially if I have a well functioning Gutsy system running, I personally prefer beginning by creating an altogether new Hardy partition - basically adding one more OS to the machine.

The benefits are (1)having the capability of still booting Gutsy while I work out any Hardy issues at my leisure, (2)being able to restore GRUB to Gutsy and remove Hardy altogether if I decide to just wait for Intrepid, and (3)the ability to transfer existing files from Gutsy to Hardy once you have Hardy fine tuned.

Of course there are limitations, ie:number of existing partitions, drive free space, etc. And your knowledge of partitioning, editing GRUB, etc. are also important to consider.

---

