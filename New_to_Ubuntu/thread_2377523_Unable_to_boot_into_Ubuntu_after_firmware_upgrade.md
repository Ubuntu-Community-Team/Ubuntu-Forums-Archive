---
title: "Unable to boot into Ubuntu after firmware upgrade"
date: 2017-11-14
forum: New to Ubuntu
---

### Post by vernot on 2017-11-14
0 down vote favorite
    A year ago, I bought a Dell XPS with Windows  10 installed in the factory. When it arrived, I created new volumes on  the internal hard disk, and installed Ubuntu 16.04.3 LTS on one of the  new partitions. Today, I was offered a firmware update, which I  accepted. Now, when the laptop boots, it no longer recognizes the Ubuntu  operating system, but it will boot into Windows.

Previously, if i wanted to switch to operating systems, I pressed the F2 key to bring up the BIOS.
To boot into Ubuntu, I would:


[LIST]
[*]    Choose the Ubuntu partition at the Boot Sequence page (I don't remember its exact title) 
[*]    Choose AHCI at the SATA Operation page 
[/LIST]

To boot into Windows, I would:


[LIST]
[*]    Choose the Windows Boot Manager at the Boot Sequence page 
[*]    Choose RAID On at the SATA Operation page 
[/LIST]

Now,  I see `[&#10003;] UEFI: THNSN5256GPU7 NVMe TOSHIBA 256 GB, Par(tition 1)` as  one of the entries at the Boot Sequence page, but if I put that first  and choose AHCI for the Sata Operation, I get a Windows Blue Screen of  Death. I am guessing that the UEFI boot settings are invalid.

I have run Boot-Info, and the output is available here:u [https://paste.ubuntu.com/25959941/](https://paste.ubuntu.com/25959941/)

I would be most grateful if someone could talk me through the steps of getting my laptop to boot into Ubuntu again.
Is this the right place to post such a question?

---

### Post by oldfred on 2017-11-14
Boot-Repair uses bootinfoscript as the first part of its report & it has not been updated to correctly parse NVMe drives.

I do not see /etc/fstab and you have a Windows type boot loader for BIOS boot in gpt drive's protective MBR.

And the way you describe how you booted, is more like Windows in UEFI mode & Ubuntu in BIOS/CSM/Legacy boot mode.

Better to have all systems in UEFI boot mode.

I might see if Boot-Repair's advanced mode and choosing uninstall of grub & reinstall of grub when booted in UEFI mode works. 
You may need to install newest kernel option also.
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

