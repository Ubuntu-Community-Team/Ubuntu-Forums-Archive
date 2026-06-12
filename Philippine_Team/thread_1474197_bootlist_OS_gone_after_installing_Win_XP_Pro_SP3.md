---
title: "bootlist OS gone after installing Win XP Pro SP3"
date: 2010-05-05
forum: Philippine Team
---

### Post by neehs on 2010-05-05
Masters,

Good day. My notebook working fine with dual boot with Ubuntu 10.04 & Win7 Ultimate then I install WinXP Pro SP3 on with dedicated 80GB NTFS partition.

I boot it to CD to install XP Pro SP3, then i select the proper / right partition 80GB then it install successfully. The problem is the bootlist OS is gone, I can't select anymore the OS I want to boot on. It direct to WinXP Pro SP3. As I see on My Computer all partition are intact.

Kindly help guys.

TIA

---

### Post by mikewhatever on 2010-05-05
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Are%20you%20using%20Grub%20or%20Grub%202?](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Are%20you%20using%20Grub%20or%20Grub%202?)

10.04 has Grub2, so please follow the right howto.

---

### Post by jaceleon on 2010-05-07
Don't tell me you formatted ALL partitions...

Anyway, try this. Format it just this one time, then try doing a partition in the Windows Setup. Make a partition for Windows and another for Linux. Then install Windows. Finally, install Ubuntu on the other partition.

IF you already have a dedicated partition for Ubuntu, and you installed Windows on a partition, most likely your MBR has been overwritten. Try using the liveCD and install GRUB2 on your MBR to recover your first Ubuntu installation.

---

### Post by neehs on 2010-05-08
It has a issue with my eMachines D725 SATA Mode = IDE & AHCI settings. Anyway thanks for the input. My notebook is ok now. Thanks

---

