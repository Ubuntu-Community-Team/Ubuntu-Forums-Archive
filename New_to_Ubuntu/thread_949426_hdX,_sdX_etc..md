---
title: "hdX, sdX etc."
date: 2008-10-16
forum: New to Ubuntu
---

### Post by v2102ap on 2008-10-16
Hello everyone, i just have a question to ask here. From what I know, in linux, partitions are given names like hda0, sda0 etc, with hdXX for ide drives and sdXX for SCSI drives. I have an IDE drive but its sdaX. Can anyone explain? Thanks in advance.

---

### Post by bumanie on 2008-10-16
What you are saying was in  deed the case previously. Once sata drives came in, they were also known as sdx,x Recently, all drives whether IDE or SATA or SCSI have had the designation sdx,x with the exception of /boot/grub/menu.lst that sill refers to IDE and SATA as hdx,x - not sure why it was changed, but did read somewhere (have no idea to the veracity of this) that changing everything to sdx,x was an attempt to standardize things a bit. Sorry can't give any more detailed information. No doubt someone else will have a better, more detailed explanation.

---

### Post by The Cog on 2008-10-16
I read somewhere that SATA disk drivers were made using SCSI emulation (so they looked like SCSI to the OS) despite the fact that they are more like IDE. Then it was then discovered that the SCSI IDE emulators actually had better performance that the original IDE drivers to they started using the SCSI/SATA drivers for normal IDE drives too. I don't know if it's true, but that's what I read somewhere.

---

