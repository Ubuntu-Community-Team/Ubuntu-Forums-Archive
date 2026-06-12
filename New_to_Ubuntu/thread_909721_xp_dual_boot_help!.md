---
title: "xp dual boot help!"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by feedmeh8 on 2008-09-03
So i am more than a little frustrated. I have ubuntu 8.04 .. and am trying to get xp on dual boot. Now i have used gparted, and made 20 gigs available for this on my HDD. I have tried formatting it with both ntsf and fat32, but every time i start the xp installer it tells me it cannot find a HDD. I have spent the past few days googling for help and have realized that i have a SATA drive. I have downloaded the driver from Lenovo that i think i need but alas! no floppy drive which xp requires to add the driver. Please help :) I am totally stumped.

---

### Post by ThomasHC on 2008-09-03
You need the SATA drivers included.
Google nlite.
Or go into BIOS & change the HDD to Compatibility mode.

---

### Post by feedmeh8 on 2008-09-03
change the bios how? in ubuntu.and Nlite for linux?

---

### Post by thesurgeon on 2008-09-03
In the BIOS there will be an option for SATA support which is enabled. Try disabling it, I had the same issue with a laptop which wasnt recognised by XP or any Linux distro. You should of sorted it by mow like but for anyone in the future. Try disable SATA support in the BIOS, boot up into Windows or Linux installer and it should work.

The BIOS will be F2, DEL, F10, ESC...depending on the model of the machine, on bootup. Different BIOS have different menus so it would be crazy to think anyone could pinpoint the option and menu without any other information. IE machine make, model, BIOS version, BIOS type and version ie 2005-2006 etc etc.

---

### Post by feedmeh8 on 2008-09-03
hmm thanks :) but how do i get into the bios?

---

### Post by feedmeh8 on 2008-09-03
ic. thanks a lot for the help :) the machine im using is a lenovo t61.. il look into how to get into it.

---

### Post by Miljet on 2008-09-03
Do I understand correctly that you already have Hardy installed and are now trying to install XP?
If so, Windows is going to balk. It expects to be the first system on the disk. If the partition that you created for Windows is not the first partition, XP won't look any further.
Also be advised that the XP installation will overwrite the MBR, resulting in a loss of the ability to boot Ubuntu.

---

