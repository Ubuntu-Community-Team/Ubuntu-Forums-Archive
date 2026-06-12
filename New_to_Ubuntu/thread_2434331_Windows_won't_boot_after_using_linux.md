---
title: "Windows won't boot after using linux"
date: 2020-01-03
forum: New to Ubuntu
---

### Post by e-ser on 2020-01-03
I am new to Ubuntu and i booted it from a usb for the first time today.
Everything was working fine untill i shutdown Ubuntu intending to boot back up into windows 10 (which was pre-installed on my laptop)
When i tried to reboot windows it displayed text at the bottom of the screen that said something along the lines of repairing disk followed by diagnosing your computer then it displayed a blue screen with restore and repair options on it. I tried everyone and nothing worked.
So i then booted back up Ubuntu and used boot-repair on recommended which also didn't work.
It gave me this URL [http://paste.ubuntu.com/p/Kc63q7XmJy/](http://paste.ubuntu.com/p/Kc63q7XmJy/)
Help?



I have an Acer aspire laptop (usually) running Windows 10

---

### Post by yancek on 2020-01-03
You need to access the BIOS firmware on the computer and change the boot options to boot the windows boot manager since it is currently set to boot the USB on which the 'live' Ubuntu installer exists.  Since you are using an Acer, you will probably need to access the BIOS and set a supervisor password so that you can enable trust if you wish to install another OS.  The key needed to access boot options and/or BIOS firmware should show on screen when initially booting.  Boot repair is basically used to repair Linux boot problems and all you have is windows.

---

### Post by e-ser on 2020-01-03
i have moved priority to windows in BIOS or Ubuntu would have just booted again

---

### Post by e-ser on 2020-01-03
[IMG]https://photos.app.goo.gl/Gvmd2Ej9N1Z3eGbw7[/IMG]

---

### Post by yancek on 2020-01-04
In order to boot Ubuntu from the usb, you needed to change the boot priority in the BIOS  In order to go back to booting the OS installed on the drive of the computer, you simply change the boot options back to their original.  Booting a system from a USB or DVD isn't going to do anything to the installed OS.  Of course, the user can generally access the installed system and make changes unknowingly if they are not familiar with the system.  The point here being that simply booting an OS from a usb is not going to change/damage anything in and of itself.  Obviously, you have not installed Ubuntu but just used the live version so not knowing what you did while using it, we can't be much help.

Given your current situation, it would be imperative to actually get the specific messages you get on attempting to reboot windows 10 that you referred to in your original post.  I think you would be better off trying a windows forum or the microsoft support site.

---

