---
title: "Can't get XP to boot from GRUB"
date: 2015-04-14
forum: New to Ubuntu
---

### Post by liboicl2 on 2015-04-14
I am new to Ubuntu, but not new to Linux. I am a little rusty with Windows, though, as I left it behind long ago. I am setting up a computer for a friend who wishes to have Windows XP, Windows 8, and Linux installed. Windows 8 was on a disconnected drive while I installed XP on a new drive, with unformatted space reserved for Ubuntu. After both Windows versions were booting I installed Kubuntu, the choice of Ubuntu. Windows 8 boots fine, but grub fails to pick up Windows XP. I ran os-prober which returned
```
/dev/sdb2@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
```

I also ran boot-repair, which found XP, but still failed to add it to the boot menu. I tried adding in custom menu entries, but still could not get it to boot.
[http://paste.ubuntu.com/10822412/](http://paste.ubuntu.com/10822412/)

Thank you in advance.

---

### Post by dino99 on 2015-04-14
Xp might be dropped now, as there is no more updates/maintenance. Continuing with it its like opening the door to all viruses and spyers

---

### Post by liboicl2 on 2015-04-14
Thanks for your concern, but I still want to know how to boot it. The system is not planned to go online. Either way, the boot-repair log finds XP. Is there anyway to get this to work if it is dropped? Grub legacy?

---

### Post by liboicl2 on 2015-04-14
Also, I just figured out I can get to Windows XP by choosing the CD Drive as the boot device and letting the XP press any key to boot from CD time out.

---

### Post by liboicl2 on 2015-04-14
I feel like I have made some progress. Going off what I found out about the CD, I made a custom grub entry
```
menuentry "Windows XP x64" {
    exit
}
```
The first time I select it grub restarts. Upon selecting it again, Windows XP boots. Is there anyway to avoid having to select it a second time?

---

### Post by Vladlenin5000 on 2015-04-14
What you're trying to do is impossible. Here's why: It's a new machine with UEFI and both the factory installed Windows 8 and Ubuntu are installed in that mode (assuming both boot from grub, as you say). Old Windows XP cannot be installed in UEFI mode and that's why you had to use the CD hack, making the CD itself boot in UEFI mode then taking advantage of its own dumb bootloader.

PS - Why XP? Is it because your friend already owns a retail license? OEM licenses are tied to the machine where they were originally installed. You can't legally reuse those licenses. That said, the still supported and acceptably stable Windows 7 is a much smarter choice *and*, with the proper tweaks can also be installed in UEFI mode.

---

