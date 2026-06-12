---
title: "HOWTO: Install WINE and Diabo II LOD"
date: 2005-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by KrazyPenguin on 2005-06-29
The old guide has been removed.

The NEW guide is found here:
[http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine](http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine)

including an Ubuntu Dapper Guide.

Good luck!!!

---

### Post by Nasso on 2005-07-10
sweet :) Can anyone confirm that this works? I had a friend that used wine to emulate diablo 2 but he has troubles with random crashes, no problem with that here?

Aint cedega better to use then wine? what is the difference?

---

### Post by KrazyPenguin on 2005-07-10
[QUOTE=Nasso]sweet :) Can anyone confirm that this works? I had a friend that used wine to emulate diablo 2 but he has troubles with random crashes, no problem with that here?

Aint cedega better to use then wine? what is the difference?[/QUOTE]

Yes, I confirm that this works.  I used it with Mepis and I have updated the guide to work with Ubuntu.

No random crashes.  I just started playing again and my Sorc is level 50, and I haven't crashed once ;-)

Cedega might be better, but WINE is FREE  :) 

And at the end of the guide I ask a question about disabling the alt-key + left click mouse button in Gnome.
Well.....  I figured it out on my own and here is the answer incase anybody wants to know:
[B]To pick up items while holding down the <alt> key, the alt key must be disabled.
Open System -> Preferences -> Windows -> Where it says “Movement Key” switch it form “Alt” to “Super”[/B]

If you want to find out if this works then just try it.  It will probably take about 30 minutes to install and configure.

---

### Post by Nasso on 2005-07-11
> **KrazyPenguin]Yes, I confirm that this works.  I used it with Mepis and I have updated the guide to work with Ubuntu.

No random crashes.  I just started playing again and my Sorc is level 50, and I haven't crashed once  said:**
> To pick up items while holding down the <alt> key, the alt key must be disabled.
Open System -> Preferences -> Windows -> Where it says “Movement Key” switch it form “Alt” to “Super”[/B]

If you want to find out if this works then just try it.  It will probably take about 30 minutes to install and configure.
 will try. just got a 10 gb hdd in my laptop though so i need to do some cleanup :) i used to have a windowspartition and a linuxpartition on that hdd before, just for diablo 2. :) now i wont need it anymore. thanks! :D

---

### Post by mike998 on 2005-07-11
Darn! This comes a couple of weeks after I sold Diablo 2 and LOD because Cedega didn't want to play!

---

### Post by nickless on 2005-07-19
Nice one.
But, I have some problems here. When I try to run it fullscreen, the gnome-panel is still above the game. Run in a window the mouse has serious problems and there are areas I can't move my mouse to. For example the whole right side, about two or three inches is blocked.
Performance is also really poor. Also I could run the game full on high detail under windows without problems and I am using 2D now...
Any tweaking tips? :neutral:

---

### Post by nickless on 2005-07-24
I am now using cedega and it works nearly flawlessly, even 3D :D
Only the little tweak to use a no-cd crack didn't work for me. I have tried different cracks, none worked, has anyone a crack that works and is so nice to tell me where he/she got it from? :)
Also battle.net doesn't recognize my version... no idea why  ](*,)

edit:
damn :D at the same time I post this I remember why this could be  :-P 
I didn't even install LOD with cedega, I just started it with it, becouse I already had installed it with this How-To for wine. Well it works, but obviously it (should?) could create some little errors and this might be the reason :D

---

### Post by tros22 on 2005-07-24
Hey,

I bought my Diablo and I have made backup copies, now since I have moved the only cd's I found are my backups...and when I try to play after I install it says to verify that my Expansion Disk is in the drive.  I am assuming it's because I don;t have my original.  Is there anyway to still play my game?  I am running XP Home
512 of DDRAM, P4.  Thanks a lot if you can help!\Mat

---

### Post by nickless on 2005-08-01
Use a no-cd crack, but I guess you have to copy all .mpq files from the expansion disk to your diablo II folder...

---

### Post by Strangerdave on 2005-08-02
I tired this with gnome and it all seemed to work fine, the installation went smooth...real smooth.  But when i type in the command to play, it says it can't find game.exe.  I wonder what to type?

