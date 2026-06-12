---
title: "[SOLVED] Partitions"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-07-10
I am having a little trouble... I would like to make the HP Pavilion partition larger and the sda5 smaller (this is where the unallocated space came from), but I can't get gparted to make the HP Pavilion partition any larger.  How would I get the unallocated space out of the sda3 partition?
screenshot:
[ATTACH]77229[/ATTACH]

---

### Post by sydbat on 2008-07-10
Might be because it's a primary partition. Can you shrink the unallocated space first?

---

### Post by ChameleonDave on 2008-07-10
I think it may be necessary to update to the latest version of GParted.  You can do that in Synaptic.  Then try again.

---

### Post by pikabuntu on 2008-07-10
> **ChameleonDave said:**
> I think it may be necessary to update to the latest version of GParted.  You can do that in Synaptic.  Then try again.

The thing is that im trying to do this from a live cd

how could i do this without a live cd

---

### Post by ChameleonDave on 2008-07-10
> **pikabuntu said:**
> The thing is that im trying to do this from a live cd

how could i do this without a live cd

I noticed that from the screenshot.

Although I have not tried it myself, I am led to believe that once can install software whilst using a live CD.  It will not persist after a reboot, of course, but it will be available during the live session.

---

### Post by pikabuntu on 2008-07-10
I feel really dumb.
One of the partitions was mounted!
I unmounted it & it worked just fine... 
thanks for all of the help and sorry i wasted ur time :(

---

