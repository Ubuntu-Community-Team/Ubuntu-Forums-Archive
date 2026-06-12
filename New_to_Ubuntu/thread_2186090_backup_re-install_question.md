---
title: "backup re-install question"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-11-05
i have a laptop with only linux installed and use redo backup. have no problems. i will be purchasing a new laptop soon and am sure it will come preinstalled with win8. i am going to delete and install my linux using the redo. do i first have to reformat to ext4. or since i have the redo backup can i just install. or would it be better to download linux burn a cd and install and then update my new laptop with my most current redo backup. tks

---

### Post by oldfred on 2013-11-05
You cannot use redo backup unless your current install is UEFI with gpt partitioning. Do not know details of redo backup, but do you have a separate /home? Or can you extract from the backup just /home?

With a new UEFI system pre-installed with UEFI and secure boot, the install is a bit more complicated and if a higher end laptop that is an Ultraboot with the small SSD then that adds even more things to work thru.

A few have totally erased Windows 8 and had system work. But some are hard coded to only boot the Windows efi file and work arounds have to be done to make those boot grub2's secure boot shim file.  A few have also just given up on UEFI and converted it to BIOS/CSM boot like your old computer. Most work ok in that mode, but in the future they may not. UEFI has a lot of updates and BIOS may not have all the new features. Suggest dual booting before erasing Windows and a full backup of Windows as installed just in case.

See links in my signature for lots of info on UEFI install.

I like the idea one user posted. He buys a system with just a hard drive and removes hard drive with Windows and installs a SSD to install with Ubuntu. Then later if he wants to sell system, he has a new (but not updated) version of Windows on the hard drive that he puts back in.

---

### Post by rburkartjo on 2013-11-09
has anyone ever tried what i can to do. let me know and if it worked for you.tks

---