-SD-

---

### Post by lynng on 2005-08-02
[QUOTE=Strangerdave]I tired this with gnome and it all seemed to work fine, the installation went smooth...real smooth.  But when i type in the command to play, it says it can't find game.exe.  I wonder what to type?

-SD-[/QUOTE]
 I believe it's Game.exe not game.exe

---

### Post by Feanor on 2005-08-03
I have an original copy of diablo 2: LOD, and I have not windows at all on my laptop, can D2LOD run without no cd crack?

---

### Post by NoTiG on 2005-08-03
can someone post their userdef.reg file ? i get a critical error cannot initialize directdraw  i start. I think its because it doesnt support the resolution of my monitor. How do i start wine without full screen but 640 X 480 ?

edit: it says 

> err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes) 

how to i enable it for more resolutions ? do i have to edit my xorg.conf file in /etc/X11 or my userdef.reg file???

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
``` 

I editted each line and added  "1280x1024" "1280x960" "1024x768". Do i have to edit the Modeline entry as well?

```
WINE REGISTRY Version 2
;; All keys relative to \\User\\.Default

[Software\\Battle.net\\Configuration] 990000000
"Diablo II Battle.net gateways"=str(7):"1002\00000\0uswest.battle.net\08\0U.S. West\0useast.battle.net\0006\0U.S. East\0asia.battle.net\0-9\0Asia\0europe.battle.net\0-1\0Europe\0"
"Server List"="exodus.battle.net"

[Software\\Blizzard Entertainment\\Diablo II] 990000000
"Always Run"=dword:00000001
"AutoMap Fades"=dword:00000001
"AutoMap Party"=dword:00000000
"AutoMap Party Names"=dword:00000000
"Aux Battle.net"="216.148.246.34"
"Blended Shadows"=dword:00000001
"CmdLine"="-skiptobnet"
"Contrast"=dword:0000005a
"DiabloIICD"="/mnt/Diablo"
"GAMEOVER"=dword:00000000
"Gamma"=dword:000000b9
"Help Menu"=dword:00000001
"InstallPath"="/home/notig/.wine/drive_c/Diablo II"
"Light Quality"=dword:00000002
"Mini Panel"=dword:00000001
"NPC Speech"=dword:00000002
"Program"="/home/notig/.wine/drive_c/Diablo II/Diablo II.exe"
"Save Path"="/home/notig/.wine/drive_c/Diablo II/Save"
"SmallInstall"=dword:00000000
"Text Display Beta"=dword:00000001
"UseCmdLine"=dword:00000000

[Software\\Blizzard Entertainment\\Diablo II\\VideoConfig] 990000000
"DeviceDDraw"=dword:00000000
"DeviceName"=""
"DeviceName0"=""
"DeviceName1"=""
"DeviceName2"=""
"DeviceName3"=""
"DeviceName4"=""
"DirectDrawDevice0"=dword:00000001
"dwFlags"=dword:0000000b
"dwFlags0"=dword:0000000b
"dwFlags1"=dword:00000000
"dwFlags2"=dword:0000029b
"dwFlags3"=dword:00000000
"dwFlags4"=dword:00000000
"GUID"=hex:00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"GUID0"=hex:00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"GUID1"=hex:00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"GUID2"=hex:00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"GUID3"=hex:00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"GUID4"=hex:00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"Recommend0"=dword:00000002
"Recommend1"=dword:00000000
"Recommend2"=dword:00000002
"Recommend3"=dword:00000000
"Recommend4"=dword:00000000
"Render"=dword:00000000
"TestD3D"=dword:00000002
"TestDDraw"=dword:00000002
"TestGLIDE"=dword:00000002

[Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\Shell Folders] 1123075497
"Cookies"="c:\\windows\\profiles\\notig\\Cookies"
"Desktop"="c:\\windows\\profiles\\notig\\Desktop"
"Favorites"="c:\\windows\\profiles\\notig\\Favorites"
"History"="c:\\windows\\profiles\\notig\\History"
"NetHood"="c:\\windows\\profiles\\notig\\NetHood"
"Personal"="c:\\windows\\profiles\\notig\\My Documents"
"PrintHood"="c:\\windows\\profiles\\notig\\PrintHood"
"Programs"="c:\\windows\\profiles\\notig\\Start Menu\\Programs"
"Recent"="c:\\windows\\profiles\\notig\\Recent"
"SendTo"="c:\\windows\\profiles\\notig\\SendTo"
"Start Menu"="c:\\windows\\profiles\\notig\\Start Menu"
"StartUp"="c:\\windows\\profiles\\notig\\Start Menu\\Programs\\StartUp"
"Templates"="c:\\windows\\profiles\\notig\\Templates"

[Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\User Shell Folders] 1123075497
"Cookies"=str(2):"%USERPROFILE%\\Cookies"
"Desktop"=str(2):"%USERPROFILE%\\Desktop"
"Favorites"=str(2):"%USERPROFILE%\\Favorites"
"History"=str(2):"%USERPROFILE%\\History"
"NetHood"=str(2):"%USERPROFILE%\\NetHood"
"Personal"=str(2):"%USERPROFILE%\\My Documents"
"PrintHood"=str(2):"%USERPROFILE%\\PrintHood"
"Programs"=str(2):"%USERPROFILE%\\Start Menu\\Programs"
"Recent"=str(2):"%USERPROFILE%\\Recent"
"SendTo"=str(2):"%USERPROFILE%\\SendTo"
"Start Menu"=str(2):"%USERPROFILE%\\Start Menu"
"StartUp"=str(2):"%USERPROFILE%\\Start Menu\\Programs\\StartUp"
"Templates"=str(2):"%USERPROFILE%\\Templates"
```

---

### Post by NoTiG on 2005-08-03
Well i solved that problem by editing the conf file in .wine and uncommenting the resolution line.

Now i have an obscure file read error about archivecpp and line # 59 . I think i have a corrupt ISO. I bought the cd yeeears ago and lost them but still had the case so i just redownloaded the isos.

btw does any1 know why when I moun tthe first ISO image to /mnt/Diablo .. and run 

wine /mnt/Diablo/INSTALL.EXE , it asks me for the install cd when the install is the first image ?????

---

### Post by trivialpackets on 2005-08-03
Does this work on battle.net?  I had thought it would not, but if it will... I'm looking forward to this.

---

### Post by Feanor on 2005-08-04
Here is what I'm getting

```
wine /media/cdrom0/Install.exe
wine: cannot determine executable type for L"D:\\Install.exe"
```

Why??

---

### Post by Strangerdave on 2005-08-05
[QUOTE=lynng]I believe it's Game.exe not game.exe[/QUOTE]

Yeah, it doesn't matter what case the letters are in I get the following:

```
Invoking /usr/lib/wine/wine.bin Game.exe ...
wine: cannot find 'Game.exe'
Wine failed with return code 1
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
/usr/bin/wine: line 605:  9471 Terminated              $XMESSAGE -timeout 30 -buttons "    Dismiss    ":0," Never display this message again ":3 -title "Wine Launch Window" "Invoking $WINEBIN/$WINE_BIN_NAME $@ ...

        This dialog box is a temporary status dialog to let you know
        that Wine is attempting to launch your application.

        Since Wine is still very much in a development stage,
        many applications will fail silently.
        This dialog box is your indication
        that we're *trying* to run your application.

        This dialog box will automatically disappear after 30 seconds,
        or after your application finishes.

        You can permanently disable this dialog by selecting
        the option below.
        " 2>/dev/null
