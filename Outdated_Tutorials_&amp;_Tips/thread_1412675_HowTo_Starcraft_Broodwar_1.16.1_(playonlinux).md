---
title: "HowTo: Starcraft Broodwar 1.16.1 (playonlinux)"
date: 2010-02-21
forum: Outdated Tutorials &amp; Tips
---

### Post by lilstenly on 2010-02-21
Okey lets say that I ran sc bw 1.16.1 at full speed.

TESTED WITH:
Ubuntu 9.04 
Linux ubuntu 2.6.28-18-generic
Operating System: Linux-x86
NVIDIA Driver Version: 195.36.03
Server Version Number: 11.0
Server Vendor Version: 1.6.0 (10600000)
NV-CONTROL Version: 1.22
Playonlinux 3.7.3

**1st what you need?**
- Playonlinux
- Starcraft and broodwar cd or digital distribution installer or preinstalled game
- Installed gpu drivers with working acceleration and opengl
- internet connection
**2nd what you need to do**
- Install playonlinux 3.7.3 - [http://www.playonlinux.com/en/download.html#ubuntu](http://www.playonlinux.com/en/download.html#ubuntu) (follow the instructions)
- run playonlinux and go to >tools >manage wine versions... then install 1.1.38
- download "advance wine configurations" package - [http://www.playonlinux.com/en/download.html#plugins](http://www.playonlinux.com/en/download.html#plugins)
- from the playonlinux menu click plugins > plugins manager > add > then add that plugin > restart playonlinux
**3rd the different ways to install the game**

[I][B]NOTE: TO SAY THAT WE GONNA INSTALL THE GAME IN
#C:\Program Files\Blizzard Entertainment\StarCraftBroodWar[/B][/I]

**- CD (not actually tested)**
-+ mount or insert the starcraft cd
-+ run playonlinux
-+ go to install > then to "install a .pol package or unsupported application"
-+ manual installation
-+ install a program in a new prefix
-+ name of the prefix (DO NOT USE SPACE BETWEEN THE WORDS)
-+ check "assing wine version to a programm" and "configure wine"
-+ from the drop down menu which version to use, choose "wine 1.1.38"
-+ configure wine > graphics > check "emulate virtual desktop" > write "800" x "600" > click "ok"
-+ follow the instructions
-+ point the installer of your cd
-+ install the game
-+ make a shortcut to your exe
-+ done

**- Digital Distribution install (untested)**
-+ Run play on linux
-+ click install
-+ choose "Games" section
-+ find the digital distribution script and install the game
-+ done

**- Preinstalled game (tested and works)**
-+ you need the actual game and windows registry
-+ run playonlinux
-+ go to install > then to "install a .pol package or unsupported application"
-+ manual installation
-+ install a program in a new prefix
-+ name of the prefix (DO NOT USE SPACE BETWEEN THE WORDS)
-+ check "assing wine version to a programm" and "configure wine"
-+ from the drop down menu which version to use, choose "wine 1.1.38"
-+ configure wine > graphics > check "emulate virtual desktop" > write "800" x "600" > click "ok"
-+ follow the instructions
-+ when playonlinux ask about installer you hit alt+tab and...
-+ copy your preinstalled sc bw 1.16.1 folder to the prefix folder
EXAMPLE: "home/USER/.PlayOnLinux/wineprefix/THE_NAME_YOU_ENTER_LIKE_A_PREFIX/drive_c/Program Files/Blizzard Entertainment/StarCraftBroodWar" (you just need to copy the game into "program files)
-+ then hit back alt+tab to your playonlinux and for installer choose bnupdate.exe (just null installation)
-+ then you will get installation message that you need to un bnet to check for patches and nothing will happens
-+ click that you already finish your installation
-+ add the shortcut to your starcraft.exe
-+ done

**4th Configuring the game**
- highlight the game at your playonlinux menu
- click "configure this application"
- choose forward and then "use advance configuration wine plugin", click forward
- select your starcraft from the window
- choose to be modified option... select all and click forward
- choose directdraw renderer mode > opengl (default is gdi)
- activate glsl support > enable (by default is enabled)
- how much is your graphic card memory in MBs > mine is 256
- choose offscreen rendering > backbuffer (by default is on backbuffer)
- choose render target lock mode > auto (by default is auto)
- choose multisampling support > disabled (by default is disabled)
- active mouse warp override > enabled (by default is enabled)
- everything is done... click forward and then close

**_This is only for the preinstalled game way _**
-+ configuring the registry
-+ click with the right mouse button on the game
-+ choose registry editor
-+ and follow the example
-+ you may save the code as a starcraft.reg file and just to change evry line that is [COLOR=Red]RED[/COLOR] highlighted with your game directory
> REGEDIT4 
 
[HKEY_LOCAL_MACHINE\Software\Blizzard Entertainment\Starcraft] 
"Brood War"="y" 
"InstallPath"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]" 
"Program"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]\\Starcraft.exe" 
"Retail"="y" 
"StarCD"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]" 
"StarEdit"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]" 
 
