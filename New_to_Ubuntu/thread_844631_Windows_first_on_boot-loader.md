---
title: "Windows first on boot-loader"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Seablue on 2008-06-29
Hi,

How do I put Windows Vista as the first item on the GRUB- Bootloader menu? I start up my computer a lot and use Windows more than Ubuntu. If I edit menu.lst and put Windows at the top, will I get any problems with Ubuntu Updates?

Thanks,
Seablue

---

### Post by Ub1476 on 2008-06-29
Check out this [thread]("http://ubuntuforums.org/showthread.php?p=2245129").

---

### Post by kansasnoob on 2008-06-29
You could just go to synaptic and install:

> startupmanager

It will then be in the Administration menu and you can select which OS to boot at startup:

[ATTACH]75756[/ATTACH]

---

### Post by NikS on 2008-06-29
Go to:
/boot/grub/menu.lst

Then in the file you'l find
**default		0**

Set it to the number your Vista is showed up in the list, usually 4.

U can also set the Time u get to select OS!!

**timeout		10**

Change the 10 to your desired time in seconds

---

### Post by Victormd on 2008-06-29
Another alternative is to set a savedefault. That way, it will always boot to the last "booted" OS.
```
sudo gedit /boot/grub/menu.lst
```
and where it reads **DEFAULT 0** replace the "0" with "saved" (no quotes), scroll down to where it reads:
> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
**savedefault**
and add the term in bold.

This is good because if you're in ubuntu and during an update you need to restart, you don't have to worry about the boot menu. The same goes for Windows. If you're in windows and need to restart, it will restart in windows.

---

### Post by NikS on 2008-06-30
> This is good because if you're in ubuntu and during an update you need to restart, you don't have to worry about the boot menu. The same goes for Windows. If you're in windows and need to restart, it will restart in windows.

Wow!!
Thats Great!!!:)

Thanks Victormd

---

### Post by stchman on 2008-06-30
> **Seablue said:**
> Hi,

How do I put Windows Vista as the first item on the GRUB- Bootloader menu? I start up my computer a lot and use Windows more than Ubuntu. If I edit menu.lst and put Windows at the top, will I get any problems with Ubuntu Updates?

Thanks,
Seablue

Yes, do not edit the menu.lst file.

---

### Post by mcduck on 2008-06-30
> **Seablue said:**
> Hi,

How do I put Windows Vista as the first item on the GRUB- Bootloader menu? I start up my computer a lot and use Windows more than Ubuntu. If I edit menu.lst and put Windows at the top, will I get any problems with Ubuntu Updates?

Thanks,
Seablue

If you move it above Ubuntu entries, and above the are marked as "debian automagick kernel list" everything will be just fine.

However if you put it inside the automagick area the entry will disappear during the next kerenel update, as the update rewrites this section of Grub.

---

### Post by Seablue on 2008-06-30
I already saved and edited the menu.lst :o

Will this have to change for the "Reboot automatically into same system" thing? Because this thread was really about how I could leave my computer without worry of my computer booting into Linux.

---

