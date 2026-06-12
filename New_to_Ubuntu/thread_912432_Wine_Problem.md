---
title: "Wine Problem"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-09-06
Just instgalled Wine, it doesnt show up in applicatins>wine>programs. When i double click on the .exe file nothing happens, when i do it through the terminal i get this

```
 wine crysis
wine: could not load L"C:\\windows\\system32\\crysis.exe": Module not found

```

Anyone help?

---

### Post by pyromanic123boom on 2008-09-06
Well, try uninstalling wine and then re-installing through terminal.

uninstall

sudo apt-get remove wine

reinstall

sudo apt-get install wine

---

### Post by Codemastadink on 2008-09-06
> **pyromanic123boom said:**
> Well, try uninstalling wine and then re-installing through terminal.

uninstall

sudo apt-get remove wine

reinstall

sudo apt-get install wine

Tried, didnt work

---

### Post by 7raTEYdCql on 2008-09-06
Is the software supported by wine. visit the wine website and find out?

---

### Post by Codemastadink on 2008-09-06
> **i.mehrzad said:**
> Is the software supported by wine. visit the wine website and find out?

Yes, it says it should install and run just fine, but its not :/

---

### Post by cwsnyder on 2008-09-06
Did you re-install the program 'crysis' under Wine?  In other words, did you go into Terminal and type ```
wine crysis.msi
``` or whatever the name for the install program was to run under Wine?

---

### Post by Codemastadink on 2008-09-06
> **cwsnyder said:**
> Did you re-install the program 'crysis' under Wine?  In other words, did you go into Terminal and type ```
wine crysis.msi
``` or whatever the name for the install program was to run under Wine?

Yes, did that. Was still installed. did nothing, still having problem

---

### Post by cwsnyder on 2008-09-06
When you type in the terminal: ```
wine /home/[your user name]/.wine/drive_c/'Program Files'/[wherever the .exe file is]/crysis.exe 
```replacing [your user name] with whatever your login name is and [wherever the .exe file is] with the correct path name for the executable file (only using forward slashes because you are working in Linux, not Windows), what happens?

---

### Post by Codemastadink on 2008-09-06
> **cwsnyder said:**
> When you type in the terminal: ```
wine /home/[your user name]/.wine/drive_c/'Program Files'/[wherever the .exe file is]/crysis.exe 
```replacing [your user name] with whatever your login name is and [wherever the .exe file is] with the correct path name for the executable file (only using forward slashes because you are working in Linux, not Windows), what happens?

```
cody@cody-laptop:~$ wine /home/cody/.wine/drive_c/'Program Files'/cryteck/crysis/crysis.exe
wine: cannot find '/home/cody/.wine/drive_c/Program Files/cryteck/crysis/crysis.exe'
cody@cody-laptop:~$ 


```

you can see it in the SC tho...

---

### Post by cwsnyder on 2008-09-06
According to your screen shot, though the correct path is ```
cody@cody-laptop:~$ wine /home/cody/.wine/drive_c/'Program Files'/'Electronic Arts'/Crytek/Crysis/Bin32/Crysis.exe 
```

---

### Post by Codemastadink on 2008-09-06
> **cwsnyder said:**
> According to your screen shot, though the correct path is ```
cody@cody-laptop:~$ wine /home/cody/.wine/drive_c/'Program Files'/'Electronic Arts'/Crytek/Crysis/Bin32/Crysis.exe 
```

haha typed it in wrong, well i did it and this is what i get

```
cody@cody-laptop:~$ wine /home/cody/.wine/drive_c/'Program Files'/'Electronic Arts'/Crytek/Crysis/Bin32/Crysis.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Electronic Arts\\Crytek\\Crysis\\Bin32\\Crysis.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Electronic Arts\\Crytek\\Crysis\\Bin32\\Crysis.exe" failed, status c0000135

```

---

### Post by cwsnyder on 2008-09-06
One last suggestion, because I don't know if even this will work. In terminal type the non-underlined, bold type: ```
_~$ _**cd /home/cody/.wine/drive_c/'Program Files'/'Electronic Arts'/Crytek/Crysis/Bin32**
_~$ _**wine Crysis**
```

---

### Post by RequinB4 on 2008-09-06
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880)

> 
Howto:
If you're using ATI hardware there may be even worse problems since their drivers suck (for now)

    * Compile Wine 1.1.0 with this patch to get it to do "proper" mouse warping
    * Put d3dx9_36.dll and XINPUT1_3.dll in windows/system32. You can get them from a DLL site like dll-files.com
    * Install the game and use a Crack on it 
    * Enable OffscreenRenderingMode=fbo. Look here under the Direct3D section to see what I mean
    * Set Shaders to High, else you will get graphical problems
    * If you have problems with insane HDR lighting (believe me, you will), open a console and issue con_restricted 0 and r_glow 0

Issues:

    * FPS are even worse than on Windows (~15 FPS on a 8600GT low settings except shaders). Don't even try to run the game on hardware lower than a GF8
    * Severe graphical corruption
    * Sound may vanish under some circumstances
    * Movies don't have sounds at all
    * Crysis will freeze whenever it feels like it 
    * FPS will drop to below 1 at some resolutions
    * Also FPS may suddenly drop at any point, usually accompanied by graphical corruption. Restart the game and reload the level to fix this
    * The patcher will not work in Wine 


---

### Post by Codemastadink on 2008-09-06
> **RequinB4 said:**
> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880)

I have an intel CPU and a Nvidia GPU lol so i dont think this will help

---

### Post by RequinB4 on 2008-09-06
> **Codemastadink said:**
> I have an intel CPU and a Nvidia GPU lol so i dont think this will help

Why....? you still need the appropriate dlls and settings...

---

### Post by Codemastadink on 2008-09-06
> **RequinB4 said:**
> Why....? you still need the appropriate dlls and settings...

Oh.. i thought it was for ATI hardware only haha okay, well i'll do that in the morning then. Thanks

---

### Post by Codemastadink on 2008-09-07
This is from the [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107)

```
Compile Wine 1.1.0 with this patch to get it to do "proper" mouse warping 
```

What exactly does "compile" mean. What do i do with the patch?

```
Install the game and use a Crack on it 
```

What does using the crack mean? I already have the game installed, do i need to reinstall and do something to it?

---

### Post by Codemastadink on 2008-09-07
.

---

### Post by Codemastadink on 2008-09-07
.

---

