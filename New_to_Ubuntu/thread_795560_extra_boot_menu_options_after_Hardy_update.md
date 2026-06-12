---
title: "extra boot menu options after Hardy update"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by corkscrew on 2008-05-15
I have succesfully updated my laptop from gutsy to hardy heron using the alternative cd.
However my boot menu now has 4 entries for linux where as there used to be 2 which if any of these should i delete the entires are as follows

8.04 Kernel 2.6.24-16 -generic
8.04 Kernel 2.6.24-16 -generic-recovery
8.04 Kernel 2.6.22-14 -generic
8.04 Kernel 2.6.22-14 -generic-recovery

i'm thinking the bottom 2 are left overs from Gutsy Gibbon??

---

### Post by mkoehler on 2008-05-15
Yeah, Hardy is using the ....24 kernels.  Most people leave more than one kernel installed at any given point in time (in the rare case that you encounter problems with the newest one).  If not, you can uninstall the old kernel (....22) using "linux-image" in synaptic (see this new post for more info: [http://ubuntuforums.org/showthread.php?t=795550](http://ubuntuforums.org/showthread.php?t=795550))

---

### Post by celticbhoy on 2008-05-15
The bottom two are just old kernel versions, if your system is working you can delete both the grub entries and the old kernels.

---

### Post by drs305 on 2008-05-15
There is a parallel thread running on what to do if you don't want to see all the extra/old kernels.

[http://ubuntuforums.org/showthread.php?t=795550](http://ubuntuforums.org/showthread.php?t=795550)

---

### Post by corkscrew on 2008-05-15
hey thanks thats neat so if have any probs with hardy i can just select the older kernel from this menu and Gutsy will start again?? is that correct

---

### Post by rockerphil on 2008-05-15
i personally just edited my grub menu.lst file to get rid of the older entries since Hardy is working perfectly

---

### Post by celticbhoy on 2008-05-15
No still Hardy just an older kernel

---

### Post by Oldsoldier2003 on 2008-05-15
> **corkscrew said:**
> hey thanks thats neat so if have any probs with hardy i can just select the older kernel from this menu and Gutsy will start again?? is that correct

no. the kernel will load and Hardy will start with the older kernel.

---

### Post by corkscrew on 2008-05-15
Hmm ok i'll just leave alone, i'm planning on upgrading my desktop to Hardy as well but with a clean install will i get the same result ie the old kernel still on the menu?

---

### Post by celticbhoy on 2008-05-15
If you do a clean install you will only have one kernel - until there is a kernel upgrade.

---

### Post by corkscrew on 2008-05-15
ok thanks everybody

---