[HKEY_LOCAL_MACHINE\Software\Blizzard Entertainment\Starcraft\DelOpt0] 
"File0"="spc" 
"File1"="mpc" 
"Path0"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]\\characters" 
"Path1"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]\\characters" 
 
[HKEY_LOCAL_MACHINE\Software\Blizzard Entertainment\Starcraft\DelOpt1] 
"File0"="sng" 
"File1"="mlt" 
"File2"="snx" 
"File3"="mlx" 
"Path0"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]\\save" 
"Path1"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]\\maps\\save" 
"Path2"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]\\save" 
"Path3"="[COLOR=Red]C:\\Program Files\\Blizzard Entertainment\\StarCraftBroodWar[/COLOR]\\maps\\save" -+ just open the registry editor and click file > inport registry > find your starcraft.reg you just created and add it

5th DONE
- you may run the game
[B]
Note:[/B] Preinstalled way is tested and works
**Note:** Game may work better with wine 1.0.1
**Note:** If you run the game in fullscreen will work perfectly but may crash when you exiting and to change your resolution
**Note:** I recomend you to use a virtual cd drive to play the game if you don't have any loader
**Note:** If you installing the game from the cd then copy install.exe from the cd to you game directory
**Note:** With that version of wine (1.1.38) battle.net seems to get into a bug
**Note:** Nice playing there.
And here is one cool icon for your game!
[IMG]http://i45.tinypic.com/34i5wuw.png[/IMG]
[B]P.S. Tell me if I missing something or something doesn't work, I'll try to help out as much as I can!
[/B]
I'll make one installer exe for preinstalled version so everything will be easier and you will just have to point your preinstalled game directory to copy everything in the installation dir... since then you will have to use this ways.
:)
Luck!

---

### Post by AI52487963 on 2010-05-26
Toshiba Portege R100
Ubuntu 9.10
Dunno what headers I have, latest probably (recently updated)

PlayOnLinux version 3.7.6
Wine 1.1.38

So I followed the instructions for the digital distrubion copy, seeing as how my laptop here doens't have a CD drive attached to it. Everything goes smoothly until I try and install the game from within the blizzard launcher. I navigate to c: and then to program files and then try to install but I keep getting an error saying it's an invalid directory to place it in.

Literally it says, "Invalid path chosen! Please choose again." I'm trying to install to C:/program files/  Should I install to C:/program files/StarCraft instead? I don't have that folder in there if I should...


Also, the therminal spits out a huge amount of stuff. I don't know what to make of it, but I'll assume it's bad:

```

scott@scott-laptop:~$ playonlinux
PlayOnLinux v3.7.6

Checking python :                 [ Ok ]
Running install menu
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT

http error code = 404
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:shdocvw:PersistStorage_InitNew (0x137140)->(0x510f38)
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
fixme:iphlpapi:NotifyAddrChange (Handle 0x7e80e9b8, overlapped 0x7e80e99c): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x138ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1371dc)->((null) 1 0x323d00 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1371dc)->((null) 25 2 0x323d14 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1371dc)->((null) 26 2 0x323d14 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1371dc)->(0x323d58)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1371dc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x323e14 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x135ea0)->(L"" L"" 0 0x323e4c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1371dc)->((null) 29 2 0x32f02c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1371dc)
fixme:shdocvw:ClientSite_GetContainer (0x1371dc)->(0x32ecc0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1371dc)->(0x60021b71)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1371dc)->((null) 25 2 0x32ebcc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1371dc)->((null) 26 2 0x32ebcc (nil))
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x3299dc, uiNumDevices=2, cbSize=12) stub!
fixme:shdocvw:ClOleCommandTarget_Exec (0x1371dc)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1371dc)->((null) 28 2 0x32ee3c (nil))
fixme:shell:BrsFolder_OnCreate flags BIF_NEWDIALOGSTYLE partially implemented
fixme:bidi:mirror stub: mirroring of characters not yet implemented



```Any ideas?

---

