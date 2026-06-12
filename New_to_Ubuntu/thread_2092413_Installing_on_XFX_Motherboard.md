---
title: "Installing on XFX Motherboard"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by Joerice50 on 2012-12-07
Hi Guys

I have the following:
General  
    Operating System    Microsoft Windows XP Professional 
    Central Processor    AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ 
    User Name    Joe 
Graphics  
    Video Adapter    NVIDIA GeForce 8500 GT 
    Video Memory    512.00 MB 
    Screen Resolution    1280 x 960 

And would like to install Ubuntu. I have installed plop on windows so I can boot from a USB and installed the community edition remix as I am informed it has newer drivers that might see my SATA drives.

However, no drives discovered on Try or install plus opening a terminal and using pci=nomsi or sudo fdisk -l does not reveal any disk.

Any other tricks I can apply so that Ubuntu can see my NTFS SATA drives, note winXP is running in standard IDE not ACHI

Cheers

Joe Rice

---

### Post by Nightcreeper on 2012-12-07
Have you tried making sure that the bios is set to plug and play os = yes, and I would try changing the sata ports to ahci, as I am running ahci on all of my drives and they show up fine. What distro are you trying to install?

**Also, Make sure if you the BIOS antivirus option, make sure it is set to off, as that "can", not "will", interfere when trying to access base system resources on a different level than windows does.

---

### Post by Joerice50 on 2012-12-07
Interestingly if I  run Fatdog ( a 64bit puppy linux distro) and use the F2 boot option to force pci=noacpi all disks in the machine are displayed. I still need to get other drivers optimized in Fatdog for display etc. but its interesting that it will display all the drives and I can mount them all!

---

### Post by Joerice50 on 2012-12-12
A Little Progress.

I have installed Ubuntu 11.10 as this fits on a CDROM and using all the ACPI boot options I managed to install from this iso to my E: drive SDB/1.

However,  using Grub stops at a busy box Ubuntu boot error and drops the process at an initramfs prompt Note Grub will boot WinXP. The record from boot repair is posted here http:/paste2.org/p/2598791

I suspect that the system is failing to access drive E: sdb/1 whereas, if I manually enter all the ACHI boot option on the install disk it installed to drive sdb/1 or so it informs me. 

I suspect I need to edit grub with some boot string so that Ubuntu sees the sdb drive and advice on what that string should be appreciated.

This final comment was posted using Ubuntu / firefox running from a CDROM and two harddives can be seen as acpi=off, noapic and nolapic were asserted prior to the CDROM boot, in particular I can see a 750GB drive and a 449Gb drive which I suspect is sda1 and sdb1 searching sdb1 for Grub results in the drive displaying the following files: 

```

/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/boot/grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/grub.d
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/doc/grub2-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/bug/grub-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/doc/grub-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/grub-gfxpayload-lists
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/doc/grub-gfxpayload-lists
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/grub-legacy
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/bug/grub-pc
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/doc/grub-pc
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/bug/grub-pc-bin
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/doc/grub-pc-bin
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/pm/sleep.d/10_grub-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/linux-boot-probes/mounted/40grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/linux-boot-probes/mounted/40grub2
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/lib/plymouth/themes/default.grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/alternatives/default.plymouth.grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/ucf/cache/:etc:default:grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/bash_completion.d/grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/default/grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/lib/recovery-mode/options/grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/grub/default/grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/recovery-mode/options/grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/boot/grub/grub.cfg
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/doc/grub-common/examples/grub.cfg
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/info/grub.info.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/grub/default/grub.md5sum
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/locale-langpack/en_AU/LC_MESSAGES/grub.mo
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/locale-langpack/en_CA/LC_MESSAGES/grub.mo
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/locale-langpack/en_GB/LC_MESSAGES/grub.mo
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub2-common.list
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub2-common.md5sums
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-bin2h
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-bin2h.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/init.d/grub-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/update-rc.d/grub-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-common.conffiles
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-common.list
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-common.md5sums
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-common.postinst
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-common.postrm
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-common.preinst
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-common.prerm
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/info/grub-dev.info.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-editenv
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-editenv.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/boot/grub/grubenv
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-fstest
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-fstest.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-gfxpayload-lists.list
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-gfxpayload-lists.md5sums
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-gfxpayload-lists.postinst
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-gfxpayload-lists.prerm
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/grub/i386-pc/grub-install
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/grub-install
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/grub-install.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-kbdcomp
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/doc/memtest86+/examples/grub-menu.lst
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-menulst2cfg
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-menulst2cfg.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/grub-mkconfig
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/grub-mkconfig.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/grub/grub-mkconfig_lib
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/grub-mkdevicemap
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/grub-mkdevicemap.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-mkfont
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-mkfont.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-mkimage
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-mkimage.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-mklayout
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-mklayout.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/grub/i386-pc/grub-mknetdir
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/grub-mknetdir
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/grub-mknetdir.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-mkpasswd-pbkdf2
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-mkpasswd-pbkdf2.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-mkrelpath
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-mkrelpath.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-mkrescue
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-mkrescue.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-mount
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-mount.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-ntldr-img
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/grub/i386-pc/grub-ntldr-img
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc.conffiles
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc.config
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc.list
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc.md5sums
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc.postinst
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc.postrm
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc.preinst
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc.prerm
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc.templates
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/lintian/overrides/grub-pc-bin
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc-bin.list
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/var/lib/dpkg/info/grub-pc-bin.md5sums
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/grub-probe
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/grub-probe.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/grub-reboot
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/grub-reboot.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/bin/grub-script-check
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man1/grub-script-check.1.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/grub-set-default
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/grub-set-default.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/grub/i386-pc/grub-setup
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/grub-setup
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/grub-setup.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/nvidia-173/nvidia-173.grub-gfxpayload
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/rc2.d/S99grub-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/rc3.d/S99grub-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/rc4.d/S99grub-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/rc5.d/S99grub-common
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/apport/package-hooks/source_grub2.py
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/grub-legacy/update-grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/update-grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/update-grub.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/update-grub2
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/update-grub2.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/update-grub-gfxpayload
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/share/man/man8/update-grub-gfxpayload.8.gz
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/lib/grub/update-grub_lib
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/usr/sbin/upgrade-from-grub-legacy
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/alternatives/x86_64-linux-gnu_grub_fb_blacklist
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/kernel/postinst.d/zz-update-grub
/media/8d68281f-4c72-440b-a8d1-18e8414e1ea0/etc/kernel/postrm.d/zz-update-grub

```

So I suspect this is sdb1 drive and this is the Ubuntu install. 

I just need a method of asserting the acpi workaround in a file called by grub.  Which file do I need to edit?   And what strings do I need to enter to get Ubuntu to boot?
 
Cheers

Joe Rice

---

