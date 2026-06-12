---
title: "Trying to get an old computer to boot to hard disk"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by Horsepower on 2014-03-26
It will only boot to the cd, then I select boot to first hard disk. I tried boot repair here: [http://paste.ubuntu.com/7157636/](http://paste.ubuntu.com/7157636/)

---

### Post by Herman on 2014-03-26
Have you tried looking in the BIOS or CMOS settings? There should be a tab in there where you can set up which devices you want the computer to try to boot and you should also be able to set the boot order. 

If it is a very old computer and it has the old IDE ribbon cables it might have jumper settings on the HDDS for setting which HDD will be 'master' and which ones will be 'slave' hard drives. If you think someone might have been messing around in there unplugging hard drives and plugging them back in again it could be something to check. The old IDE ribbon cables have black plugs are for the 'master' drives and the grey plugs are for the 'slave' drives too.

---

### Post by Vladlenin5000 on 2014-03-26
> **Herman said:**
> Have you tried looking in the BIOS or CMOS settings? There should be a tab in there where you can set up which devices you want the computer to try to boot and you should also be able to set the boot order.

Exactly. Letting it boot following its predefined (by user) order at BIOS, where the HDD is supposedly the first drive already or telling it to run from HDD after booting from a CD, results _exactly_ the same. As such, if the computer doesn't boot correctly to the already installed Ubuntu - due to whatever reason we still need to troubleshoot - it won't boot either by telling it to boot from the same HDD in the CD menu. So...
We need you to make sure the HDD is the first boot device in BIOS, then let it boot normally (forget the CD for now), or at least attempt to, and then tell us _exactly_ what happens.

> If it is a very old computer and it has the old IDE ribbon cables it might have jumper settings on the HDDS for setting which HDD will be 'master' and which ones will be 'slave' hard drives. If you think someone might have been messing around in there unplugging hard drives and plugging them back in again it could be something to check. The old IDE ribbon cables have black plugs are for the 'master' drives and the grey plugs are for the 'slave' drives too.

You can safely ignore this bit. The information isn't really helpful, first and foremost because there's only one HDD involved, and it's also inaccurate, incomplete and misleading, albeit with good intentions. In order to avoid this well-intentioned but confusing wild guesses **please give all the informations you know about your hardware (brand/model if available, CPU, GPU, RAM, etc., etc.)**

---

### Post by Horsepower on 2014-03-26
Got it fixed. I found a setting in the bios that said "boot first drive" and it was disabled. Now all is well. Thank you for your timely input.

---

