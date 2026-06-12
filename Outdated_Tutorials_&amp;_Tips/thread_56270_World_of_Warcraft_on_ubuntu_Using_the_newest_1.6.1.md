---
title: "World of Warcraft on ubuntu: Using the newest 1.6.1 patch"
date: 2005-08-11
forum: Outdated Tutorials &amp; Tips
---

### Post by crxgames on 2005-08-11
In my plan to leave windows, I've been planning to get my games going on ubuntu, well this has been a success. Here is how we do it.

First off, go here and follow the instructions to install cvscedega: [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

Once that is done compiling, download [http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42) and place it in your /home/username/.cvscedega/c_drive_windows/system folder

Once that is done create a symlink to your truetype fonts:
```

sudo ln -s /usr/share/fonts/truetype/ /usr/X11R6/lib/X11/fonts/truetype

```
Now since WoW patches after 1.3.0 break openGL WoW in cedega(and directX never worked) we need to get the newest openGL32 lib for cedega.
Download: [http://downloads.transgaming.com/misc_downloads/cedega_4.3/libopengl32.so](http://downloads.transgaming.com/misc_downloads/cedega_4.3/libopengl32.so)
Run the following command and then copy libopengl32.so to /usr/lib/cvscedega/lib
```

sudo chown INSERTYOURUSERNAMEHERE /usr/lib/cvscedega/lib

```
Then just open up nautilus and copy the file to that location.

Stick in your WoW cd's, wait until they are auto-mounted, change to the directory(/media/cdrom0 in my case) and run the following command:
```

cvscedega  Installer.exe

```
Choose your program files directory and click install.
On the install don't select a desktop icon. After switching all the cd's during the install, you should now be able to go to your program files folder and run WoW.
```

cd ~/.cvscedega/c_drive/Program\ Files/World\ of\ Warcraft

```
Now in order to get the game to run, you need to tell it to use openGL, so open up WTF/Config.wtf in your favorite text editor(after changing to the directory as in the above codebox) We'll use gedit in this tutorial.
```

gedit WTF/Config.wtf

```

Now at the very top of that file add
```

SET gxApi "opengl"

```
Now save your changes and run the following command to start WoW:
```

cvscedega WoW.exe

```

The auto updator should startup after you login with your account and start downloading and installing the update.

Enjoy.  :) 

**NOTE:** I've read on the internet that you are not suppose to use the internet updater as it doesn't work. It worked for me, but if it doesn't for you, head over ot [www.fileplanet.com](www.fileplanet.com) and download the patches then just do:
```

cvscedega patchname.exe

```
and they will start to install.

EDIT:
References and helpful links:
[http://digital-conquest.ath.cx/wiki/index.php/World_of_Warcraft](http://digital-conquest.ath.cx/wiki/index.php/World_of_Warcraft)
[http://undeadpenguin.org/phpbb/viewtopic.php?t=40](http://undeadpenguin.org/phpbb/viewtopic.php?t=40)
[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

---

### Post by i3dmaster on 2005-08-12
[QUOTE=crxgames]In my plan to leave windows, I've been planning to get my games going on ubuntu, well this has been a success. Here is how we do it.

First off, go here and follow the instructions to install cvscedega: [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

Once that is done compiling, download [http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42) and place it in your /home/username/.cvscedega/c_drive_windows/system folder

Once that is done create a symlink to your truetype fonts:
```

sudo ln -s /usr/share/fonts/truetype/ /usr/X11R6/lib/X11/fonts/truetype

```
Now since WoW patches after 1.3.0 break openGL WoW in cedega(and directX never worked) we need to get the newest openGL32 lib for cedega.
Download: [http://downloads.transgaming.com/misc_downloads/cedega_4.3/libopengl32.so](http://downloads.transgaming.com/misc_downloads/cedega_4.3/libopengl32.so)
Run the following command and then copy libopengl32.so to /usr/lib/cvscedega/lib
```

sudo chown INSERTYOURUSERNAMEHERE /usr/lib/cvscedega/lib

```
Then just open up nautilus and copy the file to that location.

Stick in your WoW cd's, wait until they are auto-mounted, change to the directory(/media/cdrom0 in my case) and run the following command:
```

cvscedega  Installer.exe

```
Choose your program files directory and click install.
On the install don't select a desktop icon. After switching all the cd's during the install, you should now be able to go to your program files folder and run WoW.
```

cd ~/.cvscedega/c_drive/Program\ Files/World\ of\ Warcraft

```
Now in order to get the game to run, you need to tell it to use openGL, so open up WTF/Config.wtf in your favorite text editor(after changing to the directory as in the above codebox) We'll use gedit in this tutorial.
```

gedit WTF/Config.wtf

```

Now at the very top of that file add
```

SET gxApi "opengl"

```
Now save your changes and run the following command to start WoW:
```

cvscedega WoW.exe

```

The auto updator should startup after you login with your account and start downloading and installing the update.

Enjoy.  :) 

**NOTE:** I've read on the internet that you are not suppose to use the internet updater as it doesn't work. It worked for me, but if it doesn't for you, head over ot [www.fileplanet.com](www.fileplanet.com) and download the patches then just do:
```

cvscedega patchname.exe

```
and they will start to install.

EDIT:
References and helpful links:
[http://digital-conquest.ath.cx/wiki/index.php/World_of_Warcraft](http://digital-conquest.ath.cx/wiki/index.php/World_of_Warcraft)
[http://undeadpenguin.org/phpbb/viewtopic.php?t=40](http://undeadpenguin.org/phpbb/viewtopic.php?t=40)
[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)[/QUOTE]
 wow... Nice. Does this game need a fancy card to play... after reading your thread, I really want to try it out..

---

### Post by seethru on 2005-08-12
Great howto, thought it was gonna get WoW running in nix for me finally, but :/

err:module:PE_fixup_imports Module (file) OPENGL32.dll (which is needed by C:\Games\World of Warcraft\WoW.exe) not found

This error occurs even if you choose not to use OpenGL, which to me makes no sense.

almost to the point where I'm just gonna break down and buy cedega. Regular wine I can get it to do everything but target with the mouse, and I get no sound, cvscedega doesn't work period.

---

### Post by crxgames on 2005-08-14
[QUOTE=seethru]Great howto, thought it was gonna get WoW running in nix for me finally, but :/

err:module:PE_fixup_imports Module (file) OPENGL32.dll (which is needed by C:\Games\World of Warcraft\WoW.exe) not found

This error occurs even if you choose not to use OpenGL, which to me makes no sense.

almost to the point where I'm just gonna break down and buy cedega. Regular wine I can get it to do everything but target with the mouse, and I get no sound, cvscedega doesn't work period.[/QUOTE]
 You have to use openGL mode in cedega, or it doesn't display properly. :(
But it ran faster for me using cvscedega than it did running natively on windows 0.o

---

### Post by seethru on 2005-08-15
[QUOTE=crxgames]You have to use openGL mode in cedega, or it doesn't display properly. :(
But it ran faster for me using cvscedega than it did running natively on windows 0.o[/QUOTE]

I get that error whether I have the SET gxApi "opengl" in Config.wtf or not :/

---

### Post by crxgames on 2005-08-17
[QUOTE=seethru]I get that error whether I have the SET gxApi "opengl" in Config.wtf or not :/[/QUOTE]
 You forgot to download [http://downloads.transgaming.com/misc_downloads/cedega_4.3/libopengl32.so](http://downloads.transgaming.com/misc_downloads/cedega_4.3/libopengl32.so) it seems like, and install it in the correct directory. As after doing that it runs fine here.

---

### Post by Perfect Storm on 2005-08-17
Great howto, two thumbs up  \\:D/  \\:D/

---

### Post by seethru on 2005-08-17
[QUOTE=crxgames]You forgot to download [http://downloads.transgaming.com/misc_downloads/cedega_4.3/libopengl32.so](http://downloads.transgaming.com/misc_downloads/cedega_4.3/libopengl32.so) it seems like, and install it in the correct directory. As after doing that it runs fine here.[/QUOTE]

did that, however I didn't install off the cd's. I copied my windows install over to my linux partition. That wouldn't have anything to do with it, would it?

edit: reinstalled it using cvscedega, patched up to 1.6.1 using the .exe patches, and still getting the opengl32 error. Could you paste your cedega config?

---

### Post by crxgames on 2005-08-19
[QUOTE=seethru]did that, however I didn't install off the cd's. I copied my windows install over to my linux partition. That wouldn't have anything to do with it, would it?

edit: reinstalled it using cvscedega, patched up to 1.6.1 using the .exe patches, and still getting the opengl32 error. Could you paste your cedega config?[/QUOTE]
 I don't have it as I accidentally screwed my partition up. Can you paste your Config.wtf?

---

### Post by EnderTheThird on 2005-08-21
I followed the instructions given here and via the links, but I still wind up with this error:
```
phil@ubuntu:/media/cdrom0$ sudo cvscedega Installer.exe
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
wine: Unhandled exception, starting debugger...
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.
phil@ubuntu:/media/cdrom0$
```

Any thoughts on how to fix this?  I used synaptic to get everything for wine except wine-dev because it wouldn't let me get that for some reason.  But that said it was for developers, a group to which I do not belong.  I could definitely use some help here though.  Thanks.

---

### Post by TheOneGuy on 2005-08-22
I'm having the exact same problem as EnderTheThird. To the 'T'. I thought I'd finally have the ability to play WoW on Ubuntu, but then this happened. Sigh.

Any help would be appreciated.

---

### Post by supercado on 2005-08-23
[QUOTE=TheOneGuy]I'm having the exact same problem as EnderTheThird. To the 'T'. I thought I'd finally have the ability to play WoW on Ubuntu, but then this happened. Sigh.

Any help would be appreciated.[/QUOTE]
 I've went through the steps here, no errors. When I run WoW however i have really screwed up graphics. Any ideas?

---

### Post by factotum218 on 2005-08-24
Ran into a problem part way through at the step where I copy the file libopengl32.so to /usr/lib/cvscedega/lib. 

No such file or directory.

Any ideas what to do next? Should I just sudo and create these dirs? Or maybe a bad cedega install??  Anyone?

---

### Post by Unix_Wizard on 2005-08-25
Lets say I can't access the internet from ubuntu and I have to boot into windows. Can I still get cedega without paying? Thanks in advance.

---

### Post by sneax on 2005-08-25
Yes, when you fix your internet  :grin: Seriously, I think you can go into the CVS directory (when ur booted in windows) download all the files into a map, transfer that map to linux any way you like and then go at it (just compile). Download the latest opengl in windows then move it to linux.

If the problem is moving files from windows to linux this is what you can do:
- If you have a FAT32 partition (NOT NTFS) then you can mount it into linux and just grab the file as if it was a normal parititon (ubuntu probably mounts those automaticaly).
- You can put them on a usb stick, leave the usb stick in and just rebout to linux.
- Burn on cd (bad way of doing it).

Now, if the problem realy is that you can't connect to the internet with linux I think you should fix that before bothering to use any games ...

---

### Post by dickohead on 2005-08-27
Hey guys,

Thanks for this tutorial it was great! Just one problem.... When trying to load WoW.exe - i get this error:

"World of Warcraft was unable to start 3D acceleration"

Now had i not installed fglrx yesterday it would make sense, so i tried using "glxinfo | grep direct" to see if direct rendering was enabled, and it is, i also tested glxgears and tuxracer - all working fine, so i wen nito the WTF folder and edited the file, removing the line about gxApi and it started - but the video was all whacky..... every few seconds areadible word or menu item would come up but be replaced with jibberish.

Did anyone else have this problem? If so - how was it solved?

Dickohead.

---

### Post by crxgames on 2005-08-27
first off for a post on the first page, I've never heard of WoW running in wine, You have to follow the link to get cvscedega and compile it.

About  the Unable to...blah errors, can you guys past your wtf Config.wtf?

---

### Post by EnderTheThird on 2005-08-29
I'm getting the "World of Warcraft was unable to start up 3D acceleration" error now.  I'll also note that I copied a Windows WoW installation over to my Linux HDD because for some reason it wouldn't let me change CDs while installing (CD-ROM wouldn't eject).  Anyway, here's my config.wtf:
```
SET gxApi "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "48"
SET farclip "777"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET gxMultisampleQuality "0.000000"
SET readEULA "1"
SET gxTripleBuffer "1"
SET shadowLevel "0"
SET alphaLevel "0"
SET anisotropic "16"
SET M2UsePixelShaders "1"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET realmName "Shattered Hand"
SET profanityFilter "0"
SET MusicVolume "0.5"
SET SoundVolume "0.80000001192093"
SET MasterVolume "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceLast "11.909568"
SET cameraPitchLast "20.300029"
SET cameraDistanceMaxFactor "1"
SET AmbienceVolume "0.69999998807907"
SET statusBarText "1"
SET uiScale "1"
SET accountName "EnderTheThird"
SET mouseInvertPitch "1"

```

I have an ATI Radeon 9800 AIW with the most recent drivers installed.

---

### Post by mega on 2005-08-29
when I launch warcraft, I have to use "wine WoW.exe -opengl"

it didnt work right without the "-opengl"


what type of framerates are everyone getting in cities or on raids?

---

### Post by crxgames on 2005-08-30
[QUOTE=EnderTheThird]I'm getting the "World of Warcraft was unable to start up 3D acceleration" error now.  I'll also note that I copied a Windows WoW installation over to my Linux HDD because for some reason it wouldn't let me change CDs while installing (CD-ROM wouldn't eject).  Anyway, here's my config.wtf:
```
SET gxApi "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "48"
SET farclip "777"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET gxMultisampleQuality "0.000000"
SET readEULA "1"
SET gxTripleBuffer "1"
SET shadowLevel "0"
SET alphaLevel "0"
SET anisotropic "16"
SET M2UsePixelShaders "1"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET realmName "Shattered Hand"
SET profanityFilter "0"
SET MusicVolume "0.5"
SET SoundVolume "0.80000001192093"
SET MasterVolume "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceLast "11.909568"
SET cameraPitchLast "20.300029"
SET cameraDistanceMaxFactor "1"
SET AmbienceVolume "0.69999998807907"
SET statusBarText "1"
SET uiScale "1"
SET accountName "EnderTheThird"
SET mouseInvertPitch "1"

```

I have an ATI Radeon 9800 AIW with the most recent drivers installed.[/QUOTE]
 You have to unmount your cd then eject.

I was averaging 35-40FPS. Which was about 10-15fps higher than running it natively on windows.

---

### Post by TheOneGuy on 2005-08-31
> About the Unable to...blah errors, can you guys past your wtf Config.wtf?
Excuse my ignorance, yesno? I'm obviously new to Ubuntu (and Linux in general). Where is this file located? I ran a search for it, but couldn't find it.

Also, I'm not using wine, like the other guy was (the guy who had the same error as me). I'm definitely using cvscedega.

---

### Post by TheOneGuy on 2005-08-31
Oops...

---

### Post by EnderTheThird on 2005-08-31
Does it matter which cvscedega version I choose when I'm installing it?  I cleared everything off of there last night so I'm going to give it another try when I get home after work tonight.

---

### Post by mega on 2005-08-31
isnt cedega/cvscedega just repackaged wine?  Same thing I think, just a fork from wine

---

### Post by EnderTheThird on 2005-09-01
*Sigh*

I tried when I got home, but now it's not even creating the .cvscedega directory.  It doesn't give me any errors when I install it (no matter which version I choose) though.  I've tried the installation while using both the 386 and the 686 kernels.  Is there another way to get this thing running with cedega?

Or do any of you know of a good HOWTO for getting it running with wine if cedega isn't going to be working for me?

---

### Post by puncroqr on 2005-09-05
i am too getting the wow was unable to start 3d...
has there been any solution to this?
have a clean cedega install 4.4.1, have set the opengl flag in config.wtf, but no wow for me
it works in d3d though, but at very bad framerates...

---

### Post by seethru on 2005-09-05
[QUOTE=puncroqr]i am too getting the wow was unable to start 3d...
has there been any solution to this?
have a clean cedega install 4.4.1, have set the opengl flag in config.wtf, but no wow for me
it works in d3d though, but at very bad framerates...[/QUOTE]
 for everyone getting the wine was unable to start 3d, try removing the opengl line in the Config.WTF and just running it w/ the -opengl command line.

---

### Post by TheOneGuy on 2005-09-05
I see people don't take kindly to ignorace around here. Well I'll ask again anyway. Where is Config.wtf located? I can't paste it if I don't know what it is.

I'm still getting this error:
```
me@Ubuntu:/media/cdrom0$ cvscedega Installer.exe
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
wine: Unhandled exception, starting debugger...
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.
me@Ubuntu:/media/cdrom0$
```

---

### Post by IeU on 2005-09-06
did some find a solution ?

with wow installed, patched to the latest version . . . 

with . . .
```

tuche@tuche:/home$ glxinfo | grep direct
direct rendering: Yes
tuche@tuche:/home$ glxgears
31325 frames in 5.0 seconds = 6265.000 FPS
35724 frames in 5.0 seconds = 7144.800 FPS
35713 frames in 5.0 seconds = 7142.600 FPS
35723 frames in 5.0 seconds = 7144.600 FPS

```

and . . . without the opengl in the WTF file . . .
```

cvscedega WoW.exe --cmdline -opengl

```

i still get the 3d accelaration start error . . . :(
geforce 6600gt


error print . . . oh . . im a linux newbie :)

```

root@tuche:/home/tuche/.cvscedega/c_drive/Program Files/World of Warcraft # cvscedega WoW.exe
err:win32:PE_fixup_imports No implementation for GLU32.dll.48(gluTessNormal) imported from G:\home\tuche\.cvscedega\c_drive\Program Files\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.49(gluTessProperty) imported from G:\home\tuche\.cvscedega\c_drive\Program Files\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.44(gluTessBeginPolygon) imported from G:\home\tuche\.cvscedega\c_drive\Program Files\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.43(gluTessBeginContour) imported from G:\home\tuche\.cvscedega\c_drive\Program Files\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.47(gluTessEndPolygon) imported from G:\home\tuche\.cvscedega\c_drive\Program Files\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.46(gluTessEndContour) imported from G:\home\tuche\.cvscedega\c_drive\Program Files\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
Warning: Language 'en_DE' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
fixme:keyboard:X11DRV_KEYBOARD_DetectLayout Your keyboard layout was not found!
Using closest match instead (German keyboard layout without dead keys) for scancode mapping.
Please define your layout in windows/x11drv/keyboard.c and submit them
to us for inclusion into future Wine releases.
See the Wine User Guide, chapter "Keyboard" for more information.
fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win32:PE_CreateModule Security directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:msvcrt:_fstat :dwFileAttributes = 32, mode set to 0
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a12074,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a11e6c,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a12430,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a12430,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a11b9c,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a1239c,0x00000000), stub!
fixme:system:SystemParametersInfoA Unknown action: 113
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7a12388,0x00000000), stub!
fixme:x11drv:X11DRV_DD_GetCurrentMode :stub
fixme:x11drv:X11DRV_DD_SetCurrentMode :stub
err:opengl:X11DRV_DescribePixelFormat No OpenGL support compiled in.
err:opengl:X11DRV_ChoosePixelFormat No OpenGL support compiled in.
fixme:x11drv:X11DRV_DD_SetCurrentMode :stub
root@tuche:/home/tuche/.cvscedega/c_drive/Program Files/World of Warcraft #

```

what to do ?


thanks.

---

### Post by seethru on 2005-09-06
[QUOTE=TheOneGuy]I see people don't take kindly to ignorace around here. Well I'll ask again anyway. Where is Config.wtf located? I can't paste it if I don't know what it is.

I'm still getting this error:
```
me@Ubuntu:/media/cdrom0$ cvscedega Installer.exe
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
wine: Unhandled exception, starting debugger...
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.
me@Ubuntu:/media/cdrom0$
```[/QUOTE]

Config.WTF is located in World of Warcraft/WTF once it's installed.

---

### Post by IeU on 2005-09-06
[QUOTE=seethru]Config.WTF is located in World of Warcraft/WTF once it's installed.[/QUOTE]
 actually the Config.WTF doesnt exist before the first start . . .

so you just have to create it.


well, i am still stuck at the "start 3d" problem :(

also installed the latest nvidia linux driver . . .

---

### Post by TheOneGuy on 2005-09-06
Oh, well, in that case, no wonder I can't find it. I can't even install WoW in the first place. That error in my last post is what happens when I try to install it. So...any ideas, then?

(Also, the reason I was asking where the file was located is because people were telling me to post it.)

---

### Post by IeU on 2005-09-08
[QUOTE=TheOneGuy]Oh, well, in that case, no wonder I can't find it. I can't even install WoW in the first place. That error in my last post is what happens when I try to install it. So...any ideas, then?

(Also, the reason I was asking where the file was located is because people were telling me to post it.)[/QUOTE]

try copying every cd to the hd . . .

```

tuche@ubuntu:~/WoW/CD1$ ls
Autorun.inf  Installer.exe  Installer Tome 2.mpq  Installer Tome 4.mpq
DirectX      Installer.ico  Installer Tome 3.mpq  Installer Tome.mpq
tuche@ubuntu:~/WoW/CD1$

```

you need to have every "Installer Tome X.mpq" at the same directoy . . .
then just run . . .

cvscedega Installer.exe

at first i could install the game, patch to the latest patch ( downloaded from filefront ), but then couldnt run the game, got that 3d acceleration problem . . .

then i uninstalled everything . . . but then i found a "maybe" a solution to this problem, by running in "window" mode, you might avoid the 3d acceleration problem . . .

so im reinstalling everything again, but now having anothers problems . . .

---

### Post by TheOneGuy on 2005-09-09
[QUOTE=IeU]try copying every cd to the hd . . .

```

tuche@ubuntu:~/WoW/CD1$ ls
Autorun.inf  Installer.exe  Installer Tome 2.mpq  Installer Tome 4.mpq
DirectX      Installer.ico  Installer Tome 3.mpq  Installer Tome.mpq
tuche@ubuntu:~/WoW/CD1$

```

you need to have every "Installer Tome X.mpq" at the same directoy . . .
then just run . . .

cvscedega Installer.exe[/QUOTE]
 Still no luck. Still the exact same error. I'll post it again so you don't have to go back a page if you haven't already seen it (anyone who feels like helping).

```
me@ubuntu:~/Desktop/CD1$ cvscedega Installer.exe
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
wine: Unhandled exception, starting debugger...
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.

```

---

### Post by Oni-Dracula on 2005-09-11
disregaurd this post!

---

### Post by Giturar on 2005-09-12
[QUOTE=TheOneGuy]Still no luck. Still the exact same error. I'll post it again so you don't have to go back a page if you haven't already seen it (anyone who feels like helping).

```
me@ubuntu:~/Desktop/CD1$ cvscedega Installer.exe
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
wine: Unhandled exception, starting debugger...
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.

```[/QUOTE]

similar problem as above. ideas?

```

pete@Vision:/media/cdrom$ cvscedega Installer.exe
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
Fontconfig error: "local.conf", line 17: not well-formed (invalid token)
wine: Unhandled exception, starting debugger...
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.
pete@Vision:/media/cdrom$

```

---

### Post by draugen on 2005-09-12
i'm experiencing an odd problem playing WoW using cedega 4.4.1. 

 - I installed the cedega debs as per the guide on the Unoficcial transgaming Wiki (--force-arch - i'm on ubuntu64)

 - then installed the ia32 library packages (used a server install - like my installs lean-and-mean)

 - compiled latest kernel and installed the latest Nvidia drivers (7667)

when i run

cedega WoW.exe -opengl

the game starts up nicely, I can log in etc. everything is running smoothly infact -until i log in. then, the game just hangs.

the odd thing is, this worked perfectly before i reinstalled ubuntu after borking my rig. i could even _use_ d3d mode then. this was notably on the stock kernel with the nvidia-glx package, but i cannot se the problem there. now, even the login screen is _incredibly_ slow in d3d.

i do not have the mesa glx libraries installed though. could this be it? glxgears is giving me ~6500fps, so glx works.

as to the game hanging, this is noted [here](http://http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#known_Issues), but only in wine.

I am severely confused! are there any recent updates that break wine(x)? i had this working last week... why not now?

installing the opengl fix noted in the first post did not help either, btw.

--martin

EDIT: looked in the wrong place in synaptic - i DO have the xlibsmesathingy. will try with the ubuntu stock kernel and nvidia-glx pakage and see if that helps.

EDIT 2:
stock kernel made X grumble, so that was no go. turns out the nvidia driver installer couldnt install the 32bit libs. got that fixed by manally copying the relevant files from the nvidia-installer's folders in /tmp into /usr/lib32, and manually creating the symlinks (using /usr/lib as my reference). game now works :)

---

