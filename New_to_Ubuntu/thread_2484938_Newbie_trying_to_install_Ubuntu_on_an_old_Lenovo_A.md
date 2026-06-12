---
title: "Newbie trying to install Ubuntu on an old Lenovo All-in-One"
date: 2023-03-14
forum: New to Ubuntu
---

### Post by frpd1995 on 2023-03-14
Hello there, I'm relatevly new woking with Ubuntu. Recently I installed it in my main PC and it has been working wonderfully. But now I'm having issues installing Ubuntu on an older pc. This time is an All-In-One from Lenovo from 2011. Yeah I know is old but I still works and it does have still a Windows 10 on it working just fine. Now, the issue I'm having is that for some reason no matter what formatting I try, the boot menu to install is always saying the message "error file /boo/ not found" and "can't find command  grub_platform". If I try the option to install Ubuntu, it does load the beggining screen but after some loading a massive message of info that I admit cannot understand fully appears, with the final message being "Failed to start snap daemon.y  coller and submit kernell signatures..."

I searched around to see if this is a common problem, noting that maybe is an issue of UEFI not neing supported or that the pen drive I used needed to be converted to MBR which I did do with Gparted, but still the issue remains which Is a shame since I do want to just delete Windows10 on that PC to use pure Ubuntu (since this PC is connected to a TV for pure entertainment purposes)

Anything I should check around to make this work properly? Sorry in advanced if I sound like a total noob about this, because I'm haha

Images of the screen in question:

---

### Post by SeijiSensei on 2023-03-14
I'd create the USB installation image on the other machine that's running Linux. On vanilla Ubuntu, run
```
sudo apt install usb-creator-gtk
```
If you can't find its icon, you can run it from the terminal by typing "usb-creator-gtk". (If you run Kubuntu, use usb-creator-kde instead.)

If you want to convert the entire machine to Ubuntu, choose the option during installation to erase the disk and dedicate it all to Ubuntu.

---

### Post by tea for one on 2023-03-15
Second screenshot:-
Windows ntfs partition is in unsafe state.

Please boot into Windows 10 and poweroff/shutdown without hibernating.
While you are there, disable Bitlocker if it is enabled.

Finally, as your PC is 12 years old, a lighter flavour of the Ubuntu family may be more suitable i.e. Xubuntu or Lubuntu?

---

### Post by frpd1995 on 2023-03-16
Thanks guys! I managed to do it! And yeah , the USB formatting had to be done in Ubuntu in my regular PC rather than in WIndows. SIlly me for still using that to flash the USB. Just to be sure at first, I installed lubuntu instead while deleting Windows completly. After that I tested Ubuntu and it went perfect on the machine so now everything works wonders. Thank you again for the help [CENTER][COLOR=#E8E6E3]\\:D/[/COLOR][/CENTER]

---

