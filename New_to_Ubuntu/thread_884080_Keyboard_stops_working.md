---
title: "Keyboard stops working"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by coolnfunky_raj on 2008-08-08
Hi

I have been using ubuntu 8.04 for a while now in my Dell 1501. I have AMD 64 processor and 1 GB RAM. Sometimes, ubuntu just refuses to take the inputs from my kepboard. When I press Caps Lock, the light turns on, indicating its not a hardware problem. 
But ubuntu just doesnt recognize the keyboard inputs. The mouse works fine. 

The Applications menu, Places menu and System menu does not open either. So I have to hard reboot to get the keyboard working again. Is this a bug in Ubuntu? Everytime this has happened, I have had firefox open. But I cannot narrow the problem to firefox as I have firefox open most of the time anyway.

Has anyone encountered the same problem? Does anyone know of any fix?

Thanks
Raj

---

### Post by silkstone on 2008-08-08
Is it a PS/2 keyboard or USB?

I found PS/2 temperamental with Hardy although it worked OK with previous releases, but USB works fine.

---

### Post by LowSky on 2008-08-08
Dell 1501 is a notebook so its built in, most likely using a usb port
Seems like an odd problem. What i would do is run ubuntu in recovery mode and reset xorg.

Maybe delete the content of your .firefox folder

---

