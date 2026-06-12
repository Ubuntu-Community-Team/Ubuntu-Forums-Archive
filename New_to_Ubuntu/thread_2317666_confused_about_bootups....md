---
title: "confused about bootups..."
date: 2016-03-18
forum: New to Ubuntu
---

### Post by indicolts on 2016-03-18
Hello, I'm fairly new to Ubuntu, but so far I am liking what I see.  Once I am in, I have had no problems updating software, choosing my browser, using my email (with evolution), and experimenting with the different applications that are available.  However, I am a bit confused about what I am seeing during my computer's bootup procedure. I have an HP laptop with Windows 10 installed.  This is what I am seeing during bootup...

GNU GRUB version 2.01 beta 2-9ubuntu1.7


Ubuntu - (I can wait for the "countdown" or click on Ubuntu and it does load Ubuntu for me)
Advanced options for Ubuntu
Windows Boot Manager (on /dev/sda2) - (when I attempt to click on this, this is what I am seeing - reference ***)
System setup


*** /EndEntire 


file path: /ACPI (lots of hieroglyphics) then (cannot load image)


I then click on system setup for which I get:


F1 System Information
F2 System Diagnostics
F9 Boot Device Options - (ref ****)
F10 BIOS Setup
F11 System Recovery


ENTER - Continue Startup


**** Boot Manager


Boot Option Menu
OS boot Manager (UEFI) - ubuntu (TOSHIBA MQ01ABD100)
OS boot Manager (UEFI) - Windows Boot Manger (TOSHIBA MQ01ABD100)  (this is where I click in order to finally get into Windows when I want to)
Boot From EFI File

My question is, isn't there a less convoluted way to get into Windows when I want to?

thanks in advance!

---

### Post by grahammechanical on 2016-03-18
Grub is the Linux boot manager. It gives you an option to load either Ubuntu or Windows 10. Is Windows 10 not loading correctly? Your post does not make this clear. If Windows 10 is not loading correctly from the Grub menu then something is wrong.

The issue with dual booting Linux with Windows 10 is the need for both OS to be installed in the same mode. Windows 10 is usually installed in EFI mode and that means that Ubuntu must also be installed in EFI mode. But if Ubuntu is installed in BIOS/Legacy/CSM mode then that could be the cause of this problem and this convoluted way of loading Windows 10 is the best you get until the problem is rectified.

Regards.

---

### Post by Rocky_Bennett on 2016-03-18
I read your post several times and I am confused. Doesn't Windows 10 load when you scroll down to it and hit enter? If it does, then what is question?

---

### Post by indicolts on 2016-03-18
Sorry, I was afraid my post the way I wrote it may be confusing, here is what I see via Grub:

[COLOR=#000000]Ubuntu[/COLOR]
[COLOR=#000000]Advanced options for Ubuntu[/COLOR]
[COLOR=#000000]Windows Boot Manager (on /dev/sda2)[/COLOR]
[COLOR=#000000]System setup[/COLOR]

When I choose Ubuntu, it boots perfectly in to Ubuntu, when I choose the 3rd option (Windows Boot Manager (on /dev/sda2), that's when I run into an error.  So to ultimately boot into Windows, I have to go with the 4th option (System setup) and go from there.  Thank you.

---

### Post by indicolts on 2016-03-18
Hi and thank you for your reply, how would I find out if Ubuntu is installed in BIOS/Legacy/CSM mode?

---

### Post by indicolts on 2016-03-18
Just ran the following command in terminal ```
([ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD")
```

and got this result: ```
EFI boot on HDD
```

---

### Post by oldfred on 2016-03-20
Grub only boots working Windows.
Or Windows cannot need chkdsk nor be hibernated. And Windows 10 fast startup is always on hibernation.
You are directly booting Windows using the UEFI boot manager or menu using f9 which will boot Windows that is hibernated as that is a default Windows boot.
If only occasionally booting Windows, turn off fast start up and then you can boot from grub menu. Or you can boot either system from f9 UEFI boot menu. If not booting Windows from grub menu you can remove that, so it directly loads Ubuntu.

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by indicolts on 2016-04-07
Thanks! That answers my other question, how come when I boot into Windows from Ubuntu I see Windows load up like I never restarted the machine (apps that were up are still up). Of course when I shut the computer completely off and start Ubuntu, and then boot into Windows, Windows starts cold.

---

