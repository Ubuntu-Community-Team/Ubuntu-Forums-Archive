---
title: "Problems formatting HDD during installation"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by cshard on 2008-11-15
I attempted to install Ubuntu 8.04 onto my primary PC, but ran into a roadblock when the program stopped the installation in the middle of creating the main partition. Although the system booted into the temporary version of Ubuntu from the CD, when I attempted to install again, I kept facing the exact same problem.

At present, my HDD is locked up, due to a improper format during one of my attempts to install the software. Any advice on how to get my HDD back?

*note - I'm not sure if all my terminology is correct, so if I've made an error, please correct me.

Summary of events:
1. Booted into Ubuntu install menu
2. Selected Check CD for defects - CD checks out ok and system restarts
3. Back to Install Menu - Install Ubuntu selected
4. Steps to installation filled in - guided partitioning (use entire hard disk) is selected
5. Installation stalls during partition HDD step
6. Ubuntu Live CD is loaded
7. I format my HDD again in ext3
8. Installation attempted again from the desktop shortcut
9. Steps to installation filled in - guided partitioning (use entire hard disk) is selected
10. Installation stalls during partition HDD step
11. I attempt to reformat the HDD again and find it locked - unmounting the drive unlocks it and I reformat it again in ext3
12. Installation attempted again from the desktop shortcut
13. Steps to installation filled in - manual partitioning is selected
14. Root partition, Home Partition and swap partition are created
15. First partition is created without a hitch, but partition 2 stalls halfway. Installation aborted.
16. I decide to shut down and restart. I do not unmount the drive beforehand
17. Computer restarted and I try to boot into the Live CD. The Live CD stalls because it can't find the HDD.

---

### Post by cariboo on 2008-11-15
You may need one of the apic option available when you press F6 at the menu screen. The best thing to do right now is to walk away and try again tomorrow.

Jim

---

### Post by cshard on 2008-11-15
Well, I haven't reached the "tearing my hair out with murderous intent" stage so I think I shall continue to struggle with my HDD. XD I'm not about to do anything funny to my computer. 

Anyway, turning on noapic and nolapic helped in booting the LiveCD. Many thanks.

edit: It seems I spoke in haste. The CD I burned may have somehow become unusable as I placed another HDD into the computer and tried to boot from the LiveCD. No luck there. Booting into win xp again did reveal that my HDD was still working correctly - it was properly partitioned the way I had organised it.

I'm downloading another copy of Ubuntu 8.04 LTS now just in case the first copy I used had errors. Does anyone know if older ISOs of 8.04 (about 2-3 months ago or so) had any issues during installation?

---

