---
title: "HOWTO: Customize Ubuntu A-Z"
date: 2008-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by sayakb on 2008-07-11
[FONT=trebuchet ms][SIZE=3][SIZE=5][COLOR=Sienna]Software you may need[/COLOR][/SIZE]
[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=trebuchet ms][SIZE=3] Let's start from scratch. This is what your screen looks like just after a clean install:[/SIZE][/FONT][SIZE=3][ATTACH]77297[/ATTACH] 
[/SIZE][FONT=trebuchet ms][SIZE=3]First, we would install everything necessary to do the customization job. I would be putting up terminal commands here. Using terminal commands is the simplest way to install packages/getting things done. Make sure you have the repositories enabled. To enable repositories:
[/SIZE][/FONT]
[LIST=1]
[*][FONT=trebuchet ms][SIZE=3]Goto **System->Administration->Software Sources**[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]Enter the password[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]Enable the first four checkboxes on the  **Software Sources **window[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]Click on the **Third Party Software **tab and check all entries[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]Click on the **Updates **tab and check **Important **and **Recommended** update sources.[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]Close the Software Sources window and press **Reload **button when prompted to.[/SIZE][/FONT][SIZE=3]
[/SIZE]
[/LIST]
[FONT=trebuchet ms][SIZE=3]Now, to start with, open a terminal: [/SIZE][/FONT][FONT=trebuchet ms][SIZE=3]**Application->Accessories->Termina**[/SIZE][/FONT][FONT=trebuchet ms][SIZE=3]**l**[/SIZE][/FONT][FONT=trebuchet ms][SIZE=3] and type in the following comman[/SIZE][/FONT][SIZE=3]d:

```
sudo apt-get install ubuntu-restricted-extras vlc compizconfig-settings-manager catfish audacious wine startupmanager firestarter thunderbird localepurge emerald rar unrar-free flashplugin-nonfree virtualbox-ose gparted xchat

```[/SIZE][SIZE=3][FONT=courier new][FONT=trebuchet ms][I]Users having a good idea about the linux packages can omit whatever packages they want to.

[/I][/FONT][FONT=trebuchet ms]The above command will install the following on your system:
[/FONT][/FONT][/SIZE]
[LIST]
[*][SIZE=3]Multimedia Codecs + A few extra plugins (*package: ubuntu-restricted-extras*)
[/SIZE]
[*][SIZE=3]The VLC Media Player (*package: vlc*)
[/SIZE]
[*][SIZE=3]Compiz Settings Manager (*package: compizconfig-settings-manager*)
[/SIZE]
[*][SIZE=3]Catfish Search Utility (*package: catfish*)
[/SIZE]
[*][SIZE=3]Audacious Music Player (*package: audacious*)
[/SIZE]
[*][SIZE=3]Wine -- Windows Emulator (*package: wine*)
[/SIZE]
[*][SIZE=3]Startup Manager -- Grub Configuration Utility (*package: startupmanager*)
[/SIZE]
[*][SIZE=3]Firestarter -- Firewall Configuration Utility (*package: firestarter*). Firestarter is simply a firewall configuration utility. Ubuntu has its own default firewall using IPTables. In most cases, you do not need firestarter, unless you are looking forward to advanced ICMP filtering. Most users can skip this application.
[/SIZE]
[*][SIZE=3]Thunderbird -- Email Client (*package: thunderbird*)
[/SIZE]
[*][SIZE=3]Localepurge -- Temporary and junk file remover (*package: localepurge*)
[/SIZE]
[*][SIZE=3]Emerald Theme Manager (*package: emerald*)
[/SIZE]
[*][SIZE=3]RAR and UNRAR: To be able to read and create RAR archives (*packages: rar, unrar-free*)
[/SIZE]
[*][SIZE=3]Flash plugin for Mozilla Firefox (*package: flashplugin-nonfree*)
[/SIZE]
[*][SIZE=3]Virtualbox: A virtual PC software on which you may install other operating systems. Link: [http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox) (*package: virtualbox-ose*)
[/SIZE]
[*][SIZE=3]GParted Partition Editor (*package: gparted*)
[/SIZE]
[*][SIZE=3][FONT=courier new][FONT=trebuchet ms][FONT=trebuchet ms]XChat IRC Client ([/FONT][FONT=trebuchet ms]*package: xchat*[/FONT][FONT=trebuchet ms])[/FONT]
[/FONT][/FONT][/SIZE]
[/LIST]
[FONT=trebuchet ms][SIZE=3]*Note: You may remove whatever package you do not need from the command before executing it. The package names are mentioned within brackets next to the name of the application.*[/SIZE][/FONT][SIZE=3]

