---
title: "Install 32 bit wine to 64 bit Dapper without chroot"
date: 2006-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Kilz on 2006-05-31
**Feisty has a 64bit wine deb available from the[ the WineHQ]("http://www.winehq.org/site/download-deb"). This page is no longer supported on new versions of Ubuntu but is left in place for those running older versions that are still current releases like the Long term release Dapper Drake. (My personal favorite Ubuntu version)**

I was recently asked to [add this howto to the Ubuntu Wiki]("https://help.ubuntu.com/community/WineForAMD64") :D 
I will be keeping both versions up to date and this thread will serve as a place to help those who have problems with both this post and the wiki entry.

Here is the howto for Edgy and Dapper

Ok download the wine package.  The version number is now at 9.43 but could change. There is a package for Edgy and Dapper, if you run either of those get that one and just edit the commands.

[http://wine.budgetdedicated.com/apt/pool/main/w/wine/](http://wine.budgetdedicated.com/apt/pool/main/w/wine/)

get the libxxf86dga1 package

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibxxf86dga%2Flibxxf86dga1_1.0.0-0ubuntu3_i386.deb&md5sum=f1f2a20a6db2bf5eb44db45cdb3a1337&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibxxf86dga%2Flibxxf86dga1_1.0.0-0ubuntu3_i386.deb&md5sum=f1f2a20a6db2bf5eb44db45cdb3a1337&arch=i386&type=main)
Save the files to your desktop.

First we will install the needed libraries.
```
cd ~/Desktop
dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb libs
sudo cp ~/Desktop/libs/usr/lib/* /usr/lib32
```

Next we will install wine

For Dapper Drake (Ubuntu 6.06)
```
sudo dpkg --force-architecture -i wine_0.9.43~winehq0~ubuntu~6.06-1_i386.deb 
```

For Edgy Eft (Ubuntu 6.10)
```
sudo dpkg --force-architecture -i wine_0.9.43~winehq0~ubuntu~6.10-1_i386.deb 
```

You may have to edit the last command to reflect the version number of the .deb you downloaded.

Test it out by typing winecfg, the wine controll pannel will should start up.

When you add windows programs the launcher it places may not have a pretty icon, you may get errors saying it cant find the icon, but this is easy to fix. Right click on the launcher, select "Properties" from the menu, then click on the icon next to name in the properties box. Search for an icon and click open.

[COLOR="Blue"][SIZE="4"]Sidenet Setup Script[/SIZE][/COLOR]
If you followed the manual instructions you need to install the Sidenet script. Wine versions  0.9.16 - 0.9.41, some additional setup needs to be done. Sidenet adds fonts, a virtual c drive in you home folder, and sets up the windows dll's in the wine registry. So you may want to install it anyway on the newer versions.
Please do not run this setup script with sudo.
[Download the file]("http://home.comcast.net/~deletebox/sidenet.tar.gz") to your desktop. Open a terminal and enter
```
cd ~/Desktop 
tar -xzvf sidenet.tar.gz sidenet

```
Then we change the directory and run the script.
```
cd ~/Desktop/sidenet 
./setup
```



[COLOR="Blue"][SIZE="4"]World of Warcraft[/SIZE][/COLOR]
This section is outdated. Wine above 0.9.32 dose not need patching and runs WoW with few problems. The section is in place in case someone running an older version wonders why it doesnt run right.
World of Warcraft can be run under wine. But it must be compiled with patches to make that possible. Compiling wine on the 64bit platform is almost impossible. But it appears that someone is making .deb files of wine that include the patches. [You can download the file]("http://thepiratecove.org/files/wine-0.9.21_wow_i386.deb") and use the install instructions above if you want to play WOW. 

[COLOR="Blue"][SIZE="4"]Edgy Eft[/SIZE][/COLOR]
I had a long conversation on the developers mailing list. In it I found out that since they now have a 64bit open office they will be removing the default install of ia32 packages from versions from Edgy on. These packages contain the 32bit libaries for running 32bit applications on 64bit Ubuntu. 
Because of this some more packages will need to be installed. They are in the repositories and should install with apt. So open a terminal and enter.
```
sudo apt-get install ia32-libs
```
We may be addibng more packages as development continues. If you have any problems make a post. The error will contain the following.
```
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv":
``` Mention that you are running Edgy  or Feisty if you are. Copy and paste into the post the complete error from the terminal.

[COLOR="Blue"][SIZE="4"]Common Errors:[/SIZE][/COLOR]
```
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
```
or 
```
X Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 142 (GLX)
Minor opcode of failed request: 3 (X_GLXCreateContext)
Serial number of failed request: 14
Current serial number in output stream: 15
```
To fix these errors you need to install/update the drivers for your video card to enable openGL. To test if they are enabled type in glxgears in the terminal. If you do not see a window open with 3 rotating gears it confirms you need the drivers.
```

error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```
[The solution for people with Nvidia cards that have this error can be found here.]("http://www.ubuntuforums.org/showthread.php?t=199589")

No Sound in Windows applications
or 
```
wine depends on libaudio2; however:
Package libaudio2 is not installed.
```
You may need to install the 32bit sould libraries. You can use Synaptic  to install lib32asound2 and ia32-libs-sdl or open a terminal and type in.
```
sudo apt-get install lib32asound2 ia32-libs-sdl
```
You can also try and install the [32bit alsa-oss package ]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb")I made for Firefox32. It may help in some cases.

Cant save registry error.
```
$ wineserver: could not save registry branch to /home/*****/.wine-*****/system.reg : No such file or directory
```
You need to install the sidenet script.

[COLOR="Blue"][SIZE="4"]Windows Applications[/SIZE][/COLOR]
Wine is not perfect. You are not guaranteed of getting every Windows application working. If you need information or help setting up a Windows application please Visit the [URL="http://appdb.winehq.org/"]Wine Application Database. 
[/URL] This Howto only covers Wine itself. There are to many Windows Applications to be able to support the installation of all of them in this thread.

Updated: Added latest version of Wine - 9.17
Edit - 7-13-2006: Added modified sidenet script to fix setup issues with newer wine versions.
Edit - 8-16-2006: Added wine-9.19 script and changed howto to reflect new version.
Edit 3-16-07: Updated to wine 0.9.32
Edit 4-25-07: Added Feisty package and updated howto to Feisty and wine 0.9.35

---

### Post by Hickeroar on 2006-06-05
I get this when running winecfg:

ryan@Hickeroar:~/WINEINSTALL$ winecfg
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual

The config program starts up, but thats about it.  I'm not sure what exactly i'm doing wrong here.  Any help would be appreciated...  Is there some part of the setup that i havent done right?

Also, I'm trying to run (Valve's) steaminstall.exe and it gives me a popup that says:
"Could not initialize installation.  File size expected=725365, size 725365."

and in the console it says:
Warning: could not find DOS drive for current working directory '/home/ryan/Downloads', starting in the Windows directory.
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual

Thanks!

---

### Post by Rhadamanthos on 2006-06-06
Rock.
This totally worked, and is the simplest way I've seen yet to get AMD64 working with wine. Thanks for the great guide! I've spent **hours** on this, and these steps took me all of 10 minutes.

---

### Post by Kilz on 2006-06-07
[QUOTE=Rhadamanthos]Rock.
This totally worked, and is the simplest way I've seen yet to get AMD64 working with wine. Thanks for the great guide! I've spent hours on this, and these steps took me all of 10 minutes.[/QUOTE]
Your welcome, Im just glad someone found my first howto useful. :)


[QUOTE=Hickeroar]I get this when running winecfg:

ryan@Hickeroar:~/WINEINSTALL$ winecfg
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual

The config program starts up, but thats about it.  I'm not sure what exactly i'm doing wrong here.  Any help would be appreciated...  Is there some part of the setup that i havent done right?

Also, I'm trying to run (Valve's) steaminstall.exe and it gives me a popup that says:
"Could not initialize installation.  File size expected=725365, size 725365."

and in the console it says:
Warning: could not find DOS drive for current working directory '/home/ryan/Downloads', starting in the Windows directory.
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual

Thanks![/QUOTE]

Im not sure either, have you set up your video drivers to enable opengl?

---

### Post by bonzodog on 2006-06-07
hrm...this hasn't worked on my system. I am getting this:
```

Dwarfstar:~/Desktop$ winecfg
/usr/bin/winecfg: line 29: /usr/bin/wine: No such file or directory
/usr/bin/winecfg: line 29: /usr/bin/wine: Success

```

It also mentioned some other dependencies, such as libsane earlier. I installed libsane, then re-ran the install of wine. But it appears to have failed to actually install wine itself.

---

### Post by Kilz on 2006-06-08
[QUOTE=bonzodog]hrm...this hasn't worked on my system. I am getting this:
```

Dwarfstar:~/Desktop$ winecfg
/usr/bin/winecfg: line 29: /usr/bin/wine: No such file or directory
/usr/bin/winecfg: line 29: /usr/bin/wine: Success

```

It also mentioned some other dependencies, such as libsane earlier. I installed libsane, then re-ran the install of wine. But it appears to have failed to actually install wine itself.[/QUOTE]

Is wine in /usr/bin? can you see it if you navigate to the directory with nautilus? If not would you please try again and paste in here the terminal session you used to install wine.

---

### Post by tzenes on 2006-06-08
```
tzenes@Cerveza:~/Desktop$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:winecfg:load_drives GetVolumeInformation() for 'C:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0

```

