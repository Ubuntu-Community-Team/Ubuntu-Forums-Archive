---
title: "Windows unable to boot, Ubuntu drops me into busybox"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by jacky2 on 2013-08-28
Hey guys, I need some help. The win8/ubuntu dual boot thing was working fine until a few days ago. Currently, if I try to boot into windows it just loads forever. I'm able to boot into ubuntu after I type exit into busybox. I re-installed ubuntu, but the problem persists. 

This is the pastebin from running boot-repair: [http://paste.ubuntu.com/6037632/](http://paste.ubuntu.com/6037632/)
It also says the boot files are far from the start of the disk. I tried following  [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) but if I have to partition something in the first 100gb of the disk, then it'll have to be my windows partition. It says that I can't use gParted to resize the windows partition. I can't boot into windows so what should I use?

GSmartcontrol says my hard drive is fine. 

Any help would be appreciated ^^.

---

### Post by oldfred on 2013-08-28
Welcome to the forums.
The issue on files far from start is for BIOS systems and primarily USB hard drive installs. I have yet to see a UEFI system need the separate /boot. And if Ubuntu worked before then no change should be required.

Windows issues are separate from Ubuntu issues. If Ubuntu worked before, reinstalling Ubuntu would not fix Windows issues. And most Windows issues need to be fixed from Windows. Boot-Repair can just install a boot loader and fixes Linux boot issues, but cannot do much for Windows.

It also looks like you have Ubuntu in both BIOS boot mode with grub2's boot loader installed to the MBR of the gpt drive and the grub efi boot files in the efi partition. I cannot tell which is the default, but it looks like Boot-Repair fixed the UEFI grub boot.

Did you run Windows repairs and it turned hibernation back on (Fast Boot) or reset UEFI to default to Windows? Hibernation causes all sorts of issues and needs to be off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

### Post by jacky2 on 2013-08-28
I'm a total newb so I'm not quite sure if I "ran" windows repairs. However, whenever I booted into windows it would say that it was "scanning and repairing F:" which is the drive I installed Ubuntu on. I can't boot into windows to turn off fast boot though.

EDIT: Just to clarify it a bit: Grub works fine. When I turn on my laptop, it loads into grub and gives me options to choose from (windows/ubuntu). If I try to boot into windows, it just won't work and if I try to boot into ubuntu I'm thrown into busybox.

---

### Post by oldfred on 2013-08-28
Have you tried directly booting Windows from UEFI menu with or without secure boot?

For whatever reason grub chainloads to Windows efi file just like UEFI would and it usually works. But when Windows has issues with chkdsk or hibernation then only direct boot seems to work. There really should not be any difference.

---

### Post by jacky2 on 2013-08-28
Without secure boot, it just loads forever and never boots. With secure boot, it prompts "preparing automatic repair" and still doesn't boot

---

### Post by oldfred on 2013-08-28
If it has to run chkdsk that can take a bit. Wait 5 or 10 minutes. Beyond that then it is a Windows 8 boot issue.

[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

From Ubuntu this may be the only thing you can do.
 Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

### Post by jacky2 on 2013-08-29
Alright I'm back! There was a boot-repair update that I hadn't installed yet so I did that, ran boot-repair again and now I'm not thrown into busybox! yay! 

I did the force removal of hiberfile, but that only helps the ubuntu boot right? I still can't boot into windows. I posted on microsoft answers for help with the windows boot trouble. In the meantime, thanks and if you anyone has any idea on how to get windows to boot well, I'll love you forever.

---

### Post by oldfred on 2013-08-29
The hiberfile is Windows, not Ubuntu. With that gone, you should be able to directly boot Windows or at least get it to run its repairs. Otherwise it is Windows 8 repairs well beyond me.

From grub which boot entry are you using for Windows. The two that os-prober creates are wrong. Boot-Repair creates correct one.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)


These are now older, not sure if a root delay may help as boot parameter or other boot parameter is required.
      
 See post #4 busybox exit & boot - blue screen;s post
[http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay)
busybox See quixote post
[http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay)

What model Lenovo?
Some others:
      
 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

---

### Post by jacky2 on 2013-08-30
I have an Ideapad Y500. 

Regarding the boot entries, I have both [COLOR=#000000]"Windows UEFI bootmgfw.efi" and [/COLOR][COLOR=#000000]"Windows Boot UEFI loader" except that both of them say Recovery in them, e.g., [/COLOR][COLOR=#000000]"Windows Recovery UEFI bootmgfw.efi" and it's like bkpbootmgfw.efi or something like that. I found one of your old posts about that being a problem so I tried the boot-repair with the rename enabled, but it didn't change anything.
 
Ubuntu doesn't put me in busybox anymore, but it just loads really slow instead (15-20seconds). Will adding rootdelay to the kernel via boot-repair help?[/COLOR]

---

### Post by oldfred on 2013-08-30
If booting from hard drive 15-20 sec is not really slow. But you can look in log files and dmesg and see if there are any large time differences in posted tasks. One user had 30 sec and it tried task twice. I think it was a UEFI/BIOS setting on some device that did not exist - floppy or DVD. So UEFI reported to Ubuntu to look for a non-existing device and Ubuntu tried and failed, but took a long time.

Some systems Boot-Repair does put recovery into the UEFI boot stanza. Not sure why it sees it that way with some systems and not others. Unless you have one of the few buggy UEFI Windows systems that only boots bootmgfw.efi you do not need the rename to bkpbootmgfw.efi.

---

