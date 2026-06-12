---
title: "Ubuntu noobie here"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by rolldawg on 2012-03-31
Hey there guys! Just installed ubuntu 11 :D. Cant wait to learn how to use this thing w/ windows 7. Anyways, I cant find nor google this particular question in my head. How do you stop the choose "what to boot" option when my laptop starts up? I want my laptop to continue normally booting up to the login screen which then i want to choose whether to boot my windows accounts or linux account. Much help would be appreciated. @_@ Thanks! :D

---

### Post by roger_1960 on 2012-03-31
Hi

The login screen is particular to the operating system (OS).  You have to choose the OS before you login.  You could have a different login for each OS (but not a good plan really on the same machine)

---

### Post by lisati on 2012-03-31
I think the OP was referring to the Grub menu. Some information can be found here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/DualBoot/Grub](https://help.ubuntu.com/community/DualBoot/Grub)

---

### Post by santosh83 on 2012-03-31
> **rolldawg said:**
> Hey there guys! Just installed ubuntu 11 :D. Cant wait to learn how to use this thing w/ windows 7. Anyways, I cant find nor google this particular question in my head. How do you stop the choose "what to boot" option when my laptop starts up? I want my laptop to continue normally booting up to the login screen which then i want to choose whether to boot my windows accounts or linux account. Much help would be appreciated. @_@ Thanks! :D

Hi,

By login screen do you mean the screen which asks for your user account name and password, allowing you to load your desktop?

If so, this is something that happens LONG (in computer terms) after an operating system (Windows 7 or Ubuntu in this case) has ALREADY STARTED! So login screen is specific to each system. From the Windows login screen you can only login to Windows accounts and from the Linux login screen you can only login to your Linux accounts.

You can choose which OS to boot soon after your computer is powered-up at the so-called 'bootloader' menu. In this case I think Grub would've been installed as bootloader as a normal part of your Ubuntu install, and it should show you a menu listing all operating system you've installed in your machine.

Hope this helps!

---

### Post by lisati on 2012-03-31
Ah yes, I think I see now.

As santosh83 point out, the menu to choose between Windows and Ubuntu happens BEFORE the login screen appears, and is controlled by Grub (the bootloader)

---

### Post by rolldawg on 2012-03-31
Thanks for the fast reply guys. Good to know that we have a friendly community. :D

And yes sorry for my misleading post, but you all got what i wanted to know. :D

Grub? maybe. Gonna do heavy research on that, i just did some light research - it gives me a dos like feature. Not what i wanted but close enough.

Is it possible to do what you guys said? After computer starts up, then choose an OS using windows logon screen and the user accounts accustomed to the OSs'? (similar to bootcamp on macs wanting to run windows)

---

### Post by zombifier25 on 2012-03-31
Linux and Windows are 2 different operating systems, and thus uses 2 different login screens that is only started when the OS start.
(I think you can install a Windows-lookalike theme for Burg... dunno if one exists though. ignore this if you don't know what's Burg)

---

### Post by santosh83 on 2012-03-31
> **rolldawg said:**
> Thanks for the fast reply guys. Good to know that we have a friendly community. :D

And yes sorry for my misleading post, but you all got what i wanted to know. :D

Grub? maybe. Gonna do heavy research on that, i just did some light research - it gives me a dos like feature. Not what i wanted but close enough.

Is it possible to do what you guys said? After computer starts up, then choose an OS using windows logon screen and the user accounts accustomed to the OSs'? (similar to bootcamp on macs wanting to run windows)

It may not be possible to do exactly what you want but check out WUBI:
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Although I've never used it, I think this allows you to 'start' Linux from WITHIN your Windows desktop just like another application (though after it's started, Windows will be temporarily suspended until you've finished with Linux I believe.)

Other than this, you can use a virtualisation program like VirtualBox or VMWare to run both Windows and Linux (and many other OS) side-by-side, as and when needed.

---

### Post by santosh83 on 2012-03-31
> **santosh83 said:**
> It may not be possible to do exactly what you want but check out WUBI:
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Although I've never used it, I think this allows you to 'start' Linux from WITHIN your Windows desktop just like another application (though after it's started, Windows will be temporarily suspended until you've finished with Linux I believe.)

Other than this, you can use a virtualisation program like VirtualBox or VMWare to run both Windows and Linux (and many other OS) side-by-side, as and when needed.

Hi,

What I said regarding WUBI above is somewhat incorrect. Although it will allow you to INSTALL/UNINSTALL Ubuntu from within your Windows (like another Windows app), eliminating the need to repartition your disk, you'll still be presented with the same GRUB bootloader menu and will have to choose which OS to start much before you get to any login screen!

Do check out
[http://www.andlinux.org/](http://www.andlinux.org/)
and
[http://www.colinux.org/](http://www.colinux.org/)
though. These projects DO aim to get Linux running inside (or alongside?) Windows, but I don't think are suitable for newbie use quite yet. You might be better off with traditional virtualisation (VirtualBox/VMWare) or WUBI or the normal separately partitioned install you already done presumably.

---

