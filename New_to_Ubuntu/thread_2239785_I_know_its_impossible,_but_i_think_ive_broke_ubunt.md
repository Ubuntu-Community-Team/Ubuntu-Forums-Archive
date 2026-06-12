---
title: "I know its impossible, but i think ive broke ubuntu"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by michaeljameswade25 on 2014-08-15
ok, so i was on my laptop and wanted to delete ubuntu, as i only had 2gb in windows....
i proceeded to go on partition and i deleted it... yep stupid:( following that i had restarted my laptop and i still have the GRUB menu, but when i click ubuntu.... i cant, it doesnt select, just has a star on the left of it... what should/could i do?? thanks!

---

### Post by westie457 on 2014-08-15
Welcome michael

Did you install Ubuntu via Wubi (Windows Ubuntu installer)? Or did you have a dual-boot with Ubuntu on its own partition?

Each of these installation methods has a different recovery procedure.

---

### Post by grahammechanical on 2014-08-15
Re-install Ubuntu.

---

### Post by yancek on 2014-08-15
You broke the Grub bootloader by deleting the Ubuntu partition on which almost all the files needed to boot existed.  Since you had Grub in the mbr, that's what happens.  If you just want windows you can repair its bootloader with the installation medium for whichever version of windows you have.

---

### Post by Sanctimonious_Ape on 2014-08-15
Windows likes to think it's the only OS in the world, so it boots directly from the MBR (Master Boot Record - the first thing loaded from disk when a PC starts up).  You need to use your Windows install disk to repair it.  I can't give you specifics since you didn't specify what version of Windows you're using, but a simple Google search for "Repair Windows XX MBR" should get you going in the right direction (replacing XX with your version, of course).

---

