---
title: "LVM unable to boot (stuck at busybox screen)"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by leo_mancini on 2014-05-31
[COLOR=#444444][FONT=Calibri]Hi all,[/FONT][/COLOR][COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]I'm unable to boot into my Ubuntu system. I'm running 14.04 LTS.
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]I had attempted to clean up my boot partition restarted the PC and it then after booting through Grub stopped at the busybox screen stating "gave up waiting for root device".[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
I have since attempted to use the boot repair application via both an ubuntu live installation and an actual boot repair ISO.
I have managed to restore my grub, though it still doesn't boot through giving me the same error "gave up waiting for root device" before crashing and not logging in.

[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Please refer to my pastebin [http://paste.ubuntu.com/7561974/](http://paste.ubuntu.com/7561974/) for more information.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Please advise if you would like me to provide more information.

[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Thank you for your assistance.[/FONT][/COLOR]

---

### Post by oldfred on 2014-05-31
Is this an encrypted install, or just full drive LVM? And is this a 32 bit install?
What system & video card?

I do not know either, but do not see anything really wrong in the BootInfo report.
It says you have the /boot in fstab, but did not post the fstab?

---

### Post by leo_mancini on 2014-05-31
Hi

It's a full disk drive lvm installation. I have an amd dual core cpu with an nvidia video card. I'm unsure how to post fstab but once i return ill research how to do it and post the results.

---

### Post by leo_mancini on 2014-06-01
Hi there my fstab is the following [http://paste.ubuntu.com/7565540/](http://paste.ubuntu.com/7565540/)
The ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid and sudo fdisk -l details are as follows [http://paste.ubuntu.com/7565563/](http://paste.ubuntu.com/7565563/)

Any help would be greatly appreciated.

Thank  you.

---

### Post by oldfred on 2014-06-01
I do not know LVM. 
Edited your title to add LVM, so those that do know it may respond.

Generally correct, But do not know if this is a real error or not.

> Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Various partition tools do not see other types of partitions correctly so it could be ok.

Usually you could not mount a partition if it is incorrect, but you are able to see fstab and other info in your LVM.

Do you get grub menu if you hold shift key from BIOS. Menu will not be shown normally since you have only one install. And can you boot recovery mode or an older kernel?

---

### Post by leo_mancini on 2014-06-02
Hi there,

Yes I can get into the Grub menu when I press shift. 
No I cannot successfully access a previous kernel that I could previously access.
:S 
I have not tried a recovery kernel though. I will give that a try.

---

### Post by leo_mancini on 2014-06-02
ok So I've tried a boot with a recovery kernel. Linux 3.13.0.27-Generic (recovery mode)

The following is what appears after the reboot:

> [31.146824] [FONT=Calibri][COLOR=#444444]random: lvm urandom read with 25 bits of entropy available
Gave up waiting for root device.  Common problems:
 - Boot args (cat/proc/cmdline)
    - check rootdelay = (did the system wait long enough?)
    - Check root = (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls / dev)
ALERT! /dev/mapper/ubuntu-root does not exist. Dropping to a shell!

BusyBox v 1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)[/COLOR][/FONT][FONT=Calibri][COLOR=#444444]

** Please note, this doesn't allow any keyboard input at this point.[/COLOR][/FONT]

---

### Post by leo_mancini on 2014-06-03
additional information..

lshw command [http://paste.ubuntu.com/7579301/](http://paste.ubuntu.com/7579301/)
lspci [http://paste.ubuntu.com/7579300/](http://paste.ubuntu.com/7579300/)

any help would be appreciated.

Thanks

---

