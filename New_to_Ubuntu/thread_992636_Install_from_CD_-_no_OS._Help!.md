---
title: "Install from CD - no OS. Help!"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by strata2 on 2008-11-24
Operating System not found (expected)
PXE-E61: Media Test Failure, check cable

But the CD drive was working before, failed install of Ubuntu Server 8.10.
Formatted the drives (no OS)
Anybody run into this problem?
Been pouring over the install directions...

HP X-class Visualize Workstation 733Mhz
1 gig RAM
2 processors
SCSI Drives (3)

---

### Post by diablo75 on 2008-11-24
Can you please be a little more detailed about what you exactly did?  Because it seems pretty obvious that you'd not be able to find an OS on a blank (formated) hard drive (if you're trying to boot from that drive, anyway).  Now, if you're saying that this error comes up and you're trying to boot from the CD (because you know the hard drive is blank)... then we can work from there...

---

### Post by strata2 on 2008-11-24
yeah, thanks for asking. I'm trying to boot from the CD drive.

---

### Post by strata2 on 2008-11-24
yeah, i'm trying to boot from the CD - thanks for replying/asking.

---

### Post by diablo75 on 2008-11-24
Well if your computer is giving you a "No Operating System" found, it's either because the disc you're using wasn't burned very well (its recommended that you burn ISO's for installing at a slow speed like 4x), the drive is having trouble reading the disc... there is even a possibility that you need to update your BIOS (hey, solved a problem for me once... it was a firmware bug that had to do with trying to boot with a DVD drive that was on the same IDE channel as the primary HD).

I'd try to reburn the disc, and double-check your boot priority order.

---

### Post by strata2 on 2008-11-24
Thanks for the thorough reply and advice - I'll give it a shot!

---

### Post by strata2 on 2008-11-25
so the new CD is still giving me the "no OS found" - boot order is set.
updating the BIOS? new drivers? sorry for my ineptitude, they pass at "set-up". How do I go about this? Thanks again.

---

### Post by diablo75 on 2008-11-25
Do you happen to have any other CD's that are bootable (such as a Windows XP installation CD) that you can use as a "control" for this experiment to confirm that the drive works?  Because if it can boot from an XP CD, then it should boot from an Ubuntu CD that was just burnt (if you burned it correctly).  Be sure that you don't burn a plain ol' data CD and copy the iso file over to the file structure.  You have to use a burning utility (like Infra Recorder) to "Burn an Image" and point it to the ISO image file.

---

