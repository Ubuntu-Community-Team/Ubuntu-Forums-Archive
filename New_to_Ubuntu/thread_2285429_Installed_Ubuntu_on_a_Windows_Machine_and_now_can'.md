---
title: "Installed Ubuntu on a Windows Machine and now can't boot on Windows"
date: 2015-07-05
forum: New to Ubuntu
---

### Post by deepax on 2015-07-05
Hi all,

I am fairly new to Ubuntu so I needed a bit of help here.

I had Windows 7 running on my Sony vaio machine, and tried installing Ubuntu on it today. I was able to do installation (Point worth making: When I tried expanding Ubuntu partition initially, installation gave me error. However, when I went back a few steps and didn't change partition size, I was able to install Ubuntu. However, I did get a dialog box about something moving to sda2 (or something like that, I don't remember details of dialog box)).

Now, when I try to boot into Windows initially, the screen goes blank for 2 seconds and computer just reboots.

I am attaching report from boot-repair so that people can get an idea of what is happening: [http://paste.ubuntu.com/11828971/](http://paste.ubuntu.com/11828971/)

---

### Post by oldfred on 2015-07-05
Either you left your Windows in sda2 hibernated, or you did not run chkdsk after its resize which it should automatically do on reboot.
But you probably cannot get into Windows repair console with f8 when booting from grub as it is too quick.

Best to use your Windows repair flash drive or CD to run Windows repairs. Those cannot be done from Linux.

[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

Did you make this before starting?
       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by deepax on 2015-07-06
Hey oldfred, thanks for helping out.

Unfortunately, I didn't create the repair USB before Ubuntu installation. Can I use a bootable Win 7 Installation DVD or is it only possible via the repair USB?

Right now, priority for me is personal files on windows (it doesn't matter if I have to reinstall OS). I do have a SATA to USB interface. Do you think I can take my HDD out and it would show the windows files if I connect it as an external HDD to a different computer?

---

### Post by westie457 on 2015-07-06
> [COLOR=#000000]Can I use a bootable Win 7 Installation DVD or is it only possible via the repair USB?[/COLOR]

Yes you can. the installation DVD has repair functions built in.
Boot the DVD, at the install screen select 'Repair my computer' or something similar.
Try the Automatic repair first - it may or may not work. You will be informed of what is happening.

> [COLOR=#000000]Do you think I can take my HDD out and it would show the windows files if I connect it as an external HDD to a different computer?[/COLOR]

Probably no files will be shown until the MFT errors have been repaired.

Just ask when you need some more guidance.

---

