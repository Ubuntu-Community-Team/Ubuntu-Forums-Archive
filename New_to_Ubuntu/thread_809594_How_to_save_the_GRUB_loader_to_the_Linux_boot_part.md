---
title: "How to save the GRUB loader to the Linux boot partition?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by bettyhills on 2008-05-27
How to save the GRUB loader to the Linux boot partition?  

I am backing up my AMD 64 Dual Boot WinXP Home/UbuntuGG PC using Acronis True Image 9.0 to an external drive.  The instructions caution that later restoring will overwrite the MBR with an Acronis boot code, thus destroying the GRUB startup sequence.

Can anyone tell me how to save the GRUB loader to the "Linux root (boot) or boot partition record" as Acronis recommends?

---

### Post by quelx on 2008-05-27
Presumably Acronis is making some kind of rescue boot options, grub will break this if you restore grub after creating the backup.

What you can do is load Linux from the Windows boot loader which Acronis should leave alone.

[http://highlandsun.com/hyc/linuxboot.html](http://highlandsun.com/hyc/linuxboot.html)

---

### Post by Paqman on 2008-05-27
If your grub ever gets overwritten for any reason it's pretty simple to restore. Just boot into a LiveCD and follow these instructions:

[HowTo restore Grub](http://www.sorgonet.com/linux/grubrestore/)

(Except that to start you'll need "sudo grub" instead of just "grub")

---

### Post by lswest on 2008-05-27
Yeah, my first instinct would be to just restore GRUB using either the how-to posted above, the one i wrote (3rd line of my sig) or another one.

However, you could use (in windows) something like mbrfix.exe to create a backup of your mbr, which you could restore.

Or, you could just re-install GRUB to the partition (it's a slight variation on the restoring of GRUB, and I'm not 100% sure of the steps, but it is possible i think).

*EDIT* googled it and found some info on how it's originally installed, which gave me an idea.  so I'll add that to my how-to now.

---