``` 

I know the file is there, I have found it, just don't know what to type.

---

### Post by Strangerdave on 2005-08-14
Okay well I have figured out something.

When I type:

```
wine /media/cdrom0/install.exe
```  I get the launcher menu, then all I have to do is click "play" and it boots up fine.

The only thing is that the gnome menu bars on the top and bottom remain, so the screen size is smaller.  Not sure if changing my resolution down to 800x600 would work, but I will try that later.

-SD-

---

### Post by dtessier on 2005-08-15
[QUOTE=Strangerdave]The only thing is that the gnome menu bars on the top and bottom remain, so the screen size is smaller.  Not sure if changing my resolution down to 800x600 would work, but I will try that later.

-SD-[/QUOTE]

If find that when I get that, if I press Alt-SPACE and select "On Top", it gets rid of the panels.

---

### Post by KrazyPenguin on 2005-08-15
[QUOTE=eric.proctor]Does this work on battle.net?  I had thought it would not, but if it will... I'm looking forward to this.[/QUOTE]


Sure does work on Battle.net.

I also have included a post about upgrading to the newly released patch 1.11.

And for those that say they can see the Gnome panel, you have to click a different window, and then the one that Diablo is running in to go full screen (easy to do -- just 2 clicks) 

;-)

---

### Post by KrazyPenguin on 2005-08-15
I would also like to add,that even though the game runs on 2D instead of 3D, it is a 2D game and I don't see the difference.

The only difference I notice is D2LOD runs smoother with Linux !!!

And my favorite char is Summoner Necro.

I am currently level 52 on the new ladder with very crappy gear :-(

No + to skills except + to raise skeleton :-(

Here is my build:

EdgeOMancer
20 Raise Skeleton
20 Skeleton Mastery
15-20 CE
15-20 Dim Vision
1 Clay Golem
1 Blood Golem
1 Iron Golem
1 Fire Golem
1 - 10 Golem Mastery 
1 Summon Resist
1 Amp, 1 Decrepify, 1 Weaken, 1 Terror
1 Teeth, 1 Bone Armor

Strategy: Create Edge bow Tir -- Tal -- Amn
This will give level 12 thorns.
Raise Skeletons, then weapon switch to the bow and use Fire Golem instead of Clay. 
Always use amp except on some bosses use decrepify.
As soon as a body drops CE, CE, CE.

Edited: Oops, and of course --- NM Might Merc with Insight (Ral + Tir +Tal +Sol)
gives meditation aura, extra damage, and critical strike.

When switching to the bow you will lose a couple of skellies, but they keep there level they were raised at so no biggy.
;-)

---

### Post by nickyb on 2005-08-22
Hello, 

I've followed the guide in the first post. Except i used the 1.11 patch instead of the 1.10 patch. Installation works very smooth. But i cannot launch the game. Wine gives me the following error:

Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 00000001
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 00000001
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x126e,00007f00),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x1276,00007f8a),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x127e,00007f03),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x1286,00007f01),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x128e,00007f88),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x1296,00007f86),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x129e,00007f83),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x12a6,00007f82),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x12ae,00007f84),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x12b6,00007f04),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x65140000 
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x65140000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6514006c 
fixme:user:SetSystemCursor (0x12be,00007f02),stub!
fixme:ntdll:FILE_GetNtStatus Converting errno 16 to STATUS_UNSUCCESSFUL
fixme:user:SetSystemCursor (0x11c6,00007f8a),stub!
fixme:user:SetSystemCursor (0x11ce,00007f00),stub!
fixme:user:SetSystemCursor (0x11de,00007f03),stub!
fixme:user:SetSystemCursor (0x11e6,00007f01),stub!
fixme:user:SetSystemCursor (0x11f6,00007f88),stub!
fixme:user:SetSystemCursor (0x1206,00007f86),stub!
fixme:user:SetSystemCursor (0x1216,00007f83),stub!
fixme:user:SetSystemCursor (0x1226,00007f85),stub!
fixme:user:SetSystemCursor (0x1236,00007f82),stub!
fixme:user:SetSystemCursor (0x1246,00007f84),stub!
fixme:user:SetSystemCursor (0x1256,00007f04),stub!
fixme:user:SetSystemCursor (0x1266,00007f02),stub!
fixme:advapi:SetSecurityInfo stub
wine: Unhandled exception (thread 0009), starting debugger...
err:seh:start_debugger Couldn't start debugger ("winedbg --debugmsg -all 8 140") (2)
Read the Wine Developers Guide on how to set up winedbg or another debugger

Any ideas on what could be wrong?

Regards,
Nicky

---

### Post by KrazyPenguin on 2005-08-26
Are you trying to run "Game.exe" ????

Open the folder and double click it to see what happens.

Also this could be a video problem.

Are you running it in 2D cuz that's the setting you have to use!!!

Also , try to get it to work without the 1.11 patch.

It should start and try to load the new patch, but it won't work but at least you know that it is installed correctly.

Did you change the lines that I said needed changes as well???

Sorry I can't be of more help, but I installed DiabloII LOD on two different computers using two different versions of Linux without any problems.

;-)

(maybe post your computer specs)

Edited: One additional thought.  Try to get a slightly older version of WINE and try that. I have heard of games/etc working on some versions and not others.
This is a pain in the @$$ I know, but try a slightly older version without the patch.
If it loads you can install the patch manually later
;-)

Double EDIT: LOL
version of Wine that it works with for sure is 20050419.
Guess they go by dates.  Try that.
;-)

---

### Post by FLeiXiuS on 2005-08-26
[QUOTE=Nasso]sweet :) Can anyone confirm that this works? I had a friend that used wine to emulate diablo 2 but he has troubles with random crashes, no problem with that here?

Aint cedega better to use then wine? what is the difference?[/QUOTE]

This could be a numerous amount of things.  The reason in which I believe the author is using wine rather then cedega would be cedega introduces OpenGL much much better.  Wine on the other hand is basically direct3d / some OpenGL.  Diablo's game engine doesn't render OpenGL at all.  So this would improve performance a whole lot by sticking with wine.

---

### Post by nickyb on 2005-08-26
When i run the Game.exe it crashes with an error 2. However, in another forum i found someone using a no-cd crack. Which i also use right now. And the game plays fine.. full screen. But no sound yet. So i'll have to fix that. Anyone have any idea?

Greetz.

---

### Post by Cyberkef on 2005-09-01
[QUOTE=NoTiG]btw does any1 know why when I moun tthe first ISO image to /mnt/Diablo .. and run 

wine /mnt/Diablo/INSTALL.EXE , it asks me for the install cd when the install is the first image ?????[/QUOTE]
I have exactly the same problem :|

I added the /media/iso to the wine config as D: (cdrom) but that doesn't help :-?

---

### Post by niels2005 on 2005-09-01
hi,
if I try to install winesetuptk wine and libwine are being deinstalled ???
whats wrong ?
niels

---

### Post by Cyberkef on 2005-09-01
[QUOTE=Cyberkef]I added the /media/iso to the wine config as D: (cdrom) but that doesn't help :-?[/QUOTE]
I burned the iso's on CD-RW's, now 1.11 works here :)

But i still got the annoying GNOME panel bars & still no sound :neutral:

---

### Post by cib on 2005-09-01
Great guide, very detailed.  Allowed me to install/setup wine and Diablo II (I don't have the LOD expansion, though so I left those bits out).

Everything went REALLY SMOOTH.

Until I tried to actually run D2.

Then I got THIS message:
Invoking /usr/lib/wine/wine.bin Game.exe ...
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
/usr/bin/wine: line 472: 10073 Segmentation fault      $WINEBIN/$WINE_BIN_NAME "$@"
Wine failed with return code 139
Segmentation fault

If ANYONE has encounterd this or anything similar and has beaten it, please let me know what the secret is.  I'm thinking (something I shouldn't do, in all probability) that possibly there is a clash between the settings under which the game wants to run (640X480 for mysterious reasons) and the video setting for my current X server (1024X768).

I think the answer lies in the registry HKEY (etcetc) but I'd like a hint or bit of a roadmap as I'm not feeling too confident.

If that ISN'T the solution then I fear I shall have to look into setting up (I think this is right) a second x server (or client? sorry - new to the lingo, still picking it up) for the game to run under.  Or possiblysetting up an alternate (or second (parallel) video card - this I would like to do anyway but more on that later).

Any helpful advice/suggestions would be greatly welcomed.

Thanks, in advance,
CIB

---

### Post by Phibes on 2005-09-02
first i could install wine and libwine. but after when i install winesetuptk, it remove wine and libwine. after install winesetuptk, this time winesetuptk is uninstalling. how can i install all of them together.

---

### Post by tntc1978 on 2006-01-04
[QUOTE=Phibes]first i could install wine and libwine. but after when i install winesetuptk, it remove wine and libwine. after install winesetuptk, this time winesetuptk is uninstalling. how can i install all of them together.[/QUOTE]

I have the same problem :(

---

### Post by Dark Damo on 2006-01-15
When i put my Diablo 2 or LOD discs in the drive it just says CD-ROM and just has a few jpg's on the cd?

---

### Post by Dark Damo on 2006-01-15
I fixed the problem but now it says please insert cd rom

---

### Post by johnno56 on 2006-05-14
I'm wondering how to install Wine. From the above responses, if I am not mistaken, I would have to have both Windblows and Linux installed?

Can I install Wine onto a "Linux only" machine? If so, how?

I am relatively new to Linux and would appreciate any responses to be kept fairly simple.

Regards

J

---

### Post by lynng on 2006-05-15
[quote=johnno56]Can I install Wine onto a "Linux only" machine? If so, how?[/quote] 
Yes, you can install it to a Linux-only machine.  It creates a sort of pseudo-Windows directory structure in Linux.  Follow the instructions in the first post.

---

### Post by Copter on 2006-05-17
[QUOTE=Phibes]first i could install wine and libwine. but after when i install winesetuptk, it remove wine and libwine. after install winesetuptk, this time winesetuptk is uninstalling. how can i install all of them together.[/QUOTE]
same here...

---

### Post by YokoZar on 2006-05-19
Do not install winesetuptk.  It is old and useless and shouldn't exist as a package (and, in dapper, it doesn't.)

---

### Post by novik420 on 2006-05-31
I need some help.. when i put in diablo 2 it goes into a hdd file?!?!??

---

### Post by KrazyPenguin on 2006-05-31
[QUOTE=novik420]I need some help.. when i put in diablo 2 it goes into a hdd file?!?!??[/QUOTE]


I removed the old guide and have included an updated link to the NEW GUIDE in the 1st post.

Good luck!!!

---

### Post by flapane on 2006-06-07
hi
i followed the new guide but i have
[[IMG]http://img237.imageshack.us/img237/2750/sk155ag.th.jpg[/IMG]](http://img237.imageshack.us/img237/2750/sk155ag.jpg)

after this, i can hear the menu music from d2lod, but i can't see anything, only the desktop

---

### Post by cheuschober on 2006-06-09
Thanks for the guide KrazyPenguin.

Curious to know if you've run into the following and or have any ideas on how to fix it:

```
chad@kain:~/.wine/dosdevices$ wine ../drive_c/games/diabloii/Diablo\ II.exe
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 6\Logical Unit Id 0
fixme:ole:ITypeInfo_fnRelease destroy child objects

