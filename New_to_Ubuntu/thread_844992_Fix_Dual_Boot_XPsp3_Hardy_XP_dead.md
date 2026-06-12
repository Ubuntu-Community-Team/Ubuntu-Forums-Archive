---
title: "Fix Dual Boot XPsp3/ Hardy: XP dead"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by metasolaris on 2008-06-30
Hi,

I have a dual core amd64 and dual boot XPsp3 and Ubuntu Hardy on the same hard drive.

I got the "blue screen of death" when I tried to boot XPsp3 this morning - something about an unmounted hard drive. Last thing I did last night was a hard reset because a game froze. I am posting this from my Ubuntu OS so thats clearly still working fine.

I would guess I need to reinstall XPsp3 but how can I do this without hurting the ubuntu where all my important files are? Or will I have to back up my personal files and reinstall both os. from scratch - I hope not :(

Any help gratefully received!

meTa

---

### Post by WRDN on 2008-06-30
Boot into Ubuntu and do a normal restart. This will allow it to unmount the disk.
Then boot back into 'XPsp3' and it should mount properly.

---

### Post by metasolaris on 2008-06-30
didnt work
when I tried to boot into windows I got a screen which told me that windows didnt start normally and offering me the option of a safe mode start or proceeding to boot normally.
i selected normal boot. got the windows logo but the system just hung whith the red pc light on continously. i restarted and this time selected safe mode. that didnt work either - just got a page of disk partion infomation and the system hung and the red light was on continously.
finally restarted and went back into ubuntu!

---

### Post by Canis familiaris on 2008-06-30
Try booting in safe mode and then reboot to Normal Windows. 
I faced the same problems after installing SP3. And this worked for me.

---

