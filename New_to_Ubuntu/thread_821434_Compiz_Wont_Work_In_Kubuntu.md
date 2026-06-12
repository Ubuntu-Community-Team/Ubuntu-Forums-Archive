---
title: "Compiz Wont Work In Kubuntu"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by cafeinoz on 2008-06-07
I have tried everything. I use a Compaq Presario C700 Laptop with the RAM upgraded to 2GB. By Kubuntu I mean KDE installed in Ubuntu as well as Gnome.:confused:

---

### Post by philinux on 2008-06-07
So it works in gnome but not the kde desktop environment.

Whats the graphics card?

Is it KDE 4 or 3?

---

### Post by Stefanie on 2008-06-07
have you tried running compiz --replace in the terminal? i have to do this in KDE but not in gnome.

---

### Post by cafeinoz on 2008-06-07
I'm new to Kubuntu so could you tell me how to check if its KDE 3 or 4.

---

### Post by philinux on 2008-06-07
> **cafeinoz said:**
> I'm new to Kubuntu so could you tell me how to check if its KDE 3 or 4.

Did you try compiz --replace like Stephanie said.

To check look in synaptic see what you installed.
Just click any app the type kde it will go straight to it.

---

### Post by cafeinoz on 2008-06-07
Thanks Stefanie but now the window decoration is the same as in Gnome. Do you know the command that I have to put in compiz. What is the Kubuntu window decorator and does Emerald have something to do with it?

---

### Post by philinux on 2008-06-07
> **cafeinoz said:**
> Thanks Stefanie but now the window decoration is the same as in Gnome. Do you know the command that I have to put in compiz. What is the Kubuntu window decorator and does Emerald have something to do with it?

Have you got the menu item 

System>Prefs >Advanced Desktop effects.

If not install from synaptic compizconfig-settings-manager
or sudo apt-get install compizconfig-settings-manager

---

### Post by cafeinoz on 2008-06-07
I have access to it but i don't know how to put the KDE theme back on.

---

### Post by Stefanie on 2008-06-07
> **cafeinoz said:**
> Thanks Stefanie but now the window decoration is the same as in Gnome. Do you know the command that I have to put in compiz. What is the Kubuntu window decorator and does Emerald have something to do with it?

does compiz work now? to get the cube you have to change some settings in the advanced desktop effects manager (under general options, go to the tab Desktop and set horizontal virtual size to 4) 

i also noticed that running compiz --replace enables both compiz and emerald, but that didn't really bother me. if you want to enable the kde window borders maybe kde-window-decorator --replace will work?

---

### Post by philinux on 2008-06-07
This link might be useful
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by cafeinoz on 2008-06-07
I tried it and it said this:

username@username-laptop:~$ kde-window-decorator --replace
The program 'kde-window-decorator' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-kde
bash: kde-window-decorator: command not found
username@username-laptop:~$ sudo apt-get install compiz-kde
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package compiz-kde

---

### Post by cafeinoz on 2008-06-07
Thanks for the help. I have to choose between effects and emerald or nothing so do you know where I can get a KDE emerald theme.

---

### Post by radagast1155 on 2008-06-17
If you have an ATI card you might have to use restricted software. Connect to the internet and go through the menu to Hardware Drivers Manager in the System set on the KDE menu and click next to your Graphics Card if its there. You can also get your wireless working this way too!

---

### Post by radagast1155 on 2008-06-17
[www.kde-look.org](www.kde-look.org)

---

