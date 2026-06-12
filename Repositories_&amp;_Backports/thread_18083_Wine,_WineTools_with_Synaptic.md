---
title: "Wine, WineTools with Synaptic?"
date: 2005-03-04
forum: Repositories &amp; Backports
---

### Post by Mike Pacasi on 2005-03-04
Hello all,

I'm trying install Wine and WineTools using the Synaptic package manager. I've tryed to use wine.sourceforge.net repositories. Wine installed fine (only the last version was allowable) but  Synapic fails with WineTools with a "Lack-of-Xdialog" error. 

So, is it possible to do this task using the Ubuntu repositories or alternative ones? If not, how to install specific versions of Wine and WineTools (for instance Wine 20041019 and the compatible WineTools wt207jo-wt211jo) according to recomendations of the WineTools developer?

I just need wine working on Ubuntu!
Tanks for any help! :-)

Mike P.

---

### Post by bored2k on 2005-03-04
go to settings> repoS [synaptic
and check every single on


then search wine and happy "whining" :P

---

### Post by Mike Pacasi on 2005-03-04
Thanks! I also have followed the instructions of the Ubuntu 4.10 Starter Guide on "How to add extra repositories?", and the newest Wine version 20050211-1, plus WineTools 2.1.0-1 have been installed and are running without problems. This new version of WineTools is very friendly: It installs a good wine configuration file (probably with a lot of previous tweaks), create a new fake windows drive (mandatory!), installs DCOM98, IE-6-SP1, true-type fonts, Windows printers, and a lot of additional utility software (if you are connected to the Web), and also MS Office and many other MS software if you have the corresponding CD-Roms.  In fact I still have some questions:
1- During the installation of Wine/WineTools, the correct identification of my CD-ROM-1 device on Ubuntu Linux (drive D: on my former XP) has been requested. I just confirmed what the installer sugested to me (from my Ubuntu configuration file) and the CD-Rom is not working on Wine (I can't install any WIN SW from my CD-rom). How to check for the correct name of the CD-Rom allowing Wine to directly access my actual CD-Rom, and how (where) to edit the Wine config file?
2- Using WineTools, I've installed several windows software like Acrobat Reader, Internet Explorer, etc. BUT neither Ubuntu nor WineTools placed the corresponding icons or folders in the Gnome applications menu or even on the desktop as links allowing easy starting of the applications. This means that I will need to search for the placements of each executable file and run them manualy by the names using the command line?

Thank you very much for the help.

Mike P.

---

### Post by Mike Pacasi on 2005-03-06
Hello All,

For those following this thread I would like to inform that I've found a way to add new items (of new installed Linux or Wine programs) to each one of the main menu itens of the Gnome Start (or Applications, that small foot at the tool bar corner):
1- Install the program using Synaptic, apt-get (command line) or Wine/WineTools;
2- After installation, check if the corresponding menu (internet, system, accessories, multimedia, etc.) or sub-menu (the a.m. installed program) item has been automatically created by Gnome. I don't know why, but some of the programs will have  installed its menu or sub-menu item automatically;
3-  If you don't find the a.m. created sub-menu item, chose a menu item among those existing ones, when the sub-menu window opens, right click on any sub-item, point to probably the lower option ("whole menu"), and left click on the option "add new item to this menu". A sub-menu configuration window will open: at least fullfill a name for the recently installed application, inform the command name (add the path if necessary), click on the icon buttom and choose one, mark the check box informing if the application shall execute in a terminal. Click "OK" when it's done.
4- You should now find the new sub-menu option for launching your new application.

Notes: a) I don't now how to create/organize additional MAIN menu items, only sub-menus as I described abobe. It seems that Gnome creates it automatically based on the tipe of application you install. For example, when I've installed Blue-Fish using Synaptic, there was no "Development" main menu item created on my Gnome "start", and I manually created it in the existing System main menu item as a.m.. For my surprise, after restarting gnome after a normal shut-down of my PC, I've found the new menu item "Development" with only my recent installed Blue-Fish in it! I don't know if Gnome just imitated my previous steps!?  
b) For the KDE Desktop, the a.m. process is much more transparent, because its is easy to localize the corresponding menu and desktop configuration files.

I still don't know how to correct (change) the configuration of the value of my CD-ROM drive on WINE/WineTools. At least I've found that the correct value to be informed to wine for direct access is: /dev/hdc (according to Gnome Device Manager), and not /mnt/cdrom which actually  is not working.

Any help?

Mike P.

---

### Post by Mike Pacasi on 2005-03-10
Hello my friends!

For those following this thread, here I am again  ;-)

Ok, I've found other easy ways to edit start menu items, for KDE and GNOME:

1- KDE: Just use the intuitive program kmenuedit:

$ kmenuedit                              (for  locally installed programs, menus and icons, as "user")

OR

$ sudo kmenuedit                     (for globally installed programs, menus and icons, as root, or sudo)

Off course you can get the kmenuedit program if needed:

$ sudo apt-get install kmenuedit

2- GNOME: Just use the nautilus start menu editing commands:
(see also Ubuntu Starter Guide)
For example, installing qtparted and configuring the corresponding start menu items:

   2.1.
      $ sudo apt-get install qtparted
      $ nautilus applications:///System

   2.2. File Browser: System Tools

      Remove the existing QTParted Icon

      File Menu -> Create Launcher
      Basic Tab ->
      Name: QTParted
      Command: gksudo qtparted
      Icon: /usr/share/pixmaps/qtparted.xpm

   2.3. Read How to restart GNOME without rebooting computer?
   2.4. Applications -> System Tools -> QTParted

Mike P.  
The newbie on learning... :-)

---

