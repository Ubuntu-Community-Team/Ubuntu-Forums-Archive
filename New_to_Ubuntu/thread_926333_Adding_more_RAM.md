---
title: "Adding more RAM"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by usererror on 2008-09-21
Do I have to do anything after I add more RAM to my system?  I am going from 1GB to 3GB.

---

### Post by SuperSonic4 on 2008-09-21
You shouldn't. My motherboard manual says you should clear the CMOS before booting up but it will show in power-up, just before it lists your devices

---

### Post by sharks on 2008-09-21
no need to do anything. just install(insert) the new ram.

---

### Post by vikramaditya on 2008-09-21
Are they all 1 gig sticks?  How many mem slots does your mobo have?  Did you research compatibility with existing ram & mobo?  If "yes" to all 3, it _should_ be automagically detected just fine.

---

### Post by MegaJim on 2008-09-21
The only issue to consider as far as ubuntu is concerned is the size of your swap partition.  If you are going to be suspending/hibernating you might need to increase the available swap space for the contents of RAM to be safely stored.  Dependent on how much memory you use in your everyday computing, the swap space should be equal to or just larger than the amount of RAM for computers which hibernate.

---

### Post by usererror on 2008-09-21
> **MegaJim said:**
> The only issue to consider as far as ubuntu is concerned is the size of your swap partition.  If you are going to be suspending/hibernating you might need to increase the available swap space for the contents of RAM to be safely stored.  Dependent on how much memory you use in your everyday computing, the swap space should be equal to or just larger than the amount of RAM for computers which hibernate.

Thanks, that is what I was really curious about, I should have stated that.  I am dualbooting currently, but would like to eliminate dual booting now that I have VirualBox installed.

Can you point me to how to resize the swap partition to be ~4GB ?  I'm afraid of losing my data by fouling up the resize of the partition. :)

---

### Post by steveneddy on 2008-09-21
> **usererror said:**
> Thanks, that is what I was really curious about, I should have stated that.  I am dualbooting currently, but would like to eliminate dual booting now that I have VirualBox installed.

Can you point me to how to resize the swap partition to be ~4GB ?  I'm afraid of losing my data by fouling up the resize of the partition. :)

Use a gparted CD. It has a GUI that should be intuitive.

---

### Post by lisati on 2008-09-21
> **usererror said:**
> Do I have to do anything after I add more RAM to my system?  I am going from 1GB to 3GB.
Make sure it is seated in the socket properly. A month or two back, I moved my desktop, into which I'd installed some extra ram. Out of the blue (pun not intended) XP started having the BSOD quite regularly, citing a memory problem, and Ubuntu locked up on shut-down. Re-seating the extra ram cured both problems.

---

### Post by Mister.Vash on 2008-09-22
You probably won't run into this - for some machines, such as some of the dells, require you to go into the bios so it can read the memory.  The bios then picks up that you have the new memory in the system, you then save and exit the bios and the O/S has access to it.

You can usually tell fairly easily if this would be needed.  If you have 1 GB, and add another 1 GB, and the system is still only reporting 1 GB, it is an indication that the bios might need to pick it up.  I've have to futz around with that on all my Dell machines.

---

