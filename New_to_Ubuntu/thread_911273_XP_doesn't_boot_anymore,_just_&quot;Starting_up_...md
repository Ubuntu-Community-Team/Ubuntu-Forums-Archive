---
title: "XP doesn't boot anymore, just &quot;Starting up ...&quot;"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by NoplaN on 2008-09-05
Hello,

I just installed Ubuntu for the first time, and now if I want to boot XP via GRUB, it just shows: "Starting up..." .


I'd be happy if you could help me.

With best regards,

NoplaN

---

### Post by cariboo on 2008-09-05
In a Applications-->Accessories-->Termianl type:

```
sudo fdisk -l
```

Then post the output in your next post.

Jim

---

### Post by NoplaN on 2008-09-05
There are some german words in it, because I am german, but I think you'll understand it.

```
Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x75d58714

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       24100   193583218+   7  HPFS/NTFS
/dev/sda2           24101       28876    38357488    f  W95 Erw. (LBA)
Partition 2 endet nicht an einer Zylindergrenze.
/dev/sda3           28876       30402    12256723+   7  HPFS/NTFS
Partition 3 endet nicht an einer Zylindergrenze.
/dev/sda5           25657       28876    25855168+   7  HPFS/NTFS
/dev/sda6           24101       25585    11928199+  83  Linux
/dev/sda7           25586       25656      570276   82  Linux Swap / Solaris

```

---

### Post by tuxulin on 2008-09-05
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Tuxulin

---

### Post by NoplaN on 2008-09-05
> **tuxulin said:**
> [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Tuxulin

I already found that on google, but it doesn't really help me...

---

### Post by LowSky on 2008-09-05
in grub choose windows to boot then hit F8 as quick as possible and see if you can boot into windows safe mode.

---

### Post by NoplaN on 2008-09-05
Okay I'll try that out now.

Uhm, I changed something in my /boot/grub/menu.lst , could you tell me how my Windows XP entry should look like? Because now I get some kind of error because I changed something I shouldn't have done there.

Currently it's:

```
title Windows XP Pro
map   (hd1,0)(hd0,0)
map   (hd0,0)(hd1,0)
root   (hd1,0)
makeactive
chainloader +1
```

---

### Post by NoplaN on 2008-09-05
Sry for doublepost, otherwise I wouldn't get any attention.

Pressing F8 didn't work because of: "Error 11: Unrecognized device string", but that's because I changed something on that Windows entry in menu.lst.

---

### Post by Irihapeti on 2008-09-05
Try this:

```
title Windows XP Pro
rootnoverify   (hd0,0)
chainloader +1

```

---

### Post by NoplaN on 2008-09-05
Still just the "Starting up..." and no chance to press F8.

---

### Post by Irihapeti on 2008-09-05
Sounds to me like a problem with XP itself rather than GRUB. Do you have the original disks so that you could do a system repair?

I've never run XP so I can't help any further, sorry. Hopefully someone else can help.

---

### Post by NoplaN on 2008-09-05
> **Irihapeti said:**
> Sounds to me like a problem with XP itself rather than GRUB. Do you have the original disks so that you could do a system repair?

I've never run XP so I can't help any further, sorry. Hopefully someone else can help.

I'd have to get the original CD from a friend, that's not a problem, then I'd fix the boot manager of XP, but I think/hope there is another solution, because I read on other forums about people who had the same problem and fixed it with their menu.lst Windows XP entry.

---

### Post by caljohnsmith on 2008-09-05
When you are in Ubuntu, can you mount the Windows partition sda1 OK, and see all your files? If you can, do you have the following three files in your Windows root directory:
```
boot.ini
NTDETECT.COM
ntldr
```
Also, if you can get your Windows CD from your friend, it would be good to run a "chkdsk /r" and then "fixboot".

---

### Post by NoplaN on 2008-09-05
Files are there just boot.ini isn't.

---

### Post by caljohnsmith on 2008-09-05
Ok, I attached a boot.ini file to this message that should work for you; just save it in your Windows root directory, reboot, and let us know what happens on start up.

---

### Post by NoplaN on 2008-09-05
Still the same problem, but thanks.

---

### Post by caljohnsmith on 2008-09-05
If you can then, I would run "chkdsk /r" on your Windows partition, and it won't hurt to make sure the boot sector is OK by running "fixboot".

---

### Post by NoplaN on 2008-09-05
> **caljohnsmith said:**
> If you can then, I would run "chkdsk /r" on your Windows partition, and it won't hurt to make sure the boot sector is OK by running "fixboot".

I'm unable to anything except booting Ubuntu.

---

