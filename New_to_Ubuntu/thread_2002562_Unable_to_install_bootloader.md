---
title: "Unable to install bootloader"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by Nico156 on 2012-06-12
Hi!
I'm new to linux

Dell xps 15 L502X
Hd 500 GB
Win 7 64bit
Downloaded and installed ubuntu 12.04
Side by side install
Gave 40 GB to linux partition
Install process interrupt with ''bootloader install failed'' error message
Didn't know what to do so I choosed ''finish install without bootloader''
Shutdown laptop
Win start normally, genuine control to do again but did it and works fine
I did the boot info here is the link: [http://paste.ubuntu.com/1037158/](http://paste.ubuntu.com/1037158/)
Want to have a win/ubuntu option menu at laptop startup

thanks for attention

---

### Post by oldfred on 2012-06-12
Your install is missing grub2's boot loader from the MBR, but also missing grub.cfg.

I think if you install grub2's boot loader with Boot Repair,  you will then just get a grub rescue.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

The full chroot uninstall & reinstall should also create the missing grub.cfg.

You also may be able to boot without grub with this and then from inside your install, you then could reinstall grub2.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

### Post by Nico156 on 2012-06-12
Thanks!
I read a few pages of the threads linked above then I run bootrepair (from live cd) and go in advanced section, selected reinstall grub, all works fine!
Now I'm going to edit the grub because I was unable to do it with the bootrepair gui.
I think I could open and edit it with a simple like notepad text editor.
We can flag this thread as solved!

---

### Post by drs305 on 2012-06-12
Grub Customizer can't repair things like Boot Repair, but it is a good app for modifying most features of grub. Link in my signature line.

---

### Post by Nico156 on 2012-06-12
Thanks!

---

