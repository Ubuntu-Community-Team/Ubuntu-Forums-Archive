---
title: "Start up problem"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by eternalnewbee on 2008-10-03
Hi there,
I recently bought a new dvd writer and took the cables off the old one and plugged them in the new one. Ever since, I have to press F1 before Ubuntu fires up. How can I get rid of this?
Thanks.

---

### Post by bluefrog on 2008-10-03
enter the BIOS before booting as it is certainly suggesting you and make the necessary "information update" in it about your DVD drive.

Entering the BIOS differs on machines.
Could be <enter>, <F2>, <F12>, it should tell you when you switch on the computer which key you have to press.

---

### Post by eternalnewbee on 2008-10-03
Thanks.
I know how to get into the bios, but what do I do then? I'm afraid to do something wrong and mess up the system...

---

### Post by bluefrog on 2008-10-03
in the "general" tab where you see your disks and drives, select the old drive and update it by choosing "auto" for example (or something similar depending on your BIOS).

---

### Post by eternalnewbee on 2008-10-03
OK, thanks. will try that.

---

### Post by eternalnewbee on 2008-10-17
Alas...
Didn't work.
Is there any way to get rid of the message during boot from the command line. The DVD ROM works just fine.
Thanks.

---

### Post by nhasian on 2008-10-17
its definately your BIOS complaining about the change of hardware.  its not the OS.  each computer's bios is different so i dont know exactly where it would be, but try under general or attached devices or something similar.  maybe if you changed it from auto to CDROM it would stop complaining.  

it would help to know if your dvd writer is IDE or SATA because it will have a different line to update.  If its an IDE drive, are the jumpers set properly for single/master/slave?

finally make sure you save & exit!  I hope this can help.

---

### Post by eternalnewbee on 2008-10-17
> **nhasian said:**
> its definately your BIOS complaining about the change of hardware.  its not the OS.  each computer's bios is different so i dont know exactly where it would be, but try under general or attached devices or something similar.  maybe if you changed it from auto to CDROM it would stop complaining.  

it would help to know if your dvd writer is IDE or SATA because it will have a different line to update.  If its an IDE drive, are the jumpers set properly for single/master/slave?

finally make sure you save & exit!  I hope this can help.

Thanks for your advice.
Tried it again, got a red warning (something with system halt), had to go into BIOS again and now no red warning, just:
Sec Master HDD Error
Pri Slave Drive - ATAPI Incompatible
Press F1 to resume.
And back at square one.
I'll just have to find someone to physically help me solve this annoying little problem...

---