[/SIZE][SIZE=3][FONT=trebuchet ms]Once the command is complete, there are a few more things that you may find handy. These are some direct links to download pages. Select the correct distribution and architecture you have and download the appropriate version (If available).
**Real Player Linux: **[http://www.real.com/linux](http://www.real.com/linux)[/FONT]
[/SIZE][SIZE=3][FONT=trebuchet ms]**Ubuntu Tweak: **[http://getdeb.net/release.php?id=2889](http://getdeb.net/release.php?id=2889)
**Screenlets: **[http://getdeb.net/app/Screenlets](http://getdeb.net/app/Screenlets)
**GPicView: **[http://getdeb.net/app/GPicView](http://getdeb.net/app/GPicView) (This maybe an old version but you can install it on Hardy)
**AWN Dock: **[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

[I][B]Installing Cairo Dock:
[/B][/I]I myself prefer Cairo Dock to AWN because it can be set to show up on the top edge and has the cool "Caroussel" look with 3D arrangement of icons.
To install Cairo Dock, goto [B]System->Administration->Software Sources
[/B]Click on **Third Party Software** tab and press Add to add this line:
[/FONT]```
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
```[/SIZE][SIZE=3][FONT=trebuchet ms]

Now, at a terminal:
[/FONT][/SIZE]```
[SIZE=3][SIZE=3]wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -[/SIZE]
sudo apt-get update  
sudo apt-get install cairo-dock cairo-dock-plug-ins[/SIZE]
```[SIZE=3]

[/SIZE][SIZE=3]
[/SIZE]
[SIZE=3][FONT=trebuchet ms] [I][B]Installing Medibuntu:
[/B][/I][/FONT][/SIZE][FONT=trebuchet ms][SIZE=3]Some packages like the Adobe Reader are not available in the standard-repositories. The easiest way to make such packages available to your system is to add the medibuntu repository. If you want to add this repository open a terminal and type in:
[/SIZE][/FONT][SIZE=3]```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```[/SIZE][FONT=courier new][SIZE=3]
[FONT=trebuchet ms]And then, Import the gpg key and update your package list by typing:
[/FONT][/SIZE][/FONT][SIZE=3]```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```[/SIZE][SIZE=3]


[/SIZE][SIZE=3]***[FONT=trebuchet ms]To run some MS stuff (like wma/wmv files and to have MS fonts)[/FONT]***[/SIZE][SIZE=3]
[/SIZE][FONT=trebuchet ms][SIZE=3]Open a terminal and type in:
[/SIZE][/FONT][SIZE=3]```
sudo apt-get install w32codecs libdvdcss2 msttcorefonts
```[/SIZE][FONT=trebuchet ms][SIZE=3][FONT=courier new]


[I][B][FONT=trebuchet ms]To install Adobe Reader
[/FONT][/B][/I][FONT=trebuchet ms]At a terminal, type in:
[/FONT][/FONT][/SIZE][/FONT][SIZE=3]```
sudo apt-get install acroread acroread-plugins mozilla-acroread
```[/SIZE][FONT=trebuchet ms][SIZE=3][FONT=courier new][FONT=trebuchet ms]
[/FONT][/FONT]
[/SIZE][/FONT][SIZE=3]
[/SIZE][SIZE=3][FONT=trebuchet ms]After you have installed everything, open a terminal again and type in:
[/FONT]```

sudo apt-get autoremove
sudo apt-get autoclean
sudo localepurge

```[/SIZE][SIZE=3][FONT=trebuchet ms][FONT=courier new]
[FONT=trebuchet ms]This would clear out unneeded junk packages from your installations.

**Note: **At this point, you might be prompted of updates (The orange icon on the notification area). We'll update later.
[/FONT][/FONT][/FONT][/SIZE][CENTER][SIZE=3][[IMG]http://bp3.blogger.com/_pba65pfDRJc/SHM71Mu6Z1I/AAAAAAAAAC8/fSJiCpedhpo/s320/ubuntu-debian-update-notification.png[/IMG]]("http://bp3.blogger.com/_pba65pfDRJc/SHM71Mu6Z1I/AAAAAAAAAC8/fSJiCpedhpo/s1600-h/ubuntu-debian-update-notification.png")
[/SIZE][/CENTER]
[SIZE=3]
[/SIZE][SIZE=3][FONT=trebuchet ms][FONT=courier new][FONT=trebuchet ms]Now we will install the latest Compiz-Fusion on your computer.
Open [B]System->Administration->Software Sources
[/B]Click on **Third Party Softwares** tab. Press the **Add** button.
In the text area **Apt-line**, type in (or paste) this:

[/FONT][/FONT][/FONT]```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```[/SIZE][SIZE=3]

[/SIZE][SIZE=3][FONT=trebuchet ms]Press **Add Source. **Then press **Close** to close the **Software Sources** window and press **Reload** when prompted to.

Now click on the **Update Manager **applet in the notificati[/FONT][/SIZE][SIZE=3][FONT=trebuchet ms]on area or (if applet not available), goto **System->Administration->Update Manager** and press the **Check** button. After it downloads and shows available updates, press **Install Updates **button. Updating may take a long time depending upon connection speed. After the update, you may need to reboot your computer if prompted for. A blue arrowed icon appears in the notification area. Click on it and you will see this:
[/FONT][[IMG]http://www.easy-ubuntu-linux.com/images/installed-software-updating-system-restart-now-or-later-cropped.png[/IMG]]("http://www.easy-ubuntu-linux.com/images/installed-software-updating-system-restart-now-or-later-cropped.png")

[/SIZE][FONT=trebuchet ms][SIZE=3]Press the **Restart Now** button to restart your computer.
[/SIZE][/FONT][LEFT][FONT=trebuchet ms][SIZE=3]Let your computer restart. Once it restarts, you are done with installing essential software! You have quite many things that you need :)

[SIZE=5]
[/SIZE] [SIZE=5][COLOR=Sienna]Setting up your system A-Z[/COLOR][/SIZE]

[/SIZE][/FONT][FONT=trebuchet ms][SIZE=3]Download this file: [/SIZE][/FONT][SIZE=3][[FONT=trebuchet ms]http://www.mediafire.com/?wugxanmdy0m[/FONT]]("http://www.mediafire.com/?wugxanmdy0m")[/SIZE][FONT=trebuchet ms][SIZE=3]Extract the file. This has two files: **Compiz.profile** and **Theme.emerald**[/SIZE][/FONT][SIZE=3][B][FONT=trebuchet ms][I][I]


Setting up Compiz (Works with Compiz 0.7.5 or later)[/I][/I][/FONT][/B][/SIZE][FONT=trebuchet ms][SIZE=3]
Goto **System->Preferences->Advanced Desktop Effects Settings** (known as CCSM)
Press **Preferences** button (bottom left)
Press **Import** button and select the **Compiz.profile** file.
This would import a fairly good looking compiz animation profile which works on almost all configurations.


[I][B]Setting up Emerald
[/B][/I]Goto **System->Preferences->Sessions **and press the **Add** button. Type in the **Name **as ***Emerald***. Type in the **Command** as ***emerald --replace ***and press the OK button. Close the sessions window.
Now, press Alt+F2 and type in ***emerald --replace*** and press Enter.Now goto **System->Preferences->Emerald Theme Manager** and click the **Import** button. Open the **Theme.emerald** file. You will find a new entry in the theme list

[/SIZE][/FONT][SIZE=3][[IMG]http://i28.tinypic.com/5lrp8p.png[/IMG]]("http://i28.tinypic.com/5lrp8p.png")

[/SIZE][FONT=trebuchet ms][SIZE=3]Just click on this theme to apply it. Close the emerald theme manager.
More emerald themes:
[http://www.gnome-look.org/?xcontentmode=103](http://www.gnome-look.org/?xcontentmode=103)
[http://www.gnome-look.org/?xcontentmode=102](http://www.gnome-look.org/?xcontentmode=102)


[I][B]Wallpaper Selection
[/B][/I]You can find nice wallpapers here at:
[/SIZE][/FONT][SIZE=3][http://www.interfacelift.com/](http://www.interfacelift.com/)
[http://www.dual-display.com/pages/wallpaper.php](http://www.dual-display.com/pages/wallpaper.php) [/SIZE][FONT=trebuchet ms][SIZE=3](Dual display wallpapers)


[I][B]Icons
[/B][/I]Here are some good looking icon sets:
[http://www.gnome-look.org/content/show.php/AER-OS-XK?content=49990](http://www.gnome-look.org/content/show.php/AER-OS-XK?content=49990)
[http://www.gnome-look.org/content/show.php/CrashBit?content=71140](http://www.gnome-look.org/content/show.php/CrashBit?content=71140)
[http://www.kde-look.org/content/show.php/Vista-Inspirate?content=31585](http://www.kde-look.org/content/show.php/Vista-Inspirate?content=31585)

Or choose from here:
[http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=120x121](http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=120x121)

I use a AER-OS-XK + NuovoXT.2.2 + Crashbit icon fusion.


***Panel Background***
Download this: [http://www.mediafire.com/?xgjysmkmisd](http://www.mediafire.com/?xgjysmkmisd)
Extract the Panels.rar file. It would have 7 png files enclosed.
Now right click on any panel, select **Properties** and click the **Background** tab. Click on **Background Image** and click on the box below to select one of these 7 png files.


[I][B]Menu
[/B][/I]This would install USP (Ubuntu System Panel).
[http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation)
Follow the instructions on the page.
To add USP to the panel, right click on a panel and select **Add to Panel** and from the list, add **Ubuntu System Panel**


[I][B]Screenlets (Widgets)
[/B][/I]Goto Applications->Accessories->Screenlets to start the Screenlets daemon. You can add any screenlet by clicking on **Launch** button. You may also set it to auto start on boot by **checking** the *Auto start on Login* checkbox.

[I][B]Login Screen (gdm)
[/B][/I]Using this, you can use custom gdm themes.
This is one of my favorites: [http://www.gnome-look.org/content/show.php/Avio-GDM?content=37395](http://www.gnome-look.org/content/show.php/Avio-GDM?content=37395)
You will get **.tar.gz** files from this ^^^ link.
After downloading, goto **System->Administration->Login Window**
Click on **Local** tab and press **Add** button. Find the tar package you just downloaded there and press **Install**.
*Note: If you just downloaded the package to your desktop and you cannot find it there in the Login Window's file selector (it would be displaying root's desktop), just click on ****File System*** on left panel, and goto /home/username/Desktop *to find the file.*

After you set the file, click on the Avio-GDM entry to select it.
Click on the Theme drop menu and select **Selected Only**. (Do this step even if it already has Selected Only on it).
If the theme does not come in the gdm, then again perform the previous step. (Seems to be a bug, dunno if it is fixed yet)
Also, select the **Background Color** on the Login Window Preferences to a grayish (Code: #ACACAC) or whatever you think matches with the theme.


[I][B]Lock Dialog
[/B][/I]You can lock the screen by pressing Ctrl+Alt+L
To change this key combination, you can goto System->Preferences->Keyboard Shortcuts
To change the Unlock Dialog theme that appears, download a lock dialog from here: [http://www.gnome-look.org/content/show.php/lock-dialog-turbolence?content=67573](http://www.gnome-look.org/content/show.php/lock-dialog-turbolence?content=67573)

Extract the file. Now press Alt+F2 and type in **gksudo nautilus** and press Enter. Now using the newly opened Nautilus window, copy the 4 enclosed files (inside the downloaded tar file) to **/usr/share/gnome-screensaver**
CAUTION: gksudo nautilus will launch the File Browser with root/superuser/administrative privileges. You can harm your system by deleting any system file. You should not use this unless you know what you are doing.
Now close the root nautilus window and press Alt+F2 again, and type in [B]gconf-editor
[/B]Expand apps and click on gnome-screensaver. In the right column, double click the **lock_dialog_theme** and change the **Value **to **turbolence **and press OK. Close the gconf-editor.


*Specific operations using Ubuntu Tweak*Goto Applications->System Tools->Ubuntu Tweak to launch the application.
You may perform these actions:
[/SIZE][/FONT][FONT=trebuchet ms][SIZE=3]
1. **To display Computer, Home and Trash on desktop:**[/SIZE][/FONT][SIZE=3]
[/SIZE][FONT=trebuchet ms][SIZE=3]Expand **Desktop **and click on **Desktop Icons** and check whichever icon you want to be on the desktop.
2. [B]To add a shortcut to "Set as Wallpaper" on right click menu for pictures:
[/B]Expand **System **and click on **Nautilus** and check **Nautilus with wallpaper** under Nautilus Extensions and press **Apply **button adjacent to it.


[I][B]Configuring Firestarter
[/B][/I]You do **not** need an antivirus on your Ubuntu. Firestarter is a firewall configuration utility. Open firestarter and go through the simple processes to configure it.
Note: At beginning, firestarter is set to block all incoming connections to your computer. You have to click on the **Events** tab of firestarter, right click on a specific connection from a specific IP address and select Allow connections to add it to the **Allowed **list.


[/SIZE][/FONT][FONT=trebuchet ms][SIZE=3][I][B]Font Smoothing
[/B][/I]Goto System->Preferences->Appearance->Fonts tab and select **Subpixel Smoothing**, **Full** hinting and RGB hinting.[/SIZE][/FONT][FONT=trebuchet ms][SIZE=3]

[/SIZE][/FONT][CENTER][SIZE=3][[IMG]http://bp0.blogger.com/_pba65pfDRJc/SHOSm1JEr3I/AAAAAAAAADM/mUxpHgoGmko/s400/fonts2.jpg[/IMG]]("http://bp0.blogger.com/_pba65pfDRJc/SHOSm1JEr3I/AAAAAAAAADM/mUxpHgoGmko/s1600-h/fonts2.jpg")
[/SIZE][/CENTER]
[SIZE=3]
[/SIZE][FONT=trebuchet ms][SIZE=3]
[/SIZE][/FONT][SIZE=3]
[/SIZE][FONT=trebuchet ms][SIZE=3][SIZE=5][COLOR=Sienna]
Some quick tips[/COLOR][/SIZE] [SIZE=5]
[/SIZE]  
[/SIZE][/FONT][FONT=trebuchet ms][SIZE=3][FONT=trebuchet ms][COLOR=#3333ff]Here are some points that may be of importance to you:[/COLOR]
[/FONT][/SIZE][/FONT]
[LIST]
[*][SIZE=3]Your computer may [/SIZE][SIZE=3]**not**[/SIZE][SIZE=3] receive files from a phone/smartphone. To send data from the phone to the computer, enable bluetooth on both phone and computer, right click on the bluetooth icon in the notification area and click on [/SIZE][SIZE=3]**Browse Device.**[/SIZE][SIZE=3] Select your phone from the list and press [/SIZE][SIZE=3]**Connect.**[/SIZE][SIZE=3] Enter a common passkey on both sides when asked to and the phone will open in a file browser in your computer.[/SIZE]
[*][SIZE=3]You can find the USP search feature. For example, if you want to launch [/SIZE][SIZE=3]**Text Editor**[/SIZE][SIZE=3], just type in [/SIZE][SIZE=3]**text**[/SIZE][SIZE=3] (just start typing, it will automatically be typed in the search box), and press Enter.[/SIZE]
[*][SIZE=3]If you do not have a bluetooth device, then goto System->Administration->Services. Press [/SIZE][SIZE=3]**Unlock**[/SIZE][SIZE=3] button and enter your password. [/SIZE][SIZE=3]**Uncheck**[/SIZE][SIZE=3]*Bluetooth device management (bluetooth)*[/SIZE][SIZE=3] from the list and close the Services window.
[/SIZE]
[*][SIZE=3]You may include a delete command for files that would bypass the trash. Open any Nautilus window, goto Edit->Preferences. Click on [/SIZE][SIZE=3]**Behavior**[/SIZE][SIZE=3] tab and check [/SIZE][SIZE=3]*Include a delete command that bypasses trash.*[/SIZE]
[*][SIZE=3]Whenever you install any package, do remember to do: [/SIZE][SIZE=3]**sudo apt-get autoremove ; sudo apt-get autoclean **[/SIZE][SIZE=3]and [/SIZE][SIZE=3]**sudo localepurge**[/SIZE][SIZE=3] in the terminal to clean-up junk files.[/SIZE]
[*][SIZE=3]You may find this handy: [http://tinyurl.com/26yxoc](http://tinyurl.com/26yxoc)[/SIZE]
[/LIST]
[SIZE=3]

[SIZE=5][COLOR=Sienna]Screenshots:
[/COLOR][/SIZE][/SIZE][CENTER][ATTACH]77301[/ATTACH][ATTACH]77302[/ATTACH]
[ATTACH]77303[/ATTACH][ATTACH]77304[/ATTACH] [/CENTER]
[/LEFT]

---

### Post by azer89 on 2008-07-11
hmmm i'm still confusin' with localepurge

reza@reza-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 190 not upgraded.
reza@reza-laptop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
reza@reza-laptop:~$ sudo localepurge
sudo: localepurge: command not found
reza@reza-laptop:~$

---

### Post by erwall on 2008-07-11
> **azer89 said:**
> hmmm i'm still confusin' with localepurge

reza@reza-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 190 not upgraded.
reza@reza-laptop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
reza@reza-laptop:~$ sudo localepurge
sudo: localepurge: command not found
reza@reza-laptop:~$
try:
```
sudo aptitude install localepurge
sudo localepurge
```

---

### Post by Hubi17 on 2008-07-11
Nice guide! Some useful instructions there. Thx

---

### Post by sayakb on 2008-07-11
> **azer89 said:**
> hmmm i'm still confusin' with localepurge

reza@reza-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 190 not upgraded.
reza@reza-laptop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
reza@reza-laptop:~$ sudo localepurge
sudo: localepurge: command not found
reza@reza-laptop:~$

As erwall said, you have to install localepurge first. The outputs of the first two commands you executed are ok.
I indicated the installation of localepurge in this part of the post:

> **LinuxIsInnovation said:**
> [FONT=trebuchet ms][SIZE=3]Now, to start with, open a terminal: [/SIZE][/FONT][FONT=trebuchet ms][SIZE=3]**Application->Accessories->Termina**[/SIZE][/FONT][FONT=trebuchet ms][SIZE=3]**l**[/SIZE][/FONT][FONT=trebuchet ms][SIZE=3] and type in the following comman[/SIZE][/FONT][SIZE=3]d:

```
sudo apt-get install ubuntu-restricted-extras vlc compizconfig-settings-manager catfish audacious wine startupmanager firestarter thunderbird localepurge emerald rar unrar-free flashplugin-nonfree virtualbox-ose gparted xchat

```[/SIZE]

---

### Post by hyper_ch on 2008-07-12
why do you install firestarter?

---

### Post by sayakb on 2008-07-12
ICMP Filtering: protection from Denial of Service, Brute Forcing, Packet Capture etc. I don't have ICMP filtering by just configuring the IPTables (Though if it can be done by just configuring the IPTables, you may not install firestarter then).

---

### Post by nycste on 2008-07-12
First great thread, thanks for the advice in the other thread

since im a total linux newb im trying to learn as much as possible everyday and part of them is customizing and making ubuntu run faster or different in anyway you want

my question is if i run

sudo apt-get install ubuntu-restricted-extras vlc compizconfig-settings-manager catfish audacious wine startupmanager firestarter thunderbird localepurge emerald rar unrar-free flashplugin-nonfree virtualbox-ose gparted xchat

and i already have X Y Z installed, what happens when i tell it to install it again? is it safe? 

next question, what if i currently have installed newer versions then what is in synaptic repo... what happens then.. 

thanks

---

### Post by sayakb on 2008-07-12
1. If you have a package installed and you type in a command to install it again, it would just notify that the package is already in it's newest version. You may test by typing:
```
sudo apt-get install gdm
```
Where gdm is the login prompt of ubuntu, which is already installed.

2. If you install new version of some package, which is newer to that listed in Synaptic, the newer version would be now displayed in synaptic and the older version of the software that is available in the repositories (ie. via synaptic) will become inactive.

Both these are 100% safe, and will not cause any damage to your system.

---

### Post by nycste on 2008-07-12
> **LinuxIsInnovation said:**
> 1. If you have a package installed and you type in a command to install it again, it would just notify that the package is already in it's newest version. You may test by typing:
```
sudo apt-get install gdm
```
Where gdm is the login prompt of ubuntu, which is already installed.

2. If you install new version of some package, which is newer to that listed in Synaptic, the newer version would be now displayed in synaptic and the older version of the software that is available in the repositories (ie. via synaptic) will become inactive.

Both these are 100% safe, and will not cause any damage to your system.

once again fast and good response thanks

---

### Post by sayakb on 2008-07-12
Np.. Glad I could help! :)

---

### Post by hyper_ch on 2008-07-12
I still think firestarter does not belong there ;) by default you don't have any need to alter iptables...

---

### Post by sayakb on 2008-07-12
Youre right.. thats why I added the line that people may skip some packages if they want to :)

---

### Post by hyper_ch on 2008-07-12
Yes, but the people coming from windows think they must have some antivirus protection and a firewall like on windows. This is not the case and that should be pointed out IMHO. So I'd rather to see a note directly next to firestarter that it is very likely not needed ;)

The rest of the howto is great ;)

---

### Post by sayakb on 2008-07-12
Happy? ;)

---

### Post by hyper_ch on 2008-07-12
> **LinuxIsInnovation said:**
> Happy? ;)

actually I'm still waiting to win EuroMillions - but pretty close to it ;)

thx

---

### Post by mrphoenix on 2008-07-12
Thanks for your tutorials.

I just would share mine here with all Ubuntu users:

[All goodness here...]("http://phoenix_art.extra.hu/")

---

### Post by nycste on 2008-07-12
> **hyper_ch said:**
> Yes, but the people coming from windows think they must have some antivirus protection and a firewall like on windows. This is not the case and that should be pointed out IMHO. So I'd rather to see a note directly next to firestarter that it is very likely not needed ;)

The rest of the howto is great ;)

i know you must be trying to help but having an AV program that scans your files every so often in linux is beneficial if not a must needed program

what happens when you download filex.whatever, then send it to your friend or even your family member, that file is corrupted and you didnt even know it, then it breaks their computer and so fourth

how to solve that? well if you had a AV scanner and the scanner found this file, well you would then know its a naughty file and delete or fix it

see where i am going?

most of you ubuntu geeks (dont take this personally) assume just because people are now using ubuntu or linux they stop using windows, or dont dualboot or something like that...

a virus free world involves everyone helping to remove and rid the worlds systems of such things, there will always be good and bad guys, running something once a week or once a month will help in the fight :)

---

### Post by hyper_ch on 2008-07-12
> **nycste said:**
> what happens when you download filex.whatever, then send it to your friend or even your family member, that file is corrupted and you didnt even know it, then it breaks their computer and so fourth
then their computer would get infected anway by others if they fail to protect themselves...

> **nycste said:**
> see where i am going?
Not really

> **nycste said:**
> most of you ubuntu geeks (dont take this personally) assume just because people are now using ubuntu or linux they stop using windows, or dont dualboot or something like that...
I don't assume that but it is not my responsability and neither my job to protect them... if they can't protect themselves their system will get corrupted anyway... nothing I can do against that.

> **nycste said:**
> a virus free world involves everyone helping to remove and rid the worlds systems of such things,
Or secure their machines accordingly - even if that requires changing the OS.

> **nycste said:**
> running something once a week or once a month will help in the fight :)
not really... most malware isn't sent from people you know... and it wastes my system resources.

---

### Post by sayakb on 2008-07-12
nycste:
Most email service providers have built in protection for viruses and malware. For example, yahoo uses Norton Antivirus to scan the files you attach: [http://help.yahoo.com/tutorials/mmail/mmail/mm_attachments3.html](http://help.yahoo.com/tutorials/mmail/mmail/mm_attachments3.html)
There is no actual need of an antivirus on an Ubuntu (or maybe any linux machine). That is because all programs are executed as user privileges, and not as superuser/administrator. So the virus cannot actually access and modify your system files :)
Read here: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by nycste on 2008-07-12
> **LinuxIsInnovation said:**
> nycste:
Most email service providers have built in protection for viruses and malware. For example, yahoo uses Norton Antivirus to scan the files you attach: [http://help.yahoo.com/tutorials/mmail/mmail/mm_attachments3.html](http://help.yahoo.com/tutorials/mmail/mmail/mm_attachments3.html)
There is no actual need of an antivirus on an Ubuntu (or maybe any linux machine). That is because all programs are executed as user privileges, and not as superuser/administrator. So the virus cannot actually access and modify your system files :)
Read here: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

nah its cool, im letting the topic drop, i still think most of you are wrong since most of you dont seem to deal with naughty files, because if you did then you wouldnt want to destroy your friends windows boxes just because it doesnt affect yours.

like i said topic dropped. while in ubuntu/linux there is like a 1 percent need for an antivirus program or no need at all !

either way great guide lets drop this topic ^

---

### Post by sayakb on 2008-07-12
lol.. okay..!
PS: I do care about my friends boxes. If you want an antivirus, see here: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
I have once used avast, and I kinda like it :)

---

### Post by querent on 2008-07-12
I'm limited to a pretty slow connection here, so I left the first apt-get running.  When I returned, my terminal was a "Configuring localepurge" menu.  I'm an american (sigh), english speaker.  What do I do with this?  running

man localepurge

is a no-go...no such manual.

thanks in advance,
q

---

### Post by querent on 2008-07-12
ok...told it to kill everything, it expressed doubts, i concurred, and it deferred.  so there's a man now, but no list of two letter locales.  Weird.  and there seems to be a tendency to pre-apologize for weird behavior resulting from localepurge's use.  should i be concerned?  (and what do i tell it to keep?)

---

### Post by sayakb on 2008-07-13
Do you get any dpkg error message when you try to install anything? Try doing:
```
sudo dpkg --configure -a
```
At a terminal.

---

### Post by hyper_ch on 2008-07-13
P.S.: Looking forward to your next howtos ;)

---

### Post by bapoumba on 2008-07-14
[http://ubuntuforums.org/showthread.php?t=858959]("http://ubuntuforums.org/showthread.php?t=858959")
Typos discussions moved to a new thread in FFH.

---

### Post by Lakjin on 2008-07-14
First of all, nice guide!

But I have two questions.
1) how do i remove any of those apps i installed? i.e. localpurge?
2) what program did you use to get that MAC OS type looking bar at the bottom? I want that =D

thx!!

EDIT: Nevermind i figured out how to remove those apps. But i still want to know how to get that MAC OS type looking bar =D

---

### Post by sayakb on 2008-07-14
That is Avant Window Navigator (Installation guide included in HOWTO). After installing AWN, right click on it and select **Dock Properties**. From there, select the **Curves** look.

---

### Post by Lakjin on 2008-07-15
> **LinuxIsInnovation said:**
> That is Avant Window Navigator (Installation guide included in HOWTO). After installing AWN, right click on it and select **Dock Properties**. From there, select the **Curves** look.

thx!

i tried avant but decided to go with cairo, it seems better for me =)

---

### Post by sayakb on 2008-07-15
Yepp... Cairo has some cool effects! :)

---

### Post by d1sdain on 2008-07-15
i am Out the Box new to linux. I just wiped vista business and put on ubuntu last night.

This guide is great but i have one question.

I installed everything and now my log in screenis buggy. It is blue and asks me how I want to log on "Default" Gnome" "KDE"... I dont even know what those are yet... I always choose default.

It also makes me enter my user pass to reboot or hibernate now...


And sometimes when I log in my upper and lower bars are completely gone... just a blank desktop.

Are there short cuts to get to my menus? (i.e. windows famous "window key")

and is there a fix for that?


Thanks for the help!

---

### Post by Abu_Dayya on 2008-07-16
Can you please elaborate more on emerald and compiz.profile ? I'm trying to learn about window managers and such, but I'm too confused at the moment, and most of my googling results are way too geeky for me

Thanks

---

### Post by sayakb on 2008-07-23
> **Abu_Dayya said:**
> Can you please elaborate more on emerald and compiz.profile ? I'm trying to learn about window managers and such, but I'm too confused at the moment, and most of my googling results are way too geeky for me
 
Thanks
 
Compiz is a window manager and emerald is a window decorator (provides window borders) Have you installed CCSM? If so, then follow the instructions to import the compile.profile
This file is a set of customized settings that look fairly good.

---

### Post by tackatucka on 2008-07-24
Great guide how to customize a desktop. thx a lot

As i am quiete newb with ubuntu.You might wonder, but i really cant find a way how to use the ubuntu system panel within the cairo dock bar.
I didnt found any command to start the usp ](*,)

Would be really nice if someone could help me.

---

### Post by Chame_Wizard on 2008-07-24
Isn't here a Kubuntu version?:popcorn:

---

### Post by SammyBoy247 on 2008-07-24
localepurge!

I know you added the caveat...
[INDENT]
> Note: You may remove whatever package you do not need from the command before executing it. The package names are mentioned within brackets next to the name of the application.[/INDENT]

but with the practice of copy 'n' paste, think later I think apps with the power of localepurge should be fully explained before being put in the hands of... well people as stupid as me.

To say that localepurge is a "Temporary and junk file remover" doesn't quite describe to power and potential damage this little prog can unleash.

Otherwise an excellent guide.

---

### Post by rohan1 on 2008-07-28
Hi

Have downloaded and installed the software as described..followed it up with setting up compiz and emerald theme..however still have the default ubuntu desktop theme on startup,,,am I missing a step here? Thanks in advance!

---

### Post by rohan1 on 2008-07-28
Also read that one needs to set the visual effects to normal or extra but on system-preferences-appearences-visual effects, on clicking the normal or extra tabs I get the message desktop effects not enabled??

---

### Post by nbayiha on 2008-07-28
Just " Chapeau Bas " for this guide really useful and nice for not so advanced Linux user. Easy to read and understand. 
Thanks a lot for Your time.

But i still have some question :lolflag: , Why didn't you show how to make Cairo-dock to automatically appear every time we log-in ?
And secondly why didn't you show to how to install icon nor icon themes ? you just gave the link on where we should download.

I think if you started your thread by being so explicit from the start ,you should keep it like this, till the end :KS .
Anyway this is a Terrific job from you , and i think this will help a lot of us around . :popcorn:

---

### Post by dot2kode on 2008-07-29
I just came across your post today and I have been using ubuntu for about 2 months now[IMG]http://i275.photobucket.com/albums/jj285/3d0k/snoozer_likelinux_man.gif[/IMG]and the only thing I can say is where were you a couple months ago?! #-o any way thanks for taking the time to put this togather, anyone who has already been using ubuntu or just starting can find this very helpful! Thanks again!!  =D>

---

### Post by mr.moch on 2008-08-18
Just a fast question:  I tried doing emerald --replace, but it didn't do anything....including a logoff and logon.  I did what was said in the instructions, but it didn't work.  Does the Xwindow system play a role in this?

Anyways, great guide!

---

### Post by sayakb on 2008-08-20
You need to have compiz running when you do emerald --replace. What is the output of the command **emerald --replace &  **in the terminal?

---

### Post by Giggity on 2008-08-25
Edit:  found another thread to help with specific problem.  My Compiz wasn't loading up, but it was because I hadn't enabled the latest nVidia driver via the Restricted Hardware Manager.  I did so and now it works.

---

### Post by sayakb on 2008-08-25
> **Giggity said:**
> Edit:  found another thread to help with specific problem.  My Compiz wasn't loading up, but it was because I hadn't enabled the latest nVidia driver via the Restricted Hardware Manager.  I did so and now it works.

Good to know that it worked out for you (btw, seems like you are still using Ubuntu 7.10).

---

### Post by Giggity on 2008-08-25
> **LinuxIsInnovation said:**
> Good to know that it worked out for you (btw, seems like you are still using Ubuntu 7.10).Thanks for the reminder.  I fixed my profile to say 8.04...

---

### Post by Brock Samson on 2008-08-28
Nice tutorial, saved me a lot of time, over the past couple of months I have had to re-install ubuntu a few times (slow learner!) but this is great for people new to ubuntu who want to spice it up the easy way. 
keep 'em coming =D>

---

### Post by nouseforaname7 on 2008-08-30
When I click on the theme in emerald, nothing happens

Any ideas?

---

### Post by sayakb on 2008-09-01
Press Alt+F2 and type in **emerald --replace** and then click on the theme.

---

### Post by randu53 on 2008-09-12
So I installed most of the stuff you had in the HOWTO (very helpful by the way) but now when I try to open /usr/bin/emacs-snapshot-gtk I see it appear for a split second then flash off the screen to the top.  I know the program is running because it shows up in a ps listing but I can't find it anywhere on the desktop.

---

### Post by hey_ram on 2008-09-22
hey!

amazing tutorial!!! 
ubuntu seems to have suddenly come alive on my laptop!!
nice work!
hope to read more of such tutorials in the future!!

---

### Post by sayakb on 2008-09-23
Glad that it was useful to you! :)

---

### Post by RoyHobbs on 2008-09-27
hi
Thanks for this tutorial it is fantastic!  I'm not sure how you do this, but I think this thread should be in the absolute beginners section as well.  Everything has worked (I think) except for localpurge.  Basically, every time I have tried to install it / run it I get the following error:

andrei@home-downstairs:~$ sudo localepurge

    You have to configure "localepurge" with the command

        dpkg-reconfigure localepurge

    to make /usr/sbin/localepurge actually start to function.

    Nothing to be done, exiting ...

andrei@home-downstairs:~$ 

I am a newbie so any advice would be greatly appreciated.  Thanks

---

### Post by sayakb on 2008-09-30
Try:
```
sudo dpkg-reconfigure localepurge
sudo localepurge
```

---

### Post by RoyHobbs on 2008-10-03
> **LinuxIsInnovation said:**
> Try:
```
sudo dpkg-reconfigure localepurge
sudo localepurge
```

Hi, that worked perfectly, thanks for your help!

---

### Post by SSVegito888 on 2008-10-08
> **LinuxIsInnovation said:**
> ICMP Filtering: protection from Denial of Service, Brute Forcing, Packet Capture etc. I don't have ICMP filtering by just configuring the IPTables (Though if it can be done by just configuring the IPTables, you may not install firestarter then).



Is it safe to just use the GUI for ufw "gufw" instead of Firestarter?

---

### Post by qwertymodo on 2008-10-11
Linux n00b here, muchly grateful for the tips.  One question tho, when you configure localepurge, how do you select which locales to keep?  I've tried every key on the keyboard and mouse clicks (didn't expect those to work, it's terminal after all, but it was worth a shot :P).  Is it a key combo or did I just miss a key?  I saw in another post what looked like a slightly different version where each locale had a number and at the bottom it asked for which numbers you wanted.  In the one I have each locale is preceeded by a [ ], so i assume you type something in there??  Thanks.

---

### Post by sayakb on 2008-10-11
When you configure it, move up and down by the arrow keys and select the [ ] box by the spacebar. When you are done, press Enter.

---

### Post by SSVegito888 on 2008-10-14
How would you properly configure the ICMP Filtering in Firestarter?



Also, what program does it use to create the firewall. Eg. ufw, iptables, netfilter, etc.

---

### Post by dcjose20 on 2008-10-17
How do you use Cairo Dock. I cant seem to get it to work. FYI im a ubuntu noob so maybe im doing something wrong here. Thanks for the help

---

### Post by qwertymodo on 2008-10-19
I stand corrected.  I tried hitting every button on the keyboard *except* spacebar :P

---

### Post by Rickles65 on 2008-11-01
Hi! Thanks for this tutorial, I used it on 8.04 perfectly.

How does this apply to 8.10? I'm assuming it's all the same tricks but wanted to ask before I took off down that road.

:popcorn:

---

### Post by fooballz on 2008-11-12
Hi, when I try to run the command: 

emerald --replace

All it does is make my windows titles disappear. Using the emerald theme manager afterwards doesn't seem to do anything. I have compiz fusion installed with decorations enabled. Am I doing something wrong?

---

### Post by fooballz on 2008-11-13
Okay, I managed to get emerald to work...but now when I click on links from firefox that open new windows, they get opened such that 90% of the window is on another work space and only a little of it is poking into my current workspace...I'm guessing this is a problem with the compiz fusion option: "window placement", except I've played about with almost every combination and have been unable to fix this problem. Any ideas?

---

### Post by phantom3113 on 2008-11-15
> **fooballz said:**
> Hi, when I try to run the command: 

emerald --replace

All it does is make my windows titles disappear. Using the emerald theme manager afterwards doesn't seem to do anything. I have compiz fusion installed with decorations enabled. Am I doing something wrong?

I'm having the same problem. my window titles/edges are completely gone along with the "close window" and "minimize/maximize" buttons.

---

### Post by fewjr on 2008-12-11
Hello All,
 I started following this thread when I was a little bleary eyed. I should have read it through more closely before I started. Anyway, I ran the first set of commands:
```
sudo apt-get install ubuntu-restricted-extras vlc compizconfig-settings-manager catfish audacious wine startupmanager firestarter thunderbird localepurge emerald rar unrar-free flashplugin-nonfree virtualbox-ose gparted xchat
```
I really didn't need to install firestarter and probably a couple other things there also. Anyway while it was installing these programs, it came to the configuration part of localpurge. I couldn't figure out what to do. I tried to set it to english, but like I said I was out of it and some how got out of that before it was done. Today I tried to uninstall Firestarter in synaptic, but I got this after I click on "mark for complete removal"
```
(Reading database ... 143465 files and directories currently installed.)
Removing firestarter ...
Purging configuration files for firestarter ...
Processing triggers for man-db ...
Processing triggers for menu ...

    You have to configure "localepurge" with the command

        dpkg-reconfigure localepurge

    to make /usr/sbin/localepurge actually start to function.

    Nothing to be done, exiting ...
```
If I try to run the dpkg command it says:
```
goblin@goblin-lanbox:~$ sudo  dpkg-reconfigure localpurge
[sudo] password for goblin: 
Package `localpurge' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: localpurge is not installed

```
I confirmed that it is not install via synaptic. A search finds that it isn't there. So i try to install it again and it says this in the terminal:
```
goblin@goblin-lanbox:~$  sudo apt-get install localepurge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
localepurge is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Why does it tell me it isn't installed and then say that it is installed? Also what does localpurge have to do with uninstalling Firestarter? What can I do to get things back to where I was. Do I even need localpurge? 

Thanks
fewjr

---

### Post by fewjr on 2008-12-12
bump bump

---

### Post by deadbug159 on 2008-12-15
Thanx for the tutorial... 
One prob though... when i go to download compiz.profile and emerald.theme the site is set to private... can i access the file elsewhere?

---

### Post by gychang on 2008-12-16
thanks for the effort, found it very useful.

gychang

---

### Post by douham on 2008-12-19
> **deadbug159 said:**
> Thanx for the tutorial... 
One prob though... when i go to download compiz.profile and emerald.theme the site is set to private... can i access the file elsewhere?

+1
I'll have a look for other themes on gnome-look

---

### Post by Free4Eternity on 2009-01-22
great thread, thanks bro!

---

### Post by valex on 2009-01-27
> [http://www.mediafire.com/?wugxanmdy0m](http://www.mediafire.com/?wugxanmdy0m) 


This link is not working.

---

### Post by gabo.cr on 2009-02-12
I love this thread too !

\\:D/

---

### Post by The MAX on 2009-02-15
This thread is great.
Everything worked fine when I used 32 bit but now that I have 8.10 64 bit installed if I try to DL any of those packages it spits this out

```
hughie@The-Flash:~$ sudo apt-get install gparted
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing blender (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_intrepid-updates_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

Any ideas why its doing this? I'd like to get a lot of these packages.
It doesn't look like it's letting me install any packages, I've restarted my x-server but it is still not letting me install other packages either (ie sensors-detect).
If anyone here has an Idea I'd appreciate it.

---

### Post by borlosky on 2009-02-16
> **The MAX said:**
> This thread is great.
Everything worked fine when I used 32 bit but now that I have 8.10 64 bit installed if I try to DL any of those packages it spits this out

```
hughie@The-Flash:~$ sudo apt-get install gparted
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing blender (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_intrepid-updates_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

Any ideas why its doing this? I'd like to get a lot of these packages.
It doesn't look like it's letting me install any packages, I've restarted my x-server but it is still not letting me install other packages either (ie sensors-detect).
If anyone here has an Idea I'd appreciate it.


Sounds like you gotta install 64 bit flash first: [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

---

### Post by androidkerra on 2009-03-09
sweet!!!! very nice post man... would really help a lot of new users onto knowing linux' potential...

helped me alot!!!

thanks!!

:KS:KS:KS:KS:KS

---

### Post by Steelfan555 on 2009-03-15
Is there a way to change the font color of the taskbar? I found a great dark image for it, and now i cant read anything on the taskbar...
EDIT: Found it.

---

### Post by mattie01 on 2009-03-23
great tutorial, expect for the mediafire file that is linked to says it is set to private. any chance this can be changed or anyone else that downloaded it repost it somewhere else?

thanks in advance.

looks like the other mediafire links doesn't work either :( 


I really can't wait till i can get ubuntu looking like the screenshot in the bottom right of the tutorial as that looks amazing.

---

### Post by awfeucht on 2009-04-13
It occurs to me that it's been three weeks since this thread has been posted in, but I'm having a bit of a problem. I'm using Jaunty, and I don't have a System > Preferences > Session menu, and I'm not sure what (or if) the replacement is. This prevents me from properly setting up emerald per the instructions, and I haven't quite wrapped my head around it yet enough to make it work on my own. Any tips?

---

### Post by Grievous on 2009-04-14
Cairo dock doesnt seem to start automatically when it loads my desktop settings.  Any ideas?

---

### Post by munishvit on 2009-04-18
Nice thread:D

To change the "default terminal size" permanently:

sudo gedit /usr/share/vte/termcap/xterm
change the line
:co#80:it#8:li#24:\
to
:co#75:it#8:li#14:\
if you want a 75×14 terminal
[http://dendiz.verisux.com/2009/03/21/gnome-terminal-default-size/](http://dendiz.verisux.com/2009/03/21/gnome-terminal-default-size/)

---

### Post by juky on 2009-05-27
Great guide! Although, I have installed Foxit PDF reader instead of Adobe Reader. It is much more lightweight and faster the Adobe Reader:

[http://www.foxitsoftware.com/pdf/desklinux/download.html](http://www.foxitsoftware.com/pdf/desklinux/download.html)

Cheers,
juky

---

### Post by mcretzu on 2009-05-28
Very good info!
My Ubuntu looks awsome now. :)

---

### Post by conradin on 2009-06-15
Cool Im glad to know about localpurge and how to clean up.

How can i modify my login background image?

---

### Post by linux-hack on 2009-06-16
can you please upload agen the compiz.profile cause the links is dead..

Thanks a lot

---

### Post by Chevanova on 2009-06-19
WOW this is great, 
Thanks a lot

---

### Post by Chevanova on 2009-06-19
When i try to add the cairo dock repository i get the following error

W: GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877

What should i do?

---

### Post by Forming on 2010-06-24
Thanks. :)

---

### Post by codeevolution on 2010-07-27
hi i am new to linux i tried to enable the repositories but i am getting the following error
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory
 please help me i am useing ubuntu10.04 lst32bit

---

### Post by ZhuaSD on 2010-08-12
Thanks for the post!  I use it every time I re-install, just change hardy to lucid.

code ev, sounds like you got too many terminals open or your software sources manager has some problems.  This guide doesn't seem to work for mediabuntu anymore.

---

### Post by Mike_tn on 2010-11-20
Nice and thanks.

Two years later now, how would you edit this?

Don't change the lady with the lettuce, that's the best part.

---

### Post by DunZH on 2010-12-20
I have used this howto for a year or more for my basic setup of new installs.  I don't follow everything but do follow most of the basics.

The only thing that needs changing is for the mediabuntu.  This is written for hardy and I use karmic.  So the code changes slightly:

```
sudo wget http://www.medibuntu.org/sources.list.d/karmic.list -O /etc/apt/sources.list.d/medibuntu.list
```

Thanks!:popcorn:

---

