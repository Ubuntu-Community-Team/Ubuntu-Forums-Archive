---
title: "install xp"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Snappo on 2008-06-04
I want to install xp so i can play my games etc. I already have ubuntu installed so how do i go around doing this without deleting ubuntu.

---

### Post by Paqman on 2008-06-04
Just create some space on your drive using Gparted. Boot up with the XP CD in the drive and select that blank space during the XP install process.

You'll need to restore Grub and add an entry to it for XP once you've got it installed.

[How To recover Ubuntu after installing Windows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by housam on 2008-06-04
Just prepare a separate partition with ntfs format and install windows on it . then [[COLOR="Red"]_reinstall grub _[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?")to allow booting both systems.

---

### Post by Duck2006 on 2008-06-04
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Mauler5858 on 2008-06-04
+1 Paq.

Just a note make sure that the gparted resize process goes uninterrupted.  If it is interrupted it may render your hard drive unuseable.  As always before a process like this, make sure you backup your importantant files.

---

### Post by Cadmus on 2008-06-04
The GRUB super-disc deems to be the preferred way of getting GRUB back on after it's been removed from what I have seen.

---

### Post by Paqman on 2008-06-04
> **Mauler5858 said:**
> make sure you backup your importantant files.

Absolutely. Always, always do this if you've got anything you'd be sad to lose.

---

### Post by Paqman on 2008-06-04
> **Cadmus said:**
> The GRUB super-disc deems to be the preferred way of getting GRUB back on after it's been removed from what I have seen.

I just use the LiveCD. Burning a whole extra disk for such a quick job seems a bit excessive to me.

---

### Post by Sef on 2008-06-04
> The GRUB super-disc deems to be the preferred way of getting GRUB back on after it's been removed from what I have seen.

[Super GRUB Disk]("http://www.supergrubdisk.org/")

---

### Post by Mauler5858 on 2008-06-04
> Originally Posted by Mauler5858  
make sure you backup your important**ant** files.

Wow i cant spell today....lol

---

### Post by Snappo on 2008-06-04
> **Duck2006 said:**
> [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Cheers bud :)

---

