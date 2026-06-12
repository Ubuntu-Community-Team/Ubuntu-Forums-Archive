---
title: "[SOLVED] Hotplug eSata support?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by timandjulz on 2008-05-15
Hi all, I can't get hot plugging eSata working.  Googling indicates 2.6.14 kernel should support it.

Is there a secret?  I haven't installed any packages so maybe there is one required?

Thanks,
Tim

---

### Post by timandjulz on 2008-05-19
bump

---

### Post by djRobbieF on 2008-05-22
Bump.  Please help.

---

### Post by djRobbieF on 2008-05-22
NVM.  Got it.

Making sure AHCI was active (which I always have active, but I'm commenting it so you check) in bios, then booting with an eSATA drive attached and running.

I mounted that drive, and then shut down my computer.

Now, I boot my computer without the eSATA drive attached, and from now on the unit works perfectly... plug and play, just like it was a USB drive.

Ubuntu Hardy Heron.  Using a Thermaltake BlackX along eSATA.

I'll review this product and show how I got it working on this week's episode of Category5.  Tuesday, May 27.  [www.Category5.tv](www.Category5.tv).  Episode 36, in case you miss it live and want to pick it up in the episode index after the fact.

Cheers,
Robbie

---

### Post by djRobbieF on 2008-05-22
Oh - and remember, if you're dual-booting Windows, MAKE SURE you install your controller's AHCI drivers into Windows PRIOR to enabling AHCI, otherwise you won't be able to boot Windows anymore, unless you go BACK into bios and set it back to IDE.  ;)

See, I'm always looking out for ya's.  ;)

---

