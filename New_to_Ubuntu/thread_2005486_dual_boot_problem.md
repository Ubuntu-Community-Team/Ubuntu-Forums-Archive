---
title: "dual boot problem"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by pancho45 on 2012-06-17
Running XP on master hard drive
Ubuntu on slave drive.

I just installed Ubuntu LT Release on slave drive and when booting i get the following message:
error: no such device:2ffc2790-2764-4bed-b6b2-1bba01dd878a
grub rescue>

But if i boot from slave drive then i can get to GNU GRUB dual boot menu and choose XP
or Ubuntu.I have no idea what went wrong when Ubuntu installed.Is there a way to fix this
issue?Thanks

---

### Post by ChrisNZ on 2012-06-17
It sounds like the Bios setting could be the issue? Possibly by changing the boot sequence could solve that. Then agin if you change the jumpers on the drives to Ubu Primary and Xp slave that could do the same thing?

---

### Post by pancho45 on 2012-06-17
> **ChrisNZ said:**
> It sounds like the Bios setting could be the issue? Possibly by changing the boot sequence could solve that. Then agin if you change the jumpers on the drives to Ubu Primary and Xp slave that could do the same thing?



I going to try it.Thanks

---

### Post by drs305 on 2012-06-17
pancho45

Welcome to the Ubuntu Forums. :-)

The easiest solution is to boot into Ubuntu and then install the Boot Repair app. It should be able to diagnose things and repair it by clicking the Recommended Repair button.

If it can't fix it, you can generate a report from within the app for us to review.

Link to Boot Repair in my signature line.

---

### Post by pancho45 on 2012-06-17
> **drs305 said:**
> pancho45

Welcome to the Ubuntu Forums. :-)

The easiest solution is to boot into Ubuntu and then install the Boot Repair app. It should be able to diagnose things and repair it by clicking the Recommended Repair button.

If it can't fix it, you can generate a report from within the app for us to review.

Link to Boot Repair in my signature line.

Thank you thank you very much .Great help.It was very very easy to fix following your instruction actually all i had to do was click and it was fixed.Thank you for your help.

---

