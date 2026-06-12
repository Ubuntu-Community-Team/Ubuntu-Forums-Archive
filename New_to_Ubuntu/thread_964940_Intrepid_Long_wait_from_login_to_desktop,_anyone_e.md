---
title: "Intrepid: Long wait from login to desktop, anyone else got this."
date: 2008-10-31
forum: New to Ubuntu
---

### Post by philinux on 2008-10-31
From boot up to login screen it's really quick. But from hitting the enter key after the password takes longer than Hardy.

---

### Post by mjwhitfield on 2008-10-31
> **philinux said:**
> From boot up to login screen it's really quick. But from hitting the enter key after the password takes longer than Hardy.How long did 8.04 take?
How long does 8.10 take?

---

### Post by Joeb454 on 2008-10-31
> **mjwhitfield said:**
> How long did 8.04 take?
How long does 8.10 take?

Also - does this happen EVERY time you logon?

---

### Post by Pconfig on 2008-10-31
Same here actually. I didn't time it on hardy but i'm pretty sure it's way slower.

---

### Post by philinux on 2008-10-31
Was just rebooting to time it when fsck kicked in. :)

Right oh. 
Intrepid
From grub to login screen 31 Seconds.
From login screen to usable desktop 32 seconds.
Same thing every boot. I'm not sure where to look to bug it. I've checked the normal logs but they dont have anything from the gdm.

Hardy
I've not got Hardy to test but from memory
From grub to login screen ~40 Seconds.
From login screen to usable desktop <20 seconds.

---

### Post by philinux on 2008-10-31
Solved.

I'd upgraded as a test as I'd been running Intrepid on Disk 2.
Just done a clean install and the gnome start time to desktop has gone down to <20 seconds. I've home on it's own partition so really easy to reinstall.

---

### Post by philinux on 2008-10-31
Spoke too soon. The lag is back now I've installed the nvidia driver. Baahhh:confused:

---

### Post by aramadia on 2008-10-31
Compiz is messing up.  See [http://ubuntuforums.org/showthread.php?t=963800](http://ubuntuforums.org/showthread.php?t=963800)

---

