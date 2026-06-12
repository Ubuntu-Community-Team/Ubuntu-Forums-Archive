---
title: "Login screen missing"
date: 2016-10-23
forum: New to Ubuntu
---

### Post by eeyoresowl on 2016-10-23
I installed lubuntu 14.04.5 (LTS) for my Odroid xu4 with the MATE desktop. The installation seemed to go perfectly, with no obvious issues. When I boot my system, I do not get a login screen (I have created a user - johnny), and the system automatically boots into root.. How do I configure my system so that I get a login splash screen upon startup?

When I choose "switch user" or "logout," I get a blank screen, with a blinking cursor at the top left of the screen (which I cannot do anything with). All I know to do at that point is to pull the plug and restart - right into root again! I'm pretty sure these are related.

The system appears to use lightdm as a window manager - I'm used to gdm from other systems ... perhaps that's the issue?

Do I need to manually configure a splash screen?

Thanks.

John

---

### Post by ajgreeny on 2016-10-23
I know nothing about ordroid hardware, nor whether it has any major differences from the more normal PC hardware when it comes to installing Ubuntu, but it may be that you need to reinstall lightdm which may offer you some reconfiguration options.

Lightdm is a display manager, not a window manager, so it will not give you a GUI for the whole OS, but only a login-screen, so I do not think your problem is quite so simple as you suggest.

---

