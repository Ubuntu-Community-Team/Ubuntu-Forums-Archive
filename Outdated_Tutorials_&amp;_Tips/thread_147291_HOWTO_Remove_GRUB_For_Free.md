---
title: "HOWTO: Remove GRUB For Free"
date: 2006-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by josh34 on 2006-03-19
If you need to remove GRUB and you don't have a Windows CD do this:
(This will make it so Windows boots by default and removes any boot managers.)

1. Download UBCD here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) and burn it to a cd.
2. Boot the UBCD and select "DOS/Linux Boot Disks."
3. Select "FreeDOS," and let FreeDOS boot all of its default configurations.
4. Change to you boot hard drive (drive letters are listed above the prompt).
5. Type "fdisk /mbr"
6. Hit ctrl+alt+delete to reboot and remove the CD. Windows should now boot.

Hope This Helps,
Josh

---

### Post by unf on 2006-03-21
[QUOTE=josh34]If you need to remove GRUB and you don't have a Windows CD do this:
(This will make it so Windows boots by default and removes any boot managers.)

1. Download UBCD here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) and burn it to a cd.
2. Boot the UBCD and select "DOS/Linux Boot Disks."
3. Select "FreeDOS," and let FreeDOS boot all of its default configurations.
4. Change to you boot hard drive (drive letters are listed above the prompt).
5. Type "fdisk /mbr"
6. Hit ctrl+alt+delete to reboot and remove the CD. Windows should now boot.

Hope This Helps,
Josh[/QUOTE]
By removing mbr? Dont really think that removing mbr will help to bootup windows. I recommend to use windows recovery console fixboot fixmbr. If you do fdisk/mbr you just remove things that should be there to boot.

---

