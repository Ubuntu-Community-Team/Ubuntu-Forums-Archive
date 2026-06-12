---
title: "No Hibernate After Deleting Grub"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by madmatrixz3000 on 2008-09-17
To start this may not be the correct location for this.

So I have recovered my laptop from a Grub install to a Vista MBR.  After doing this, my computer will not hibernate, the option is available, but when hibernate is clicked, the screen darkens then returns to the login screen.  I am still running off of the original install of Vista although the second half of the harddrive has hosted multiple OSs over the last 4 months.

Since the MBR would not load after reformatting, I was not able to recreate my MBR from my system specific recovery disk as I have not burned it to this day.  Instead I was able to find from Microsoft an MBR/simple recovery CD which rewrote my MBR to a working state.

Does anyone know how to get this working again, and could you guide me through the steps as recovering this in Vista is a much greater hassle than the recoveries of my XP desktop in the past.

---

### Post by Locutus_of_Borg on 2008-09-17
check to make sure the hibernate button is using /usr/sbin/hibernate

then check /etc/hibernate/common.conf and make sure it is pointing to your swap partition

---

### Post by madmatrixz3000 on 2008-09-18
This no longer is a Ubuntu install such is why I said that I don't think this is the right place in the forum for the question.  My problem is that Vista is not hibernating anymore.

---

### Post by Telanis on 2008-09-26
I have a similar problem, except that after installing Ubuntu (on partition 3 of my drive) I can no longer hibernate in Vista (on partition 2).  Partition 1 is XP and partition 4 is swap.  Vista just logs me off instead of hibernating.  Anyone now how to make GRUB play nice?

---

