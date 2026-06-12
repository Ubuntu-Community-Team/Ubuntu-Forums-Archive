---
title: "Cannot create Bootable usb for ubuntu-12.04.4-desktop-i386"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by Rasmsingh on 2014-03-09
[COLOR=#070F14][FONT=Verdana]Hello, Iam new to this form I tried creating bootable usb stick using, [/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]
universal usb installer[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]unetbooting[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]linux live usb installer softwares[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]but after finishing Iwhen iam trying to reboot my system with my usb all it is saying is boot error.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Can anyone help me please?[/FONT][/COLOR]:(

---

### Post by marco-parillo on 2014-03-09
I have never had a problem with unetbootin.
Have you checked your download for errors?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Rasmsingh on 2014-03-09
Hi Marco- Parillo
I have checkedmy download for errors, but there are no errors check sums are same.

---

### Post by marco-parillo on 2014-03-09
OK, next two questions:
 - You are running the older BIOS, not the newer UEFI, right? Otherwise, I would check out: **[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)**
 - Your BIOS can boot from a USB? In fact, I put the USB first in the boot sequence.

---

### Post by Rasmsingh on 2014-03-10
Hi Marco-Parillo,
I dont know about my BIOS, My system is Sony Vaio E Series, with i3 processor, 3gb ram etc.,
and Yes my bios can boot from USB, and kept USB as the first boot sequence.

---

### Post by sudodus on 2014-03-10
It could be many different problems:

- bad USB pendrive (maybe good for storage but bad for booting)
- bad installation
- bad USB port - try all ports on the computer. Try with and without USB hub.
- bad combination of computer and pendrive

Please specify the computer

- brand name and model
- CPU
- RAM
- graphics chip/card
- wifi chip/card

and please specify your USB drive (pendrive or hard disk drive)

and if you have BIOS or UEFI. Please check when booting, what hotkey to press in order to enter the BIOS or UEFI menus, go there and check:-)
It will be much easier to help, when we know these things.

You can also read the following wiki pages / tutorials to get some tips

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")
[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")
[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

---

### Post by opendevlite on 2014-03-10
when you format your usb flash stick, try to format it to FAT or FAT32, give it a try on both, start with FAT then burn the ubuntu image to the USB flash stick

---

