---
title: "[HELP] ???? removing bits and pieces of left over program?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Elos on 2008-06-07
Hi , i am a newbie in using ubuntu, and i have encounter some problems in which i would hope to receive help from the more advance users of ubuntu.
please help me step by step as i only know about mouse clicking and typing extremely simple commands in the terminal.

i had installed 
>>fceu ([http://linuxondesktop.blogspot.com/2007/03/playing-classic-games-under-ubuntu.html](http://linuxondesktop.blogspot.com/2007/03/playing-classic-games-under-ubuntu.html)) , 
>>nexuiz ([http://www.alientrap.org/nexuiz/](http://www.alientrap.org/nexuiz/)),
>>Americas Army ([http://www.americasarmy.com/](http://www.americasarmy.com/))
>>tremulous ([http://tremulous.net/](http://tremulous.net/)) and 
>>wine 
and now i wanted to removed them.

when i uninstall them i try both using the command (sudo apt-get remove *) whereby "*" = program as well as going to synaptic package manger 

However when i type "locate *"

i get 

FECU: 

liang@liang-desktop:~$ locate fceu
/usr/share/app-install/desktop/fceu.desktop
/usr/share/app-install/desktop/gfceu.desktop
/usr/share/app-install/icons/gfceu.png

NEXUIZ
liang@liang-desktop:~$ locate nexuiz
/usr/share/app-install/desktop/nexuiz.desktop
/usr/share/app-install/icons/nexuiz48x48.png

TREMULOUS
liang@liang-desktop:~$ locate tremulous
/usr/share/app-install/desktop/tremulous.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_tremulous.xpm

AMERICASARMY
sorry but cant locate?????

liang@liang-desktop:~$ locate AMERICASARMY
liang@liang-desktop:~$ 


WINE
liang@liang-desktop:~$ locate wine
/etc/apt/sources.list.d/winehq.lis
/etc/apt/sources.list.d/winehq.list
/etc/apt/sources.list.d/winehq.list.save
/home/liang/.wine
/home/liang/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fliang%2FDesktop%2Fwine.xml
/home/liang/Desktop/wine
/usr/share/app-install/desktop/wine.desktop
/usr/share/app-install/desktop/wineconfig.desktop
/usr/share/app-install/desktop/winefish.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_winefish-icon.png
/usr/share/app-install/icons/wineconfig.png
/usr/share/apps/katepart/syntax/winehq.xml
/usr/share/icons/crystalsvg/128x128/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/16x16/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/22x22/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/32x32/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/48x48/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/64x64/mimetypes/exec_wine.png
/usr/share/python-support/guidance-backends/wineread.py
/usr/share/python-support/guidance-backends/winewrite.py
/var/cache/apt/archives/wine-dev_1.0~rc3~winehq0~ubuntu~8.04-1_i386.deb
/var/cache/apt/archives/wine_0.9.59-0ubuntu5_i386.deb
/var/cache/apt/archives/wine_1.0~rc3~winehq0~ubuntu~8.04-1_i386.deb
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_hardy_main_binary-i386_Packages
/var/lib/apt/lists/partial/wine.budgetdedicated.com_apt_dists_hardy_Release
/var/lib/apt/lists/partial/wine.budgetdedicated.com_apt_dists_hardy_Release.gpg
/var/lib/dpkg/info/wine.list
/var/lib/dpkg/info/wine.postrm
/var/lib/python-support/python2.5/wineread.py
/var/lib/python-support/python2.5/wineread.pyc
/var/lib/python-support/python2.5/winewrite.py
/var/lib/python-support/python2.5/winewrite.pyc


I search in ubuntu forums for help and i tired using sudo apt-get autoclean and sudo apt-get autoclean AS WELL AS deleting the .wine folder in the home folder (for wine) 

but when i type locate * the same results keep turning up ???

so this are MY CONCLUSIONS (correct me if i am wrong thank you)

for fceu, nexuiz, TREMULOUS, and Americas Army????

those results are installer programs in synaptic package manger?? and i should leave them alone???

FOR WINE
NO matter how i look at it , the results doesn't seen to be installer files in synaptic package manger but REALLY LEFT OVER files from my old installation?

so if they are really left over files how do i go about removing them ???
please help thank you all in advance.

---

### Post by Paqman on 2008-06-07
When you uninstalled from Synaptic did you do a regular uninstall or a complete uninstall?

---

### Post by steve101101 on 2008-06-07
If you do a complete uninstall all associated files are erased. Therefore, you may have already deleted the files. Your are correct in your code to remove packages though ...
```

sudo apt-get remove NAMEOFPROGRAM

```

---

### Post by steve101101 on 2008-06-07
also try this ...
```

sudo apt-get autoremove

```

This will remove unused packages.

---

### Post by Elos on 2008-06-07
Hi thanks paqman for replying , first i go to synaptic package manager right click the program and select mark for removal. after the actions are applied i go to synaptic manager again and click status , then select not installed(residual config) and marked the programs listed there for complete removal.

---

### Post by steve101101 on 2008-06-07
if you want to remove everything including configuration files do a complete removal.

---

### Post by steve101101 on 2008-06-07
can you type this in your terminal for me 

```

sudo apt-get autoremove

```

---

### Post by Elos on 2008-06-07
thanks steve , i have tried the autoremove and autoclean but the results keep coming back 

autoremove : 
liang@liang-desktop:~$ sudo apt-get autoremove

Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by steve101101 on 2008-06-07
> **Elos said:**
> thanks steve , i have tried the autoremove and autoclean but the results keep coming back 

autoremove : 
liang@liang-desktop:~$ sudo apt-get autoremove

Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have the same files as you do when i removed wine from my computer. I would not worry about it b/c they are basic config files or an icon or 2.

---

### Post by Elos on 2008-06-07
that was what i thought at first , and i would agree with you but the problem now is that because i wanted to play a game called "touhou",so i tried installing and uninstalling different version of wine, and in the end after multiple install and reinstall, when i type locate wine,
the results keep getting longer???
it seems as though with each install and uninstall, more and more pieces of wine leftovers are in my ubuntu???

---

### Post by steve101101 on 2008-06-07
> **Elos said:**
> that was what i thought at first , and i would agree with you but the problem now is that because i wanted to play a game called "touhou",so i tried installing and uninstalling different version of wine, and in the end after multiple install and reinstall, when i type locate wine,
the results keep getting longer???
it seems as though with each install and uninstall, more and more pieces of wine leftovers are in my ubuntu???

you can always delete these files manually using nautalis (the file manager) or the terminal. If they are in a root area of the drive you will have to use the terminal to delete them. 

Also if you want to get a game running in linux, your best bet is to find someone who has done it already so they can help you.

---

### Post by steve101101 on 2008-06-07
to delete files using the terminal use the following code

```

sudo rm /LOCATION/.../LOCATION/FILETOBEREMOVED

```

---

### Post by sailor2001 on 2008-06-07
are they in /usr/share/applications?

---

### Post by Elos on 2008-06-07
Steve : errm about the gaming of touhou , i give up aready, since the best wine version for it would be 0.9.45 which required libldap2 but the current ubuntu 8.04 has auto upgrade it to libldap-2.4-2

sailor: sorry i don't know but i posted this hope it helps ? :

FECU:

liang@liang-desktop:~$ locate fceu
/usr/share/app-install/desktop/fceu.desktop
/usr/share/app-install/desktop/gfceu.desktop
/usr/share/app-install/icons/gfceu.png

NEXUIZ
liang@liang-desktop:~$ locate nexuiz
/usr/share/app-install/desktop/nexuiz.desktop
/usr/share/app-install/icons/nexuiz48x48.png

TREMULOUS
liang@liang-desktop:~$ locate tremulous
/usr/share/app-install/desktop/tremulous.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_tremulous.xpm

AMERICASARMY
sorry but cant locate?????

liang@liang-desktop:~$ locate AMERICASARMY
liang@liang-desktop:~$


WINE
liang@liang-desktop:~$ locate wine
/etc/apt/sources.list.d/winehq.lis
/etc/apt/sources.list.d/winehq.list
/etc/apt/sources.list.d/winehq.list.save
/home/liang/.wine
/home/liang/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fliang%2FDesktop%2Fwine.xml
/home/liang/Desktop/wine
/usr/share/app-install/desktop/wine.desktop
/usr/share/app-install/desktop/wineconfig.desktop
/usr/share/app-install/desktop/winefish.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_winefish-icon.png
/usr/share/app-install/icons/wineconfig.png
/usr/share/apps/katepart/syntax/winehq.xml
/usr/share/icons/crystalsvg/128x128/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/16x16/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/22x22/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/32x32/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/48x48/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/64x64/mimetypes/exec_wine.png
/usr/share/python-support/guidance-backends/wineread.py
/usr/share/python-support/guidance-backends/winewrite.py
/var/cache/apt/archives/wine-dev_1.0~rc3~winehq0~ubuntu~8.04-1_i386.deb
/var/cache/apt/archives/wine_0.9.59-0ubuntu5_i386.deb
/var/cache/apt/archives/wine_1.0~rc3~winehq0~ubuntu~8.04-1_i386.deb
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_hardy_main_bina ry-i386_Packages
/var/lib/apt/lists/partial/wine.budgetdedicated.com_apt_dists_hardy_Release
/var/lib/apt/lists/partial/wine.budgetdedicated.com_apt_dists_hardy_Release.g pg
/var/lib/dpkg/info/wine.list
/var/lib/dpkg/info/wine.postrm
/var/lib/python-support/python2.5/wineread.py
/var/lib/python-support/python2.5/wineread.pyc
/var/lib/python-support/python2.5/winewrite.py
/var/lib/python-support/python2.5/winewrite.pyc

TO ALL
 question 1) :is it ok if i leave the results files  FECU:NEXUIZ TREMULOUS and AMERICASARMY  alone?
 .
question 2 ) FECU:NEXUIZ TREMULOUS and AMERICASARMY as well as wine : which files when remove will not harm the system. and i am able to still reinstall the programs FECU:NEXUIZ TREMULOUS and AMERICASARMY as well as wine through synaptic package manager if i want to play those games again in the future?

questions 3) which files should i remove and which files i should just leave it alone? sorry for all the troubles cause

---

### Post by Paqman on 2008-06-07
> **Elos said:**
> 
it seems as though with each install and uninstall, more and more pieces of wine leftovers are in my ubuntu???

Well Wine is, by definition, a cludge. It's an amazingly useful piece of software, and i'm amazed it works at all, but it's not very elegant and there's a lot that you have to do by hand.

Just manually delete anything that relates to software that's not on your system any more.

---

### Post by steve101101 on 2008-06-07
I believe those are installation files. sorry I am tired. I have been up for over a day now.

Any file in /usr/share/app-install/ is fine to keep. There will be a few of these for every program in symnaptic I believe.

---

### Post by steve101101 on 2008-06-07
These are all fine :

FECU:

liang@liang-desktop:~$ locate fceu
/usr/share/app-install/desktop/fceu.desktop
/usr/share/app-install/desktop/gfceu.desktop
/usr/share/app-install/icons/gfceu.png

NEXUIZ
liang@liang-desktop:~$ locate nexuiz
/usr/share/app-install/desktop/nexuiz.desktop
/usr/share/app-install/icons/nexuiz48x48.png

TREMULOUS
liang@liang-desktop:~$ locate tremulous
/usr/share/app-install/desktop/tremulous.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_tremulous.xpm

-----------------------------------------------------------------------------

how come your wine files keep increasing, have you completely uninstalled it and/or used autoclean / autoremove

---

### Post by Elos on 2008-06-07
paq & steve : i dunt mind manually deleting wine leftovers but i am scared that i might delete installer files (not sure how to call it), which would result in me being unable to install wine again through synaptic package manager or terminal or worse, delete something that would harm my system.===>( it happened before as i follow some instruction to use deborphan to remove orphan packages, which result in my system to be unable to get pass its routine check thus now i have to press esc every time my system boots to skip the routine check. )

*PS i am NOT blaming the person who thought others how to clean up the system through deborphan or anything.

thus i would appreciated it if someone would tell me what to delete and what to leave it alone

---

### Post by Paqman on 2008-06-07
> **Elos said:**
> paq & steve : i dunt mind manually deleting wine leftovers but i am scared that i might delete installer files (not sure how to call it), which would result in me being unable to install wine

The trash bin is your friend. If you delete something and it causes breakage, just restore it from the bin.

---

### Post by Elos on 2008-06-07
thanks steve, so other then /usr/share/app-install files , the rest i can delete? 

**pls feel free to reply when u feel fine after your rest.
and many thanks again.

---

### Post by Elos on 2008-06-07
paq : agreed , but what i fear is like the deborphan incident, after deleting, i can't even get into ubuntu's log in page , can't even get close to trash bin to recover deleted files.

in addition, when i use terminal to delete(steve 's method),the delete files are not in trash bin as they are removed completely .

---

### Post by soxs on 2008-06-07
```
sudo apt-get remove --purge <yourapp>
``` will clear allmost all userdata
.xpms will be kept

wine is a special case. It will always keep $HOME/.wine folder, as it would suck to have to reinstall apps you installed in a previous version of wine.

In generall you will always have to use
```
sudo updatedb #(to update the locate database)
locate <yourapp>
```and remove it via```
 rm -Rvf <wherever the pendandt folder/thingy is>
```** (NOTE:this command can be evil (as it removes the data unrecoverably!), if you do not know what you do, so CAUTION FIRST!)**
Note: There will always stay some small files (e.g. warsow will keep user settings and so on, which in general is useful as you will keep your settings inbetween versions when you simply upgrade it)

---

### Post by Elos on 2008-06-07
soxs : thank you for your help , about the wine , i did delete the whole wine folder by going into my user's home folder and keying control-H , to show hidden folder and delete the ".wine" folder but when i use "locate wine"  i still get this :

liang@liang-desktop:~$ locate wine
/etc/apt/sources.list.d/winehq.lis
/etc/apt/sources.list.d/winehq.list
/etc/apt/sources.list.d/winehq.list.save
/home/liang/.wine
/home/liang/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fliang%2FDesktop%2Fwine.xml
/home/liang/Desktop/wine
/usr/share/app-install/desktop/wine.desktop
/usr/share/app-install/desktop/wineconfig.desktop
/usr/share/app-install/desktop/winefish.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_winefish-icon.png
/usr/share/app-install/icons/wineconfig.png
/usr/share/apps/katepart/syntax/winehq.xml
/usr/share/icons/crystalsvg/128x128/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/16x16/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/22x22/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/32x32/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/48x48/mimetypes/exec_wine.png
/usr/share/icons/crystalsvg/64x64/mimetypes/exec_wine.png
/usr/share/python-support/guidance-backends/wineread.py
/usr/share/python-support/guidance-backends/winewrite.py
/var/cache/apt/archives/wine-dev_1.0~rc3~winehq0~ubuntu~8.04-1_i386.deb
/var/cache/apt/archives/wine_0.9.59-0ubuntu5_i386.deb
/var/cache/apt/archives/wine_1.0~rc3~winehq0~ubuntu~8.04-1_i386.deb
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_hardy_main_bina ry-i386_Packages
/var/lib/apt/lists/partial/wine.budgetdedicated.com_apt_dists_hardy_Release
/var/lib/apt/lists/partial/wine.budgetdedicated.com_apt_dists_hardy_Release.g pg
/var/lib/dpkg/info/wine.list
/var/lib/dpkg/info/wine.postrm
/var/lib/python-support/python2.5/wineread.py
/var/lib/python-support/python2.5/wineread.pyc
/var/lib/python-support/python2.5/winewrite.py
/var/lib/python-support/python2.5/winewrite.pyc

and the problem is after repeat installing and uninstalling wine the small files keep getting more and more as the list keep growing.

**the last four files are the same???? seem like the same small files left over after repeat installing and uninstalling wine.

last i appreciate your help but just as u have said your method needs to practice precaution, thus can u help me identify which files i shouldn't delete?

as i feared a repeat of my deborphan incident.

sorry for the trouble cause and thanks again.

---

### Post by soxs on 2008-06-07
no .py and pyc are _NOT_ identically
it may grow with different wine versions, as they always bring extensions/bugfixes and so on..
There is a thank you button :-P

---

### Post by Elos on 2008-06-08
soxs , i jus click the thank you button ,:)

just curious what does the button does actually? other than thank you i mean , sorry just got into this forum so there are lots of things i do not know

---

### Post by cariboo on 2008-06-08
You are getting some band info about autoremove and clean. Autoremove removes files that have been replaced by newer versions and are no longer needed. clean just removes packages from /var/cache/apt/archives. If you remove programs by using synaptic it will always leave a few residual files that have no effect on the running of your computer.

Jim

---

