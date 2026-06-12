---
title: "How do you edit the boot list?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by FTBPrimeEvil on 2008-06-23
How do you edit the boot list?
I have 3 version kernels listed and my primary vista os.
Is there an advantage of keeping the other kernel versions?

Sincerely,
:)

---

### Post by Duck2006 on 2008-06-23
From the terminal,

gksudo gedit /boot/grub/menu.lst

and you can edit it from there.

---

### Post by RequinB4 on 2008-06-23
Backup, mostly.  What you see (and what the options correspond to) are in your /boot/grub/menu.lst.  If you want to remove an option, the safest way is to comment (put a # before) each line of sections you don't want to show up.  BACKUP FIRST!

This won't delete the kernels, but I don't know how to get rid of them entirely.

---

### Post by wilson47 on 2008-06-23
You can delete the old kernels using synaptic package manager. I believe they can be found by searching linux-image. Run *uname -r* to see what kernel you are currently running, then in synaptic uncheck the boxes corresponding to the kernels which are not the result of the output of the previous command. You can also get rid of the old headers similarly. 

Many posts say to keep at least one old kernel, in case the new one breaks, you have a backup.

---

### Post by Pudworthy on 2008-06-23
I installed KGRUBEditor from the Add/Remove programs

It's got a lovely GUI and it backs it all up for you - simple as!

P

---

### Post by FTBPrimeEvil on 2008-06-23
Thanks for all the input, got it fixed now.:guitar:

---

