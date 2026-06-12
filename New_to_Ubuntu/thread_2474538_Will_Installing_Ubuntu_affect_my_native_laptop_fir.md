---
title: "Will Installing Ubuntu affect my native laptop firmware?"
date: 2022-05-02
forum: New to Ubuntu
---

### Post by cardinal4 on 2022-05-02
I'm a slightly experienced user of Linux (e.g. RHEL and Debian distros) but I've always done so on virtualization (e.g. VirtualBox or WSL). Now I want to try installing on my laptop for real, without virtualization.

I realised my laptop is tightly integrated with Windows, as I can see an ASUS logo in the background when my machine was performing a reset of Windows OS.

I am interested in switching to Ubuntu, but I'm worried my laptop firmware might be affected. Things like WiFi driver, display driver, battery driver, etc. will it still function efficiently under Ubuntu?

And if I ever do intend to switch back to Windows, will my laptop firmware and Windows installer/license still be valid, or would it have been wiped and unrecoverable?

---

### Post by tea for one on 2022-05-02
> **cardinal4 said:**
> I am interested in switching to Ubuntu, but I'm worried my laptop firmware might be affected. Things like WiFi driver, display driver, battery driver, etc. will it still function efficiently under Ubuntu?
Your laptop firmware will not be compromised.
Whether the wifi, display etc. will function efficiently depends on the exact hardware. Many systems work seamlessly, some have problems.

> **cardinal4 said:**
> And if I ever do intend to switch back to Windows, will my laptop firmware and Windows installer/license still be valid, or would it have been wiped and unrecoverable?
Your Windows OS and license will be fine if you follow the correct procedure for dual boot systems.

Are you familiar with running a [COLOR="#0000FF"]live[/COLOR] Ubuntu session on your PC (i.e. a temporary session to test graphics/ hardware etc)?

---

### Post by cardinal4 on 2022-05-02
Thanks so much for your quick reply!

> [COLOR=#000000]Your Windows OS and license will be fine if you follow the correct procedure for dual boot systems.[/COLOR]

Ah that makes sense. I did not think of dual booting - it should work!

I have 2 physical disks: an OS disk and a data disk. Form what I can see under Windows Disk Management, the OS disk contains a Recovery Partition, an EFI System, and a NTFS partition. While the data disk just has a 1 NTFS partition.

If I understand correctly, as long as I don't touch the OS disk, my ASUS firmware and Windows OS/license will be fine?

> [COLOR=#000000]Are you familiar with running a [/COLOR][COLOR=#0000FF]live[/COLOR][COLOR=#000000] Ubuntu session on your PC[/COLOR]

Yeps I am familiar with it, basically creating a Live USB yes?

---

### Post by tea for one on 2022-05-02
Two physical disks is ideal.
One for Windows and one for Ubuntu - perfect.
Isolate your Windows disk via UEFI settings before installing Ubuntu on the second disk.

First task is to make a bootable live USB and see if you like the OS and also test your wifi etc.

Don't forget to back up your personal data before attempting any new OS installation.
Better to be safe than sorry.

---

