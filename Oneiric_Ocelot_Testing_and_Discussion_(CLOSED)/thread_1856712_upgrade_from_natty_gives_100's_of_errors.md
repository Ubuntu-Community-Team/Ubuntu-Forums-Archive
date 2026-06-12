---
title: "upgrade from natty gives 100's of errors"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by joolsr on 2011-10-08
Hello

On trying to upgrade my natty install to 11.10 tonight (only 5 days from release), i ended up with an extremely borked system.

basically i got errors about half the way thru the upgrade. 

Most of the errors point back to an issue with glibc-2.0 I believe, but on trying a dpkg-reconfigure -a or an apt-get upgrade -f, nothing helps.

I've been using Ubuntu since Warty and upgraded many times, without issue, but never seen anything like this.

The pc still operates up to a point, ie i still have cmd line access, web and networking but most gui apps no longer work.

Can someone help me ? Sorry I dont have many logs as I ;m not at the broken pc at the moment. I really dont want to re-install everything ??

---

### Post by drawkcab on 2011-10-09
Actually if you install from live session ubiquity will give you an option to keep your files along with whatever settings and installed software it can preserve from 11.04.  It works really well and may save you a lot of hassle.

See option #2 below:

---

### Post by joolsr on 2011-10-09
Ok, thats handy to know.

But, at the moment, I dare not reboot as I dont think my current install is robust enough to boot that far with a half mangled 11.04 to 11.10 upgrade.

I did wonder whether to set all refs of oneiric to natty in the apt sources list and attempt a downgrade, as the upgrade got about 1/3 of the way thru, ie downloading all packages, and installing new packages on top but not doing the final setting up stage of the install (ie the upgrade got went wrong with 49 mins to go on an i5 box)

Any ideas how to fix ?

---

### Post by awam66 on 2011-10-09
Try booting to recovery mode and selecting "Fix Broken Packages". Or load Synaptic and do the same "Edit>fix broken packages" them "Mark all Upgrades", then "Apply". This happened to me on one of my upgrades and the first method fixed it.

---

### Post by joolsr on 2011-10-09
I cant get synaptic to run. if libglibc is broke an awful lot depends on it ...

---

### Post by awam66 on 2011-10-09
> **joolsr said:**
> I cant get synaptic to run. if libglibc is broke an awful lot depends on it ...

Then you need to bite the bullet and re-boot into recovery mode. Otherwise a fresh install is required perhaps.

---

### Post by joolsr on 2011-10-09
> **awam66 said:**
> Then you need to bite the bullet and re-boot into recovery mode. Otherwise a fresh install is required perhaps.

Yes, you might be right - I dont like to reboot until I have to, but it looks like it may be my only option. I'm just d/l ing a recent daily build of 11.10 so i can try upgrading with that at some point ...

---

