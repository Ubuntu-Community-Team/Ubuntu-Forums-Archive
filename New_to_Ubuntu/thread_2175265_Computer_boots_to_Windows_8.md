---
title: "Computer boots to Windows 8"
date: 2013-09-18
forum: New to Ubuntu
---

### Post by laura3 on 2013-09-18
I have installed Ubuntu 13.04 on my computer.  When I restart the computer it goes directly to Windows 8, and I have to go to the PC settings and restart the computer from there.  
I thought that the computer would give me the option of booting into Windows 8 or Ubuntu when it starts up, but it does not.  How do I make it do that?  And if I cannot make it do that, how can I make Ubuntu my primary OS?

---

### Post by oldfred on 2013-09-18
From UEFI menu can you boot ubuntu entry? You then should be able to see ubuntu as first boot choice, just like changing hard drive or DVD as first boot option.

Have you run Boot-Repair? Grub2 has a bug and its os-prober does not create correct chain load entries to Windows efi entry, it still creates BIOS type entries that do not work.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry from os-prober that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
os-prober fix in grub2_2.00-14 and os-prober_1.58 from Debian

---

