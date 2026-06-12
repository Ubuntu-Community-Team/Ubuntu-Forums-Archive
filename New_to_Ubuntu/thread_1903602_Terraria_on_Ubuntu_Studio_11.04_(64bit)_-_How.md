---
title: "Terraria on Ubuntu Studio 11.04 (64bit) - How?"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by deckerry on 2012-01-02
(I am running 64 bit Ubuntu Studio 11.04 and some version of the Gnome desktop interface.)

I know that other people have gotten [COLOR="Red"]Terraria [/COLOR]to work on Linux machines. That is for certain.

The problem is that I have spent hours and hours and hours trying to get it to work on my computer and can't figure it out.

I can get [COLOR="Blue"]Steam [/COLOR]to work through [COLOR="blue"]Wine 1.3.36[/COLOR] but just not [COLOR="Red"]Terraria[/COLOR].

**_*[COLOR="Red"]Can anybody please help me figure out how to get Terraria to run on my computer?[/COLOR]*_**

---

### Post by sadaruwan12 on 2012-01-03
You can use Play on Linux which have pre-configured bottles for games so you can just install the game and rest is done automatically. I use it in my pc to run AOM and another game.

Give it a go.

---

### Post by deckerry on 2012-01-03
I installed Play On Linux 4.0.14.

I opened Run On Linux and installed Steam.

I opened Steam and installed Terraria via Steam.

I tried to open Terraria in the Steam interface and either Steam or Terraria prompted me to install  XNA framework before playing.

After installing XNA, Terraria didn't open so I clicked to open it again in the Steam interface. It still didn't open.

I closed Steam and reopened it via Play On Linux.

Then I clicked to play Terraria again in the Steam interface. Steam said "preparing to launch Terraria" and nothing happened.
I tried opening Terraria again... Steam said "preparing to launch Terraria" again. Then guess what? Nothing happened.

Thanks for the tip about PlayOnLinux. I thought that that would do the trick but now that it hasn't, I'm stumped.

---

### Post by sadaruwan12 on 2012-01-03
Ok, Have you tried this one [Click Here]("http://www.steamgamesonlinux.com/terraria/")

This might help you as well [Click Here]("http://ubuntuforums.org/showthread.php?t=1791416")

---

### Post by deckerry on 2012-01-03
For several hours, I have thoroughly read and tried everything you have given me and I have two problems:

1) I tried installing Direct X through Wine according to the instructions here: _[http://www.dedoimedo.com/games/wine-directx.html](http://www.dedoimedo.com/games/wine-directx.html)_. When I got to the heading of that article titled: ***Test Direct X 9.0c***, I tried running dxdiag.exe and this is the result:

```
user@computer:~$ wine ~/.wine/drive_c/windows/system32/dxdiag.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\dxdiagn.dll"
err:ole:CoGetClassObject no class object {a65b8071-3bfe-4213-9a5b-491da4461ca7} could be created for context 0x1
err:dxdiag:collect_dxdiag_information IDxDiagProvider instance creation failed with 0x80070005
err:dxdiag:wWinMain DxDiag information collection failed
```

2) I opened steam through a terminal using ```
wine Steam.exe
``` then I opened Terraria through steam. Then I got a popup error message complaining about my graphics card. (I attached an image of the error.) I closed everything, ran Steam through a terminal again, and the program just automatically closed.

---

### Post by deckerry on 2012-03-05
Just wondering if anybody else had a chance to look into this.

---

### Post by IparryU on 2012-06-05
> **deckerry said:**
> For several hours, I have thoroughly read and tried everything you have given me and I have two problems:

1) I tried installing Direct X through Wine according to the instructions here: _[http://www.dedoimedo.com/games/wine-directx.html](http://www.dedoimedo.com/games/wine-directx.html)_. When I got to the heading of that article titled: ***Test Direct X 9.0c***, I tried running dxdiag.exe and this is the result:

```
user@computer:~$ wine ~/.wine/drive_c/windows/system32/dxdiag.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\dxdiagn.dll"
err:ole:CoGetClassObject no class object {a65b8071-3bfe-4213-9a5b-491da4461ca7} could be created for context 0x1
err:dxdiag:collect_dxdiag_information IDxDiagProvider instance creation failed with 0x80070005
err:dxdiag:wWinMain DxDiag information collection failed
```

2) I opened steam through a terminal using ```
wine Steam.exe
``` then I opened Terraria through steam. Then I got a popup error message complaining about my graphics card. (I attached an image of the error.) I closed everything, ran Steam through a terminal again, and the program just automatically closed.
I have the same exact issue... If I find the solution I will reply.

I am referring to this BTW:
[http://portingteam.com/topic/5338-hearts-of-iron-iii-wrapper/](http://portingteam.com/topic/5338-hearts-of-iron-iii-wrapper/)

Not on Mac nor trying to play the listed game. but i googled my error and this came up. winetricks is still dling the files, so i will repost with some results.

UPDATE:
in winetricks, check the following boxes for install:
d3dxof
devenum
dsound
dxdiag
dxdiagn

all the d3dx files should be checked off i would assume, my was and know i am on the next phase... getting StarCraftII working...

---

