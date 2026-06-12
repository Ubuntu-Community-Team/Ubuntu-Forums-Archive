---
title: "[SOLVED] Flash Drive Help"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by majikhotline on 2008-08-09
Hello Ubuntu country,

I have a 4 gig flash drive that will not auto mount, my 2 gig flask drive will but the 4 gig wont.  How do i fix this manually and how to fix the automount for the 4 gig?

Thankx

---

### Post by silkstone on 2008-08-09
We seem to be having a lot of people with flash drive problems recently!

Does it work with Windows?

Is it password protected? If so, you'll need to remove this in Windows. Often there's a hidden partition containing the encryption. You may be able to disable the password protection, or reformat the drive FAT32.

You could also see if gparted picks up the flash drive in Ubuntu - you can install that from Synaptic if it's not already there. If so, you can reformat it with gparted.

Hope that helps. Unfortunately it looks as if there are some encrypted drives that don't want to play at all with Linux.

---

### Post by majikhotline on 2008-08-09
mysteriously now it work, very strange

---