I also have this opengl problem.  Now I know I have opengl and Freeglut3 installed, however my graphics card is a ATI Radeon Xpress 200M for which neither flgx nor the ati drivers work (so I'm using the Vesa driver), which may be my problem.

Also for some reason I can't seem to change the C: drive.  It defaults to /media/hda1 (which is my NTFS partition), and every time I change it to something on my ext3 partition and hit apply and then close and start up again, its reset to /media/hda1.

---

### Post by Kilz on 2006-06-08
[QUOTE=tzenes]```
tzenes@Cerveza:~/Desktop$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:winecfg:load_drives GetVolumeInformation() for 'C:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0

```

I also have this opengl problem.  Now I know I have opengl and Freeglut3 installed, however my graphics card is a ATI Radeon Xpress 200M for which neither flgx nor the ati drivers work (so I'm using the Vesa driver), which may be my problem.

Also for some reason I can't seem to change the C: drive.  It defaults to /media/hda1 (which is my NTFS partition), and every time I change it to something on my ext3 partition and hit apply and then close and start up again, its reset to /media/hda1.[/QUOTE]

I use sidenet to do the setup of my drives. You have winecfg starting so wine is installed, its just a config problem. [If you would like to try sidenet you can get it here]("http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.9.1.tgz"). It can just setup wine, or setup and install ie and or windows media player.
Do you have your ntfs partition mounted in Ubuntu?

---

### Post by tzenes on 2006-06-08
[QUOTE=Kilz]I use sidenet to do the setup of my drives. You have winecfg starting so wine is installed, its just a config problem. [If you would like to try sidenet you can get it here]("http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.9.1.tgz"). It can just setup wine, or setup and install ie and or windows media player.
Do you have your ntfs partition mounted in Ubuntu?[/QUOTE]

my ntfs partition is mounted in Ubuntu

when I try to use sidenet I get the following errors:

```
SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
Creating shortcut: Start -> Programs -> Program Magager
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
Creating shortcut: Start -> Control Panel
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
Creating shortcut: Start -> Application Uninstaller
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
Creating shortcut: Start -> Wine Configuration
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
Creating shortcut: Start -> Task Manager
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
Creating shortcut: Start -> Programs -> Accesories -> Notepad
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
err:ole:CoGetClassObject class {00021401-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00021401-0000-0000-c000-000000000046} could be created for context 0x1

```

---

### Post by tzenes on 2006-06-08
[QUOTE=tzenes]my ntfs partition is mounted in Ubuntu

when I try to use sidenet I get the following errors:

...[/QUOTE]


Ok, so I ran glxinfo and it showed a serious problem with opengl, which I fixed by changing from the vesa driver to fglrx which fixed that problem, however...

I still get this error:
```
SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
Creating shortcut: Start -> Programs -> Program Magager
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Control Panel
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Application Uninstaller
Creating shortcut: Start -> Wine Configuration
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Task Manager
Creating shortcut: Start -> Programs -> Accesories -> Notepad
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper

```


however it did fix the ```
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
``` problem when I run winecfg

and even better, notepad works (which I assume is a good sign

---

### Post by eran- on 2006-06-09
Hmm... I managed to get rid of that libgtk-1.2.so -problem by installing it manually to my /lib32 folder.

But now I've got another problem, which I cannot solve since I don't know where I can find these packages:
```
LD_PRELOAD=
found gettext in path
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgmodule-1                    .2.so.0: cannot open shared object file: No such file or directory
Wine 0.9.12
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.12".
/usr/local/bin/wt2: line 2946: [: 0.9.12: integer expression expected
/usr/local/bin/wt2: line 2946: [: 0.9.12: integer expression expected
Version of Wine is OK.
Calls to wine are executed as  "wine".
Config is /home/user/.wine/winetools.log.
CDROM is .
/usr/local/winetools/Xdialog: error while loading shared libraries: libgmodule-1                    .2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgmodule-1                    .2.so.0: cannot open shared object file: No such file or directory

```


[offtopic]
Oh, that link to the wine -package on the first page doesn't work anymore... So I tried to install wine by other way instead and winetools.

But if that link would work, I'd try that... Is there a page where I can find that package?
[/offtopic]

---

### Post by Bokonon on 2006-06-09
Wine has just been upgraded, so the  links to .14 don't work anymore.

[Check here]("http://wine.budgetdedicated.com/apt/pool/main/w/wine/")

---

### Post by Kilz on 2006-06-09
[QUOTE=tzenes]Ok, so I ran glxinfo and it showed a serious problem with opengl, which I fixed by changing from the vesa driver to fglrx which fixed that problem, however...

I still get this error:
```
SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
Creating shortcut: Start -> Programs -> Program Magager
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Control Panel
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Application Uninstaller
Creating shortcut: Start -> Wine Configuration
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Task Manager
Creating shortcut: Start -> Programs -> Accesories -> Notepad
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper

```


however it did fix the ```
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
``` problem when I run winecfg

and even better, notepad works (which I assume is a good sign[/QUOTE]

Its just telling you it cant find some icons. You will notice that when you install windoz apps that the lancher wont have a pretty icon. Thats easy to change, right click on the launcher, select properties, click on the icon next to name, search for another icon to replace it. Notepad is working so wine is working.

[QUOTE=Bokonon]Wine has just been upgraded, so the links to .14 don't work anymore.[/QUOTE]
Thanks for the link. I updated the howto to go to the location of the deb file in case the version changes again.

[QUOTE=eran-]But now I've got another problem, which I cannot solve since I don't know where I can find these packages:[/QUOTE] Those are needed for winetools, let me see if I can find a place.

---

### Post by paulpb on 2006-06-09
great howto kilz!  i had the opengl problem too, but installing the nvidia drivers (as opposed to the default drivers that dapper installed) fixed that.

cheers,
paul.

---

### Post by nbv4 on 2006-06-13
I did this yesterday and it totally eorked, but today I had to flatten & reinstall, and this method will not work anymore. I get an error saying "archive type not supported" when I try to open the deb file. Any ideas?

EDIT: I fixed the problem. You need build-essentials installed for the deb files to be extracted. This should be added to the OP.

---

### Post by mo_roodi on 2006-06-14
Dude this is totally awsome, one of the reasons I nearly installed the 32bit version of ubuntu was because of Wine (need Dreamweaver and Photoshop). The only think that doesn't appear to work is the sound... Needs a couple more libraries by the looks of it:

libartsc0
libaudio2

I suppose a bit of googling should help me with those!

Thanks for the nice how-to man!

---

### Post by nbv4 on 2006-06-14
Is it possible to get WineTools to work using this method of installing? Are there any other libraries I have to "sneak" in?

---

### Post by Kilz on 2006-06-15
[QUOTE=nbv4]I did this yesterday and it totally eorked, but today I had to flatten & reinstall, and this method will not work anymore. I get an error saying "archive type not supported" when I try to open the deb file. Any ideas?

EDIT: I fixed the problem. You need build-essentials installed for the deb files to be extracted. This should be added to the OP.[/QUOTE]
The original howto did say that you need to have dpkg-dev installed. This gets installed when you install the build-essentials package. But to help others I am modifying the howto to make it clear to install the dpkg-dev package.

[QUOTE=mo_roodi]Dude this is totally awsome, one of the reasons I nearly installed the 32bit version of ubuntu was because of Wine (need Dreamweaver and Photoshop). The only think that doesn't appear to work is the sound... Needs a couple more libraries by the looks of it:

libartsc0
libaudio2

I suppose a bit of googling should help me with those!

Thanks for the nice how-to man![/QUOTE]
Your welcome, If you find you need some libs that you dont already have installed [you can search here.]("http://packages.ubuntu.com/")

[QUOTE=nbv4]Is it possible to get WineTools to work using this method of installing? Are there any other libraries I have to "sneak" in?[/QUOTE] From what I have read on the subject winetools is having problems finding gtk lib's, even if they are installed. You can try and [look here]("http://packages.ubuntu.com/") for the lib's. But I cant say if it will work or not. Personaly I perfer [sidenet]("http://sidenet.ddo.jp/winetips/config.html") to setup wine, then use winecfg that comes with wine.

---

### Post by henriquemaia on 2006-06-15
I followed your HowTo and installed wine just fine. It works great. Thanks a lot.

---

### Post by calenton on 2006-06-18
How do I extract the archive data.tar.gz from libxxf86dga1_1.0.0-0ubuntu3_i386.deb (I'm a newbie)?

---

### Post by Kilz on 2006-06-19
[QUOTE=calenton]How do I extract the archive data.tar.gz from libxxf86dga1_1.0.0-0ubuntu3_i386.deb (I'm a newbie)?[/QUOTE]
Right click on the .deb archive and select extract here. You can also click "Open with Other Application and select the Archive Manager :D  We were all newbies once.

---

### Post by killzoneman0 on 2006-06-20
how do i start wine? does it have a gui?

---

### Post by Kilz on 2006-06-24
[QUOTE=killzoneman0]how do i start wine? does it have a gui?[/QUOTE]
Wine dose not have a gui. Right click on an exe, select "open with other application" if you dont see wine. At the bottom of the application list click "use a custom command" type in wine and click open.

---

### Post by cimotablue on 2006-06-24
Whenever i go to get the libxxf86dga1 package, i get another .deb file, and not an archive. its i386 so it won't open either

---

### Post by cimotablue on 2006-06-24
I have 64x amd, and the architecture is i386, when i go to winecfg, it wont install, nor will the add/remove programs work.

---

### Post by Kilz on 2006-06-24
[QUOTE=cimotablue]Whenever i go to get the libxxf86dga1 package, i get another .deb file, and not an archive. its i386 so it won't open either[/QUOTE]
Yes the libxxf86dga1 is a .deb file, if you installed dpkg-dev like the first step of the howto says, your archive program should be able to open it up to extract its contents.
[quote=cimotablue]I have 64x amd, and the architecture is i386, when i go to winecfg, it wont install, nor will the add/remove programs work.[/quote]
If you installed the i386 version of Dapper, but have a 64 bit possessor this howto is not for you. The howto is for people running the amd64 version of Dapper. If you have the i386 version of Dapper Synaptic will install wine.
Winecfg is a a configuration program for wine. The add and remove program buttons you see when it opens are not to add programs to wine. But rather to tell wine what version of windows to emulate and other program specific configurations to run.
To install windows programs to Ubuntu with wine installed. Right click on the install exe, select "open with other application" if you don't see wine. At the bottom of the application list click "use a custom command" type in wine and click open.

---

### Post by Arathorn on 2006-06-27
I've installed Wine following the procedure in the how-to and it seems to be installed, but when I type winecfg in the Konsole I get the following error:
```
maurits@mauritscomp:~$ winecfg
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
```
I've tried running the notepad.exe from */drive_c/windows but then there's only a loading thingy in the taskbar for a while, untill that disappears.
I have the official ATI drivers installed. Can anybody help me?

---

### Post by Kilz on 2006-06-28
[QUOTE=Arathorn]I've installed Wine following the procedure in the how-to and it seems to be installed, but when I type winecfg in the Konsole I get the following error:
```
maurits@mauritscomp:~$ winecfg
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
```
I've tried running the notepad.exe from */drive_c/windows but then there's only a loading thingy in the taskbar for a while, untill that disappears.
I have the official ATI drivers installed. Can anybody help me?[/QUOTE]

You might want to go back over the Howto This line from your errors

```
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
```
Tells me that wine is looking for the lib you place when you extract and copy the libxxf86dga1 package. It might have not worked for some reason. Look in /usr/lib32 and see if you can find "libXxf86dga.so.1" if not , thats defiantly the reason it isn't working.

---

### Post by Arathorn on 2006-06-30
Thank you, that was indeed the case. I copied the lib again and now it seems to work.

---

### Post by maximilian35 on 2006-07-03
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual


Can you please tell me how can i fix the opengl problem?

---

### Post by Kilz on 2006-07-04
[QUOTE=maximilian35]fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual


Can you please tell me how can i fix the opengl problem?[/QUOTE]
You need to install/update the drivers for your video card.

---

### Post by x64Jimbo on 2006-07-07
YES! Thank you so much! Now I can run 32 bit windows programs in my 64 bit Linux OS! What a cool thing!
Next thing I'm going to try is getting a Windows Firefox running in 64 bit linux so I can install flash. ;)
Edit: Done! All I had to do was download the installer file and run it. Then I went to homestarrunner.com (my default site for testing flash) and then installed the plugin automatically! Woo Hah! 
I even installed my Command & Conquer games with Wine so I can now play my favorite PC games in Linux. Next up is Unreal Tournament ;) I'll probably get a subscription to Cedega at some point to support their development. On second thought, I might just donate straight to the Wine project.

---

### Post by cucisan on 2006-07-11
great howto! works flawlessly

---

### Post by bluppfisk on 2006-07-11
doesn't do it for me. OpenGL trouble, and apparently I cannot get it working on my SiS760 integrated card. So I tried the software mesa instead. Doesn't do either. So I left it for a while. Today, when I was installing Google Picasa for Linux, I noticed that it uses Wine for certain tasks. So I conclude that it must be possible to run wine without openGL support, but I don't know how.

---

### Post by Miki01 on 2006-07-11
Hey Kilz! Me again >_<. Anyways, I was going through your tutorial, and when i got to this point, I had this error:

> miki@Ubuntu:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.16~winehq1~ubun tu~6.06-1_i386.deb
dpkg: error processing wine_0.9.16~winehq1~ubuntu~6.06-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.16~winehq1~ubuntu~6.06-1_i386.deb


For some reason, everything I do in terminal, there's never a file or directory. When I go to my desktop, I can see it perfectly clear...

---

### Post by Kilz on 2006-07-11
> **Miki01 said:**
> Hey Kilz! Me again >_<. Anyways, I was going through your tutorial, and when i got to this point, I had this error:



For some reason, everything I do in terminal, there's never a file or directory. When I go to my desktop, I can see it perfectly clear...
Thats strange, but let me see what I can do.

---

### Post by Miki01 on 2006-07-11
EDIT: Okay, its working now, I got my setup.exe file to appear on the applications box. What now? How do I install it? Is it installed already? How do I go about executing my game? Or is it not installed yet? I clicked it, its on the list now, right under Default Settings... So what do I do in order to get it to work?

---

### Post by hothamp on 2006-07-12
I used your insall script and get this error
[PHP]shell-init: error retrieving current directory: getcwd: cannot access parent directories: No s uch file or directory
wine: creating configuration directory '/home/hampm/.wine'...
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No s uch file or directory
chdir: error retrieving current directory: getcwd: cannot access parent directories: No such f ile or directory
chdir: error retrieving current directory: getcwd: cannot access parent directories: No such f ile or directory
Warning: could not find DOS drive for current working directory '', starting in the Windows di rectory.
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  3323
  Current serial number in output stream:  3324
wine: wineprefixcreate failed while creating '/home/hampm/.wine'.
hampm@hampm-dt:~/Desktop/wine$ wineserver: could not save registry branch to /home/hampm/.wine -x59Mso/system.reg : No such file or directory
wineserver: could not save registry branch to /home/hampm/.wine-x59Mso/userdef.reg : No such f ile or directory
wineserver: could not save registry branch to /home/hampm/.wine-x59Mso/user.reg : No such file  or directory
[/PHP]

---

### Post by symbol on 2006-07-12
hi,thanks a lot
and I get a new problem

my local is zh_CN-UTF8&#65292;wine can work,but wine runs too slow!!!


How can I make wine run fast?

system:ubuntu 6.06+KDE desktop  amd 64bit edition
wine:0.9.16

---

### Post by Kilz on 2006-07-12
> **hothamp said:**
> I used your insall script and get this error
[PHP]shell-init: error retrieving current directory: getcwd: cannot access parent directories: No s uch file or directory
wine: creating configuration directory '/home/hampm/.wine'...
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No s uch file or directory
chdir: error retrieving current directory: getcwd: cannot access parent directories: No such f ile or directory
chdir: error retrieving current directory: getcwd: cannot access parent directories: No such f ile or directory
Warning: could not find DOS drive for current working directory '', starting in the Windows di rectory.
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  3323
  Current serial number in output stream:  3324
wine: wineprefixcreate failed while creating '/home/hampm/.wine'.
hampm@hampm-dt:~/Desktop/wine$ wineserver: could not save registry branch to /home/hampm/.wine -x59Mso/system.reg : No such file or directory
wineserver: could not save registry branch to /home/hampm/.wine-x59Mso/userdef.reg : No such f ile or directory
wineserver: could not save registry branch to /home/hampm/.wine-x59Mso/user.reg : No such file  or directory
[/PHP]

Dose the wine control panel start up if you enter the command winecfg in a terminal?

---

### Post by BatteryCell on 2006-07-12
> **Kilz said:**
> I have started writing install scripts. [If you want it is avalaible here]("http://tghc.org/files/wine-install.tar.gz"). It will automaticly install everything needed for wine with 2 simple commands found in the readme file in the archive.


Lol thanks these work perfectly :-)

---

### Post by Kilz on 2006-07-12
> **BatteryCell said:**
> Lol thanks these work perfectly :-)

The script has been removed. There are issues with it I'm going to have to work out dealing with writing to the .wine file. If you installed wine with the script please remove it with.
```
sudo apt-get remove wine32
```
Then follow the normal howto.

---

### Post by Ryan H on 2006-07-12
How do I
> 
extract the data.tar.gz from libxxf86dga1 to your desktop
extract the contents of data.tar.gz to your desktop

?

The file I downloaded was libxxf86dga1_1.0.0-0ubuntu3_i386.deb, now what do I do with it?

-Ryan

---

### Post by Kilz on 2006-07-12
> **Ryan H said:**
> How do I

?

The file I downloaded was libxxf86dga1_1.0.0-0ubuntu3_i386.deb, now what do I do with it?

-Ryan

extract the data.tar.gz from libxxf86dga1 to your desktop
extract the contents of data.tar.gz to your desktop
There should be a /usr/lib folder on the desktop now

```
sudo cp ~/Desktop/usr/lib/* /usr/lib32 
cd ~/Desktop 
sudo dpkg --force-architecture -i wine_0.9.14~winehq1~ubuntu~6.06-1_i386.deb
```


You may have to edit the last command to reflect the version number of the .deb you downloaded.
Test it out by typing winecfg, the wine controll pannel will should start up.

When you add windows programs the launcher it places may not have a pretty icon, you may get errors saying it cant find the icon, but this is easy to fix. Right click on the launcher, select "Properties" from the menu, then click on the icon next to name in the properties box. Search for an icon and click open.

---

### Post by wazzie on 2006-07-12
what does wine do? why install 32 bit? whats chroot? im like an outta control five year old playing twenty questions.

---

### Post by hothamp on 2006-07-13
> **Kilz said:**
> Dose the wine control panel start up if you enter the command winecfg in a terminal?No it doesn't :(

---

### Post by hothamp on 2006-07-13
I redid my os because of some networking issues I had earlier since it was a farily fresh install was quick and painless so I followed the instructions and after I got the libc6-dev installed lol (was giving me errors) this is what I got when I did the winecfg.  Also the winecfg window did not come up.
[PHP]Preparing to replace wine-dev 0.9.16~winehq0~ubuntu~6.06-1 (using wine-dev_0.9.16~winehq0~ubuntu~6.06-1_i386.deb) ...
Unpacking replacement wine-dev ...
Setting up wine-dev (0.9.16~winehq0~ubuntu~6.06-1) ...
hampm@hampm-desktop:~/Desktop$ winecfg
wine: creating configuration directory '/home/hampm/.wine'...
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  3321
  Current serial number in output stream:  3322
wine: wineprefixcreate failed while creating '/home/hampm/.wine'.
hampm@hampm-desktop:~/Desktop$ wineserver: could not save registry branch to /home/hampm/.wine-HEPq55/system.reg : No such file or directory
wineserver: could not save registry branch to /home/hampm/.wine-HEPq55/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/hampm/.wine-HEPq55/user.reg : No such file or directory
[/PHP]

---

### Post by Kilz on 2006-07-13
> **hothamp said:**
> I redid my os because of some networking issues I had earlier since it was a farily fresh install was quick and painless so I followed the instructions and after I got the libc6-dev installed lol (was giving me errors) this is what I got when I did the winecfg.  Also the winecfg window did not come up.
[PHP]Preparing to replace wine-dev 0.9.16~winehq0~ubuntu~6.06-1 (using wine-dev_0.9.16~winehq0~ubuntu~6.06-1_i386.deb) ...
Unpacking replacement wine-dev ...
Setting up wine-dev (0.9.16~winehq0~ubuntu~6.06-1) ...
hampm@hampm-desktop:~/Desktop$ winecfg
wine: creating configuration directory '/home/hampm/.wine'...
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  3321
  Current serial number in output stream:  3322
wine: wineprefixcreate failed while creating '/home/hampm/.wine'.
hampm@hampm-desktop:~/Desktop$ wineserver: could not save registry branch to /home/hampm/.wine-HEPq55/system.reg : No such file or directory
wineserver: could not save registry branch to /home/hampm/.wine-HEPq55/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/hampm/.wine-HEPq55/user.reg : No such file or directory
[/PHP]

I just finished doing some resarch into the problem. It seems that theere have been some changes to wine. I have found a way to solve the problem and have added it to the first page.


As of wine version .9.16 some additional setup needs to be done. Fortunately I was able to find a script called Sidenet and modify it to do the setup, and a few more nice things. Sidenet adds fonts, a virtual c drive in you home folder, and setup the wine/windows dll's.
[Download the file]("http://tghc.org/files/sidenet.tar.gz"), extract it to your desktop.
```
tar -xzvf sidenet.tar.gz sidenet
```
then run the script.
```
~/Desktop/sidenet/setup
```
Wait for it to get done.

---

### Post by hothamp on 2006-07-13
TY TY TY finally it works!!!!  This is the first time I've ever successfully installed wine.  I had mandrake way back in the day and kept getting errors and wasn't getting all that great support but you guys are fantastic :)

---

### Post by Mickey Mouse on 2006-07-15
Re: Other threads on why people do not use Ubuntu as much as they could.
Sadly, this is the sort of stuff why...

Almost every time one needs to install something, it is this kind of story:

(several hours spent attempting to install something with obscure scripts and failing miserably)

"Oh, by the way, you also need library/script/package X".....

(several more hours spent attempting to install the thing with even more obscure scripts and failing miserably)

"Oh, by the way, you also need library/script/package Y".....

(several more hours spent attempting to install the thing with even more obscure scripts and failing miserably)

Oh, by the way, you also need library/script/package Z.....

---

### Post by sacksank on 2006-07-16
I was having error message for havent installing libxxf86dga1_1.0.0-0ubuntu3_i386.deb.. which now is no longer a problem after doing that. Thank you for the how-to.. this gives me more reason to a full convert to UBUNTU.. thx!

---

### Post by PisstMSTRCHIEF on 2006-07-16
I keep getting and error with the second code:~/Desktop/sidenet/setup

ERROR: Please run setup in wine-config-sidenet directory.

---

### Post by sacksank on 2006-07-17
Now that I got wine up and runnin, how do I install a win app onto it? Can anyone help me? :confused:

---

### Post by PisstMSTRCHIEF on 2006-07-17
As I recall, you just double click a exe. file. Wine should take care of the rest.

---

### Post by x64Jimbo on 2006-07-17
> **PisstMSTRCHIEF said:**
> As I recall, you just double click a exe. file. Wine should take care of the rest.
Alternately, you can run it from the command line if your window manager doesn't get the file association figured out.
wine windows_executable.exe

---

### Post by toykilla on 2006-07-17
When I run this command:

**~/Desktop/sidenet/setup**

I get this error.

[B]ERROR: Please run setup in wine-config-sidenet directory.
Setup aborted.[/B]

any thoughts?

---

### Post by Kilz on 2006-07-17
> **toykilla said:**
> When I run this command:

**~/Desktop/sidenet/setup**

I get this error.

[B]ERROR: Please run setup in wine-config-sidenet directory.
Setup aborted.[/B]

any thoughts?

Try this
```
cd ~/Desktop/sidenet
```
then ```
./setup
```

---

### Post by Kilz on 2006-07-17
> **wazzie]what does wine do? why install 32 bit? whats chroot? im like an outta control five year old playing twenty questions.[/quote]
[I think this will answer all your questions.]("http://www.tghc.org/staticpages/index.php/wine")

[QUOTE=Mickey Mouse said:**
> Re: Other threads on why people do not use Ubuntu as much as they could.
Sadly, this is the sort of stuff why...

Almost every time one needs to install something, it is this kind of story:

(several hours spent attempting to install something with obscure scripts and failing miserably)

"Oh, by the way, you also need library/script/package X".....

(several more hours spent attempting to install the thing with even more obscure scripts and failing miserably)

"Oh, by the way, you also need library/script/package Y".....

(several more hours spent attempting to install the thing with even more obscure scripts and failing miserably)

Oh, by the way, you also need library/script/package Z.....

Wow you had all those problems, and only 4 posts?

---

### Post by fatsheep on 2006-07-20
Downloaded the wine and sidenet scripts and ran the instructions in the wine script readme:

> 
[B]fatsheep@fatsheep:~$ cd ~/Desktop/wine
fatsheep@fatsheep:~/Desktop/wine$ sudo ./wine[/B]
Password:
./wine: line 2: cd: /home/fatsheep/Desktop/Wine: No such file or directory
E: Invalid operation dpkg-dev
--19:42:27--  [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.16~w](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.16~w) inehq0~ubuntu~6.06-1_i386.deb
           => `wine_0.9.16~winehq0~ubuntu~6.06-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:42:27 ERROR 404: Not Found.

dpkg: error processing wine_0.9.16~winehq0~ubuntu~6.06-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.16~winehq0~ubuntu~6.06-1_i386.deb
--19:42:28--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/li](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/li) bxxf86dga1_1.0.0-0ubuntu3_i386.deb
           => `libxxf86dga1_1.0.0-0ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,062 (9.8K) [text/plain]

100%[====================================>] 10,062        --.--K/s

19:42:28 (83.92 KB/s) - `libxxf86dga1_1.0.0-0ubuntu3_i386.deb' saved [10062/1006 2]


Now I open up a new terminal, and followed the sidenet instructions:

> 
[B]fatsheep@fatsheep:~$ cd ~/Desktop/sidenet
fatsheep@fatsheep:~/Desktop/sidenet$ ./setup[/B]

ERROR: Could not find wine installation.
       Setup wine first.
Setup aborted.
fatsheep@fatsheep:~/Desktop/sidenet$


---

### Post by Kilz on 2006-07-20
> **fatsheep said:**
> Downloaded the wine and sidenet scripts and ran the instructions in the wine script readme:



Now I open up a new terminal, and followed the sidenet instructions:

Looks like wine was updated, I have just updated the script, please download the new one.

---

### Post by fatsheep on 2006-07-20
Wine script:

> fatsheep@fatsheep:~$ cd ~/Desktop/wine
fatsheep@fatsheep:~/Desktop/wine$ sudo ./wine
./wine: line 2: cd: /home/fatsheep/Desktop/Wine: No such file or directory
E: Invalid operation dpkg-dev
--22:17:46--  [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.17~winehq0~ubuntu~6.06-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.17~winehq0~ubuntu~6.06-1_i386.deb)
           => `wine_0.9.17~winehq0~ubuntu~6.06-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,719,050 (8.3M) [application/x-debian-package]

100%[====================================>] 8,719,050    247.96K/s    ETA 00:00

22:18:23 (232.38 KB/s) - `wine_0.9.17~winehq0~ubuntu~6.06-1_i386.deb' saved [8719050/8719050]

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package wine.
(Reading database ... 100572 files and directories currently installed.)
Unpacking wine (from wine_0.9.17~winehq0~ubuntu~6.06-1_i386.deb) ...
Setting up wine (0.9.17~winehq0~ubuntu~6.06-1) ...

--22:18:53--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb)
           => `libxxf86dga1_1.0.0-0ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,062 (9.8K) [text/plain]

100%[====================================>] 10,062        --.--K/s

22:18:58 (89.22 KB/s) - `libxxf86dga1_1.0.0-0ubuntu3_i386.deb' saved [10062/10062]


Sidenet:

> fatsheep@fatsheep:~$ cd ~/Desktop/sidenet
fatsheep@fatsheep:~/Desktop/sidenet$ ./setup

SETUP STAGE 1
Stopping wine process ...
Creating ~/.wine ...
Setting up install-time configuration ...
Setting up wine base directory structure ...
Setting up drives ...
Linked /media/cdrom to e drive.
Linked /home/fatsheep/c/windows/fonts -> ~/.fonts
Installing base font ...

SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
Creating shortcut: Start -> Programs -> Program Magager
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Control Panel
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Application Uninstaller
Creating shortcut: Start -> Wine Configuration
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Task Manager
Creating shortcut: Start -> Programs -> Accesories -> Notepad
err:menubuilder:extract_icon32 found no icon
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper

SETUP STAGE 3
Setting up wine configuration ...

wine has been setup


There were a few errors in there yet it appeared to finished anyways.  Works fine with Super Pi.  Thanks a lot for the easy to use script! :)

---

### Post by Kilz on 2006-07-20
> **fatsheep said:**
> 
There were a few errors in there yet it appeared to finished anyways.  Works fine with Super Pi.  Thanks a lot for the easy to use script! :)
Your welcome, I wouldnt worry about the errors, wine just couldnt find some icons for the programs it sees installed. You may notice that launchers do not have pretty icons for things you install. But its easy to change icons. :D

---

### Post by fatsheep on 2006-07-21
Yea the interface does look pretty ugly...  Also, do have the same problem with the invisible text in notepad?  Not that I would ever want to use notepad, just out of curiosity really...

---

### Post by Kilz on 2006-07-21
> **fatsheep said:**
> Yea the interface does look pretty ugly...  Also, do have the same problem with the invisible text in notepad?  Not that I would ever want to use notepad, just out of curiosity really...

No , but you may just have to select a font. Go to Edit > Font in notepad.

---

### Post by jdmpike on 2006-07-22
I get the following error.

/usr/bin/winecfg: line 29: /usr/bin/wine: No such file or directory
/usr/bin/winecfg: line 29: /usr/bin/wine: Success

I saw this earlier in the thread, but didn't see a resolution... What should I do to fix this?

I have tried to re-install with dpkg serveral times, cannot seem to get around this...

Thanks jdmpike.

---

### Post by Kilz on 2006-07-22
> **jdmpike said:**
> I get the following error.

/usr/bin/winecfg: line 29: /usr/bin/wine: No such file or directory
/usr/bin/winecfg: line 29: /usr/bin/wine: Success

I saw this earlier in the thread, but didn't see a resolution... What should I do to fix this?

I have tried to re-install with dpkg serveral times, cannot seem to get around this...

Thanks jdmpike.

Thats because I requested info and never recieved a reply. Would you please look in /usr/bin/ and see if you can see the winecfg file? Also have you installed the sidenet update?

---

### Post by archmichael on 2006-07-23
> **Kilz said:**
> Thats because I requested info and never recieved a reply. Would you please look in /usr/bin/ and see if you can see the winecfg file? Also have you installed the sidenet update?

I'm having the same problem, wine and winecfg is in /usr/bin, but the system can't seem to see them.

Analyzing it, it could have been one of two problems. I didn't run the script in the second terminal, so it seems to have run as root. I chown'd the wine files to my ownership but they still wont run.

The other problem is that I am using Xubuntu, so the xarchiver couldn't unpack the deb file. Being a little too smart, I tried to dpkg libxxf86dga1 using the --force-architecture option.

---

### Post by Kilz on 2006-07-24
> **archmichael said:**
> I'm having the same problem, wine and winecfg is in /usr/bin, but the system can't seem to see them.

Analyzing it, it could have been one of two problems. I didn't run the script in the second terminal, so it seems to have run as root. I chown'd the wine files to my ownership but they still wont run.

The other problem is that I am using Xubuntu, so the xarchiver couldn't unpack the deb file. Being a little too smart, I tried to dpkg libxxf86dga1 using the --force-architecture option.

I wonder if jdmpike is running Xubuntu. 
If you used the dpkg --force-architecture option to install libxxf86dga1 then it installed the libraries to /usr/lib instead of /usr/lib32 where they are suposed to go. This will result in wine not working. I have edited my howto to avoid use of the archive program. Here is the solution after saving the .deb file to your desktop.
```
cd ~/Desktop
dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb libs
sudo cp ~/Desktop/libs/usr/lib/* /usr/lib32
```

The script that installs the wine bianaries has to be run with sudo, the sidenet setup script has a check and wont let you run it as root.

---

### Post by jdseek on 2006-07-27
how about this one, 

```
:~/c/DriversDailyLog$ fixme:ole:CoRegisterMessageFilter stub
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  135
  Current serial number in output stream:  135

```

any ideas? installing this program went fine, went to open it and got greenscreened with that error in the term

---

### Post by Vlatko on 2006-07-29
i get this error after runninf winecfg:

> fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)

i searched the forums, couldn't find anything, any ideas?

btw, the wine control panel does start, only i get that error in the terminal.

---

### Post by Vlatko on 2006-07-29
> **Vlatko said:**
> i get this error after runninf winecfg:



i searched the forums, couldn't find anything, any ideas?

btw, the wine control panel does start, only i get that error in the terminal.
fixed it by selecting alsa as the audio driver in winecfg. now i don't get the error.

---

### Post by Glass_Onion on 2006-08-03
Does anybody have an alternative link for the sidenet download? It won't let me download it.

EDIT: Nevermind, it's letting me download now.

---

### Post by LinuxConvertJune2006 on 2006-08-04
Hi , I am trying to run the two scripts available at the top of the first post in this thread. I got this:
> 
./wine: line 2: cd: /home/name/Desktop/Wine: No such file or directory
E: Invalid operation dpkg-dev
--18:26:19--  [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.17~w](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.17~w) inehq0~ubuntu~6.06-1_i386.deb
           => `wine_0.9.17~winehq0~ubuntu~6.06-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:26:20 ERROR 404: Not Found.

dpkg: error processing wine_0.9.17~winehq0~ubuntu~6.06-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.17~winehq0~ubuntu~6.06-1_i386.deb
--18:26:20--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/li](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/li) bxxf86dga1_1.0.0-0ubuntu3_i386.deb
           => `libxxf86dga1_1.0.0-0ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,062 (9.8K) [text/plain]

100%[====================================>] 10,062        --.--K/s

18:26:21 (66.10 KB/s) - `libxxf86dga1_1.0.0-0ubuntu3_i386.deb' saved [10062/1006 2]

dpkg-deb: failed to chdir to directory: Not a directory
cp: cannot stat `/home/name/Desktop/wine/usr/lib/*': Not a directory



I opened the script up and copy/paste line by line, first line gives me:
> 
sudo apt-get dpkg-dev
E: Invalid operation dpkg-dev



so I stopped and came to ask for some advice ;)

---

### Post by LinuxConvertJune2006 on 2006-08-04
Looks like the script has 2 bugs in it, first line it should be cd ~/Desktop/wine, not Wine

And then its version .18 not .17 of the wine package on the website. Thanks for the script tohugh, helped step me thru it!

---

### Post by rutger83 on 2006-08-05
another bug in the script:

The apt-get dpkg-dev          should be:
    apt-get install dpkg-dev

Wonderfull script! Also like the firerox32 script, you saved me soo much pain in the ***! Thanks a million! :D

---

### Post by Kilz on 2006-08-06
> **rutger83 said:**
> another bug in the script:

The apt-get dpkg-dev          should be:
    apt-get install dpkg-dev

Wonderfull script! Also like the firerox32 script, you saved me soo much pain in the ***! Thanks a million! :D

Thanks for pointing that out. I fixed it.  :D

---

### Post by x64Jimbo on 2006-08-07
Is there a reason you're using apt-get install instead of aptitude install? apt-get is not as good about keeping dependencies.

---

### Post by th3t1nm4n on 2006-08-11
Thanks for the GREAT and VERY MUCH NEEDED guide!!!
I have successfully installed Steam on 64-bit Dapper running and SMP kernel today thanks to your quide! So far everything is going well.
:D :D :D :D :D :D :D :D

---

### Post by AIysandra on 2006-08-11
u said to run this : sudo apt-get install dpkg-dev

and this is what i get...

[B]$ sudo apt-get install dpkg-dev
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  debootstrap: Depends: binutils but it is not going to be installed
  dpkg-dev: Depends: make but it is not going to be installed
            Depends: binutils but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/B]

---

### Post by Kilz on 2006-08-11
> **x64Jimbo said:**
> Is there a reason you're using apt-get install instead of aptitude install? apt-get is not as good about keeping dependencies.

Not really, but Im only installing one package that way, and its dependancies should already be installed. To tell you the truth installing dpkg-dev is a left over and should be removed from the howto. I stoped having people use the file roller to extract and just use dpkg -x now.

> **AIysandra said:**
> u said to run this : sudo apt-get install dpkg-dev

and this is what i get...

[B]$ sudo apt-get install dpkg-dev
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  debootstrap: Depends: binutils but it is not going to be installed
  dpkg-dev: Depends: make but it is not going to be installed
            Depends: binutils but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/B]

It isnt nessasary to install it anymore. It used to be used in the howto up untill a week ago. I forgot to remove it, Im going to now. But for the future you may want to [enable the universe repositories.]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") This will make a lot more software avaiable/installable.

---

### Post by t6435bm on 2006-08-11
Hi! Hey, thank you very very much for this howto... it's the first time i'm seeing wine working! (the last time I had tried was in 1999. Since then i hadn't tried linux again until now, when i wanted to work with blender 64bits, so i'm something like a newbie.)

Ok. I got everything running EXCEPT that i can't open or save files! (not even with notepad.exe -- i don't get the save or open dialog displayed but a crash message and the dead of the application!). There are (at least) two different crash messages... it has to do with memory, i think.

One crash message:

(trying to open or save from notepad.exe) 
```
err:seh:setup_exception nested exception on signal stack in thread 0009 eip 602d0153 esp 7ffddc80 stack 0x231000-0x340000
```

The other crash message:

(trying "Open file..." from firefox.exe)
```
err:seh:setup_exception nested exception on signal stack in thread 0020 eip 602d0153 esp 7ffddc80 stack 0x241000-0x350000
```

which is the same than:

(trying "Open file..." from Macromedia Flash 8 )
```
err:seh:setup_exception nested exception on signal stack in thread 0019 eip 602d0153 esp 7ffddc80 stack 0x241000-0x350000
```

and

(trying "Open file..." from Internet Explorer and then "Browse...")
```
err:seh:setup_exception nested exception on signal stack in thread 0009 eip 602d0153 esp 7ffddc80 stack 0x241000-0x350000
```

Any idea if this is fixable? 

Thanx again!

---

### Post by Kilz on 2006-08-11
> **t6435bm said:**
> Hi! Hey, thank you very very much for this howto... it's the first time i'm seeing wine working! (the last time I had tried was in 1999. Since then i hadn't tried linux again until now, when i wanted to work with blender 64bits, so i'm something like a newbie.)

Ok. I got everything running EXCEPT that i can't open or save files! (not even with notepad.exe -- i don't get the save or open dialog displayed but a crash message and the dead of the application!). There are (at least) two different crash messages... it has to do with memory, i think.


This is a new error I havent seen before.  Type in winecfg in a terminal. A controll pannel should open. Click on the Drives tab. How many drives are listed? Secondly, how did you install explorer?

---

### Post by t6435bm on 2006-08-11
> How many drives are listed? 

Listed are:
C: /home/adm2rtec/c
D: /home/adm2rtec/
E: /media/cdrom
F: /media/sda1/
G: /media/sda6/
H: /media/sda5/
I: /media/hda1/
K: /media/cdrom0
L: /home/adm2rtec
Z: /

All buttons from the dialog work ok.

> how did you install explorer

I used the script "ies4linux" in [http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)
...hey... i see something here now that you mention that... that script created another location for C, another "windows" and "Program Files"... -- nice. Could that be the reason for the crash? How can i remove that or change it and see? If I do "wine regedit.exe" I see keys for Internet Explorer and also for the Macromedia Programs and Firefox...

:confused:

---

### Post by t6435bm on 2006-08-12
Hey Kilz... one can get adicted to this! ](*,)  :)
I tried to remove all changes and reinstall wine, and the problem continued, so I said: "this cannot be an issue from the ies4linux installation"...

WineFile was working, and all dialogs were apparently working also, except the open and save dialogs, so I began to play around with winecfg and see: the issue was solved unlinking all "shell folders" (Desktop Integration Dialog)! :mrgreen: 

Now I can save and open files... The question is... doesn't this happen to everyone???? :-k 

What's happening is that the folder "c" is inside the user's home folder, and Desktop, My Documents, and all other things are linked by default to the home folder! so I suppose that's why the error message is saying "nested". I linked the folders to another location and the open and save dialogs where working ok. :-? 

I hope this "solution" can help someone in the future.

Anyway... now I got another question... How do I get the ALSA driver inside the winecfg dialog? I got no sound. And the ActiveX Control for Macromedias help? It's not working either. Any idea? Url? :confused: 

Thanks!

---

### Post by Kilz on 2006-08-12
> **t6435bm said:**
> Hey Kilz... one can get adicted to this! ](*,)  :)
I tried to remove all changes and reinstall wine, and the problem continued, so I said: "this cannot be an issue from the ies4linux installation"...

WineFile was working, and all dialogs were apparently working also, except the open and save dialogs, so I began to play around with winecfg and see: the issue was solved unlinking all "shell folders" (Desktop Integration Dialog)! :mrgreen: 

Now I can save and open files... The question is... doesn't this happen to everyone???? :-k 

What's happening is that the folder "c" is inside the user's home folder, and Desktop, My Documents, and all other things are linked by default to the home folder! so I suppose that's why the error message is saying "nested". I linked the folders to another location and the open and save dialogs where working ok. :-? 

I hope this "solution" can help someone in the future.

Anyway... now I got another question... How do I get the ALSA driver inside the winecfg dialog? I got no sound. And the ActiveX Control for Macromedias help? It's not working either. Any idea? Url? :confused: 

Thanks!

I can save documents fine, lets hope it was a glitch in the setup someplace. You may have to install some 32bit libs for sound
sudo apt-get install lib32asound2
I never could get flash in ie to work , I installed firefox for windows and flash 8.

---

### Post by t6435bm on 2006-08-13
thank you! i installed the 32 bit libraries and they are working very well, i got audio with wine! :D

well ... right now everything is working, except some details in the macromedia programs which aren't so important right now... i could install flash 9 in internet explorer and firefox for windows... try reading the ies4linux script, maybe there is something there that you can use... i mean, if you actually need to have flash 9 working with wine.

i don't understand why doesn't everyone have the problem with the open and save dialogs... but i'm happy i could solve that.

now i can work with the project i wanted to work using blender 64bits and enlightenment as window manager without needing to reboot too much into windows. excelent...

thanks again! see you around.

---

### Post by junnu on 2006-08-16
I have a problem with wine. At least I think so. I installed wine like shown on this thread and it installed fine, winecfg and some apps I tried run fine, with the exception that it complained about libGL.so.1. I fixed it by linking, as told to here and then it went haywire:
```
/media/cdrom0$ wine ./SETUP.EXE
err:module:load_builtin_dll failed to load .so lib for builtin L"wined3d.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:ddraw:DDRAW_Create Couldn't load WineD3D - OpenGL libs not present?

```I tried undoing the links but with no luck, same with recopying the libs. After that I installed the ATI propietary drivers hoping it would help. glxgears runs smoothly but it still gives the same error. This happens when trying to install Fallout 2.

Any help is welcome, I am a newbie after all.

---

### Post by Kilz on 2006-08-16
> **junnu said:**
> I have a problem with wine. At least I think so. I installed wine like shown on this thread and it installed fine, winecfg and some apps I tried run fine, with the exception that it complained about libGL.so.1. I fixed it by linking, as told to here and then it went haywire:
```
/media/cdrom0$ wine ./SETUP.EXE
err:module:load_builtin_dll failed to load .so lib for builtin L"wined3d.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:ddraw:DDRAW_Create Couldn't load WineD3D - OpenGL libs not present?

```I tried undoing the links but with no luck, same with recopying the libs. After that I installed the ATI propietary drivers hoping it would help. glxgears runs smoothly but it still gives the same error. This happens when trying to install Fallout 2.

Any help is welcome, I am a newbie after all.

This is the first time I have read this problem happening to someone with ATI graphics. The fix that is linked to is only for nivida graphics. Try this

```
cd /usr/lib
sudo rm libGL.so.1
sudo ln -sf libGL.so.1.2 libGL.so.1
```

---

### Post by maxehhh on 2006-08-17
Kilz i got it work :D and its great but i get a couple of errors, when i try to run LFS.exe (live for speed) it gives me an error like: Could not write to data Folder - is LFS Correctly installed on a hard drive?

and when i choose the Audio panel in winecfg the console give me this...

> err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": l ibesd.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please instal l this library to use jack

i'll be thanked if you help me with this.

btw, great guide! ;)

---

### Post by junnu on 2006-08-17
> **Kilz said:**
> This is the first time I have read this problem happening to someone with ATI graphics. The fix that is linked to is only for nivida graphics. Try this

```
cd /usr/lib
sudo rm libGL.so.1
sudo ln -sf libGL.so.1.2 libGL.so.1
```
Didn't help. Seems that I really did screw up. "Remember to allways listen in class, kids" I guess.

---

### Post by Kilz on 2006-08-17
> **maxehhh said:**
> Kilz i got it work :D and its great but i get a couple of errors, when i try to run LFS.exe (live for speed) it gives me an error like: Could not write to data Folder - is LFS Correctly installed on a hard drive?

and when i choose the Audio panel in winecfg the console give me this...



i'll be thanked if you help me with this.

btw, great guide! ;)

You may want to add the sound file in the common errors part of the howto. You may also want to look at the live for speed page in the [wine application database]("http://appdb.winehq.org/appview.php?iVersionId=3755") for tips on how to get it running.

---

### Post by Mooie on 2006-08-17
Do I need to run the sidnet script every time I install a new version of wine? when I install a new version of wine do I have to delete anything first?

It installs and runs great (for the things it works on)

---

### Post by Kilz on 2006-08-17
> **Mooie said:**
> Do I need to run the sidnet script every time I install a new version of wine? when I install a new version of wine do I have to delete anything first?

It installs and runs great (for the things it works on)

No the sidenet script should only need to be ran once. Nope, just run the newest script, or force in the newest .deb file.
Yes, wine isnt perfect, it only runs some things.

---

### Post by maxehhh on 2006-08-19
Kilz sorry for my newbiness o.O but what should i do, i have LFS in media/sda3, should i install it again? i mean, download it again? because when you download the rar it isnt installable.. you have to extract it. Thx anyway.

i get mIRC work, but i cant maximize it :\

---

### Post by Kilz on 2006-08-20
> **maxehhh said:**
> Kilz sorry for my newbiness o.O but what should i do, i have LFS in media/sda3, should i install it again? i mean, download it again? because when you download the rar it isnt installable.. you have to extract it. Thx anyway.

i get mIRC work, but i cant maximize it :\

I dont know what to do about LFS, I have never installed it. You might want to check out the wine application database to help get applications running.
Looking at your screen shot I see "Wine Desktop" at the bottom. Do you have a virtual desktop emulation set in winecfg on the graphics tab? If you do the applications can be no bigger than the size of the desktop you specify.

---

### Post by maxehhh on 2006-08-20
thx, i got it work, and about the sound even when i dont try to run a game or anything else i get this errors:

> err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack


---

### Post by Kilz on 2006-08-21
> **maxehhh said:**
> thx, i got it work, and about the sound even when i dont try to run a game or anything else i get this errors:

You may want to look at the first page for the sound errors.

---

### Post by Mnemonicman on 2006-08-25
Anyone else getting msiexec errors? I followed the instructions at the start of the thread to the letter and it installed fine. Then I proceded to follow other instructions for installing itunes and it would not install. It throws up and error about the version of the windows installer is too old. I've looked for solutions but none have worked so far. Also when I try to install v3 of the windows installer it complains of "Unable to find volume for file extraction. Please verify that you have proper permissions." I am stumped as to what to do next.

---

### Post by x64Jimbo on 2006-08-26
Why would you want iTunes? The native apps here are WAY better.

---

### Post by Mnemonicman on 2006-08-26
Maybe so but I don't want to have to move between multiple apps just to download podcasts, listen to music, and upload to my ipod. Besides what's so wrong with itunes? Aside from the lack of linux support. Maybe I can use Amarok but I would like the piece of mind knowing that itunes can work too. Besides what else in linux can play the protected content from the ITMS?

[Update]
Ok so i've been able to install itunes after some downloading of the windows installer. Woo. So now when I run it the GUI is practicaly invisible. Any text and menus are still visible and even popup windows are visible but itunes itself is hidden. Wierd isn't it. Anyways this is the last I'll mention itunes in this thread. I should start a new thread for this issue but until then I thought I should just mention whether I got the installer working in WINE.

---

### Post by Kilz on 2006-08-28
> **Mnemonicman said:**
> Maybe so but I don't want to have to move between multiple apps just to download podcasts, listen to music, and upload to my ipod. Besides what's so wrong with itunes? Aside from the lack of linux support. Maybe I can use Amarok but I would like the piece of mind knowing that itunes can work too. Besides what else in linux can play the protected content from the ITMS?

[Update]
Ok so i've been able to install itunes after some downloading of the windows installer. Woo. So now when I run it the GUI is practicaly invisible. Any text and menus are still visible and even popup windows are visible but itunes itself is hidden. Wierd isn't it. Anyways this is the last I'll mention itunes in this thread. I should start a new thread for this issue but until then I thought I should just mention whether I got the installer working in WINE.
[I suggest going here.]("http://appdb.winehq.org/appview.php?iVersionId=4450")

---

### Post by Ausus on 2006-08-28
Hi Kilz,

Correct me.

Then run the script.
Code:
[HTML]cd ~/Desktop/sidenet[/HTML]
You left out "cd" in your how to.
then 
Code:
[HTML]./setup[/HTML]
Everything else works.

Regards

---

### Post by ShadowRage on 2006-08-28
Hrmm, I just installed the latest deb and libs, what's libxxfdga for? I never installed it for wine ;X

---

### Post by Kilz on 2006-08-29
> **ShadowRage said:**
> Hrmm, I just installed the latest deb and libs, what's libxxfdga for? I never installed it for wine ;X

Its required for wine to run. If you dont install it you will get errors.

---

### Post by Kilz on 2006-08-29
> **Ausus said:**
> Hi Kilz,

Correct me.

Then run the script.
Code:
[HTML]cd ~/Desktop/sidenet[/HTML]
You left out "cd" in your how to.
then 
Code:
[HTML]./setup[/HTML]
Everything else works.

Regards

Thanks for pointing out the missing cd.

---

### Post by tymek666 on 2006-08-30
First, I'd like to thanks Kilz for there great scripts :).
However, my Wine is working (i've succesfully installed Opera :)), i don't see any letters in install windows. I mean i have window (for example after clicking on setup.exe) with working buttons, but they are empty, without 'cancel', 'start' etc...:(. Do you have any ideas how to fix it?

---

### Post by Kilz on 2006-08-31
> **tymek666 said:**
> First, I'd like to thanks Kilz for there great scripts :).
However, my Wine is working (i've succesfully installed Opera :)), i don't see any letters in install windows. I mean i have window (for example after clicking on setup.exe) with working buttons, but they are empty, without 'cancel', 'start' etc...:(. Do you have any ideas how to fix it?

Can you change the theme you are using and see if the words come back?

---

### Post by tymek666 on 2006-08-31
I haven't any theme installed. Winecfg shows me 'no theme'.
Where are themes located?

---

### Post by Kilz on 2006-08-31
> **tymek666 said:**
> I haven't any theme installed. Winecfg shows me 'no theme'.
Where are themes located?

The Kubuntu or Ubuntu theme. Im not sure where it is in Kubuntu but in Ubuntu its in System > Preferences > Theme

---

### Post by tymek666 on 2006-09-01
Thx, i'll check it at home, i thought it was about wine theme....

---

### Post by tymek666 on 2006-09-01
After changing Kubuntu themes i still don't have theme in winecfg :(

---

### Post by Kilz on 2006-09-01
> **tymek666 said:**
> After changing Kubuntu themes i still don't have theme in winecfg :(

You wont have a theme in winecfg, this was to see if the words appeared on installers. Just courious. Do you have words on buttons on winecfg? Also do you have a c folder in your home folder?

---

### Post by tymek666 on 2006-09-02
> **Kilz said:**
> You wont have a theme in winecfg, this was to see if the words appeared on installers. Just courious. Do you have words on buttons on winecfg? Also do you have a c folder in your home folder?
Yes, i have words on buttons in winecfg, but i haven't them while installing a programs. After 'blind' install apps work fine. I have a and c folders in wine directory i mean in wine/dosdevices.

---

### Post by Kilz on 2006-09-02
> **tymek666 said:**
> Yes, i have words on buttons in winecfg, but i haven't them while installing a programs. After 'blind' install apps work fine. I have a and c folders in wine directory i mean in wine/dosdevices.

Only a A and a C folder in /.wine/dosdevices? There isnt one in your home directory? Run this and paste the results so we can make sure ```
ls -l ~/
```

---

### Post by Darth Lukan on 2006-09-02
I just want you to know that you are the man for putting the time and effort into helping people out by coming up with a How To.  Especially for something as daunting as Wine under 64-bit Ubuntu OS's.  You get my Props!

---

### Post by tymek666 on 2006-09-03
> **Kilz said:**
> Only a A and a C folder in /.wine/dosdevices? There isnt one in your home directory? Run this and paste the results so we can make sure ```
ls -l ~/
```

Here's result:
drwx------ 2 kuba kuba    4096 2006-08-04 09:23 amsn_received
drwxr-xr-x 4 kuba kuba    4096 2006-08-30 21:52 c
drwx------ 9 kuba kuba    4096 2006-09-02 09:46 Desktop
lrwxrwxrwx 1 kuba kuba      26 2006-06-23 20:48 Examples -> /usr/share/example-content
-rw-r--r-- 1 kuba kuba 8561350 2006-07-29 12:57 firefox32-1.5.0.5_amd64.deb
-rw-r--r-- 1 kuba kuba       0 2006-09-03 11:46 gnash-dbg.log

Maybe it's beacuse i use KDE, since you test it on Gnome...

---

### Post by Kilz on 2006-09-03
> **tymek666 said:**
> Here's result:
drwx------ 2 kuba kuba    4096 2006-08-04 09:23 amsn_received
drwxr-xr-x 4 kuba kuba    4096 2006-08-30 21:52 c
drwx------ 9 kuba kuba    4096 2006-09-02 09:46 Desktop
lrwxrwxrwx 1 kuba kuba      26 2006-06-23 20:48 Examples -> /usr/share/example-content
-rw-r--r-- 1 kuba kuba 8561350 2006-07-29 12:57 firefox32-1.5.0.5_amd64.deb
-rw-r--r-- 1 kuba kuba       0 2006-09-03 11:46 gnash-dbg.log

Maybe it's beacuse i use KDE, since you test it on Gnome...

Thats a possibility, and one of the reasosns I asked you to change the theme. Some kde control themes have problems with forced in applications.

---

### Post by tymek666 on 2006-09-03
well, it's not a big problem. In 99% we have to press enter few times during install process. Except these issues wine works great! I've just played old rally game (Mobil 1 RC) that works more stable than under winxp :) Amazing!

---

### Post by Seryozha on 2006-09-03
OMG Kilz! You F&*king RULE!  I have had wine installed by another how to and the sound would not work.  I ran this and it WORKS!!!

---

### Post by Seryozha on 2006-09-03
ok now the only problem i have now is if i run WoW with the -open GL switch all i can see is my map and my menu at the bottom and everything else is black and flickering like crazy.  if i dont use the -opengl switch it works fine but the rendering is all screwd. (it looks kinda kewl but i would still like to fix;) )  Atached are the screen shots.  Screenshot.jpg is with out the opengl switch and Screenshot-1.png is with the opengl switch

---

### Post by Seryozha on 2006-09-03
> **Seryozha said:**
> ok now the only problem i have now is if i run WoW with the -open GL switch all i can see is my map and my menu at the bottom and everything else is black and flickering like crazy.  if i dont use the -opengl switch it works fine but the rendering is all screwd. (it looks kinda kewl but i would still like to fix;) )  Atached are the screen shots.  Screenshot.jpg is with out the opengl switch and Screenshot-1.png is with the opengl switch

ok i fixed this by running the special wow edition of wine on the first page and then the sidenet script! 8) 8) 8)

---

### Post by Kilz on 2006-09-03
> **Seryozha said:**
> ok i fixed this by running the special wow edition of wine on the first page and then the sidenet script! 8) 8) 8)

I found the Wow download last week. It makes it a lot easier that compiling it. :D

---

### Post by sYn pHrEAk on 2006-09-04
When using the normal wine package I got errors during install because libartsc0 and libaudio2 weren't installed.  I removed wine, installed those 2 packages, then reinstalled wine without error.

EDIT:
Errr... just realized I didn't install the WoW version.  So this applies to the normal version.  9.20 was the latest when I did this.

---

### Post by dullroar on 2006-09-04
[QUOTE=Hickeroar;1099656]I get this when running winecfg:

ryan@Hickeroar:~/WINEINSTALL$ winecfg
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual

The config program starts up, but thats about it.  I'm not sure what exactly i'm doing wrong here.  Any help would be appreciated...  Is there some part of the setup that i havent done right?
[QUOTE]

I get this, too. However, it doesn't appear to have affected anything. I was able to install Coding Technologies mp3Pro decoder and bring it up. The installer was SLOWWWWWW, but the program appears to work.

Good how to, thanks!

---

### Post by Kilz on 2006-09-04
> **dullroar said:**
> [QUOTE=Hickeroar;1099656]I get this when running winecfg:

ryan@Hickeroar:~/WINEINSTALL$ winecfg
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual

The config program starts up, but thats about it.  I'm not sure what exactly i'm doing wrong here.  Any help would be appreciated...  Is there some part of the setup that i havent done right?

I get this, too. However, it doesn't appear to have affected anything. I was able to install Coding Technologies mp3Pro decoder and bring it up. The installer was SLOWWWWWW, but the program appears to work.

Good how to, thanks!

From the Common Errors section
> Common Errors:

```
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
```

To fix this error you need to install/update the drivers for your video card to enable openGL. To test if they are enabled type in glxgears in the terminal. If you do not see a window open with 3 rotating gears it confirms you need the drivers.

---

### Post by Shy1 on 2006-09-08
I installed wine using the how to, amazing, up and running within a couple of minutes, however, the main reason I installed wine was to run an app called Epson Print CD, for my Stylus R300, I find it very erratic printing to CD/DVD under linux.  The problem I have is that my printer is not recognised in wine, but works perfectly in dapper 64 bit using cups.  I keep getting a message saying that I should install a printer.  After googling, I found on the Gentoo forums a post that said 32bit wine can not work with 64 bit cups.

Is it possible to install 32bit cups into 64bit dapper??  I don't know if this will be possible at all and I'm not very experienced with this sort of thing, but has anyone managed to do this? or know if it is possible.

---

### Post by Kilz on 2006-09-08
> **Shy1 said:**
> I installed wine using the how to, amazing, up and running within a couple of minutes, however, the main reason I installed wine was to run an app called Epson Print CD, for my Stylus R300, I find it very erratic printing to CD/DVD under linux.  The problem I have is that my printer is not recognised in wine, but works perfectly in dapper 64 bit using cups.  I keep getting a message saying that I should install a printer.  After googling, I found on the Gentoo forums a post that said 32bit wine can not work with 64 bit cups.

Is it possible to install 32bit cups into 64bit dapper??  I don't know if this will be possible at all and I'm not very experienced with this sort of thing, but has anyone managed to do this? or know if it is possible.

I know getting as printer or scanner [is possible]("http://www.ubuntuforums.org/showthread.php?t=253004") on dapper 64. But I dont know how its done.

---

### Post by Megistos on 2006-09-16
I'm trying to install wine on 64 bit dapper - I've done the two scripts in the first post, but whenever I try to run anything in wine (or even merely the winecfg) I get this error:

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

In addition, this error pops up for each of the shortcuts that the sidenet script tries to make. Even using the modified script made no difference.

Any ideas?

---

### Post by Kilz on 2006-09-16
This si something new. Since the errors are glx, do you have the accelerated video drivers enabled?

---

### Post by ravikm on 2006-09-17
hi,

any idea how to fix these?

> fixme:richedit:fnTextSrv_TxSendMessage 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxDraw 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxGetNaturalSize 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1ce1e0: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1ce1e0: STUB


thanks,
ravi.

---

### Post by hutch61525 on 2006-09-17
'This si something new. Since the errors are glx, do you have the accelerated video drivers enabled?'

I'm a complete newb. How do I determine if I have the accelerated video drivers enabled?

---

### Post by prince_niceguy on 2006-09-17
i am also getting the same error... :-(

Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

I have the (in)famous SiS 760 card. I do not have hardware accelerator. So used something from Mesa libgl1-mesa-swrast. the one default ligl1-mesa was not running even glxgears. Using this the glsgears are coming up. But I am not able to start winecfg or any program using wine. 

Please help....

---

### Post by Kilz on 2006-09-17
> **ravikm said:**
> hi,

any idea how to fix these?



thanks,
ravi.

Is this a wine error, or an application error? Does winecfg come up?

---

### Post by Kilz on 2006-09-17
> **hutch61525 said:**
> 'This si something new. Since the errors are glx, do you have the accelerated video drivers enabled?'

I'm a complete newb. How do I determine if I have the accelerated video drivers enabled?

open a terminal and type in ```
glxgears
``` If you dont see a little window open with 3 rotating gears in it you dont have the graphics drivers installed for your video card.


[quote=prince_niceguy]i am also getting the same error...

Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
X Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 3 (X_GLXCreateContext)
Serial number of failed request: 14
Current serial number in output stream: 15

I have the (in)famous SiS 760 card. I do not have hardware accelerator. So used something from Mesa libgl1-mesa-swrast. the one default ligl1-mesa was not running even glxgears. Using this the glsgears are coming up. But I am not able to start winecfg or any program using wine.

Please help....[/quote]

The sis 760 is a problem even I canf fix. For more information this page may be helpful.
[http://www.winischhofer.at/linuxsispart1.shtml#introduction](http://www.winischhofer.at/linuxsispart1.shtml#introduction)
The why this page section will explain why its such a problem.

---

### Post by ravikm on 2006-09-17
> **Kilz said:**
> Is this a wine error, or an application error? Does winecfg come up?

it's an application (google talk) error. winecfg displays the window, but audio seems to be a problem. i'm unable to get ALSA configured. the audio control panel doesn't launch. google talk window launches, but i don't see any text and links. also glxgears -printfps gives me about 2000 fps, but i don't see the rotating gears, only RGB colours flashing randomly.

winecfg gives this:

> Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
ALSA lib ../../../src/seq/seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.


when i click on audio in winecfg, this comes:

> err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack


thanks,
ravi.

---

### Post by Kilz on 2006-09-17
> **ravikm said:**
> it's an application (google talk) error. winecfg displays the window, but audio seems to be a problem. i'm unable to get ALSA configured. the audio control panel doesn't launch. google talk window launches, but i don't see any text and links. 
At the bottom of the howto under Windows applications is a link to the [Wine Application Database]("http://appdb.winehq.org/"). Its there because Wine is not perfect it doesnt guarantee to run everything. The [Google Talk]("http://appdb.winehq.org/appview.php?iVersionId=5683") page there proves this point. It may not be possible to run this application.

> **ravikm said:**
> also glxgears -printfps gives me about 2000 fps, but i don't see the rotating gears, only RGB colours flashing randomly.
Sounds like your graphics drivers are not properly installed. I wish I could help there but I have ATI graphics and so have no real knowlage about getting Nivida cards to work correctly.
> **ravikm said:**
> winecfg gives this:

when i click on audio in winecfg, this comes:

thanks,
ravi.

Open a terminal and type in 
```
sudo apt-get install lib32asound2
```
This may help.
Also I reciently packaged the 32bit alsa-oss for firefox32. This may help you. [You can download it here]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") , then double click on it to install it.

---

### Post by prince_niceguy on 2006-09-18
Kilz... thanks for the help...

I understand that there is no DRI support for SiS 760. But I am able to make GLX work using mesa. I am able to run glxgears and see the three gears in action. 

I am not sure but it seems wine is not able to use the same glx which is being used by glxgears or something like that. I am newbie to linux and am stuck with SiS. Isn't there any other way to enable wine without open gl or dri???

also I appreciate all your help and time you are spending on this... thank you so much... :-)...

---

### Post by hutch61525 on 2006-09-18
> **Kilz said:**
> open a terminal and type in ```
glxgears
``` If you dont see a little window open with 3 rotating gears in it you dont have the graphics drivers installed for your video card.




The sis 760 is a problem even I canf fix. For more information this page may be helpful.
[http://www.winischhofer.at/linuxsispart1.shtml#introduction](http://www.winischhofer.at/linuxsispart1.shtml#introduction)
The why this page section will explain why its such a problem.


Yeah, so I think that I broke my graphics driver somewhere in this process. How can I fix them and get this working again?

---

### Post by Perfex on 2006-09-18
Broke mine too I used [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually)
to get mine working again, typed winecfg in the terminal and walla it came up

---

### Post by Kilz on 2006-09-18
> **hutch61525 said:**
> Yeah, so I think that I broke my graphics driver somewhere in this process. How can I fix them and get this working again?

I kind of dought that wine broke the graphics driver. Thats a kernel module. Wine isnt installed anyplace near it. More likely the last kernel update a few days ago did it.
Fixing it depends on what card you have.

---

### Post by BarnOwl on 2006-09-20
Utter newbie here.  This may be related to my graphics drivers because that glxgears thing didn't work for me.  Though I did have graphics drivers installed before the last kernel update.  However just in case it's something else.  Here's what I get when I do the sidenet setup.

Oh and winecfg didn't work either.

Thanks

---

### Post by Orin on 2006-09-20
Blech. 

I'm new to Linux as well, and it spits out the following errors at me when I try to run sidenet:

SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Programs -> Program Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Control Panel
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Application Uninstaller
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Wine Configuration
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Task Manager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Programs -> Accesories -> Notepad
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

SETUP STAGE 3
Setting up wine configuration ...

wine has been setup
orin@orin-laptop:~/Desktop/sidenet$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15


Help. Please.

---

### Post by Kilz on 2006-09-20
> **Orin said:**
> Blech. 

I'm new to Linux as well, and it spits out the following errors at me when I try to run sidenet:

SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Programs -> Program Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Control Panel
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Application Uninstaller
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Wine Configuration
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Task Manager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Programs -> Accesories -> Notepad
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

SETUP STAGE 3
Setting up wine configuration ...

wine has been setup
orin@orin-laptop:~/Desktop/sidenet$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15


Help. Please.


Open a terminal, type in winecfg. If the wine control panel comes up its installed. The glx errors are probably becasue you need to install the drivers for your video card. If you need to know more about how to use wine [read here.]("http://www.tghc.org/staticpages/index.php/wine")

---

### Post by Kilz on 2006-09-20
> **BarnOwl said:**
> Utter newbie here.  This may be related to my graphics drivers because that glxgears thing didn't work for me.  Though I did have graphics drivers installed before the last kernel update.  However just in case it's something else.  Here's what I get when I do the sidenet setup.

Oh and winecfg didn't work either.

Thanks

you may need to install the video drivers again. Wine was installed , so was the sidenet setup script.

---

### Post by Orin on 2006-09-20
At the bottom of that log I'd pasted, I tried running winecfg and it gave me that error.

---

### Post by BarnOwl on 2006-09-21
Orin's problem appears to be identical to mine.  That log he posted looked pretty much like what I got.

---

### Post by Kilz on 2006-09-21
> **BarnOwl said:**
> Orin's problem appears to be identical to mine.  That log he posted looked pretty much like what I got.


Both of you, open a terminal and type in ```
glxinfo
``` paste the results here.

---

### Post by BarnOwl on 2006-09-22
My glxinfo is below.  I did some checking and it does indeed appear that I'm using the via driver.  My video is the via K8M800 chipset.

Thanks for helping :)

name of display: :0.0
__driCreateNewScreen_20050727 - succeeded
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 -1  0 r  y  . -1 -1  8  0  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 -1  0 r  .  . -1 -1  8  0  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 -1  0 r  y  . -1 -1  8  0  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 -1  0 r  .  . -1 -1  8  0  0  0  0 16 16 16 16  0 0 Slow

---

### Post by Kilz on 2006-09-23
> **BarnOwl said:**
> My glxinfo is below.  I did some checking and it does indeed appear that I'm using the via driver.  My video is the via K8M800 chipset.

Thanks for helping :)

name of display: :0.0
__driCreateNewScreen_20050727 - succeeded
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 -1  0 r  y  . -1 -1  8  0  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 -1  0 r  .  . -1 -1  8  0  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 -1  0 r  y  . -1 -1  8  0  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 -1  0 r  .  . -1 -1  8  0  0  0  0 16 16 16 16  0 0 Slow

You do not have 3d acceleration. Im not sure how to get that with your video hardware. This is the reason you are getting the glx errors with winecfg.

---

### Post by BarnOwl on 2006-09-23
That's what I figured.  I learned more about it after I posted here.  BTW I never did have 3D.  It wasn't the kernel upgrade.  I'll probably have to wait for a newer driver.  Thanks for looking though.  Time to find another thread. :|

---

### Post by prince_niceguy on 2006-09-26
OK this might help for those who are not having 3D card like sis760...

I commented outn glx in the /etc/X11/xorg.conf and restarted xserver and then I tried winecfg. It gave the window without the use of opengl and I was able to configure it without any issues. I even installed winamp and it worked fine though it hanged after some time.

The major issue I am facing is installing office2003 or project 2003. Every time I start installer it states the product key is not entered. I believe the wine is not having windows product key which is creating this issue. Any one having idea on how to set the product key. I have a valid 32 bit windows xp key with me. If some one can guide me in this it will be really helpful.

BTW... I tried playing age of empires but it didn't work as the open gl was not there. I tried putting the support for hard ware as emulated still it didn't work... :-(... Probably I will have to stick with normal applications only... ](*,)

---

### Post by BarnOwl on 2006-09-26
That might work for me but, I haven't quite given up on getting 3d working yet. If I do, I'll give that a try.

---

### Post by prince_niceguy on 2006-09-27
I have installed mesa ang glxgears and glxinfo everything works but wine some how does not use mesa it always tries to use hard ware accelaration. If I enable glx I keep getting error related to glxcreate. 

I searched on the net how to make wine look for emulator in case hardware acceleration is not there. If that is addressed then I feel it should work... 

do let me know if you are able to figure out something...

---

### Post by Saubazi on 2006-09-28
I tried to seach but it seems that noone sofar managed to make winetools run (under 64bit), right?

I suppose sidenet does the same thing, however, I am just being ignorant but shouldn't one get a control panel look-a-like with wine control, because I only got an "applet not started" message box or something?

---

### Post by EvilWeevil on 2006-09-29
Hi guys,

I am a new user to Ubuntu, and am working on trying to get WINE working correctly, I have installed it and steam, and when I try to launch CS:S it says preparing then tries to launch the app..

This is the set of errors that occur:

```
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)

```
I have my Nvidia drivers installed, and followed this guide to get WINE working. If anyone could please give me some pointers on how to correct this that would be greatly appreciated.

---

### Post by Kilz on 2006-09-29
> **EvilWeevil said:**
> Hi guys,

I am a new user to Ubuntu, and am working on trying to get WINE working correctly, I have installed it and steam, and when I try to launch CS:S it says preparing then tries to launch the app..

This is the set of errors that occur:

```
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XF86VidMode)

```
I have my Nvidia drivers installed, and followed this guide to get WINE working. If anyone could please give me some pointers on how to correct this that would be greatly appreciated.


Do you see the wineconfig panel when you open a terminal and type in ```
winecfg
```?

---

### Post by EvilWeevil on 2006-09-29
Yes,
winecfg does open a panel, I get a libjack.so error message when I goto the sound tab, but past that, it doesn't complain.

---

### Post by pudgypaw on 2006-09-29
hello everyone, let me recount what happened the past 2 weeks:
i am a windows end user buff, got annoyed and tried out linux, first CRUX, then openSUSE, then Ubuntu with FVWM-Crystal on the side. registered for this forum just now.

what's preventing me from leaving winXP altogether is Office2003. I'm posting here because I have progressed from getting ATI X1800 512 to work to getting Wine to work to installing Office2003 and now i'm having similar issues:

pudgypaw@pudgypaw-desktop:/media/cdrom$ wine Autorun
err:wgl:has_opengl  glx_version as 1.3 and GLX_SGIX_fbconfig extension is unsupported. Expect problems.

installation just dies... wine control panel also has that random error when i open the sound panel

---

### Post by fatsheep on 2006-09-29
> **pudgypaw said:**
> hello everyone, let me recount what happened the past 2 weeks:
i am a windows end user buff, got annoyed and tried out linux, first CRUX, then openSUSE, then Ubuntu with FVWM-Crystal on the side. registered for this forum just now.

what's preventing me from leaving winXP altogether is Office2003. I'm posting here because I have progressed from getting ATI X1800 512 to work to getting Wine to work to installing Office2003 and now i'm having similar issues:

pudgypaw@pudgypaw-desktop:/media/cdrom$ wine Autorun
err:wgl:has_opengl  glx_version as 1.3 and GLX_SGIX_fbconfig extension is unsupported. Expect problems.

installation just dies... wine control panel also has that random error when i open the sound panel


Do you have the latest propriety drivers for your graphics card?

---

### Post by pudgypaw on 2006-09-29
i used the 2 scripts authored by the creator of this thread, so it's not the most recent one. I did try the 2nd tactic (recompiling from scratch w/ the most recent ati) but i couldn't get past build. And now the screen is flickering like mad every time i logon. i'm going to reinstall dapper bbl.

---

### Post by Kilz on 2006-09-30
> **EvilWeevil said:**
> Yes,
winecfg does open a panel, I get a libjack.so error message when I goto the sound tab, but past that, it doesn't complain.

Then wine is installed and working. The problem you are having is getting a Windows Application to run. Wine isnt perfect. There are also way to many Windows applications for this thread to deal with them all. 
From the first page of the howto.

[COLOR="Blue"][SIZE="4"]Windows Applications[/SIZE][/COLOR]
Wine is not perfect. You are not guaranteed of getting every Windows application working. If you need information or help setting up a Windows application please Visit the [URL="http://appdb.winehq.org/"]Wine Application Database. 
[/URL] This Howto only covers Wine itself. There are to many Windows Applications to be able to support the installation of all of them in this thread.

---

### Post by Kilz on 2006-09-30
> **pudgypaw said:**
> i used the 2 scripts authored by the creator of this thread, so it's not the most recent one. I did try the 2nd tactic (recompiling from scratch w/ the most recent ati) but i couldn't get past build. And now the screen is flickering like mad every time i logon. i'm going to reinstall dapper bbl.

There is no need to reinstall Dapper. If you are refering to my [failed attempt to make a ati driver install script]("http://www.ubuntuforums.org/showthread.php?t=235145"). Im sorry but I was unable to make it work. There are just way to many variables with graphics cards. So I put a big read disclaimer on the page.

**[COLOR="Red"]For some people the 8.27.10 script works fine. For some people this script doesn't. I have no idea why it works for some people but not others. I am leaving it up in case you want to try. But I can no longer support it. Use it at your own risk.[/COLOR]**

I will edit it again to point to the [howto here. ]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually") I recommend going to that howto and following it.

---

### Post by R3linquish3r on 2006-10-01
I get the following error when I try to run visualboyadvanced. I know there is a linux native port but all my save files were made on windows and I don't feel like losing them. VBA does start but when I select to open a ROM I get the following:

```
ed@ubuntu-desktop:/media/sda1/Emulators$ wine VisualBoyAdvance.exe 
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1b0170) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1af9d0)->(0x1002c,00000008)
wine: Call from 0x5275ca to unimplemented function MFC42.DLL.6876, aborting
wine: Unimplemented function MFC42.DLL.6876 called at address 0x5275ca (thread 0009), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000008 (D) (null)
        0000000c    0
        00000009    0

```

---

### Post by Kilz on 2006-10-01
> **R3linquish3r said:**
> I get the following error when I try to run visualboyadvanced. I know there is a linux native port but all my save files were made on windows and I don't feel like losing them. VBA does start but when I select to open a ROM I get the following:

```
ed@ubuntu-desktop:/media/sda1/Emulators$ wine VisualBoyAdvance.exe 
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1b0170) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1af9d0)->(0x1002c,00000008)
wine: Call from 0x5275ca to unimplemented function MFC42.DLL.6876, aborting
wine: Unimplemented function MFC42.DLL.6876 called at address 0x5275ca (thread 0009), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000008 (D) (null)
        0000000c    0
        00000009    0

```

I have no idea how to get the visualboyadvanced application running. You might want to visit the Wine Application Database. This howto only deals with getting wine installed. Not Windows applications under Wine.

---

### Post by R3linquish3r on 2006-10-01
It ran fine under wine when I had x32 Ubuntu. It's on x64 that it is giving me that error so I figured it would be best to ask you.

---

### Post by Kilz on 2006-10-02
> **R3linquish3r said:**
> It ran fine under wine when I had x32 Ubuntu. It's on x64 that it is giving me that error so I figured it would be best to ask you.

Did you go to the Wine Application Database? The reasons I link to it is it has thousands of applications listed , each with their own page. With tips and tricks on how to make Windows Applications work. A lot of the applications for Windows I have never ran. To tell the truth the only thing I run under Wine is Firefox. So I can use Flash 8 for some sites.

Copied Directly from the Wine application Database's  VisualBoyAdvance page.

Additional Comments
The Windows9x mfc42.dll is missing some required functions needed by VisualBoyAdvance v1.8, the WindowsXP version works perfectly.

Would you be happening to run the Windows 98 version of visualboyadvanced, seeing the error is calling for mfc42.dll?

---

### Post by R3linquish3r on 2006-10-02
That could be the problem. Thanks for the tip.

---

### Post by eric.stone on 2006-10-03
Hi. Followed your excellent howto on my AMD64 to get WINE running.  I get this:

eric@Eric-LinuxBox:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
eric@Eric-LinuxBox:~$

I want to run a MS program called "Business Plan Pro" it is on a CD ROM.  What is my next step?

Thank very mush in advance:confused:

---

### Post by Kilz on 2006-10-04
> **eric.stone said:**
> Hi. Followed your excellent howto on my AMD64 to get WINE running.  I get this:

eric@Eric-LinuxBox:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
eric@Eric-LinuxBox:~$

I want to run a MS program called "Business Plan Pro" it is on a CD ROM.  What is my next step?

Thank very mush in advance:confused:

[Take a look here to learn a little more about how to use Wine.]("http://www.tghc.org/staticpages/index.php/wine")
Wine is not perfect. You are not guaranteed of getting every Windows application working. I have never ran that application. You will want to visit the [Wine Application Database. ]("http://appdb.winehq.org/") to see if it can be ran under wine and how to set it up if you can.

---

### Post by rlanders on 2006-10-05
Edgy is a bit 'on the edge' I suppose and really doesn't like anything to do with dapper.  So it seems, ... anyway ](*,) wine installs fine but doesn't want to run.  I get these fancy errors:

```
winecfg 
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:import_dll Loading library comctl32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\winspool.drv") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\winspool.drv") failed (error c000007a).
err:module:import_dll Library winspool.drv (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007a).
err:module:import_dll Library comdlg32.dll (which is needed by L"C:\\windows\\winecfg.exe") not found
err:module:import_dll Loading library comctl32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library shell32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library ole32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\winmm.dll") failed (error c000007b).
err:module:import_dll Library winmm.dll (which is needed by L"C:\\windows\\winecfg.exe") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\uxtheme.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\uxtheme.dll") failed (error c000007a).
err:module:import_dll Library uxtheme.dll (which is needed by L"C:\\windows\\winecfg.exe") not found
err:module:import_dll Loading library user32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\winecfg.exe" failed, status c0000135
```

any ideas or anyone having the same kind of problems?

---

### Post by Kilz on 2006-10-05
> **rlanders said:**
> Edgy is a bit 'on the edge' I suppose and really doesn't like anything to do with dapper.  So it seems, ... anyway ](*,) wine installs fine but doesn't want to run.  I get these fancy errors:

```
winecfg 
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:import_dll Loading library comctl32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\winspool.drv") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\winspool.drv") failed (error c000007a).
err:module:import_dll Library winspool.drv (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007a).
err:module:import_dll Library comdlg32.dll (which is needed by L"C:\\windows\\winecfg.exe") not found
err:module:import_dll Loading library comctl32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library shell32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library ole32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\winmm.dll") failed (error c000007b).
err:module:import_dll Library winmm.dll (which is needed by L"C:\\windows\\winecfg.exe") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\uxtheme.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\uxtheme.dll") failed (error c000007a).
err:module:import_dll Library uxtheme.dll (which is needed by L"C:\\windows\\winecfg.exe") not found
err:module:import_dll Loading library user32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"C:\\windows\\winecfg.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\winecfg.exe" failed, status c0000135
```

any ideas or anyone having the same kind of problems?


Is there a "C" folder in your home folder?

---

### Post by linkoraclehero on 2006-10-06
Kudos for getting this far, but for some reason, it doesn't want to work overall. Paint Shop Pro 7 doesn't work, whereas I had an older version of Wine and Linux running it perfectly. Must have some relation to the fix not doing all Wine normally does. Still, it's better than nothing :)

---

### Post by rlanders on 2006-10-06
yes, I followed all the instructions. and yes, there is a c folder

from the looks of it, it looks like I've got 64bit trying to load as 32bit but I have no idea what may be really going on and why.

---

### Post by fatsheep on 2006-10-06
I've got a question...  Ever since I upgraded wine there has been not only a "c" folder in my home directory but a "c.0609041056" folder as well.  Why is this and can I safely delete one of them?

---

### Post by Kilz on 2006-10-07
> **fatsheep said:**
> I've got a question...  Ever since I upgraded wine there has been not only a "c" folder in my home directory but a "c.0609041056" folder as well.  Why is this and can I safely delete one of them?

You may have installed the sidenet script more than once. You only need to run it once. After that you only need to force in the newest wine to upgrade. The C folder is a virtual C drive. It holds the installed windows applications depending on if you have installed anything since the upgrade, you may want to delete the new C folder and rename the "c.0609041056" to C so you dont have to reinstall everything.

---

### Post by Kilz on 2006-10-07
> **rlanders said:**
> yes, I followed all the instructions. and yes, there is a c folder

from the looks of it, it looks like I've got 64bit trying to load as 32bit but I have no idea what may be really going on and why.

What its saying is it cant find some of the wine components. It appears to be trying to run the winecfg.exe in the virtual drive instead of the winecfg in /usr/bin.
Open a terminal and enter in the following commands. Copy and paste the complete results into a reply

```
ls -l /usr/bin/wine*
```

and

```
ls -l ~/c/windows/*
```

---

### Post by Zargoon on 2006-10-07
Nvidia graphics patch for wow?  I used your howto and the wow deb file but once I install wow and try to loging under characters the screen goes flickery.  I am told this is becuase I need to apply a patch before compiling wine.  However, since these are deb files I can't apply the patch.  Any ideas?

---

### Post by Rick Henson on 2006-10-07
[SIZE="3"]I have tried over and over to get this guide to work to install Wine and both with the script and manually I get the following error:

```
Setting up wine (0.9.22~winehq0~ubuntu~6.06-1) ...
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link
```

I am running Edgy64 on an AMD 64 3500+ system. Can this be done. I have tried several different guides all resulting in the same error.

I am very computer literate but fairly new to Linux. Any help with this would be greatly appriciated.

Thanks,[/SIZE]

---

### Post by Rick Henson on 2006-10-07
[SIZE="3"]Well I did some more looking and found a mention of running this:

sudo apt-get install ia32-libs*

After running this I reran the command:

sudo dpkg --force-architecture -i wine_0.9.22~winehq0~ubuntu~6.06-1_i386.deb

and then the sidenet script and all seems to be ok now.[/SIZE]

---

### Post by glenn45 on 2006-10-08
Nice How To, Kilz! I now have flash and wine in my Ubuntu!  I did the manual install and it worked perfectly (i have no internet access at home), that is after downloading linux32 package and whatnot. 
Thanks again!:D

---

### Post by rlanders on 2006-10-08
> **Kilz said:**
> What its saying is it cant find some of the wine components. It appears to be trying to run the winecfg.exe in the virtual drive instead of the winecfg in /usr/bin.
Open a terminal and enter in the following commands. Copy and paste the complete results into a reply

```
ls -l /usr/bin/wine*
```

and

```
ls -l ~/c/windows/*
```
```

bert@rlanders-com:~$ ls -l /usr/bin/wine*
-rwxr-xr-x  1 root root   4656 2006-09-29 03:18 /usr/bin/wine
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/wineboot
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winebrowser
-rwxr-xr-x  1 root root  83624 2006-09-29 03:18 /usr/bin/winebuild
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winecfg
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/wineconsole
lrwxrwxrwx  1 root root      7 2006-10-05 08:56 /usr/bin/winecpp -> winegcc
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winedbg
-rwxr-xr-x  1 root root  89332 2006-09-29 03:18 /usr/bin/winedump
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winefile
lrwxrwxrwx  1 root root      7 2006-10-05 08:56 /usr/bin/wineg++ -> winegcc
-rwxr-xr-x  1 root root  22284 2006-09-29 03:18 /usr/bin/winegcc
-rwxr-xr-x  1 root root  14332 2006-09-29 03:18 /usr/bin/wine-kthread
-rwxr-xr-x  1 root root  17732 2006-09-29 03:17 /usr/bin/winelauncher
-rwxr-xr-x  1 root root  58999 2006-09-29 03:17 /usr/bin/winemaker
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winemine
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winepath
-rwxr-xr-x  1 root root   4338 2006-09-29 03:17 /usr/bin/wineprefixcreate
-rwxr-xr-x  1 root root  10484 2006-09-29 03:18 /usr/bin/wine-preloader
-rwxr-xr-x  1 root root   6296 2006-09-29 03:18 /usr/bin/wine-pthread
-rwxr-xr-x  1 root root 260076 2006-09-29 03:18 /usr/bin/wineserver
-rwxr-xr-x  1 root root   6069 2006-09-29 03:17 /usr/bin/wineshelllink
bert@rlanders-com:~$ ls -l /home/bert/c/windows/*
lrwxrwxrwx 1 bert roro   17 2006-10-05 08:57 /home/bert/c/windows/fonts -> /home/bert/.fonts
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 /home/bert/c/windows/notepad.exe -> /usr/lib/wine/notepad.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 /home/bert/c/windows/regedit.exe -> /usr/lib/wine/regedit.exe.so
lrwxrwxrwx 1 bert roro   29 2006-10-05 08:57 /home/bert/c/windows/rundll32.exe -> /usr/lib/wine/rundll32.exe.so
lrwxrwxrwx 1 bert roro   32 2006-10-05 08:57 /home/bert/c/windows/uninstall.exe -> /usr/lib/wine/uninstaller.exe.so
lrwxrwxrwx 1 bert roro   32 2006-10-05 08:57 /home/bert/c/windows/winebrowser.exe -> /usr/lib/wine/winebrowser.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 /home/bert/c/windows/winecfg.exe -> /usr/lib/wine/winecfg.exe.so

/home/bert/c/windows/command:
total 0
lrwxrwxrwx 1 bert roro 26 2006-10-05 08:57 start.exe -> /usr/lib/wine/start.exe.so

/home/bert/c/windows/inf:
total 0

/home/bert/c/windows/system:
total 0
lrwxrwxrwx 1 bert roro 25 2006-10-05 08:57 d3d8.dll -> /usr/lib/wine/d3d8.dll.so
lrwxrwxrwx 1 bert roro 25 2006-10-05 08:57 d3d9.dll -> /usr/lib/wine/d3d9.dll.so

/home/bert/c/windows/system32:
total 4
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 control.exe -> /usr/lib/wine/control.exe.so
lrwxrwxrwx 1 bert roro   25 2006-10-05 08:57 d3d8.dll -> /usr/lib/wine/d3d8.dll.so
lrwxrwxrwx 1 bert roro   25 2006-10-05 08:57 d3d9.dll -> /usr/lib/wine/d3d9.dll.so
drwxr-xr-x 2 bert roro 4096 2006-10-05 08:57 drivers
lrwxrwxrwx 1 bert roro   29 2006-10-05 08:57 fileman.exe -> /usr/lib/wine/winefile.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 notepad.exe -> /usr/lib/wine/notepad.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 progman.exe -> /usr/lib/wine/progman.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 taskman.exe -> /usr/lib/wine/taskmgr.exe.so
lrwxrwxrwx 1 bert roro   29 2006-10-05 08:57 winmine.exe -> /usr/lib/wine/winemine.exe.so
lrwxrwxrwx 1 bert roro   27 2006-10-05 08:57 winver.exe -> /usr/lib/wine/winver.exe.so

/home/bert/c/windows/temp:
total 0
```

---

### Post by Zargoon on 2006-10-08
Nvidia graphics patch for wow? I used your howto and the wow deb file but once I install wow and try to loging under characters the screen goes flickery. I am told this is becuase I need to apply a patch before compiling wine. However, since these are deb files I can't apply the patch. Any ideas?

---

### Post by Kilz on 2006-10-08
> **Zargoon said:**
> Nvidia graphics patch for wow? I used your howto and the wow deb file but once I install wow and try to loging under characters the screen goes flickery. I am told this is becuase I need to apply a patch before compiling wine. However, since these are deb files I can't apply the patch. Any ideas?

You may have to compile it. That may be very hard, to tell the truth I have enver sucessfuly compiled it under 64bit. But I have on a 32bit virtual machine with vmware and the standerd compile instructions.

---

### Post by Kilz on 2006-10-08
> **rlanders said:**
> ```

bert@rlanders-com:~$ ls -l /usr/bin/wine*
-rwxr-xr-x  1 root root   4656 2006-09-29 03:18 /usr/bin/wine
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/wineboot
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winebrowser
-rwxr-xr-x  1 root root  83624 2006-09-29 03:18 /usr/bin/winebuild
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winecfg
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/wineconsole
lrwxrwxrwx  1 root root      7 2006-10-05 08:56 /usr/bin/winecpp -> winegcc
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winedbg
-rwxr-xr-x  1 root root  89332 2006-09-29 03:18 /usr/bin/winedump
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winefile
lrwxrwxrwx  1 root root      7 2006-10-05 08:56 /usr/bin/wineg++ -> winegcc
-rwxr-xr-x  1 root root  22284 2006-09-29 03:18 /usr/bin/winegcc
-rwxr-xr-x  1 root root  14332 2006-09-29 03:18 /usr/bin/wine-kthread
-rwxr-xr-x  1 root root  17732 2006-09-29 03:17 /usr/bin/winelauncher
-rwxr-xr-x  1 root root  58999 2006-09-29 03:17 /usr/bin/winemaker
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winemine
-rwxr-xr-x 15 root root   1582 2006-09-29 03:17 /usr/bin/winepath
-rwxr-xr-x  1 root root   4338 2006-09-29 03:17 /usr/bin/wineprefixcreate
-rwxr-xr-x  1 root root  10484 2006-09-29 03:18 /usr/bin/wine-preloader
-rwxr-xr-x  1 root root   6296 2006-09-29 03:18 /usr/bin/wine-pthread
-rwxr-xr-x  1 root root 260076 2006-09-29 03:18 /usr/bin/wineserver
-rwxr-xr-x  1 root root   6069 2006-09-29 03:17 /usr/bin/wineshelllink
bert@rlanders-com:~$ ls -l /home/bert/c/windows/*
lrwxrwxrwx 1 bert roro   17 2006-10-05 08:57 /home/bert/c/windows/fonts -> /home/bert/.fonts
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 /home/bert/c/windows/notepad.exe -> /usr/lib/wine/notepad.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 /home/bert/c/windows/regedit.exe -> /usr/lib/wine/regedit.exe.so
lrwxrwxrwx 1 bert roro   29 2006-10-05 08:57 /home/bert/c/windows/rundll32.exe -> /usr/lib/wine/rundll32.exe.so
lrwxrwxrwx 1 bert roro   32 2006-10-05 08:57 /home/bert/c/windows/uninstall.exe -> /usr/lib/wine/uninstaller.exe.so
lrwxrwxrwx 1 bert roro   32 2006-10-05 08:57 /home/bert/c/windows/winebrowser.exe -> /usr/lib/wine/winebrowser.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 /home/bert/c/windows/winecfg.exe -> /usr/lib/wine/winecfg.exe.so

/home/bert/c/windows/command:
total 0
lrwxrwxrwx 1 bert roro 26 2006-10-05 08:57 start.exe -> /usr/lib/wine/start.exe.so

/home/bert/c/windows/inf:
total 0

/home/bert/c/windows/system:
total 0
lrwxrwxrwx 1 bert roro 25 2006-10-05 08:57 d3d8.dll -> /usr/lib/wine/d3d8.dll.so
lrwxrwxrwx 1 bert roro 25 2006-10-05 08:57 d3d9.dll -> /usr/lib/wine/d3d9.dll.so

/home/bert/c/windows/system32:
total 4
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 control.exe -> /usr/lib/wine/control.exe.so
lrwxrwxrwx 1 bert roro   25 2006-10-05 08:57 d3d8.dll -> /usr/lib/wine/d3d8.dll.so
lrwxrwxrwx 1 bert roro   25 2006-10-05 08:57 d3d9.dll -> /usr/lib/wine/d3d9.dll.so
drwxr-xr-x 2 bert roro 4096 2006-10-05 08:57 drivers
lrwxrwxrwx 1 bert roro   29 2006-10-05 08:57 fileman.exe -> /usr/lib/wine/winefile.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 notepad.exe -> /usr/lib/wine/notepad.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 progman.exe -> /usr/lib/wine/progman.exe.so
lrwxrwxrwx 1 bert roro   28 2006-10-05 08:57 taskman.exe -> /usr/lib/wine/taskmgr.exe.so
lrwxrwxrwx 1 bert roro   29 2006-10-05 08:57 winmine.exe -> /usr/lib/wine/winemine.exe.so
lrwxrwxrwx 1 bert roro   27 2006-10-05 08:57 winver.exe -> /usr/lib/wine/winver.exe.so

/home/bert/c/windows/temp:
total 0
```


Everything seems to be in place, what happenes when you open a terminal and type in 
```
cd /usr/bin
./winecfg
```

---

### Post by fatsheep on 2006-10-09
Here's a modified version of your script.  The advantage of this version is that all you have to do is double click on the "wine" script and select "run in terminal" and it will install both wine and sidenet.  Also I've used relative path names so it will work in any directory, not just the desktop.  On a sidenote, when you run a script, the terminal automatically changes its working directory to the script's location so there's no need for the *cd ~/Desktop/wine* command.  Hope you like the script,

-sheep

---

### Post by Kilz on 2006-10-10
> **fatsheep said:**
> Here's a modified version of your script.  The advantage of this version is that all you have to do is double click on the "wine" script and select "run in terminal" and it will install both wine and sidenet.  Also I've used relative path names so it will work in any directory, not just the desktop.  On a sidenote, when you run a script, the terminal automatically changes its working directory to the script's location so there's no need for the *cd ~/Desktop/wine* command.  Hope you like the script,

-sheep

The problem is , sidenet cant be run as root, how do you change that once you have used sudo?

---

### Post by fatsheep on 2006-10-11
> **Kilz said:**
> The problem is , sidenet cant be run as root, how do you change that once you have used sudo?

All the commands for installing wine are prefixed with "sudo" (and therefore are run as root).  The command to run sidenet is not (and so it is run as the normal user account).

---

### Post by weird_c00kie on 2006-10-12
AWESOME! IT FINALLY WORKS! *bows to Kilz*

:D :D :D :D

---

### Post by pinkpajamafairy on 2006-10-12
Hi

Ive just tried to install Wine using the HowTo guide and i get this:

```
lauren@lauren:~$ cd ~/Desktop
lauren@lauren:~/Desktop$ dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb libs
lauren@lauren:~/Desktop$ sudo cp ~/Desktop/libs/usr/lib/* /usr/lib32
cp: target `/usr/lib32' is not a directory
```

I only installed ubuntu a few months ago and apart from wireless, this is the first thing ive got stuck on. Any suggestions?

---

### Post by Kilz on 2006-10-12
> **pinkpajamafairy said:**
> Hi

Ive just tried to install Wine using the HowTo guide and i get this:

```
lauren@lauren:~$ cd ~/Desktop
lauren@lauren:~/Desktop$ dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb libs
lauren@lauren:~/Desktop$ sudo cp ~/Desktop/libs/usr/lib/* /usr/lib32
cp: target `/usr/lib32' is not a directory
```

I only installed ubuntu a few months ago and apart from wireless, this is the first thing ive got stuck on. Any suggestions?

Are you sure you are running the amd64 version? open a terminal and type in 
```
ls -l /usr
```
Then copy and paste your results in a reply here.

---

### Post by syounkim on 2006-10-13
Hi, I tried the script but got the following errors: 

```
syounkim@SH361-UBUNTU:~/Desktop/sidenet$ ./setup

SETUP STAGE 1
Stopping wine process ...
renamed ~/.wine to ~/.wine.0610131217
renamed /home/syounkim/c to /home/syounkim/c.0610131217
Creating ~/.wine ...
Setting up install-time configuration ...
Setting up wine base directory structure ...
Setting up drives ...
Linked /media/cdrom to e drive.
Linked /home/syounkim/c/windows/fonts -> ~/.fonts
Installing base font ...

SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Programs -> Program Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Control Panel
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Application Uninstaller
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Wine Configuration
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Task Manager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Programs -> Accesories -> Notepad
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16

SETUP STAGE 3
Setting up wine configuration ...

wine has been setup
syounkim@SH361-UBUNTU:~/Desktop/sidenet$

```

Any suggestions?

---

### Post by fatsheep on 2006-10-13
> **syounkim said:**
> Hi, I tried the script but got the following errors: 

```
syounkim@SH361-UBUNTU:~/Desktop/sidenet$ ./setup

SETUP STAGE 1
Stopping wine process ...
renamed ~/.wine to ~/.wine.0610131217
renamed /home/syounkim/c to /home/syounkim/c.0610131217
Creating ~/.wine ...
Setting up install-time configuration ...
Setting up wine base directory structure ...
Setting up drives ...
Linked /media/cdrom to e drive.
Linked /home/syounkim/c/windows/fonts -> ~/.fonts
Installing base font ...

SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Programs -> Program Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Control Panel
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Application Uninstaller
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Wine Configuration
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Task Manager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Programs -> Accesories -> Notepad
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16

SETUP STAGE 3
Setting up wine configuration ...

wine has been setup
syounkim@SH361-UBUNTU:~/Desktop/sidenet$

```

Any suggestions?

Is this the first time you have run the sidenet script?  Does wine work?

---

### Post by Kilz on 2006-10-14
> **syounkim said:**
> Hi, I tried the script but got the following errors: 


SETUP STAGE 1
Stopping wine process ...
renamed ~/.wine to ~/.wine.0610131217
renamed /home/syounkim/c to /home/syounkim/c.0610131217
Creating ~/.wine ...
Setting up install-time configuration ...
Setting up wine base directory structure ...
Setting up drives ...
Linked /media/cdrom to e drive.
Linked /home/syounkim/c/windows/fonts -> ~/.fonts
Installing base font ...

SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Programs -> Program Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16
Creating shortcut: Start -> Control Panel
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16


Any suggestions?

The GLX errors are from not having 3d accelerated graphics. Have you installed a video card driver for your system?

---

### Post by Pinoy915 on 2006-10-15
I had to redo my system and I was able to do install wine with the manual howto but I can't install any programs. The script doesn't work because the version that's in the web page is 23 instead of 22.

---

### Post by Pinoy915 on 2006-10-15
Nevermind about not being able to install programs. I can install programs but I don't think the script works but manual install does.

---

### Post by Kilz on 2006-10-15
> **Pinoy915 said:**
> Nevermind about not being able to install programs. I can install programs but I don't think the script works but manual install does.

That's because there was a new version of wine released. I have updated everything, and included improvements suggested by fatsheep. The script should now work, and only one is needed now.

---

### Post by rlanders on 2006-10-17
> **Kilz said:**
> Everything seems to be in place, what happenes when you open a terminal and type in 
```
cd /usr/bin
./winecfg
```
```

bert@rlanders-com:~$ cd /usr/bin
bert@rlanders-com:/usr/bin$ ./winecfg
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
```

Could I recompile that in 32bit?

---

### Post by molcanic on 2006-10-18
Followed the step carefully.Also installed all the right GLX files and came up with this after trying to run wine.




wine: creating configuration directory '/home/tony/.wine'...
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  12
  Current serial number in output stream:  13
wine: wineprefixcreate failed while creating '/home/tony/.wine'.
root@ubuntu:~/Desktop# wineserver: could not save registry branch to /home/tony/.wine-Yohrbq/system.reg : No such file or directory
wineserver: could not save registry branch to /home/tony/.wine-Yohrbq/user.reg : No such file or directory

---

### Post by Kilz on 2006-10-18
> **rlanders said:**
> ```

bert@rlanders-com:~$ cd /usr/bin
bert@rlanders-com:/usr/bin$ ./winecfg
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
```

Could I recompile that in 32bit?


I should have expected this. But it looks like the developers have removed the ia32-libs file because they have a working 64bit open office. You are going to need the ia32-libs package. [You can go here and get it]("http://packages.ubuntu.com/edgy/libs/ia32-libs"), or you should be able to 
```
sudo apt-get install ia32-libs
```

---

### Post by Kilz on 2006-10-18
> **molcanic said:**
> Followed the step carefully.Also installed all the right GLX files and came up with this after trying to run wine.




wine: creating configuration directory '/home/tony/.wine'...
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  12
  Current serial number in output stream:  13
wine: wineprefixcreate failed while creating '/home/tony/.wine'.
root@ubuntu:~/Desktop# wineserver: could not save registry branch to /home/tony/.wine-Yohrbq/system.reg : No such file or directory
wineserver: could not save registry branch to /home/tony/.wine-Yohrbq/user.reg : No such file or directory

Open a terminal. Type in 
```
glxgears
```
Does a little window with 3 rotating gears open up, or do you get an error?

---

### Post by molcanic on 2006-10-18
Its an error:

tony@ubuntu:~$ glxgears
Error: couldn't get an RGB, Double-buffered visual
tony@ubuntu:~$

---

### Post by Kilz on 2006-10-18
> **molcanic said:**
> Its an error:

tony@ubuntu:~$ glxgears
Error: couldn't get an RGB, Double-buffered visual
tony@ubuntu:~$

You do not have the video card drivers installd, or they were not installed correctly. You need to install video card drivers into Ubuntu.

---

### Post by molcanic on 2006-10-19
> **Kilz said:**
> You do not have the video card drivers installd, or they were not installed correctly. You need to install video card drivers into Ubuntu.

Your right,I didnt have all the right video drivers installed. After installing the proper drivers and running glxgears command in terminal,I see all three gears in motions.Thanks for the point.

---

### Post by astriskmanish on 2006-10-19
Hello there,,
I have tried the steps to install wine as given in the very first post but while testing it by using the winecfg i got the following error..
manish@powerbox:~$ winecfg
wine: creating configuration directory '/home/manish/.wine'...
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
wine: wineprefixcreate failed while creating '/home/manish/.wine'.
manish@powerbox:~$ wineserver: could not save registry branch to /home/manish/.wine-mn5Yxx/system.reg : No such file or directory
wineserver: could not save registry branch to /home/manish/.wine-mn5Yxx/user.reg : No such file or directory


after that i wont able to come to my command prompt also](*,) ,, SO finally i have to close my terminal window.
So can u please guide me abt wat to do further as i m a new user of LINUX,, so kindly provide me the commands also.
thnx in advance

---

### Post by Kilz on 2006-10-19
> **astriskmanish said:**
> Hello there,,
I have tried the steps to install wine as given in the very first post but while testing it by using the winecfg i got the following error..
manish@powerbox:~$ winecfg
wine: creating configuration directory '/home/manish/.wine'...
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
wine: wineprefixcreate failed while creating '/home/manish/.wine'.
manish@powerbox:~$ wineserver: could not save registry branch to /home/manish/.wine-mn5Yxx/system.reg : No such file or directory
wineserver: could not save registry branch to /home/manish/.wine-mn5Yxx/user.reg : No such file or directory


after that i wont able to come to my command prompt also](*,) ,, SO finally i have to close my terminal window.
So can u please guide me abt wat to do further as i m a new user of LINUX,, so kindly provide me the commands also.
thnx in advance


Exactly what steps did you do to install wine? What method howto or script?

---

### Post by jonah1980 on 2006-10-27
Hi i've got wine working great on my edgy amd64 box. i also installed the sound oss package you made and have the lastest 32bit sound files installed but i still don't get any sound and have the following errors:

jonah@jonah-desktop:~$ winecfg
ALSA lib ../../../src/pcm/pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument

Then when i hit the sound tab in cfg i get this:

err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

---

### Post by Kilz on 2006-10-28
> **jonah1980 said:**
> Hi i've got wine working great on my edgy amd64 box. i also installed the sound oss package you made and have the lastest 32bit sound files installed but i still don't get any sound and have the following errors:

jonah@jonah-desktop:~$ winecfg
ALSA lib ../../../src/pcm/pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument

Then when i hit the sound tab in cfg i get this:

err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack


Are you running Kubuntu? What Windows application does not have sound?

---

### Post by darkshadow on 2006-10-31
I am having trouble with Wine in Edgy64

I have installed the Visual Basic runtime files with NO errors even printed to the console in Wine (0.9.17) under Dapper64
I want to install the same files under Wine (0.9.24) under Edgy64 I get alot of errors and it never works what can I do?
Both versions are precompiled Ubuntu i386 binaries that are linked to from winehq.org
attached is the output from wine vbrun60sp6.exe

---

### Post by Kilz on 2006-11-01
> **darkshadow said:**
> I am having trouble with Wine in Edgy64

I have installed the Visual Basic runtime files with NO errors even printed to the console in Wine (0.9.17) under Dapper64
I want to install the same files under Wine (0.9.24) under Edgy64 I get alot of errors and it never works what can I do?
Both versions are precompiled Ubuntu i386 binaries that are linked to from winehq.org
attached is the output from wine vbrun60sp6.exe

I have no idea why some Windows files do not work in Wine. Perhaps you should try the 0.9.17 version if it worked before.

---

### Post by darkshadow on 2006-11-01
I found out whoever compiled wine did it wrong for edgy I just compiled wine from source and everything worked again. Hopefully the maintainer does better on his second attempt at edgy binaries.

---

### Post by metalfreak666 on 2006-11-06
hi ! 
i did your howto , but when i want to install wine , he says : 
 

sudo dpkg --force-architecture -i wine_0.9.24~winehq0~ubuntu~6.10-1_i386.deb 
dpkg - Warnung: Problem wird übergangen, weil --force angegeben ist:
 Paket-Architektur (i386) passt nicht zum System (amd64)
(Lese Datenbank ... 96183 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von wine 0.9.24~winehq0~ubuntu~6.10-1 (durch wine_0.9.24~winehq0~ubuntu~6.10-1_i386.deb) ...
Entpacke Ersatz für wine ...
Richte wine ein (0.9.24~winehq0~ubuntu~6.10-1) ...
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link


damn

---

### Post by Kilz on 2006-11-07
> **metalfreak666 said:**
> hi ! 
i did your howto , but when i want to install wine , he says : 
 

sudo dpkg --force-architecture -i wine_0.9.24~winehq0~ubuntu~6.10-1_i386.deb 
dpkg - Warnung: Problem wird übergangen, weil --force angegeben ist:
 Paket-Architektur (i386) passt nicht zum System (amd64)
(Lese Datenbank ... 96183 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von wine 0.9.24~winehq0~ubuntu~6.10-1 (durch wine_0.9.24~winehq0~ubuntu~6.10-1_i386.deb) ...
Entpacke Ersatz für wine ...
Richte wine ein (0.9.24~winehq0~ubuntu~6.10-1) ...
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link


damn

Run the install script please.

---

### Post by krecik_77 on 2006-11-09
Hello
I got Wine on my 64bit drapper and i installed zmud on it.
when i run zmud ( by command wine "c:\program files\zmud\zmud.exe" in terminal ) i receive these messages:

fixme:win:LockWindowUpdate (0x1004a), partial stub!pzmud Module not found
fixme:win:LockWindowUpdate ((nil)), partial stub!:\zmud
fixme:win:LockWindowUpdate (0x1003e), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!

and one windows message appears:

Access violation at address 7BC5E42D in module 'ntdll.dll'. Write of address 01C38014

Status in zmud window is "initializing" , when i click "ok" on error window it disappears, but zmud window is freezed - so i must  do "ctrl-c" in terminal.
Is there any way to run zmud in wine on my 64bit drapper? :-k 

p.s.: Sorry for my english...

---

### Post by Kilz on 2006-11-10
> **krecik_77 said:**
> Hello
I got Wine on my 64bit drapper and i installed zmud on it.
when i run zmud ( by command wine "c:\program files\zmud\zmud.exe" in terminal ) i receive these messages:

fixme:win:LockWindowUpdate (0x1004a), partial stub!pzmud Module not found
fixme:win:LockWindowUpdate ((nil)), partial stub!:\zmud
fixme:win:LockWindowUpdate (0x1003e), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!

and one windows message appears:

Access violation at address 7BC5E42D in module 'ntdll.dll'. Write of address 01C38014

Status in zmud window is "initializing" , when i click "ok" on error window it disappears, but zmud window is freezed - so i must  do "ctrl-c" in terminal.
Is there any way to run zmud in wine on my 64bit drapper? :-k 

p.s.: Sorry for my english...


Like the first post in this howto suggests, look in the Wine Application database. The reason is , that I have never ran most of the applications people use. You may want to look [at the page for it]("http://appdb.winehq.org/appview.php?iVersionId=3806") on the wine application database to see if there is anything that may be of help to you.

---

### Post by skullcorp on 2006-11-11
> **Kilz said:**
> I wonder if jdmpike is running Xubuntu. 
If you used the dpkg --force-architecture option to install libxxf86dga1 then it installed the libraries to /usr/lib instead of /usr/lib32 where they are suposed to go. This will result in wine not working. I have edited my howto to avoid use of the archive program. Here is the solution after saving the .deb file to your desktop.
```
cd ~/Desktop
dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb libs
sudo cp ~/Desktop/libs/usr/lib/* /usr/lib32
```

The script that installs the wine bianaries has to be run with sudo, the sidenet setup script has a check and wont let you run it as root.

I was having the "/usr/local/bin/wine: not found" error as well and just wanted to respond that putting these libXxf86dga files in /usr/lib32 did indeed work.  I also had to create a symlink.

```
sudo ln -s /usr/lib32/libXxf86dga.so.1.0.0 /usr/lib32/libXxf86dga.so.1
```

Got it working with the script, manual install, and the .deb file posted earlier.  Thanks Kilz!

---

### Post by fatsheep on 2006-11-11
Glad to see you combined the scripts. :)  However, my friend is having some trouble installing:

[http://pastebin.com/822285](http://pastebin.com/822285)

The first problem is the URL for the wine DL has changed.  I believe you would want the "http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb" url for your wget and dpkg commands...  

The second problem is with this command:

> cp -r -p ~/Desktop/wine/usr/lib/* /usr/lib32/

Since you are writing to /usr/lib32 (a directory the normal user does not have write permission to) you need to prefix the command with sudo:

> sudo cp -r -p ~/Desktop/wine/usr/lib/* /usr/lib32/

Here's the edited script while I'm at it:

> #!/bin/bash

curDirName=$(basename $(pwd) )
curDir=`pwd`
cd ..
rootDir=`pwd`


cd $curDir

sudo apt-get install dpkg-dev
sudo wget -c [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb)
sudo dpkg --force-architecture -i wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb
sudo wget -c [http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb)
sudo dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb ~/Desktop/wine/
sudo cp -r -p ~/Desktop/wine/usr/lib/* /usr/lib32/

#install sidenet written by fatsheep 
cd ./sidenet
./setup
cd $rootDir
sudo rm -r $curDirName

read


I made a couple of other changes just so you could download and run the script from anywhere, not just ~/Desktop...  Shouldn't effect the installation though.  

Hope this helps,

-sheep

---

### Post by KHCloud on 2006-11-11
I ran fatsheep's script on my 64-bit Ubuntu 6.06 and it works fine :)

---

### Post by Kilz on 2006-11-13
> **fatsheep said:**
> Glad to see you combined the scripts. :)  However, my friend is having some trouble installing:

[http://pastebin.com/822285](http://pastebin.com/822285)

The first problem is the URL for the wine DL has changed.  I believe you would want the "http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb" url for your wget and dpkg commands...  

The second problem is with this command:



Since you are writing to /usr/lib32 (a directory the normal user does not have write permission to) you need to prefix the command with sudo:



Here's the edited script while I'm at it:



I made a couple of other changes just so you could download and run the script from anywhere, not just ~/Desktop...  Shouldn't effect the installation though.  

Hope this helps,

-sheep


Thanks sheep, ya wine comes out with a new version every so often. I just added the fix. I also split the scripts . There is one for Dapper and one for Edgy.

---

### Post by yurtfg89327tfg0o on 2006-11-14
I ran the edgy script linked in the first post in this thread.
I got the /usr/local/bin/wine no such file.
Then I read the post above about copying some libs to /usr/lib32
Still no such file.
Then I ran the script quoted in post #216
Still nothing worked.
The I noticed to my utter amazement that my home dir had gone!
I have no idea why this should happen. It's no big deal for me, but I'd hate to think anyone else would suffer such disaster.

---

### Post by Kilz on 2006-11-14
> **yurtfg89327tfg0o said:**
> I ran the edgy script linked in the first post in this thread.
I got the /usr/local/bin/wine no such file.
Then I read the post above about copying some libs to /usr/lib32
Still no such file.
Then I ran the script quoted in post #216
Still nothing worked.
The I noticed to my utter amazement that my home dir had gone!
I have no idea why this should happen. It's no big deal for me, but I'd hate to think anyone else would suffer such disaster.

While I am not sure how that could have happened. I did check the script and reverted the ability to run the script anyplace, to the wine folder that is made when you extract like it was before. Im sorry if this has caused you any problems.

---

### Post by sdavmor on 2006-11-17
I used the sidenet tools to get Wine going last night on an Edgy laptop after banging my head on a wall for several hours.  Once I went to sidenet everything fell into place, allowing me to install a needed Windows-based terminal/comm program needed for dealing with one set of customers.  I still have a few hurdles to cross, but my laptop is now "windows free".

---

### Post by MetalSlugX on 2006-11-17
I installed wine using your script but how do I uninstall it? I've tried using make uninstall and it says the command is not found.

---

### Post by nandanator on 2006-11-18
Hi
 I installed the wine_0.9.12~winehq1-1_i386.deb and all the different libraries which i noticed mentioned in the forum.Im using an AMD64 3000+ nVIDIA GeForce 6100,nForce 410,ASUS A8N-VM .I get the follwing error msg when i do
nandu@nandu-desktop:/$ winecfg


Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).


ALso when i do wine C:\\Program\ Files\\Internet\ Explorer\\IEXPLORE.EXE
I get the msg

Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
wine: cannot find 'C:\Program Files\Internet Explorer\IEXPLORE.EXE'


Please help

---

### Post by MetalSlugX on 2006-11-18
I installed Wine using the script and Steaminstall worked. But Then I couldn't play coutner strike. So I uninstalled it and tried to build it myself. That didn't work. So I uninstalled that and tried to install Wine using the script again. But this time it dosn't work at all I get this error. 

wine Steaminstall
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:shell:IShellLinkA_fnGetPath (0x1a8dc8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1bea00): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1bea00): WIN32_FIND_DATA is not yet filled.


Also a window pops up telling me 
to stop running steam in compatibility mode. I've never got that window before it says

"Please turn off compatibility mode"
-right click Steam.exe
-select properties
-go to compatibility tab
-uncheck run this application in compatibility mode

---

### Post by vanishedsoul on 2006-11-18
There is some kind of dpkg error comes everytime when i going to install wine, i'm using 64bit ver of ubuntu

**sudo dpkg --force-architecture -i wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb**

here is the terminal processing:

[B]gangsta@gangsta-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb
dpkg: status database area is locked by another process[/B]

plzz do help...

---

### Post by nandanator on 2006-11-18
Here is the reply man

> **vanishedsoul said:**
> There is some kind of dpkg error comes everytime when i going to install wine, i'm using 64bit ver of ubuntu

**sudo dpkg --force-architecture -i wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb**

here is the terminal processing:

[B]gangsta@gangsta-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb


dpkg: status database area is locked by another process[/B]


:) Hey I have also faced such a situation and the solution is to look out for an instance of Synaptic running.If it is so ,close it and do the same ,that is.
gangsta@gangsta-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb


It would work.:D 


plzz do help...

---

### Post by Kilz on 2006-11-18
> **MetalSlugX said:**
> I installed wine using your script but how do I uninstall it? I've tried using make uninstall and it says the command is not found.

Since you did not compile anything, using make uninstall isnt going to work. The easiest way to uninstall it is to use synaptic and search for the wine package.

> **MetalSlugX said:**
> I installed Wine using the script and Steaminstall worked. But Then I couldn't play coutner strike. So I uninstalled it and tried to build it myself. That didn't work. So I uninstalled that and tried to install Wine using the script again. But this time it dosn't work at all I get this error. 

wine Steaminstall
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:shell:IShellLinkA_fnGetPath (0x1a8dc8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1bea00): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1bea00): WIN32_FIND_DATA is not yet filled.


Also a window pops up telling me 
to stop running steam in compatibility mode. I've never got that window before it says

"Please turn off compatibility mode"
-right click Steam.exe
-select properties
-go to compatibility tab
-uncheck run this application in compatibility mode

Im not sure what to sugest, Try running the script again. Then enter the ```
wincfg
``` command in a terminal and tell me if the config panel shows.

---

### Post by Kilz on 2006-11-18
> **nandanator said:**
> Hi
 I installed the wine_0.9.12~winehq1-1_i386.deb and all the different libraries which i noticed mentioned in the forum.Im using an AMD64 3000+ nVIDIA GeForce 6100,nForce 410,ASUS A8N-VM .I get the follwing error msg when i do
nandu@nandu-desktop:/$ winecfg


Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).


ALso when i do wine C:\\Program\ Files\\Internet\ Explorer\\IEXPLORE.EXE
I get the msg

Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
wine: cannot find 'C:\Program Files\Internet Explorer\IEXPLORE.EXE'


Please help

That is a rather old version of wine The errors say it doesnt recognise the language pack, You are also miccing the main library. Please reread the howto or use the script to install it.

---

### Post by Kilz on 2006-11-18
> **vanishedsoul said:**
> There is some kind of dpkg error comes everytime when i going to install wine, i'm using 64bit ver of ubuntu

**sudo dpkg --force-architecture -i wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb**

here is the terminal processing:

[B]gangsta@gangsta-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb
dpkg: status database area is locked by another process[/B]

plzz do help...

"status database area is locked by another process" says that you have another program open that can install packages like Synaptic or the updater. That application is in charge of the applications so you cant use another way of installing anything untill you close it.

---

### Post by vanishedsoul on 2006-11-19
well your hint did worked. The wine was installed but the wincfg did'nt worked, gave the following error:

[B]gangsta@gangsta-desktop:~$ winecfg
wine: creating configuration directory '/home/gangsta/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
wine: wineprefixcreate failed while creating '/home/gangsta/.wine'.
gangsta@gangsta-desktop:~$ wineserver: could not save registry branch to /home/gangsta/.wine-CzEu5L/system.reg : No such file or directory
wineserver: could not save registry branch to /home/gangsta/.wine-CzEu5L/user.reg : No such file or directory

[/B]

---

### Post by Kilz on 2006-11-19
> **vanishedsoul said:**
> well your hint did worked. The wine was installed but the wincfg did'nt worked, gave the following error:

[B]gangsta@gangsta-desktop:~$ winecfg
wine: creating configuration directory '/home/gangsta/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
wine: wineprefixcreate failed while creating '/home/gangsta/.wine'.
gangsta@gangsta-desktop:~$ wineserver: could not save registry branch to /home/gangsta/.wine-CzEu5L/system.reg : No such file or directory
wineserver: could not save registry branch to /home/gangsta/.wine-CzEu5L/user.reg : No such file or directory

[/B]

Did you install the sidenet script? Do you have accelerated graphics drivers? To check for the drivers enter ```
glxgears
``` in a terminal.

---

### Post by vanishedsoul on 2006-11-20
hi, now i have installed the sidenet script, the belows is its output, i think the eoor it is again giving ight be of the graphics drivers i dont have. I have intel 945gnt board with the default drivers which the ubuntu installed.

[B]gangsta@gangsta-desktop:~/Desktop$ cd ~/Desktop/sidenet
gangsta@gangsta-desktop:~/Desktop/sidenet$ ./setup

SETUP STAGE 1
Stopping wine process ...
renamed ~/.wine to ~/.wine.0611202017
renamed /home/gangsta/c to /home/gangsta/c.0611202017
Creating ~/.wine ...
Setting up install-time configuration ...
Setting up wine base directory structure ...
Setting up drives ...
Linked /media/cdrom to e drive.
Linked /home/gangsta/c/windows/fonts -> ~/.fonts
Installing base font ...

SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
Creating shortcut: Start -> Programs -> Program Magager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
Creating shortcut: Start -> Control Panel
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
Creating shortcut: Start -> Application Uninstaller
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
Creating shortcut: Start -> Wine Configuration
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
Creating shortcut: Start -> Task Manager
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
Creating shortcut: Start -> Programs -> Accesories -> Notepad
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18

SETUP STAGE 3
Setting up wine configuration ...

wine has been setup
[/B]


i used your given command for checking the drivers and i think i dont have the graphic drivers, is it the case??

[B]gangsta@gangsta-desktop:~/Desktop$ glxgears
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
gangsta@gangsta-desktop:~/Desktop$
[/B]

---

### Post by Kilz on 2006-11-20
> **vanishedsoul said:**
> 

i used your given command for checking the drivers and i think i dont have the graphic drivers, is it the case??

[B]gangsta@gangsta-desktop:~/Desktop$ glxgears
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
gangsta@gangsta-desktop:~/Desktop$
[/B]

That is the case, and thats the reason you are getting all the GLX errors.

---

### Post by vanishedsoul on 2006-11-21
hey thanks a lot for all your patience, i have looked for the linux ver of my motherboard divers and here is the linkfor it. Please do me a favour, there is a list of OS there and lots of LINUX OS are there like Redhat SuSe etc but cant find the UBUNTU there. The nearest to UBUNTU is ( i think) is **Debian* 3.1 Linux**. Ubuntu is debian based, is it the right OS for the UBUNTU?? here is the link for that page:
[http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=2068&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=2068&lang=eng)

---

### Post by Kilz on 2006-11-22
> **vanishedsoul said:**
> hey thanks a lot for all your patience, i have looked for the linux ver of my motherboard divers and here is the linkfor it. Please do me a favour, there is a list of OS there and lots of LINUX OS are there like Redhat SuSe etc but cant find the UBUNTU there. The nearest to UBUNTU is ( i think) is **Debian* 3.1 Linux**. Ubuntu is debian based, is it the right OS for the UBUNTU?? here is the link for that page:
[http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=2068&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=2068&lang=eng)

Im not good at intel graphics. I have an ATI x200. You might want to ask in another part of the forum for help with intel graphics. I would hate to tell you something wrong and make your system unusable because the gui wont start.

---

### Post by doniv on 2006-12-01
I'm getting this exact same problem. glxgears displays all the errors as above, but shows a window with 3 different colored spinning gears.

Any clue on what to do with this?

---

### Post by back2ubuntu on 2006-12-02
Hello,

Following you guide in edgy and running winecfg, I get:

winecfg
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
err:winecfg:load_drives GetVolumeInformation() for 'G:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'G:\' failed, setting serial to 0


And running someWXPstuff.exe I get:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
err:wgl:ConvertPixelFormatWGLtoGLX Can't find a matching FBCONFIG_ID for VISUAL_ID 0x24!
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x24!
err:wgl:ConvertPixelFormatWGLtoGLX Can't find a matching FBCONFIG_ID for VISUAL_ID 0x24!
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x24!
err:wgl:ConvertPixelFormatWGLtoGLX Can't find a matching FBCONFIG_ID for VISUAL_ID 0x24!
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x24!
err:seh:setup_exception stack overflow 0 bytes in thread 0009 eip 7bc2f380 esp 00241000 stack 0x241000-0x350000

Please help.

cheers.

---

### Post by nandanator on 2006-12-04
[QUOTE=Kilz;1777009]That is a rather old version of wine The errors say it doesnt recognise the language pack, You are also miccing the main library. 


Could you please let me know the libraries once more?.Please help me out as Iam a total newbie who is trying to do all sorts of experiments,and trying to  get more acquainted with Linux

---

### Post by Coldbird on 2006-12-04
Thanks bud... downloaded the WoW One... Changed the Script a bit... and voila... worked fine... Good Work! :D

---

### Post by Kilz on 2006-12-06
> **nandanator said:**
> [QUOTE=Kilz;1777009]That is a rather old version of wine The errors say it doesnt recognise the language pack, You are also miccing the main library. 


Could you please let me know the libraries once more?.Please help me out as Iam a total newbie who is trying to do all sorts of experiments,and trying to  get more acquainted with Linux

Just follow the howto on the first page. :D

---

### Post by xaryC on 2006-12-14
Hi,

I'm having troubles installing wine on edgy 6.10. This is what I get:

[PHP]SETUP STAGE 1
Stopping wine process ...
renamed ~/.wine to ~/.wine.0612150010
Creating ~/.wine ...
Setting up install-time configuration ...
Setting up wine base directory structure ...
Setting up drives ...
Linked /media/cdrom to e drive.
Linked /home/olivier/c/windows/fonts -> ~/.fonts
Installing base font ...

SETUP STAGE 2
Setting up default registry ...

Setting up sidenet-spicific configuration ...

Setting up language pack for Language : en ...
Install prefix is /usr/lib/wine
Installing MPlayer codec package ...
Registering MPlayer codec package ...
Installing true.exe dummy application ...
Installing ShellLinker ...
Creating shortcut: Start -> Programs -> File Magager
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
Creating shortcut: Start -> Programs -> Program Magager
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
Creating shortcut: Start -> Control Panel
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
Creating shortcut: Start -> Application Uninstaller
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
Creating shortcut: Start -> Wine Configuration
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
Creating shortcut: Start -> Task Manager
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
Creating shortcut: Start -> Programs -> Accesories -> Notepad
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135
Creating shortcut: Start -> Programs -> Accesories -> Mine Sweeper
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:import_dll Loading library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libgcc_s.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.DLL (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\shelllink.exe" failed, status c0000135

SETUP STAGE 3
Setting up wine configuration ...

wine has been setup[/PHP]

Any help appriciated :) 

thank you!

---

### Post by Kilz on 2006-12-15
> **xaryC said:**
> Hi,

I'm having troubles installing wine on edgy 6.10. This is what I get:


Any help appriciated :) 

thank you!

Did you use the automated setup script for edgy or did you follow the manual howto?

---

### Post by x64Jimbo on 2006-12-15
> **Kilz said:**
> Did you use the automated setup script for edgy or did you follow the manual howto?
That looks like script output, but I'm unsure as to which script.

---

### Post by xaryC on 2006-12-15
> **Kilz said:**
> Did you use the automated setup script for edgy or did you follow the manual howto?

I used the script on page 1 of this topic (for edgy).

manual installing did not work. Could not copy the libz dir, even with sudo...

---

### Post by reeper_aut on 2006-12-22
I've installed wine and run the sidenet-script when first installed.
the later versions, where installed automatical by adept.

now i get an error like this:

err:ddraw: DDRAW_Create Couldn't load WineD3D - OpenGL libs not present?

gears works fine
libs should be right there.

not sure if this is related, but there is one more:

fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot

---

### Post by stretchtiberius on 2006-12-22
I am new to Linux but am looking forward to using Edgy on my 64 bit laptop. I have installed wine but am having some problems. When attempting to run winecfg I get the following messages:
[INDENT]err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: wrong ELF class: ELFCLASS64
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).[/INDENT]

I have installed ia32-libs so I don't have a clue what the problem is. I am able to run glxgears so my graphics driver should be OK. What do you think?

---

### Post by JavierRodriguez on 2006-12-27
hmm i'm a linux newb, and i'm trying to setup my new zune that i got, i have a ipod nano, that runs perfect but i can't figure out this zune.

this is what i get when i try running ZuneSetup

javier@iggie:~/Desktop/ZuneSetup$ wine ZuneSetup
err:module:import_dll Library msi.dll (which is needed by L"D:\\Desktop\\ZuneSetup\\ZuneSetup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\Desktop\\ZuneSetup\\ZuneSetup.exe" failed, status c0000135

'eh, hopefully i can get this to work thru ubuntu so i don't have to go thru the pain of going back to windows.  thank you :)

---

### Post by 454redhawk on 2006-12-27
I tried to use the Edgy script.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg-dev is already the newest version.
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libgnet2.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--14:41:00--  http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb
           => `wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb'
[COLOR="Red"]Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:41:00 ERROR 404: Not Found.[/COLOR]

dpkg: error processing wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.25~winehq0~ubuntu~6.10-1_i386.deb
--14:41:00--  http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb
           => `libxxf86dga1_1.0.0-0ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,062 (9.8K) [text/plain]

100%[====================================>] 10,062        --.--K/s             

14:41:01 (65.51 KB/s) - `libxxf86dga1_1.0.0-0ubuntu3_i386.deb' saved [10062/10062]


ERROR: Could not find wine installation.
       Setup wine first.
Setup aborted.

```

---

### Post by Yaks Hairbrush on 2007-01-05
Kilz, thanks for the script. It mostly worked very well.

There are two problems I had. Firstly, wine0.9.25 doesn't seem to be where the script says it should be. Had to change to 0.9.28, and it went through.

Second, when it got to the sidenet configuration script, it output a few errors:

```
Creating shortcut: Start -> Programs -> Program Magager
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Control Panel
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Application Uninstaller
Creating shortcut: Start -> Wine Configuration
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Task Manager
Creating shortcut: Start -> Programs -> Accesories -> Notepad
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
```

Sure enough, I don't have shortcuts for Program Manager, Control Panel, Wine Configuration, or Notepad.

How do I make these shortcuts manually? I'm running Dapper.

---

### Post by wlwood on 2007-01-06
Thanks for setting up this simple process. When I tried to use the script today, it failed to find the wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb version of wine included in the script. I looked at the repository and discovered that it no longer lists that version, so I opened the script on my desktop and edited it to look for wine_0.9.28~winehq0~ubuntu~6.06-1_i386.deb instead. Everything worked perfectly. 

Thanks again.

---

### Post by Yaks Hairbrush on 2007-01-06
> **Yaks Hairbrush said:**
> Kilz, thanks for the script. It mostly worked very well.

There are two problems I had. Firstly, wine0.9.25 doesn't seem to be where the script says it should be. Had to change to 0.9.28, and it went through.

Second, when it got to the sidenet configuration script, it output a few errors:

```
Creating shortcut: Start -> Programs -> Program Magager
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Control Panel
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Application Uninstaller
Creating shortcut: Start -> Wine Configuration
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Task Manager
Creating shortcut: Start -> Programs -> Accesories -> Notepad
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Creating shortcut: Start -> Programs -> Accesories -> Registry Editor
```

Sure enough, I don't have shortcuts for Program Manager, Control Panel, Wine Configuration, or Notepad.

How do I make these shortcuts manually? I'm running Dapper.

I've figured out the problem: the directory ~/.local/share/icons seems to hold the icons. There are no icons there for Program Manager, Control Panel, Wine Configuration or Notepad. Any chance one of you could provide links to these icons?

Thanks.

---

### Post by Xureath on 2007-01-07
I used the install script to get wine working (0.9.28) on Edgy Eft and it all seemed to installed ok (except for those shortcuts) but I haven't got any ALSA sound in wine. 

When I start winecfg and go to the "Audio" tab I only have OSS to choose from and I get the following output in the console: 

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: wrong ELF class: ELFCLASS64

```

I have installed ia32-libs and I can't figure out what to do to get it working.

---

### Post by -pod- on 2007-01-08
Hi, :D 

thanks for the usefull howto.

I installed wine 0.9.28 on dapper. Everything worked fine.
I wasn't able to use the script since the [wineHQ repo]("http://www.winehq.com/site/download-deb") for older packages has been moved so i guess the script should be updated, btw following the manual installation instruction is pretty easy and works fine.

Didn't have time to test it good yet, thought

> **Xureath said:**
> I used the install script to get wine working (0.9.28) on Edgy Eft 
When I start winecfg and go to the "Audio" tab I only have OSS to choose from and I get the following output in the console: 

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: wrong ELF class: ELFCLASS64

```

I get the same error, ani have those packages (64b version) installed on my system so, somebody corrects me if i'm wrong, it's just a librarylink problem, isn't it?

---

### Post by encikraju on 2007-01-09
Hi, I'm using edgy. This is my error when I run hl.exe

```
fixme:seh:check_no_exec No-exec fault triggered at 0x1e61e39, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e66609, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e5f4b0, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e69fac, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e656d3, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e6a01e, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e6d0f2, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e64704, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e6cea5, enabling work-around
err:seh:setup_exception nested exception on signal stack in thread 0009 eip 7efd4b73 esp 7ffddbf0 stack 0x231000-0x340000
```

My glxgears is working.

---

### Post by anselmograciani on 2007-01-12
Thank you Kilz, thank you, thank you.

I've used wine_0.9.29~winehq0~ubuntu~6.10-1_i386.deb. Everything worked perfectly.

Thanks again.
Anselmo.

---

### Post by LuisD on 2007-01-14
Thanx Kilz.

Excellent!

I used wine_0.9.29~winehq0~ubuntu~6.10-1_i386.deb.

I got this error: 

err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": li       bxslt.so.1: wrong ELF class: ELFCLASS64

But it worked! If I have problems using it I'll post.   Thanx!!!

---

### Post by thricebedamned on 2007-01-23
Hey, total newb here.  I'm using Dapper.  I tried installing wine 0.9.29 using the manual how-to.

I get this:

```
david@david-desktop:~/Desktop$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18

```
Any help?

EDIT: glxgears works fine, so it's not a opengl thing.  I installed sidenet with similar error reports.

---

### Post by WhiteHorse on 2007-01-28
OK so the new wine is out(9.30) and no pkg for amd64 so I compiled from source and it worked but I had to follow these instructions(taken from the main wine site):

Building Wine on Ubuntu / Kubuntu 6.06 (Dapper Drake)

Warning: Wine will not compile if you install libicu34-dev listed at Recommended Packages on 32bit. No bi-directional text support. This causes make to fail with an ld error about relocating ELF 64 or something like that. Someone found a workaround for this but I haven't tested it: [http://www.ilfilosofo.com/blog/2007/01/12/installing-wine-on-ubuntu-edgy-610-64-bit/](http://www.ilfilosofo.com/blog/2007/01/12/installing-wine-on-ubuntu-edgy-610-64-bit/)

First one must install the necessary libraries: Finding the correct set may take a few minutes and several tries. You will need freetype or the fonts will be barely legible.

sudo apt-get install libfreetype6-dev
sudo apt-get install fontforge

configure will find several omissions, but a few will only be noticed by the 'make' steps.

Make sure you have the following packages installed:

sudo apt-get install gcc flex bison libc6-i386 libc6-dev-i386

Now add the following links that the library install does not make:

cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so

You may also want to try and link opengl. It built on my machine with the links below, but failed at runtime with an opengl error. You may have better luck. If opengl fails, remove the links, and run configure and make again.

sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so

Run configure, build and install with:

LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
make depend
make all
sudo make install

If all needed libraries are present there will be no missing-library warnings or errors anywhere.

wine seems to work (installed in /usr/local)

---

### Post by tjk on 2007-01-30
I've tried several times to install wine using your instructions, but I always get the message "bash: ./configure: No such file or directory"  when I run the command: LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure

---

### Post by rogeriovinhal on 2007-02-04
Sidenet seems to have made wine work for me at last.

But I have 2 tricky problems.

The first one is that I can't make wine lock the mouse in the wine screen, even with the option in winecfg enabled, if the mouse goes off the screen, it shows a unescaled ugly piece of the background. I tried all the combinations possible with and without virtual desktop and alowing the and not alowing the window manager to fit the screen. None worked.

The second one is with the sound. What is the problem with the sound in Wine? I could only make it work with ALSA drivers, and sound is a lot delayed, and gives a lot of buffer overrun messages while I am playing.

EDIT:
Actually, another problem came out.
Sidenet's script configures wine for the English language.
Is there a way I can reconfigure it for brazillian portuguese, so dead keys like 'é' 'ã' 'ç' could really show up?

---

### Post by IronArjen on 2007-02-06
Hi thanks for the HOWTOs (multiple indeed!),

One problem I get a badallocation error? This is some output.

arjen@beavis:~/Desktop/Alignment programming/Treeview$ winecfg
wine: creating configuration directory '/home/arjen/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
wine: wineprefixcreate failed while creating '/home/arjen/.wine'.
arjen@beavis:~/Desktop/Alignment programming/Treeview$ wineserver: could not save registry branch to /home/arjen/.wine-yR2Wey/system.reg : No such file or directory
wineserver: could not save registry branch to /home/arjen/.wine-yR2Wey/user.reg : No such file or directory

I get the same with winefile or when I try an exe that in windows does not require installation or when I try to install a program. I don 't get it: not enough resources to check whether wine works or to shows me a directory?

---

### Post by Lex-Man on 2007-03-04
I trying to install wine on an AMD 3200+ I have followed you tutorial but every time I try and install wine I get the error 

ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

I found another post by a user who used the code 

sudo apt-get install ia32-libs*

I have tried this and it doesn't work.

I am trying to install wine version 

wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb

and I am using Ubuntu 6.10

---

### Post by vinchi007 on 2007-03-08
> **Lex-Man said:**
> I trying to install wine on an AMD 3200+ I have followed you tutorial but every time I try and install wine I get the error 

ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

I found another post by a user who used the code 

sudo apt-get install ia32-libs*

I have tried this and it doesn't work.

I am trying to install wine version 

wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb

and I am using Ubuntu 6.10

You will need to create symbolic link for this file in folder /usr/lib32:
"cd /usr/lib32"

check if you have the file: 
"ls -l /usr/lib32/libXxf86dga.so.1"

If you do have this file, then create symbolic link of this file:
"sudo ln -s libXxf86dga.so.1 libXxf86dga.so"

If you do NOT  have that file then install it library package:
"sudo apt-get install ia32-libs"
and then try to create symbolic link again.
(Note: all these libraries are in /usr/lib32 folder)

Hope this helps.

---

### Post by noenter1 on 2007-03-18
Ok recently installed wine(again) these are the errors im getting:
```
$ winecfg
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```
Then when I go into the adio tab I get:
```
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: wrong ELF class: ELFCLASS64
```
I installed jack and all the libraries before I installed wine. Any help on howto fix these would be apretiated.
Also i cant seem to be able to get sound to work from any 2 programs anymore.

---

### Post by Kilz on 2007-03-18
> **noenter1 said:**
> Ok recently installed wine(again) these are the errors im getting:
```
$ winecfg
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```
Then when I go into the adio tab I get:
```
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: wrong ELF class: ELFCLASS64
```
I installed jack and all the libraries before I installed wine. Any help on howto fix these would be apretiated.
Also i cant seem to be able to get sound to work from any 2 programs anymore.

What issues were you originally trying to fix other than a error message?

---

### Post by noenter1 on 2007-03-19
I just installed a Geforce 880GTX card. I had  first installed the nvidia driver on my test boot. It had faild on my primary boot(got it working, however all sound is broken). So I reinstalled wine. At first it wouldnt even install using(amd64):
```
sudo dpkg --force-architecture -i wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb
```
When I typed this in everything seemed to install fine in the terminal, however when i went into my file manager i couldnt find any of the wine files. When i ran winecfg it gave me a pretty long list of errors. In the past I have been able to install it this way, however this time I wasn't able to. I had to use your setup script, and it seemed to work. Ran winecfg and got all the errors that I already stated. I also had already installed all the sound libraries needed according to you guide(alsa-oss to). No problems with the registry or anything else tho.

---

### Post by boomboy on 2007-03-19
> **Xureath said:**
> I used the install script to get wine working (0.9.28) on Edgy Eft and it all seemed to installed ok (except for those shortcuts) but I haven't got any ALSA sound in wine. 

When I start winecfg and go to the "Audio" tab I only have OSS to choose from and I get the following output in the console: 

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: wrong ELF class: ELFCLASS64

```

I have installed ia32-libs and I can't figure out what to do to get it working.

I also encounter the same problem. I realised that the script tries to download wine from a source that no longer exists, so I just manually downloaded the .deb package and placed it in the wine folder. The script gives a 404 error for download, but continues on to completion. Any fixes?

---

### Post by Kilz on 2007-03-19
> **noenter1 said:**
> I just installed a Geforce 880GTX card. I had  first installed the nvidia driver on my test boot. It had faild on my primary boot(got it working, however all sound is broken). So I reinstalled wine. At first it wouldnt even install using(amd64):
```
sudo dpkg --force-architecture -i wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb
```
When I typed this in everything seemed to install fine in the terminal, however when i went into my file manager i couldnt find any of the wine files. When i ran winecfg it gave me a pretty long list of errors. In the past I have been able to install it this way, however this time I wasn't able to. I had to use your setup script, and it seemed to work. Ran winecfg and got all the errors that I already stated. I also had already installed all the sound libraries needed according to you guide(alsa-oss to). No problems with the registry or anything else tho.

Errors are to be expected, but what issues do you have now, other than some error message?

---

### Post by Kilz on 2007-03-19
> **boomboy said:**
> I also encounter the same problem. I realised that the script tries to download wine from a source that no longer exists, so I just manually downloaded the .deb package and placed it in the wine folder. The script gives a 404 error for download, but continues on to completion. Any fixes?

What version of wine are you trying to install with that method, also what version (number) of the script are you running.

---

### Post by noenter1 on 2007-03-19
Having sound issues, can't get sound working from multiple programs like a game and ventrilo(giuld uses ventrilo cant get them to switch to teamspeak).

---

### Post by Kilz on 2007-03-19
> **noenter1 said:**
> Having sound issues, can't get sound working from multiple programs like a game and ventrilo(giuld uses ventrilo cant get them to switch to teamspeak).

Looking at the error

err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: wrong ELF class: **ELFCLASS64**

It appears you dont have the 32bit libraries for sound. The library it finds is 64bit.

[You can download the 32bit version here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnas%2Flibaudio2_1.8-2_i386.deb&md5sum=a0c510006f70dc6e944d6b091d5b1b82&arch=i386&type=main") You will then have to extract the files and manualy copy them to /usr/lib32.

```
cd ~/Desktop
dpkg -x libaudio2_1.8-2_i386.deb
sudo cp ~/Desktop/libs/usr/lib/* /usr/lib32
```

[You can get the other library its asking for here.]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fe%2Fesound%2Flibesd-alsa0_0.2.36-3ubuntu3_i386.deb&md5sum=7ccc3904810db6b235f2207302208bbc&arch=i386&type=main")  and [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fj%2Fjack-audio-connection-kit%2Flibjack0.100.0-dev_0.101.1-1_i386.deb&md5sum=c123a46e5e5bdd197f4b6e698d517013&arch=i386&type=main") Then use edited commands like above to do the same trick. That will get rid of the errors.

---

### Post by DevilDux on 2007-03-19
Okay, I have been trying to get this going for a  bit.  I am following the howto listed on the first page, and also some of the tips found throughout this thread for fixing my issue. 

> ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link


I get that error for several things I attempt to do, including installing wine with the dpkg command.   I also get it when installing lib32 stuff.  One of the suggestions was running:
> sudo apt-get install ia32-libs*

That also gave me the same error eventually, and wine would not install after that either. 

I am running Xubuntu Edgy AMD64

---

### Post by Kilz on 2007-03-19
> **DevilDux said:**
> Okay, I have been trying to get this going for a  bit.  I am following the howto listed on the first page, and also some of the tips found throughout this thread for fixing my issue. 



I get that error for several things I attempt to do, including installing wine with the dpkg command.   I also get it when installing lib32 stuff.  One of the suggestions was running:


That also gave me the same error eventually, and wine would not install after that either. 

I am running Xubuntu Edgy AMD64

Look in that location, /usr/lib32 for libXxf86dga.so.1. See if its a link or a file. Also see if any other libXxf86dga exists.

---

### Post by DevilDux on 2007-03-19
> **Kilz said:**
> Look in that location, /usr/lib32 for libXxf86dga.so.1. See if its a link or a file. Also see if any other libXxf86dga exists.

I have 

libXxf86dga.so (a link to libXxf86dga.so.1) and
libXxf86dga.so.1
libXxf86dga.so.1.0.0  Both are files

---

### Post by noenter1 on 2007-03-19
Ok I installed and copied the file, however its not working. Ill just have to tell my guild "If you want to hear me and want me to hear you use teamspeak"

---

### Post by Kilz on 2007-03-20
> **DevilDux said:**
> I have 

libXxf86dga.so (a link to libXxf86dga.so.1) and
libXxf86dga.so.1
libXxf86dga.so.1.0.0  Both are files

Ok, on my system libXxf86dga.so.1 is a link to libXxf86dga.so.1.0.0. So we will change a few things to get rid of the error. Open a terminal and paste in the following commands. The first 2 just rename things, then we make new links.

```
sudo mv -f /usr/lib32/libXxf86dga.so /usr/lib32/libXxf86dga.so.old
sudo mv -f /usr/lib32/libXxf86dga.so.1 /usr/lib32/libXxf86dga.so.1.old
sudo ln -s /usr/lib32/libXxf86dga.so.1.0.0 /usr/lib32/libXxf86dga.so
sudo ln -s /usr/lib32/libXxf86dga.so.1.0.0 /usr/lib32/libXxf86dga.so.1
```

---

### Post by DevilDux on 2007-03-20
> **Kilz said:**
> Ok, on my system libXxf86dga.so.1 is a link to libXxf86dga.so.1.0.0. So we will change a few things to get rid of the error. Open a terminal and paste in the following commands. The first 2 just rename things, then we make new links.

```
sudo mv -f /usr/lib32/libXxf86dga.so /usr/lib32/libXxf86dga.so.old
sudo mv -f /usr/lib32/libXxf86dga.so.1 /usr/lib32/libXxf86dga.so.1.old
sudo ln -s /usr/lib32/libXxf86dga.so.1.0.0 /usr/lib32/libXxf86dga.so
sudo ln -s /usr/lib32/libXxf86dga.so.1.0.0 /usr/lib32/libXxf86dga.so.1
```

That worked perfectly for me.  Now I get this Error:
> 
err:wgl:has_opengl  glx_version as 1.3 and GLX_SGIX_fbconfig extension is unsupported. Expect problems.

From what I have found in Google, it seems that was an issue with the Wine 0.9.21 source which I assume the link for the WoW patched wine in the first post is based on.  It doesn't seem to stop me from continuing, so I am going to try that a bit.

---

### Post by Kilz on 2007-03-20
> **DevilDux said:**
> That worked perfectly for me.  Now I get this Error:


From what I have found in Google, it seems that was an issue with the Wine 0.9.21 source which I assume the link for the WoW patched wine in the first post is based on.  It doesn't seem to stop me from continuing, so I am going to try that a bit.

You may want to try 9.32, from what I have read it runs WoW without need of patching.

---

### Post by DevilDux on 2007-03-20
> **Kilz said:**
> You may want to try 9.32, from what I have read it runs WoW without need of patching.

 Thanks for all the help you have given me, this thread and the other, mainly this was a bit of experimentation for me.  I have downloaded a couple different install CDs and I am going to try Kubuntu next, sticking with AMD64 for now.  I will definitely come back here and try the WoW install again.  Also going with the newer version of Wine.  Yes I know I can just install the Desktop Packages for Kubuntu/Ubuntu but I want to try them from the Install in. 

Well the last copy just came out of the burner I'm going to reboot now and reinstall.

---

### Post by tmalloy on 2007-03-21
I've tried this and i only have one problem, i get 

```
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

I'm thinking it might have something to do with libX11.so in /usr/lib32/ libX11.so links to libX11.so.6 which links to libX11.so.6.2.0

Should that be happening? Thanks in advance for help!

---

### Post by Kilz on 2007-03-22
> **tmalloy said:**
> I've tried this and i only have one problem, i get 

```
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

I'm thinking it might have something to do with libX11.so in /usr/lib32/ libX11.so links to libX11.so.6 which links to libX11.so.6.2.0

Should that be happening? Thanks in advance for help!

More likely you need to install a video driver with acceleration.

---

### Post by tmalloy on 2007-03-24
i think i already have a video driver with acceleration. I installed ati drivers in order to run xgl/beryl

---

### Post by cborga1985 on 2007-03-25
Edgy script didn't work so i updated it. Here is the script updated for the new version.

---

### Post by JamonTerrell on 2007-03-30
Hi,

First off, I'm running Feisty.  This tutorial worked wonderfully under fiesty until I did an update/upgrade today which apparently broke something :-)  I can no longer run any of my 32bit applications (including wine and firefox32).  Wine's error message is as follows:

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libxcb.so.1: wrong ELF class: ELFCLASS64


and another similar one for libxcb-xlib0.  If anyone else gets this, what you need to do to fix it is very similar to the other libs... just download them both (32 bit versions of course) from:
[ftp://us.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xlib0_1.0-1.1ubuntu2_i386.deb](ftp://us.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xlib0_1.0-1.1ubuntu2_i386.deb)
and
[ftp://us.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1_1.0-1.1ubuntu2_i386.deb](ftp://us.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1_1.0-1.1ubuntu2_i386.deb)

do a: dpkg -x libxcb-xlib0_1.0-1.1ubuntu2_i386.deb libs
then: dpkg -x libxcb1_1.0-1.1ubuntu2_i386.deb libs

then cp -R libs/usr/lib/* /usr/lib32

voila... that should fix it :-)

Jamon Terrell

---

### Post by CubicVirtuoso on 2007-04-02
Hello,

I have a little problem on my hands; see I had wine working... beautifully actually when I was trying to get my audio drivers installed. To make a long story short I replaced all the files in /usr/lib32 with the files in /usr/lib :S Yea I'm and idiot I know and it was a really simple typo to make.

Essentially it messed EVERYTHING up. Nothing in terms of wine works now and I'm stumped at how to fix it. I went into Synaptic and reinstalled all lib32 drivers, but whenever I do the following command:

```
sudo dpkg --force-architecture -i wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb 

```

I get the following error messages:

```
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 113684 files and directories currently installed.)
Preparing to replace wine 0.9.34~winehq0~ubuntu~6.10-1 (using wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb) ...
Unpacking replacement wine ...
Setting up wine (0.9.34~winehq0~ubuntu~6.10-1) ...
ldconfig: /usr/lib32/libavahi-common.so.3 is not a symbolic link

ldconfig: /usr/lib32/libcroco-0.6.so.3 is not a symbolic link

ldconfig: /usr/lib32/libdns.so.22 is not a symbolic link

ldconfig: /usr/lib32/libaudiofile.so.0 is not a symbolic link

ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

ldconfig: /usr/lib32/libberyldecoration.so.0 is not a symbolic link

```

There are more symbolic link errors, I just didn't list them here. Is there a way I can fix this? I feel like such and idiot. Thanks so much for your help! What a great tutorial btw.

---

### Post by JamonTerrell on 2007-04-02
I believe you need to re-install all of your ia32-libs... I think the package is ia32-lib or something like that.  In order to force it to re-install.  I'm not sure if there's a pretty way of doing that, but what I typically do is manually edit the dpkg database file and change the status line to show that it's not installed... you can just grab the syntax off of a package you've removed.  You could apt-get remove it first then apt-get install it ... but then that will try to uninstall all things that depend on it, which is a pain.  If you can't find the dpkg files, let me know and I'll post exactly what to do... I just don't have a box handy to look at the exact filenames.

Jamon

---

### Post by CubicVirtuoso on 2007-04-02
> **JamonTerrell said:**
> I believe you need to re-install all of your ia32-libs... I think the package is ia32-lib or something like that.  In order to force it to re-install.  I'm not sure if there's a pretty way of doing that, but what I typically do is manually edit the dpkg database file and change the status line to show that it's not installed... you can just grab the syntax off of a package you've removed.  You could apt-get remove it first then apt-get install it ... but then that will try to uninstall all things that depend on it, which is a pain.  If you can't find the dpkg files, let me know and I'll post exactly what to do... I just don't have a box handy to look at the exact filenames.

Jamon

Thanks for the quick reply! I will try this when I get home, but ... well maybe this is too much to ask. You think you could zip up your /usr/lib32 folder? I'm not sure how big that would be in size and maybe share it over rapid share? If this is too much I understand. Seeing as I'm at work right now I can't try what you suggested but I will try that. Thanks for the help.

- Billy

---

### Post by CubicVirtuoso on 2007-04-02
Ok, I got wine installed without the symbolic link errors but now I get the following:

```
cvirtuoso@cvirtuoso-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 118798 files and directories currently installed.)
Preparing to replace wine 0.9.34~winehq0~ubuntu~6.10-1 (using wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb) ...
Setting up wine (0.9.34~winehq0~ubuntu~6.10-1) ...

cvirtuoso@cvirtuoso-desktop:~/Desktop$ wine
bash: /usr/local/bin/wine: No such file or directory
cvirtuoso@cvirtuoso-desktop:~/Desktop$ winecfg
bash: /usr/local/bin/winecfg: No such file or directory
cvirtuoso@cvirtuoso-desktop:~/Desktop$ 

```

I'm assuming I just have to point my shell to the wine executable. Before I was just able to do wine and winecfg right after installing wine. What shall i do?

---

### Post by ernstblaauw on 2007-04-05
What's the status when using Feisty 64-bit? Does the script work? And if yes, which one do I need?

---

### Post by JamonTerrell on 2007-04-05
I think you have conflicting wine executables... the dpkg command hsould have forced an install to /usr/bin/wine... do you have a competing executable in /usr/local/bin/wine?  If so, you might want to remove those...

Jamon

> **CubicVirtuoso said:**
> Ok, I got wine installed without the symbolic link errors but now I get the following:

```
cvirtuoso@cvirtuoso-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 118798 files and directories currently installed.)
Preparing to replace wine 0.9.34~winehq0~ubuntu~6.10-1 (using wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb) ...
Setting up wine (0.9.34~winehq0~ubuntu~6.10-1) ...

cvirtuoso@cvirtuoso-desktop:~/Desktop$ wine
bash: /usr/local/bin/wine: No such file or directory
cvirtuoso@cvirtuoso-desktop:~/Desktop$ winecfg
bash: /usr/local/bin/winecfg: No such file or directory
cvirtuoso@cvirtuoso-desktop:~/Desktop$ 

```

I'm assuming I just have to point my shell to the wine executable. Before I was just able to do wine and winecfg right after installing wine. What shall i do?

---

### Post by JamonTerrell on 2007-04-06
> **ernstblaauw said:**
> What's the status when using Feisty 64-bit? Does the script work? And if yes, which one do I need?

The 64bit dapper instructions work under 64bit feisty.

---

### Post by arvevans on 2007-04-11
Lots of good info here, but why not condense it down into a script program and make that into an installer for WINE.  That way the procedure would be simplified, and under computer control to possibly eliminate user error in the process.

Arv
_._

---

### Post by Kilz on 2007-04-12
> **arvevans@earthlink.net said:**
> Lots of good info here, but why not condense it down into a script program and make that into an installer for WINE.  That way the procedure would be simplified, and under computer control to possibly eliminate user error in the process.

Arv
_._

Ummmmm, you must have missed the install script on the front page.:D  

But seriously,  I should delete it. The script isnt really needed but by the few users who cant seem to let go of the Windows "everything should be so simple a monkey could do it" mentality. Sadly you can guess what Windows thinks of its users because they do that kind of thing.

---

### Post by insaniac on 2007-04-18
hey there,

the problem im having is that the repositories i have and have tried to find all give errors downloading  the ia32-libs and the sound lib files etc.. im not sure if maybe my repositories are completely wrong? could someone help me out? my sources.list files has... 

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

#AUTOMATIX REPOS END

the error im getting:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main ia32-libs 1.5ubuntu5
  Bad header line [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/ia32-libs/ia32-libs_1.5ubuntu5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/ia32-libs/ia32-libs_1.5ubuntu5_amd64.deb)  Bad header line [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

ive tried the sudo apt-get update.. same error..

help! :) hehe
thanks

---

### Post by REMcCain on 2007-04-19
> **Kilz said:**
> ... by the few users who cant seem to let go of the Windows "everything should be so simple a monkey could do it" mentality. Sadly you can guess what Windows thinks of its users because they do that kind of thing.

What a snotty and cavalier attitude.  Let me point out a few things, my friend.

When you decide to start your automobile, do you appreciate the electric start, automatic transmission and air conditioning? I'm certain you do.  People like things to be simple.
Electric can openers. Automatic drip coffee pots. Things that don't require an hour of fiddling to make them work just because you have an new sound card or God forbid, a new video game.

However, unlike yourself, there are LOTS of people in the world that want to klik on an executable, install a program and use the darn thing - not read man's, how-to's, obscure forums, and use a command line.  They want easy to use programs, easy to read instructions, an interface that doesn't change just because you switch applications, and most of all - they want all the complexity out of sight.  People want to use their computers as a tool, not as a hobby.  I know I do - and I've spent the last 20 years of my life in the computer industry!

So lose the attitude and make Linux so easy that a * retarded monkey * could use it. 
Then you'll have a winning product that will give Bill Gates sleepless nights.

---

### Post by Kilz on 2007-04-19
> **insaniac said:**
> hey there,

the problem im having is that the repositories i have and have tried to find all give errors downloading  the ia32-libs and the sound lib files etc.. im not sure if maybe my repositories are completely wrong? could someone help me out? my sources.list files has... 

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

#AUTOMATIX REPOS END

the error im getting:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main ia32-libs 1.5ubuntu5
  Bad header line [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/ia32-libs/ia32-libs_1.5ubuntu5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/ia32-libs/ia32-libs_1.5ubuntu5_amd64.deb)  Bad header line [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

ive tried the sudo apt-get update.. same error..

help! :) hehe
thanks

Try clicking on the link to it in your post, it downloaded the file for me, then click on it and let gdebi install it. As for the repositories, if thats all thats in your sources list, you will have problems. The easiest way to add the repo's is with synaptic. [Take a look here.]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")

---

### Post by Kilz on 2007-04-19
> **REMcCain said:**
> What a snotty and cavalier attitude.  Let me point out a few things, my friend.

When you decide to start your automobile, do you appreciate the electric start, automatic transmission and air conditioning? I'm certain you do.  People like things to be simple.
Electric can openers. Automatic drip coffee pots. Things that don't require an hour of fiddling to make them work just because you have an new sound card or God forbid, a new video game.

However, unlike yourself, there are LOTS of people in the world that want to klik on an executable, install a program and use the darn thing - not read man's, how-to's, obscure forums, and use a command line.  They want easy to use programs, easy to read instructions, an interface that doesn't change just because you switch applications, and most of all - they want all the complexity out of sight.  People want to use their computers as a tool, not as a hobby.  I know I do - and I've spent the last 20 years of my life in the computer industry!

So lose the attitude and make Linux so easy that a * retarded monkey * could use it. 
Then you'll have a winning product that will give Bill Gates sleepless nights.

Thanks for the rant with your very first post on the forums.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=30074&stc=1&d=1176984339[/IMG]

I think you can maybe benefit from [reading something]("http://linux.oneandoneis2.org/LNW.htm"). Sections 3, 6 and 7 may give you a litle insight into why I made that statement.

---

### Post by REMcCain on 2007-04-19
> **Kilz said:**
> Thanks for the rant with your very first post on the forums.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=30074&stc=1&d=1176984339[/IMG]

I think you can maybe benefit from [reading something]("http://linux.oneandoneis2.org/LNW.htm"). Sections 3, 6 and 7 may give you a litle insight into why I made that statement.

I'll not apologize for the rant, I've been ranting about Linux since I first started playing with Redhat in '96 or '97

I'm quite familiar with all the <del>reasons</del> excuses that have been listed over the years, and I've always countered with the fact that the vast majority of people are stupid and lazy.  If you want to build a successful product, you must cater to the lowest common denominator.

no excuses. 

Now quit whinging and build an extremely user-friendly Linux.

On a happier note, Ububtu is *very* nice and I've loaded it on my main box for everyday use by myself and the family. The wife moans about the differences more than the kids and the kids have much more reason to moan - flash isn't working in the 64 bit version.
Yes, I know there's a fix, and no,  I'm not going to use the command line.  
I'm spoiled and lazy and I have no desire to muck about with anything that won't allow me to use a graphical interface to select which options will make the software function properly.
That means I'll be using the 32 bit version until all the kinks are worked out of the 64 bit version.

So bravo Ubuntu, for making Linux easier to use.  Keep working at it and one day, 15-20 years from now, it may just become a mainstream product.

---

### Post by Kilz on 2007-04-19
> **REMcCain said:**
> I'll not apologize for the rant, I've been ranting about Linux since I first started playing with Redhat in '96 or '97

I'm quite familiar with all the <del>reasons</del> excuses that have been listed over the years, and I've always countered with the fact that the vast majority of people are stupid and lazy.  If you want to build a successful product, you must cater to the lowest common denominator.

no excuses. 

Now quit whinging and build an extremely user-friendly Linux.

On a happier note, Ububtu is *very* nice and I've loaded it on my main box for everyday use by myself and the family. The wife moans about the differences more than the kids and the kids have much more reason to moan - flash isn't working in the 64 bit version.
Yes, I know there's a fix, and no,  I'm not going to use the command line.  
I'm spoiled and lazy and I have no desire to muck about with anything that won't allow me to use a graphical interface to select which options will make the software function properly.
That means I'll be using the 32 bit version until all the kinks are worked out of the 64 bit version.

So bravo Ubuntu, for making Linux easier to use.  Keep working at it and one day, 15-20 years from now, it may just become a mainstream product.

I tried to be nice, but .... 
1. I personaly am only a linux user. Not a developer. I could give a rats rear end about building a "user friendly" Linux. I personaly dont care about the numbers of people who use anything.
2. I do this not to build a "user friendly" Linux. But to help a few people, if they cant figure out how to type in a few lines into a terminal, I wont be able to help them.
3. Linux isnt a "product" to me. You can pay money to get it, but you cant "buy" it. If you think you have. Demand a full refund!
4. [URL="http://linux.oneandoneis2.org/LNW.htm"]Reread Section 3a. In fact reread the whole thing.
[/URL]
5. If you have any other questions or complaints see #4.

---

### Post by REMcCain on 2007-04-19
I appreciate your forthright attitude.  You are a user, not a dev but you still attempt to help people with a product in which you believe.  That's commendable and I'm certain many people appreciate your efforts. 

However, just because you subscribe to the Humphries Manifestio doesn't mean that I have to agree with your interpertation of what Linux should be to all users.  I believe that dev's should strive to make Linux so 'monkey simple' that even their aged grandmothers could use it with no problems. 

Good day, and thank you.  Should I ever re-install Ubuntu-64, I'm sure I'll be grateful for your expertise. As for now, I'm off to discover more about the 32 bit version.

*PS.
I noticed you have a thing for comics.  Have you discovered Sluggy Freelance yet?

---

### Post by Kilz on 2007-04-19
> **REMcCain said:**
> 
*PS.
I noticed you have a thing for comics.  Have you discovered Sluggy Freelance yet?

No I had not, thanks for the link.  :)

---

### Post by strumluff on 2007-04-20
Kilz thanks for these howto's they're very helpful. Just one question, does the howto work in feisty final? 

Thanks!

---

### Post by Kilz on 2007-04-21
> **strumluff said:**
> Kilz thanks for these howto's they're very helpful. Just one question, does the howto work in feisty final? 

Thanks!

I tried it in the beta without problems, it should work fine in the release.

---

### Post by Medieval_Creations on 2007-04-21
I just tried the script and recieved this error:
```

--19:05:50--  http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb
           => `wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:05:50 ERROR 404: Not Found.

```

Easy enough for me to fix.  I just downloaded the newest version of the deb & worked like a charm.

---

### Post by Kilz on 2007-04-21
> **Medieval_Creations said:**
> I just tried the script and recieved this error:
```

--19:05:50--  http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb
           => `wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:05:50 ERROR 404: Not Found.

```

Easy enough for me to fix.  I just downloaded the newest version of the deb & worked like a charm.

Yes the script is quite old. There is a 64bit package available on the forums. So I have kind of let this script go a little. The howto still works , and its pretty simple to do.

---

### Post by smartbei on 2007-04-25
Question: after installing according to the howto (downoading package, installing, running sidenet script) I qish to remove wine. How do I do so? The "c" directory in home I can just delete, but what of Wine's files?

Thanks

---

### Post by FleaBR on 2007-04-25
I tried to install Wine with the Simple64 and with this how-to but failed at both, after the supposed install i try to run winecfg and get this error:

rafael@DESKTOP:~/Rafael$ winecfg
wine: /home/rafael/.wine is not a directory
rafael@DESKTOP:~/Rafael$

When i try to install i get this error: 

ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

---

### Post by FleaBR on 2007-04-25
Ok, i got that working but now it says that its installing Wine then nothing, i try to run winecfg and it says that the ./wine directory doesn't exists

---

### Post by Kilz on 2007-04-25
> **FleaBR said:**
> Ok, i got that working but now it says that its installing Wine then nothing, i try to run winecfg and it says that the ./wine directory doesn't exists

By any chance did you install the sidenet script?

> **smartbei said:**
> Question: after installing according to the howto (downoading package, installing, running sidenet script) I qish to remove wine. How do I do so? The "c" directory in home I can just delete, but what of Wine's files?

Thanks

You should be able to remove it in synaptic/apt. Its a deb file the package name is wine.

---

### Post by FleaBR on 2007-04-25
Ok, installed the sidenet script but now when i try to run winecfg i get this errors:

> err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library OLE32.dll (which is needed by L"C:\\windows\\shelllink.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64


and it goes on and on and on,  a LOT of errors...

---

### Post by Kilz on 2007-04-25
> **FleaBR said:**
> Ok, installed the sidenet script but now when i try to run winecfg i get this errors:



and it goes on and on and on,  a LOT of errors...

I have just updated the howto and install scripts. Please go to the first post, download the install script for your Ubuntu version and run it. This will ensure that everything that needs to be done, is done. You dont have to uninstall anything to run the script.

---

### Post by FleaBR on 2007-04-25
Ok, tkz :P

Just a quest, does the wine that you put on the script runs wow ?

---

### Post by arvevans on 2007-04-25
> **Kilz said:**
> Ummmmm, you must have missed the install script on the front page.:D  

But seriously,  I should delete it. The script isnt really needed but by the few users who cant seem to let go of the Windows "everything should be so simple a monkey could do it" mentality. Sadly you can guess what Windows thinks of its users because they do that kind of thing.

Your attitude is showing.  I finally found the info that I needed, no thanks to you.  Another person was obviously much more knowledgeable and much more helpful.

BTW:  I an a Linux User, not a programmer.  Without Linux Users, is there any reason for Linux, other than as a programmer's curiosity?

The "monkey" in my background objected to your racist comment!  :wink: 

Arv
_._

---

### Post by Kilz on 2007-04-25
> **arvevans@earthlink.net said:**
> Your attitude is showing.  I finally found the info that I needed, no thanks to you.  Another person was obviously much more knowledgeable and much more helpful.

BTW:  I an a Linux User, not a programmer.  Without Linux Users, is there any reason for Linux, other than as a programmer's curiosity?

The "monkey" in my background objected to your racist comment!  :wink: 

Arv
_._

My attitude? Maybe Im just getting tired of people so used to commercial software they demand simplicity. 
Just so you know, Im not a programmer or developer either. I'm just a Ubuntu user. On the 1-10 scale of complexity, this howto is about a .5 . The script isnt needed because there are only a few minor things to do. The commands can be cut and pasted into a terminal. It shouldnt take more than 10 minutes, tops.
Also the so called "racist" comment, wasnt a racist comment. But I guess robbers only see thief's.

---

### Post by Kilz on 2007-04-25
> **FleaBR said:**
> Ok, tkz :P

Just a quest, does the wine that you put on the script runs wow ?

Yes, it should since wine 0.9.32. But I do not support installing applications. I also dont play wow so I wouldnt be much help as I wouldnt know any problems.

---

### Post by FleaBR on 2007-04-25
Got WoW and Warcraft III working, just a problem here and there nothing major thankz for the script btw

---

### Post by smartbei on 2007-05-01
I am trying to remove Wine and not quite succeeding. I am using 
```

sudo dpkg --force-architecture -P wine_0.9.35~winehq0~ubuntu~6.06-1_i386

```
but it tells me: 
> dpkg - warning: ignoring request to remove wine_0.9.35~winehq0~ubuntu~6.06-1_i386 which isn't installed.
How do I remove Wine?

---

### Post by s_spiff on 2007-05-02
hey Klisz, the lazy bum in me got me to use the script for fiesty and i keep getting an error, something to do with the target/url the script points to for downloading the package. Can you please check it out, and let me know what I should do about it?
```
--18:00:09--  http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb
           => `wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:00:15 ERROR 404: Not Found.

dpkg: error processing wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb
--18:00:15--  http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb
           => `libxxf86dga1_1.0.0-0ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.


ERROR: Could not find wine installation.
       Setup wine first.
Setup aborted.

```

---

### Post by s_spiff on 2007-05-02
Can someone tell me what is it that I'm doing wrong here?
```
alok@alok-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine-dev_0.9.36~winehq0~ubuntu~7.04-1_i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 92311 files and directories currently installed.)
Preparing to replace wine-dev 0.9.36~winehq0~ubuntu~7.04-1 (using wine-dev_0.9.36~winehq0~ubuntu~7.04-1_i386.deb) ...
Unpacking replacement wine-dev ...
dpkg: dependency problems prevent configuration of wine-dev:
 wine-dev depends on wine (= 0.9.36~winehq0~ubuntu~7.04-1); however:
  Package wine is not installed.
dpkg: error processing wine-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine-dev


```

---

### Post by s_spiff on 2007-05-02
Hey, checked around quite a bit on the www, but couldn't find anyone with a howto or even a post about porting Windows Live Messenger. Anyone?

---

### Post by Kilz on 2007-05-02
> **s_spiff said:**
> hey Klisz, the lazy bum in me got me to use the script for fiesty and i keep getting an error, something to do with the target/url the script points to for downloading the package. Can you please check it out, and let me know what I should do about it?


The reason it wasnt working is because wine has been upgraded and the packages for the old version was not available. There is a new script, for the new version on the top page.

---

### Post by YokoZar on 2007-05-03
Great news!  This whole process may now be completely unnecessary as proper packages are now being built.  Thank you Kliz for the help you've been so far.

[http://ubuntuforums.org/showthread.php?t=431503](http://ubuntuforums.org/showthread.php?t=431503)

---

### Post by Kilz on 2007-05-03
> **YokoZar said:**
> Great news!  This whole process may now be completely unnecessary as proper packages are now being built.  Thank you Kliz for the help you've been so far.

[http://ubuntuforums.org/showthread.php?t=431503](http://ubuntuforums.org/showthread.php?t=431503)

Thats great, but , we still have some people like me, that like Dapper. Im sure that there are some people who like Edgy. So Ill just keep updating the script in case. It isnt all that much work.

---

### Post by s_spiff on 2007-05-06
rocking got it. Actually I've already installed it manually. Hey I wanted to know something.
 I've installed wine+ubuntu on my 80gb primary hdd. And i got a secodnary 120 gb, which has a lot of free space+ a windows installation. Now I have two questions:
1: Can I get wine to install all the new programs I'll install into a partition on the second drive instead of the first, and how do I go about it after doing it?

2. Can I use the existing windows folder on my secondary hdd to any advantage? 

3. How do i remove a previous installtion of wine?

---

### Post by diafanos on 2007-05-07
Can anyone tell me how do I enable html rendering in wine?

I use Fiestu (amd64), and when I tried to run an .exe file which opens a browser, opened it and appeared a message: "HTML rendering is currently disabled" ....

When I tried to run the same .exe with edgy, just prompt me to download and install something (i can't remember now), and run fluently.

---

### Post by Bashed on 2007-05-07
Anyone know why I am getting this error?

I'm installing a small XP/Vista compatible software called SEcureCRT (ssh program).

How do I run a Windows program via a desktop shortcut? I double click and it only
brings up wine configuration window.

---

### Post by Bashed on 2007-05-07
How do I uninstall? For some odd reason, Synaptic does not show wine checked, neither does 'add/remove' which (I'm new to linux) is part of synaptic anyway?

---

### Post by strumluff on 2007-05-10
> **s_spiff said:**
> rocking got it. Actually I've already installed it manually. Hey I wanted to know something.
 I've installed wine+ubuntu on my 80gb primary hdd. And i got a secodnary 120 gb, which has a lot of free space+ a windows installation. Now I have two questions:
1: Can I get wine to install all the new programs I'll install into a partition on the second drive instead of the first, and how do I go about it after doing it?

2. Can I use the existing windows folder on my secondary hdd to any advantage? 

3. How do i remove a previous installtion of wine?

1 -> No you can't install applications from wine into your windows drive as for starters you'll find the file systems being completely different. Remember wine simply allows you to run windows applications in linux and therefore has it's own configuration for a virtual C driver and other settings.

2 -> Well the windows folder on your second hdd can come in handy if you want to use windows fonts in ubuntu. You can simply copy the ttf fonts over from the Windows/Fonts dir and stick them in ubuntu's font directory. You can also let wine make use of them. The only other thing that may come in handy is if wine ever asks for a certain dll, you may find your windows system32 directory handy to provide the necessary files. I had this happen when I tried to install msi files.

3 -> If you're upgrading then you shouldn't need to remove a previous installation. If you want to do a clean install of wine you will have to remove it first with:
```
sudo aptitude remove wine
```
Then remove the .wine folder in your home directory.

---

### Post by almkglor on 2007-06-07
I've followed the instructions here to install Dapper, but running winecfg shows the following error:
almkglor@almkglor-laptop:~$ winecfg
wine: creating configuration directory '/home/almkglor/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
wine: wineprefixcreate failed while creating '/home/almkglor/.wine'.
almkglor@almkglor-laptop:~$ wineserver: could not save registry branch to /home/almkglor/.wine-0lD2EY/system.reg : No such file or directory
wineserver: could not save registry branch to /home/almkglor/.wine-0lD2EY/user.reg : No such file or directory

---

### Post by Kilz on 2007-06-07
> **almkglor said:**
> I've followed the instructions here to install Dapper, but running winecfg shows the following error:
almkglor@almkglor-laptop:~$ winecfg
wine: creating configuration directory '/home/almkglor/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
wine: wineprefixcreate failed while creating '/home/almkglor/.wine'.
almkglor@almkglor-laptop:~$ wineserver: could not save registry branch to /home/almkglor/.wine-0lD2EY/system.reg : No such file or directory
wineserver: could not save registry branch to /home/almkglor/.wine-0lD2EY/user.reg : No such file or directory

You need to install the proprietary video drivers for your video card. Second, did you install sidenet?

---

### Post by almkglor on 2007-06-08
> **Kilz said:**
> You need to install the proprietary video drivers for your video card. Second, did you install sidenet?

Have just installed and run sidenet but the following problem remains:
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18

As for proprietary video drivers, my video is an intel 945GM chipset.  Searching Intel's site eventually lead me to [http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html) , which helpfully recommends that I get precompiled packages from Linux distributors.

Ubuntu Dapper Drake includes xserver-xorg-driver-i810 , which claims to be the driver for my chipset.  Which isn't working in this case.  So I guess I have to fix my drivers first.

Has anyone gotten Wine to work on a 945GM?

---

### Post by Kilz on 2007-06-09
> **almkglor said:**
> Have just installed and run sidenet but the following problem remains:
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18

As for proprietary video drivers, my video is an intel 945GM chipset.  Searching Intel's site eventually lead me to [http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html) , which helpfully recommends that I get precompiled packages from Linux distributors.

Ubuntu Dapper Drake includes xserver-xorg-driver-i810 , which claims to be the driver for my chipset.  Which isn't working in this case.  So I guess I have to fix my drivers first.

Has anyone gotten Wine to work on a 945GM?

Yes, if ```
glxgears
``` dose not bring up 3 gears rotating in a little window, you dont have accelerated graphics.

---

### Post by ba_shef on 2007-06-10
Hi,

I just installed Feisty (7.04) this morning on my new AMD64-based computer, and have spent quite a while trying to make wine install, work with no luck. I have read this post extensively, I've tried most of the things here, but haven't noticed anyone with the same errors as me.

I have tried both the script on the first page of this post and the manual install, and neither leaves me with a working version (that is, in both cases when I type winecfg I don't see a menu like I should).

When I run the script, I get an error:

wine: 4: function: not found

and the terminal hangs here (or at least, stays that way for a VERY long time)

when I Ctrl-C and then run winecfg, I get loads of "Segmentation Fault (Core Dumped) errors.

and the winecfg does not work.

When I install the package using apt-get, running wine-cfg just gives me a Segmentation Fault error and dumps me back to the terminal...

Any help on this would be greatly appreciated,

B

---

### Post by jack77 on 2007-06-22
> **ba_shef said:**
> Hi,

I just installed Feisty (7.04) this morning on my new AMD64-based computer, and have spent quite a while trying to make wine install, work with no luck. I have read this post extensively, I've tried most of the things here, but haven't noticed anyone with the same errors as me.

I have tried both the script on the first page of this post and the manual install, and neither leaves me with a working version (that is, in both cases when I type winecfg I don't see a menu like I should).

When I run the script, I get an error:

wine: 4: function: not found

and the terminal hangs here (or at least, stays that way for a VERY long time)

when I Ctrl-C and then run winecfg, I get loads of "Segmentation Fault (Core Dumped) errors.

and the winecfg does not work.

When I install the package using apt-get, running wine-cfg just gives me a Segmentation Fault error and dumps me back to the terminal...

Any help on this would be greatly appreciated,

B
I'm getting segfaults too.

---

### Post by penvzila on 2007-07-01
I am as well.

---

### Post by Kilz on 2007-07-01
What version of Ubuntu are each of you running?

---

### Post by strumluff on 2007-07-06
Hey I installed wine a while ago using your script here Kilz, I believe it is version 0.9.35

How do I go about uninstalling it now so I can just use the 64bit packages from the wine repo?

Note that sidenet was also installed with it.

Cheers.

---

### Post by amano on 2007-09-26
Hmm. I am not yet sure (no 64 bit cpu) but from the changelog I could guess that wine is now officially featured in the repos? Is that true?

[https://lists.ubuntu.com/archives/gutsy-changes/2007-September/008815.html](https://lists.ubuntu.com/archives/gutsy-changes/2007-September/008815.html)

---

### Post by Kilz on 2007-09-26
> **amano said:**
> Hmm. I am not yet sure (no 64 bit cpu) but from the changelog I could guess that wine is now officially featured in the repos? Is that true?

[https://lists.ubuntu.com/archives/gutsy-changes/2007-September/008815.html](https://lists.ubuntu.com/archives/gutsy-changes/2007-September/008815.html)

With Feisty there is a 64bit .deb file at the winehq. They even have a repository you can add. But I still watch this old thread because some people still run Dapper. Heck until 3 months ago so did I.

---

### Post by amano on 2007-09-27
Hmm.

Does that mean that there is still no wine in the repos of the Gutsy Beta?

---

### Post by Kilz on 2007-09-27
> **amano said:**
> Hmm.

Does that mean that there is still no wine in the repos of the Gutsy Beta?

Since I dont run Gutsy I couldnt tell you if there is a 64bit wine package for Gutsy in the Ubuntu repos. But even if there isnt, the Winehq has a repo.. I bet they will have Gutsy debs soon, and the feisty deb would probably work in Gutsy.

---

### Post by arep3 on 2007-10-05
Hi guys. 1st time posting long time reader. 
i keep getting this in terminal while trying to install wine.

dpkg: status database area is locked by another process

i did try to install this by typing the command lines for terminal for feisty before i realiesed they were for feisty and not dapper drake. (jumped the gun a bit) The command lines are these 1s found at the top of this page[https://help.ubuntu.com/community/WineForAMD64]("https://help.ubuntu.com/community/WineForAMD64")
What can i do to insatll wine?
Thanks, Ron

---

### Post by Kilz on 2007-10-05
> **arep3 said:**
> Hi guys. 1st time posting long time reader. 
i keep getting this in terminal while trying to install wine.

dpkg: status database area is locked by another process

i did try to install this by typing the command lines for terminal for feisty before i realiesed they were for feisty and not dapper drake. (jumped the gun a bit) The command lines are these 1s found at the top of this page[https://help.ubuntu.com/community/WineForAMD64]("https://help.ubuntu.com/community/WineForAMD64")
What can i do to insatll wine?
Thanks, Ron

You may want to remove that repository. You can edit the apt list at /etc/apt/sources.list
```
gksudo gedit /etc/apt/sources.list
``` will open it in admin mode so you can edit it.

dpkg: status database area is locked by another process

Means that some other application that installs programs is open. For instance , using dpkg while having synaptic open.

---

### Post by arep3 on 2007-10-08
Hey. 
Well i tried to have another go at installing wine and this is the new error i got:

sudo dpkg --force-architecture -i wine_0.9.45~winehq0~ubuntu~6.06-1_i386.deb
dpkg: error processing wine_0.9.45~winehq0~ubuntu~6.06-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.45~winehq0~ubuntu~6.06-1_i386.deb

What have i done?
Thanks in advance, Ron

---

### Post by arep3 on 2007-10-12
Anybody? Ive checked to see if the files downloaded correctly. I have made sure i change the typing in terminal to mirror the file name and i have the location right.

---

### Post by Kilz on 2007-10-12
> **arep3 said:**
> Anybody? Ive checked to see if the files downloaded correctly. I have made sure i change the typing in terminal to mirror the file name and i have the location right.

Please open a new terminal and attempt to install the file. If you have problems please copy everything from the opening of the terminal to the error and paste it here.

---

