---
title: "[SOLVED] Restoring Windows XP boot loader"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by m_ad on 2008-07-27
I installed Xubuntu on an old system with 256mb of ram. After days and days of trying to connect to my wireless network, I gave up on Xubuntu.

I didn't remove it the most efficient way. I went into XP's 'Disk Management' and deleted the partitions. Now when I boot the computer, I get "Error 22" after GRUB tries to load. I'm wondering if there's a good article out there that explains how to restore the original XP boot loader.

I'm assuming I need to boot into the Live CD.. :confused:

Is it as simple as booting into my XP CD and going into Recovery console, and typing 'fdisk /mbr?'

---

### Post by phidia on 2008-07-27
> **m_ad said:**
> 

Is it as simple as booting into my XP CD and going into Recovery console, and typing 'fdisk /mbr?'

In XP the exact command is > fixmbrthat should do it. If you want to see a more complete tutorial read [this]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console").
BTW different versions of windows have formatted that command differently.

---

### Post by m_ad on 2008-07-27
Marked thread as solved.

Sorry for the quick post, I was in a bit of a panic.

Booting into the XP Recovery Mode, and typing 'fixmbr' worked :popcorn:

---

### Post by phidia on 2008-07-27
Great! glad it worked. You might want to look at lighter weight distros too but wireless can be a pain. If you ever decide to try linux on that again there are some resources available.

---

### Post by m_ad on 2008-07-27
I actually got Xubuntu 8.04.1 to recognize my Netgear WG111T wireless device, and search for available networks. It found mine, but it wouldn't ever accept my passphrase. Which is weird, because my laptop connects fine (Ubuntu 8.04).

---

