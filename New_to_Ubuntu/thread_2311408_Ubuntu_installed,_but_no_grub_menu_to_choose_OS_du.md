---
title: "Ubuntu installed, but no grub menu to choose OS dual boot."
date: 2016-01-27
forum: New to Ubuntu
---

### Post by uchiha_skyline on 2016-01-27
[http://paste.ubuntu.com/14677206/](http://paste.ubuntu.com/14677206/) (boot-repair pastebin)

I think I've successfully installed Ubuntu, but after rebooting my laptop it directly go into Windows without the grub menu showing which OS I'd like to run.
I ran boot-repair to no avail. It gave me the log and told me to ask a forum if it failed, hence why I'm here. I'm running Win10 and would like to dual boot with Ubuntu, not sure why the log shows I'm using Win8, but gut feeling says it's because I did the upgrade instead of the clean install.

Anyone has any ideas on how to get the grub menu working?

Regards

---

### Post by mastablasta on 2016-01-27
have you followed the advice at the end of the file?

> If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi


---

### Post by grahammechanical on 2016-01-27
I have no practical experience with a UEFI boot system but from reading other threads on this forum I think that we need to enter the UEFI boot settings to select an OS to load first and then Ubuntu should load with the Grub menu. We may need to move Ubuntu up to the top of a list in the UEFI settings utility.

It also seems that certain manufacturers do not comply with the UEFI specifications. They alter things making it more difficult to boot any OS other than Windows. Advice on what to do in that situation is given in the many threads on this subject.

Regards.

---

### Post by oldfred on 2016-01-27
What brand/model computer?

The suggested work around from Boot-Repair often works, but you are booting into Windows and in its BCD choosing to reboot using UEFI one time reboot into Ubuntu. If primarily a Windows user that is often all you need.
Some systems will just let you choose the ubuntu entry.

Many now seem to need other work arounds, depending on brand and your use of system.

---

