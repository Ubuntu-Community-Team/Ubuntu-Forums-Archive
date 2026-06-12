---
title: "Compiz Comp-aint!"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by mwf on 2008-05-21
I am running Ubuntu 8.04. The first machine is an old Dell desktop, P4 with 512M of memory. The other is a Dell Inspiron 1501 with 2G of memory.

I installed Compiz on both machines using the package manager. That went well. However, when I try to change the desktop "look" to get something more than just the basic stuff, I get a message telling me that nothing is available.

What am I missing here? Is there something else I have to do? Yeah, the details are vague but I'm working at the school on a public computer (no internet at home for the last few days).

---

### Post by Inxsible on 2008-05-21
What graphics card do you have ? Are you sure if your card is not blacklisted?

Have you started compiz yet? Press Alt + F2 and type in ```
compiz --replace
```

If it does, have you installed compiz settings manager?```
sudo apt-get install compizconfig-settings-manager
``` That will give you a variety of plugins to play around with.

---

### Post by AstralliS on 2008-05-21
Do you have installed VGA drivers?

---

### Post by stchman on 2008-05-21
> **mwf said:**
> I am running Ubuntu 8.04. The first machine is an old Dell desktop, P4 with 512M of memory. The other is a Dell Inspiron 1501 with 2G of memory.

I installed Compiz on both machines using the package manager. That went well. However, when I try to change the desktop "look" to get something more than just the basic stuff, I get a message telling me that nothing is available.

What am I missing here? Is there something else I have to do? Yeah, the details are vague but I'm working at the school on a public computer (no internet at home for the last few days).

Compiz is installed by default on Hardy.  After I enbled the restricted driver on both my ATI and Nvidia machines Compiz worked just fine.

What kind of video card do you have?

---

### Post by CJ56 on 2008-05-21
Did you install compizconfig at the same time? That's the thing that appears in the System>Preferences menu & actually allows you to tweak Compiz -

---

### Post by mwf on 2008-05-22
All I loaded was the compiz stuff, I didn't actually start anything up. It is a bit odd as the package was not installed automatically when I installed Ubuntu. Hmmm.

I'll give the startup stuff a try tonight. Didn't know I had to do that.

Video cards: I know my laptop has ATI Radeon Xpress Series video, the desktop I'll have to check when I get home.

Restricted drivers? I have no idea, the install just worked and installed whatever it did! I assume I have VGA...? The display resolution is 1024x800 on the desktop and higher on the laptop.

I'll be back...

---

### Post by sailor2001 on 2008-05-22
> **mwf said:**
> All I loaded was the compiz stuff, I didn't actually start anything up. It is a bit odd as the package was not installed automatically when I installed Ubuntu. Hmmm.

I'll give the startup stuff a try tonight. Didn't know I had to do that.

Video cards: I know my laptop has ATI Radeon Xpress Series video, the desktop I'll have to check when I get home.

Restricted drivers? I have no idea, the install just worked and installed whatever it did! I assume I have VGA...? The display resolution is 1024x800 on the desktop and higher on the laptop.

I'll be back...

system/administration/hardware drivers

---

### Post by mwf on 2008-05-23
OK, here is a copy of what I tried last night:

mwfanelli@mwfanelli-desktop:~$ apropos compiz
compiz (1)           - OpenGL window and compositing manager
compiz.real (1)      - OpenGL window and compositing manager
gtk-window-decorator (1) - Compiz window decorator using the Gtk toolkit

mwfanelli@mwfanelli-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5446 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 

My first reaction is huh? This was the desktop, I'll try the laptop tonight.

---

### Post by stalkier on 2008-05-23
> **mwf said:**
> OK, here is a copy of what I tried last night:

mwfanelli@mwfanelli-desktop:~$ apropos compiz
compiz (1)           - OpenGL window and compositing manager
compiz.real (1)      - OpenGL window and compositing manager
gtk-window-decorator (1) - Compiz window decorator using the Gtk toolkit

mwfanelli@mwfanelli-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5446 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 

My first reaction is huh? This was the desktop, I'll try the laptop tonight.

Ok it looks as though you need to enable your restricted drivers. Do this via System - Administration - Hardware Drivers. You will need to restart. Then you need to install ccsm, emerald, and fusion-icon. Do this via Synaptic Package Manager and clicking search. Type in compiz. Make sure you have all of your repos checked just in case. After all these are installed you can click Applications - System Tools - Fusion-icon. Fusion-Icon will startup. Right Click the icon on the taskbar and then goto Select Window Decorator. Choose Emerald.

You will need to download and install some themes as none come pre installed.
[http://www.gnome-look.org/](http://www.gnome-look.org/)
[http://www.compiz-themes.org/](http://www.compiz-themes.org/)

After you get some themes downloaded open emerald via System - Preferences - Emerald. Click on import and then navigate to where you saved them. Then you should just click on the one you want to use. All of your effects etc can be enabled and customized via the Compiz Configuration Manager.

---

### Post by mwf on 2008-05-23
Cool! I'll give it a try when I get home.

---

### Post by wootah on 2008-05-23
Does anyone know why compizconfig-settings-manager is not installed by default? It seems like such an obvious choice to get a little more out of compiz-fusion...

Either way, mwf, check your output from fglrxinfo. Post results.

---

