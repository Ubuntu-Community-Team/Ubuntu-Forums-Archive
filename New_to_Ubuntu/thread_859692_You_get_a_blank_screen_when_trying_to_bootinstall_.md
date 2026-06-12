---
title: "You get a blank screen when trying to boot/install untu?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Pastortom on 2008-07-14
Hay Guis! It's me, you're favorite Pastor :D

I've just used 12 hours to try and install 2 different kinds of Ubuntu's as dual boot with my already installed Vista OS.. and let me tell you, it's been a GREAT and tiring adventure.. 

When I found this temporary solution I wanted to help everyone else on this forum with the same problem, so started posting solutions one thread at the time, but I guess it's better to make a new thread instead about the solution.. 

So here goes:

Does your computer freeze while trying to install Ubuntu Linux?

Do you begint to wonder if your computer is too crappy to handle Linux?

Have you started pulling your hair in frustration as you cant find help on the net?

Don't worry, the solution is most likely very simple.

ACPI=off

There, I said it.. I know it might not be the best way of solving the problem, but at least you get Linux booted up and ready to use.. 

You might also wanna add VGA=773 and "safe graphic mode" but I think ACPI=off is the main tag that will get you safely into Linux.. 

For those of you that are trying to install Ubuntu or any other kind of Linux and experience a blank screen/black screen or freezup after loading bar fills up, then this might be the best temporary solution for you.. You simply push F6 when youve booted up the disc and the Linux menu shows up, and you hook off for "ACPI=off" and push F4 for "Safe Graphic Mode" and this should let you continue without freezing your computer or giving you a black/blank screen..  If your computer doesnt freeze, but only gives you a black screen you might wanna try Ctrl-Alt-"+" or Ctl-Alt-"-" to change between the video resolutions, or in worst case scenario manually type "VGA=773" at the end of the kernel line..

This has also proven to work after youve successfully installed linux, by manually editing the kernel line in Grub before activating the bootup of linux.

Hope this help the most of you noobs out there, as it sure as hell helped this noob!

---