```

In the gui this is accompanied with a 'Please Insert CD' message but the cd's in, and I've tried various forms of mounting images. sym linking, etc.

Thanks.

---

### Post by yteh on 2006-06-10
Thanks for the HowTo KrazyPenguin. I ran into a couple issues but I've got LOD up and running now.

Here's my experience (in case somebody else has encountered this):

My first attempt didn't quite work. I think it had something to do with Wine configuration and maybe permissions?. 

Here is my first attempt (see #2.2 for the problem):
1. Install Wine: No issues
2.1 Install Diablo II: No issues
2.2 Install Diablo II LOD: "wine /cdrom/install.exe" popped up a message saying "Please insert disk into CDROM" (not exactly the text but you get it) although it was already there.
3. Configure Wine: No issues

I believe by configuring Wine in #3, somehow the issue was resolved. I was able to perform #2.2 on my second attempt.

Also, maybe I missed it, but I didn't see a link in your guide to get the LOD patch installed. Googling it gave me this link... which is (surprise!) a HowTo that you had put together: [http://ubuntuforums.org/showthread.php?p=282154&mode=linear](http://ubuntuforums.org/showthread.php?p=282154&mode=linear)

Thanks again!

---

### Post by flapane on 2006-06-16
[QUOTE=flapane]hi
i followed the new guide but i have
[[IMG]http://img237.imageshack.us/img237/2750/sk155ag.th.jpg[/IMG]](http://img237.imageshack.us/img237/2750/sk155ag.jpg)

after this, i can hear the menu music from d2lod, but i can't see anything, only the desktop[/QUOTE]

bump

---

### Post by Dr. Feelgood on 2006-06-20
When I click on the link to the guide it says "forbidden".  Has the guide moved?

---

### Post by F0CUS on 2006-06-20
[QUOTE=Dr. Feelgood]When I click on the link to the guide it says "forbidden".  Has the guide moved?[/QUOTE]


It seems the whole domain is inaccessable... ](*,)  Does anyone know if there is a mirror to the guide?

---

### Post by Dr. Feelgood on 2006-06-20
Problem 1 solved but now there's another problem.  Google has a cached version of the guide that you can use.  When I tried to install D2 though it keeps saying "Insert Install Disc in Drive", but the disc is already in the drive!  I keep clicking but the message keeps coming up.  Very annoying.  What happend?

---

### Post by cre8ivgil on 2006-06-20
[QUOTE=KrazyPenguin]The old guide has been removed.

The NEW guide is found here:
[http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine](http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine)

including an Ubuntu Dapper Guide.

Good luck!!![/QUOTE]

I know you have a pretty good Ubuntu Guide, but the link above does not seem to be working.

---

### Post by F0CUS on 2006-06-21
[QUOTE=Dr. Feelgood]Problem 1 solved but now there's another problem.  Google has a cached version of the guide that you can use.  When I tried to install D2 though it keeps saying "Insert Install Disc in Drive", but the disc is already in the drive!  I keep clicking but the message keeps coming up.  Very annoying.  What happend?[/QUOTE]
I am having the same problem. It always asks for the disk...

---

### Post by Dr. Feelgood on 2006-06-26
Anyone have any ideas as to why it keeps asking for the disc?

---

### Post by Dr. Feelgood on 2006-06-27
I figured out the problem.  You have to run winecfg before you do anything, go to drives and select Auto Detect.  Now when you install it wont keep asking you for the disc... it will actually continue with the installation.  Worked great for me now that everything is settled.  Thanks for the write-up.

---

### Post by cXSlayer on 2006-07-01
[QUOTE=KrazyPenguin]The old guide has been removed.

The NEW guide is found here:
[http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine](http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine)

including an Ubuntu Dapper Guide.

Good luck!!![/QUOTE]

Link is down -_-

---

### Post by chickengirl on 2006-08-03
> **Dr. Feelgood said:**
> I figured out the problem.  You have to run winecfg before you do anything, go to drives and select Auto Detect.  Now when you install it wont keep asking you for the disc... it will actually continue with the installation.  Worked great for me now that everything is settled.  Thanks for the write-up.


I did the auto detect thing with winecfg and then successfully installed Diablo II, but I can't play it. It does not recognize the disc being in the drive even though it is in and mounted.

Is it possible to actually play the game with Wine? Has anyone ever done it?

---

### Post by Dr. Feelgood on 2006-08-03
Yes it's possible, I do it.  Does it autorun when it's mounted and then it doesn't read the disc?  Are you using the Expansion pack or just D2?  If you're having alot of trouble I hear its possible to use a NoCD crack.  Maybe you can give that a whirl before you try and tackle the CD reading problem.

---

### Post by chickengirl on 2006-08-04
> **Dr. Feelgood said:**
> Yes it's possible, I do it.  Does it autorun when it's mounted and then it doesn't read the disc?

Do you mean autorun a la Windows?

I'm in Xubuntu, so when I put a CD in it autodetects it and puts an icon for it on the desktop but doesn't actually mount it until I open it in Thunar or right click on the icon and mount it.

> Are you using the Expansion pack or just D2?

Just D2.

> If you're having alot of trouble I hear its possible to use a NoCD crack.  Maybe you can give that a whirl before you try and tackle the CD reading problem.

I tried downloading a NoCD crack, but when I tried to run it it asked me to put in the Play Disc anyway. (And the Play Disc was already in and mounted.) Am I doing it wrong? Or, do you know any particularly good NoCD cracks?

---

### Post by Dr. Feelgood on 2006-08-05
After reading my original post I realized I was pretty vague...lol.  Here's how I do it.  I run the expansion pack in regular Ubuntu so that might have something to do with it.  I insert the CD and it auto mounts, then I click on the setup exe so it comes up like the autorun feature in windows.  I don't use a desktop shortcut.  It's always worked for me.  Give it a shot.

---

### Post by chickengirl on 2006-08-10
> **Dr. Feelgood said:**
> After reading my original post I realized I was pretty vague...lol.  Here's how I do it.  I run the expansion pack in regular Ubuntu so that might have something to do with it.  I insert the CD and it auto mounts, then I click on the setup exe so it comes up like the autorun feature in windows.  I don't use a desktop shortcut.  It's always worked for me.  Give it a shot.

I got around to trying it in Linux again - in both Xfce and Gnome, if I open setup.exe with wine, the autorun screen comes up, but if I click "Play Diablo II", I get a message saying it can't find the disc.

---

### Post by MST3Kakalina on 2006-08-24
I was able to install D2 successfully with wine (needed to run winecfg and add the CD-ROM drive was the only setback), but I am having some DirectDraw/DirectX problems when I go to play the game. Running the video test fails, and the dialog box tells me to install DirectX.   I have tried "wine /media/cdrom0/playd2.exe -opengl" with the same results. Do I have to install DirectX in my fake Windows directory, or what?  

Kubuntu 6.06, wine version 0.9.9.

---

### Post by Dr. Feelgood on 2006-09-10
> **chickengirl said:**
> I got around to trying it in Linux again - in both Xfce and Gnome, if I open setup.exe with wine, the autorun screen comes up, but if I click "Play Diablo II", I get a message saying it can't find the disc.

I just reinstalled Diablo on a fresh Dapper installation and ran across this exact problem.  You have to make sure the wine configuration is set the way you want it to be because for some reason it was different this time around.  I set my OS to Windows 2000 and then went to the drives tab.  Click on advanced and then click on your cdrom drive to make sure its the one that being used.  Apply changes and exit.  That did the trick for me, hope it works for you.

---

### Post by basementjack on 2006-09-25
Link is still down?... [http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine](http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine) is 403 forbidden, and so is [http://www.krazypenguin.net/](http://www.krazypenguin.net/)...

---

### Post by Tommaso on 2006-11-06
> **basementjack said:**
> Link is still down?... [http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine](http://www.krazypenguin.net/Diablo_II_LOD_for_Dapper_using_Wine) is 403 forbidden, and so is [http://www.krazypenguin.net/](http://www.krazypenguin.net/)...

Same here....

---

### Post by turkenator on 2006-11-06
does anyone else know of a guide that allows diablo 2 to work on ubuntu/linux with wine ?

---

### Post by basementjack on 2006-11-06
A guide isn't really needed any more for Edgy.. Just open up for multivers, get Wine (mine is 0.9.22), execute wine "d:\path\to\install.exe" and do everything as if your were using Windows. :)

---

### Post by chickengirl on 2006-11-06
one caveat: make sure that when you run the install, you aren't in the directory where the CD is -- because this will lock the CD drive as "in use" and you won't be able to switch CDs when the installer asks for the next one.

So, make sure it's **you:~$ wine /path/to/install.exe** and not **you:cdrom$ wine install.exe**.

---

### Post by turkenator on 2006-11-07
ok thanks guys im gonna try it now

---

### Post by turkenator on 2006-11-07
i couldnt find any no cd cracks that actually work does any1 know where i can find a working 1?

---

### Post by chickengirl on 2006-11-07
> **turkenator said:**
> i couldnt find any no cd cracks that actually work does any1 know where i can find a working 1?
I could never find any either. Just play it with the CD in, or maybe you could rip the CD to an .iso and then mount that as a CD drive? (Not that I know how to do that.)

---

### Post by flapane on 2006-11-09
unfortunately I lost my cd 3years ago, I have only the game installed on my ntfs partition, but if I try to run it from wine, it says: access violation after having played the blizzard video.
No problems in windoze

---

### Post by turkenator on 2006-11-10
try moving it to a partition that linux can write on like ext3 reiserfs etc it might work then

---

### Post by chickengirl on 2006-11-10
I didn't bother actually installing it in Linux, I just copied the game directory over from my Windows drive. Works perfectly.

---

### Post by kdawg on 2006-11-26
No problems here, just installed with wine like it all says and it worked perfectly!

---

### Post by flapane on 2006-11-28
[error]

---

