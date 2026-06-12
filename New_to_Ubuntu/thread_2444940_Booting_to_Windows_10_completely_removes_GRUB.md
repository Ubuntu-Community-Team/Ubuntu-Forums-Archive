---
title: "Booting to Windows 10 completely removes GRUB"
date: 2020-06-06
forum: New to Ubuntu
---

### Post by dbielecki on 2020-06-06
Hi
I'm currently running dual boot with Windows 10 and Ubuntu 20.04 LTS. Each time after booting to windows grub gets deleted and I'm unable to boot. Using boot-repair solves problem, but only till i try to boot windows again. When using boot-repair it says that some error occurred during repairs, but still is solves problem temporarily.
boot-repair
[https://paste.ubuntu.com/p/c8bbXfcHsr/](https://paste.ubuntu.com/p/c8bbXfcHsr/)
my boot info
[URL="https://paste.ubuntu.com/p/qNRZFvfFqW/"]https://paste.ubuntu.com/p/qNRZFvfFqW/

[/URL]

---

### Post by oldfred on 2020-06-06
What brand/model system?

Ubuntu lets you install in UEFI boot mode to MBR drives, Windows does not.
You have Ubuntu on sda which is MBR(msdos) but boots in UEFI mode from ESP - efi system partition on sdb.
It would be better but not absolutely required to have sda be gpt. But converting normally erases it. There are tools to convert, but still required good backups and reinstall of grub bootloader as UUIDs change.

Some like HP only let you change boot order with UEFI settings. Grub uses efibootmgr & it works for one boot.
Boot-Repair in line 89 has another suggestion to add info to Window's bootmgr.

---

### Post by dbielecki on 2020-06-06
Its custom build PC. I actually tried adding info to windows' bootmgr myself before writing here using command provided in boot-repair but it didn't work. Tried it again now since you mentioned it and it appears to have solved my problem. Don't know why it didn't work the first time. I have rebooted several times into different systems without any problems, so it seems to be solved. Thanks for help.

---

