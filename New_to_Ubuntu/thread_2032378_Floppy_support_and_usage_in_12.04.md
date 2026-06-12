---
title: "Floppy support and usage in 12.04"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by JD Hupp on 2012-07-23
I was flashing a BIOS and wanting to check the contents of a floppy drive, and was surprised when, after finally locating the My Computer place in Lubuntu's file manager, double-clicking on Floppy Drive (with the floppy in the drive), presented me with a dialog for choosing the application for handling the mount point.

Research showed that floppy support in Ubuntu and Linux in general is trickier than in Windows, and furthermore that there were special complications in Ubuntu 11 due to development of a package named udisks, as I recall.

I did not see a consensus about this question in Ubuntu 12.

One prescription called for use of a single command in terminal (perhaps sudo --mount /dev/fd0), and running that or something similar did allow me to open the floppy and examine the contents, but I'm very much wondering now what the general prescription is for usage of floppies under Ubuntu 12.

In short, do I have to use commands to support floppy usage in Ubuntu 12, or is there a simple GUI treatment?

---

### Post by Johnny3 on 2012-07-23
You mite could try install fdutils in synaptic package manager.
Good Luck and God Bless Johnny3 65+++

---

### Post by JD Hupp on 2012-07-24
> **Johnny3 said:**
> You mite could try install fdutils in synaptic package manager.

Thanks, Johnny, I'll have a look.

---

