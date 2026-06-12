---
title: "Partitioning step in Xubuntu installation"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by Vashstamp on 2013-05-19
[ATTACH=CONFIG]242788[/ATTACH]
 I am at this point in the installation. What do I do? I don't want to delete my old OS

---

### Post by Kevin McCready on 2013-05-19
1. Did you miss an earlier step which asked if you want to keep a current installation? Might be an idea to go back a few steps.
2. If it was me I'd do a live boot and repartition.

---

### Post by Vashstamp on 2013-05-19
If I were to repartition would I lose data? And I don't recall seeing that step. I am on a live boot doing the installation

---

### Post by jamesisin on 2013-05-19
If you install over the top of anything, that anything will be lost.  So, if you install Ubuntu 13.04 over your Windows 8 partition, everything in the Windows 8 partition would be gone.  Back up your important data (somewhere else, another machine or drive) and then wipe the old installation.

---

### Post by Kevin McCready on 2013-05-19
No you don't lose data if you repartition PROPERLY. But before you start experimenting, BACKUP.

---

### Post by Impavidus on 2013-05-20
> **Vashstamp said:**
> [ATTACH=CONFIG]242788[/ATTACH]
 I am at this point in the installation. What do I do? I don't want to delete my old OS
If this is the drive containing your windows installation and you want to keep it, quit the installation, reboot into Windows, shrink the partition from there to create unallocated disk space, reboot a few times into windows to let it do its checks and then start from the live disk again. When you install again you'll see free space on the disk, where you can install Ubuntu.

---

### Post by Vashstamp on 2013-05-20
Thanks, that suggestion worked

---

