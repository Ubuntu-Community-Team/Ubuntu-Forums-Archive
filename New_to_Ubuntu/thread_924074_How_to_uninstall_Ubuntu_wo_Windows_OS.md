---
title: "How to uninstall Ubuntu w/o Windows OS"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by blazzer on 2008-09-19
Hi,

I have problem during uninstall ubuntu on my desktop.
i've tried to boot from CDROM but it still goes to GRUB menu which goes to ubuntu.
I have no idea how could that happened on my computer.
This is only a single OS. I don't have windows xp on it, only ubuntu. I have search over internet but all have dual OS boot. :(

Could you guys help me to solve this problem? 

cheers

---

### Post by iaculallad on 2008-09-19
Make sure that your BIOS is configured to boot from your CDROM/DVDROM first before searching for other bootable devices.

---

### Post by blazzer on 2008-09-19
I did...

---

### Post by mcduck on 2008-09-19
Well, it BIOS is really set to boot from CD first, and you have bootable CD in the drive, it _will_ boot to the CD before loading Grub.

If it's not working for you, either your BIOS setting isn't correct or your CD isn't a bootable one.

---

### Post by blazzer on 2008-09-19
Yea..I have checked everything..
Even after memory checked it says 'Press any key for Boot CD' (or whatever is it)
after i press..it didn't recognize anything..but GRUB loading...
and then ubuntu is on...:confused:

---

### Post by Tatty on 2008-09-19
Its been a while but from memory doesnt that 'Press any key for Boot CD' get displayed by grub when it detects a bootable cd?

If so then that suggests it may be trying to boot from your hdd first.

Unless perhaps the CD is corrupted, in which case perhaps it simply cant boot from it.  Perhaps burn another cd at a slower speed, and check whether the md5 of the .iso is correct.

---

