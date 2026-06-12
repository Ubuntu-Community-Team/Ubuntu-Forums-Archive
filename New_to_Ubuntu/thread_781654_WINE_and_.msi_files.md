---
title: "WINE and .msi files"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-04
Hi folks,

I've hunted for beginner's guides to WINE, followed a few places' instructions on how to install .msi files for WINE... tried the instructions... and nothing worked. I'm completely confused/lost. 

The program I am trying to install in WINE is SyncToy, so I can use it to backup my files. My documents live on a separate NTFS partition from both my Linux and Windows installs. 

As to configure WINE from the ground up, I created a "Wine C Drive" folder in my home folder, and configured wine to use that as the windows C drive. However, whenever its installing a program it installs to some hidden folder .wine/drive_c... or something like that. I'm just confused as to why it won't take my designated folder for C, also. 

Very very very very lost... 

-'Mage

---

### Post by Darkdelusions on 2008-05-04
The .wine/drive_c/Programs Files/ is wines default folder. 

There are a couple of things you can do here. 

When installing Synctoys you should prompted with a screen where it should install and you can point it to your Wine_C_drive.. OR you can manually copy the folder to your Wine_C_drive.


**Edit #1**I was unable to find SyncToy in wines app datebase so there is a chance it may not work

**Edit #2** Also there is really no need to change the default folder you can access all your programs from the Applications>Wine

**Edit #3** Here is how to install an msi file

Installing from an .msi file

You can install .msi files with the msiexec.exe utility. This command is built into Wine, so you don't have to install Windows Installer from Microsoft.
If the .msi file is called msifile.msi you just have to type msiexec /i msifile.msi and the application will be installed.

Note:
Make sure you're not using a native version of msi.dll, but the builtin one.

---

### Post by RequinB4 on 2008-05-04
It is generally best to retain the default directory (.wine/drive_c/) as your C:\ drive in wine.  This is the directory that all windows program run in wine will see as C:\

Additionally, you may want to download winetricks if you are trying to install a common msi ([http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)).

To install .msi files:

```

msiexec /i FILE.msi

```

Depending on your tutorial, You may have to edit the way that wine views your new file

```

winecfg

```


When in doubt, follow the instructions before messing around with stuff in wine :guitar:

Good luck!

---

