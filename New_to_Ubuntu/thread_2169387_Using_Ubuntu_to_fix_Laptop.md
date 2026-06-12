---
title: "Using Ubuntu to fix Laptop"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by chyngyz on 2013-08-21
Few days ago my laptop wasn't booting up properly , after hours and hours of trying to fix it , some one told me to use [FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif][COLOR=#000000]Ubuntu for a[/COLOR][/FONT][COLOR=#000000][FONT=verdana] factory reset on my laptop. Is this possible?[/FONT][/COLOR]

---

### Post by tgalati4 on 2013-08-21
It depends on what your problem is, but yes, generally Ubuntu has rescued many laptops.  What version of Windows do you have?  Describe what you see on the screen during boot.  Can you get into the BIOS of the computer?  The make and model of the laptop might help as well.

---

### Post by chyngyz on 2013-08-21
Windows 7 , i would have a black screen with a white dash or underscore and yes i could get into the BIOS.
LAptop is TOshiba Satellite L650

---

### Post by RadicaX on 2013-08-21
I have done it to save several. You can also use it to rescue files. You could format the windows partition if you have the install cds and just reinstall Windows 7 if you want. You could just dump it and go straight on the Ubuntu path. If you do not have a windows install cd... it could be tricky though. Someone else might give you more things to do with that. But when in doubt, buy a usb, store your family photos or work documents on it, and reformat. Just remember, if no install cds are with your os, you can kiss it goodbye if you reformat.

---

### Post by carl4926 on 2013-08-21
> **chyngyz said:**
> Few days ago my laptop wasn't booting up properly , after hours and hours of trying to fix it , some one told me to use [FONT=verdana][COLOR=#000000]Ubuntu for a[/COLOR][/FONT][COLOR=#000000][FONT=verdana] factory reset on my laptop. Is this possible?[/FONT][/COLOR]

If by 'Factory Reset' you mean as it was shipped. No

You can use gparted to do a basic file system check on your windows install
You can scan it for virus' but you would need to install software or use a Linux CD that has it installed.
You can copy your files off of windows to a safe backup location
You could install Ubuntu alongside windows and at least have a system that works!

---

### Post by chyngyz on 2013-08-21
I don't really need any files from my old computer so wiping my computer would be fine.

---

### Post by chyngyz on 2013-08-21
how could i format the whole windows cause i installed Ubuntu but can't get past the friggin underscore so i have go through the installation menu. any way of wiping my laptop from there?

---

### Post by carl4926 on 2013-08-22
When you run the installer
You will get to a part that looks like this: [https://dl.dropboxusercontent.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)
Look for the option to replace windows and select, then continue

---

### Post by chyngyz on 2013-08-22
I have boot from usb ubuntu, it looks different .

---

### Post by carl4926 on 2013-08-22
> **chyngyz said:**
> I have boot from usb ubuntu, it looks different .

Unlikely
I do all my installs from USB
What are the options you see?

---

### Post by chyngyz on 2013-08-22
wait what version do you have ?

---

### Post by chyngyz on 2013-08-22
Can you linkit ?

---

### Post by RadicaX on 2013-08-22
Can you show a screenshot of the installer for the options you have to select? I normally delete the other partitions and then then install Ubuntu.

---

### Post by chyngyz on 2013-08-22
[http://imgur.com/rYbEoII](http://imgur.com/rYbEoII)

---

### Post by chyngyz on 2013-08-22
ok i got to the something else menu.

---

### Post by RadicaX on 2013-08-22
Okay good. Now you just need to delete all of it and install Ubuntu and the swap partition.

---

### Post by chyngyz on 2013-08-22
how do you do that? sorry im bad with computers

---

### Post by chyngyz on 2013-08-22
can you send me a screen shot?

---

### Post by carl4926 on 2013-08-23
Look at this
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png)

Above the something else it should have an option to 'Replace Windows' or some such phrase...with a warning that it will erase everything and install Ubuntu...

---

### Post by RadicaX on 2013-08-23
> **carl4926 said:**
> Look at this
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png)

Above the something else it should have an option to 'Replace Windows' or some such phrase...with a warning that it will erase everything and install Ubuntu...

Looks like he beat me to it. Should be it. If it has Gparted on the items list, this lets you manually assign stuff. So all you would need is two partitions. (or three, but it is a bit tricky for that. ) But if you follow Carl's instructions, should be the easiest way of doing things. Just give us a moment once you get to a part you are stuck at when you ask for the help, might take a moment to reply.

---

