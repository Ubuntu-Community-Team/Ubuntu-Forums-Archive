---
title: "Changing brightness"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by hfsb on 2014-09-29
Hi!

I'm new at Linux. I decided to leave Windows and try Lubuntu because I only do basic stuff in the computer (listen music, watch movies, browsergames, text, and other basic things).

I'm enjoying my new OS, however I have a doubt. How can I change the brightness of my laptop? Is there any easy way to do that? My fn keys aren't working.

Thank you :)

---

### Post by ajgreeny on 2014-09-29
It is difficult to know what to suggest without more hardware info but have a look at [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

---

### Post by hfsb on 2014-09-29
My graphic card is an Intel (**acpi_video0  intel_backlight**).

I was able to use this command (**sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf**) but when I used the second one (**sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf**), I got this message: **sudo: gedit: command not found**

---

### Post by christopher9 on 2014-09-29
Install GEdit.

---

### Post by ajgreeny on 2014-09-29
In Lubuntu you will need to use ```
gksudo leafpad
``` for now, though it may change in the future.  Gedit is the text editor for gnome including unity; Lubuntu uses leafpad.

You should never use **sudo** for a GUI application, it is for command line applications only; for GUI aplications it should to be **gksudo**, which can still be used though you will have to install **gksu** first, as it is not installed by default.

---

### Post by irv on 2014-09-29
Watch this little video, Looks like you need to click on the little sun icon to open up the setting for brightness. 
[https://www.youtube.com/watch?v=hYLZdYWSsIs]("https://www.youtube.com/watch?v=hYLZdYWSsIs")

---

### Post by hfsb on 2014-09-29
> **ajgreeny said:**
> In Lubuntu you will need to use ```
gksudo leafpad
``` for now, though it may change in the future.  Gedit is the text editor for gnome including unity; Lubuntu uses leafpad.

You should never use **sudo** for a GUI application, it is for command line applications only; for GUI aplications it should to be **gksudo**, which can still be used though you will have to install **gksu** first, as it is not installed by default.

How can I install gksu? Thanks.

> **irv said:**
> Watch this little video, Looks like you need to click on the little sun icon to open up the setting for brightness. 
[https://www.youtube.com/watch?v=hYLZdYWSsIs](https://www.youtube.com/watch?v=hYLZdYWSsIs)

I've tried that too. I can do everything except this:

[FONT=monospace]mv Controle\ de\ brilho.desktop /home/ocelot/.local/share/applications

Error:
[/FONT]mv: impossível mover «Controle de brilho.desktop» para «/home/ocelot/.local/share/applications»: Ficheiro ou directoria inexistente (it's in Portuguese)

---

### Post by hfsb on 2014-09-29
I managed to get it working. I noticed that the command had an error. When it shows ocelot, we must put our computer name. I have more questions about Office 2010 in Ubuntu and about my Epson Stylus SX105. Can I post my questions here, or is it better if I open another topic?

Thanks!

---

### Post by Vladlenin5000 on 2014-09-29
A new thread for the printer in the hardware section might be a good idea but only if it doesn't work "plug&play". If not then you have a problem: There are no proprietary drivers for SX105 that I know of. However, the vast majority of Epson printers contemporary to SX105 just work natively in Ubuntu. If you're having difficulties there are very knowledgeable users in the hardware section.

Regarding Microsoft Office 2010, nothing to worry. It can be installed with a compatibility layer - WINE - and the platinum rating (check link below) is very promising (software rated anything less than gold often doesn't work acceptably). WINE, the (Windows) compatibility layer, is often referred to as "emulator" - it actually isn't - so I think you get the picture...
However...
There's a much more important question here: Do you really want/need to? There are many good alternative, free and open source Office Suites and Ubuntu already comes with the basic LibreOffice Writer (=Word), Calc (=Excel) and Impress (=Powerpoint). Just add Draw, Math and Base and you have a full featured Office Suite with similar functionality. 
There's a also a brilliant closed source basic Office Suite developed in China by Kingsoft since 1988, free and runs in Linux, especially Ubuntu. It has the highest compatibility rate with the newer Microsoft's proprietary formats. If you don't mind the "dark side" of using proprietary closed source - many Linux purist do - WPS is the best Office solution for everyday use and free, but free as in "free beer" only.

[https://appdb.winehq.org/objectManager.php?sClass=version&iId=17336](https://appdb.winehq.org/objectManager.php?sClass=version&iId=17336)

---

### Post by hfsb on 2014-09-29
> **Vladlenin5000 said:**
> A new thread for the printer in the hardware section might be a good idea but only if it doesn't work "plug&play". If not then you have a problem: There are no proprietary drivers for SX105 that I know of. However, the vast majority of Epson printers contemporary to SX105 just work natively in Ubuntu. If you're having difficulties there are very knowledgeable users in the hardware section.

Regarding Microsoft Office 2010, nothing to worry. It can be installed with a compatibility layer - WINE - and the platinum rating (check link below) is very promising (software rated anything less than gold often doesn't work acceptably). WINE, the (Windows) compatibility layer, is often referred to as "emulator" - it actually isn't - so I think you get the picture...
However...
There's a much more important question here: Do you really want/need to? There are many good alternative, free and open source Office Suites and Ubuntu already comes with the basic LibreOffice Writer (=Word), Calc (=Excel) and Impress (=Powerpoint). Just add Draw, Math and Base and you have a full featured Office Suite with similar functionality. 
There's a also a brilliant closed source basic Office Suite developed in China by Kingsoft since 1988, free and runs in Linux, especially Ubuntu. It has the highest compatibility rate with the newer Microsoft's proprietary formats. If you don't mind the "dark side" of using proprietary closed source - many Linux purist do - WPS is the best Office solution for everyday use and free, but free as in "free beer" only.

[https://appdb.winehq.org/objectManager.php?sClass=version&iId=17336](https://appdb.winehq.org/objectManager.php?sClass=version&iId=17336)

Thanks.

My printer works fine. I can print and scan, however I would like to have a monitor to check the ink level and the option to change the cartridge, etc. 

In relation to Office 2010, I managed to get it installed and working using playonlinux. However, I would like to install a spell check update that was released for my country/language (PT-PT) and I'm having difficulties doing that. I've downloaded the update/hotfix from microsoft, but I can't install using WINE. I get a message saying something like this: there is no software that can be affected by this update.

---

### Post by Vladlenin5000 on 2014-09-29
Perhaps a new thread about the printer - in hardware - gives some results but I doubt you can have it better than what you already have. It's worth trying though...

> **hfsb said:**
> In relation to Office 2010, I managed to get it installed and working using playonlinux. However, I would like to install a spell check update that was released for my country/language (PT-PT) and I'm having difficulties doing that. I've downloaded the update/hotfix from microsoft, but I can't install using WINE. I get a message saying something like this: there is no software that can be affected by this update.

The last time I installed MS Office was a long time ago and was with the help of Codeweavers Crossover, a commercial WINE implementation that works notoriously better than PlayOnLinux, therefore I have no experience with the latter. However, same principles applies: Windows apps are installed in containers and any addon must be installed in the same container as the main program. If you installed with PlyOnLinux then you need to use it again and explicitly select the same container.

---

### Post by ajgreeny on 2014-09-30
The mtink package which is in the repos may help with ink levels of your printer, though it can be a devil to set up sometimes and will require you to add yourself to one or more groups.

I used to use it when I had an epson printer and it was very good once I got it working properly.

---

