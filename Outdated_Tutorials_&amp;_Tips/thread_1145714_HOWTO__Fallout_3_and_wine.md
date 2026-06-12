---
title: "HOWTO:  Fallout 3 and wine"
date: 2009-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by karvec on 2009-05-01
These are the steps I took to install Fallout3 on my laptop, using latest patch from Bethesda (1.5) and wine 1.1.20.

First of all, enable 3rd party apps and do:

```
sudo apt-get install libglut-dev libglu-dev xorg-dev build-essential
```
These should be all the libraries you need.

Next:  Follow the instructions at [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
```
sudo apt-get update && sudo apt-get upgrade
```

Now, download the wine source from 
[HTML]http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449[/HTML]

```
tar xvf wine-*
```

Then, get this patch:

[HTML]http://bugs.winehq.org/attachment.cgi?id=20312[/HTML]

File, save page as --> to desktop or wine-* directory.

cd to the wine-* directory and do:

```
patch -p1 < filename.diff
```

Now, you can go ahead and do a ./configure, make depend && make then go ahead and sudo make install.

This will install the patched version of wine, which is what we need.

After this, you should be able to run the launcher to set video settings, then cd to your Fallout3 install directory and you should be able to run wine Fallout3.exe no problems with no crashes after selecting New Game from the menu.

If this doesn't work for you, let me know, I forgot exactly what packages I had installed for compiling wine with OpenGL.

---

### Post by hoghunter82d on 2009-05-05
Does this fix the fallout3 cannot detect sound device while you have background music when you click on play? If so where do I put these?


Any help would be awesome.

---

### Post by razor7 on 2009-05-12
Hello...downloades, patched, configured, make, and installed wine 1.1.20

after all those struggles, i get this wile running the fallout3 launcher...

wine FalloutLauncher.exe
> 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\media\\Descargas\\Fallout3\\FalloutLauncher.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\Descargas\\Fallout3\\FalloutLauncher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\Descargas\\Fallout3\\FalloutLauncher.exe" failed, status c0000135


After installing y get sound device not found


Please advise

Thenks a lot!

---

### Post by recon04 on 2009-08-07
can anyone repeat this for a noob O_o :confused:

---

### Post by Sparticusx on 2009-08-10
This is how i got it working using Playonlinux ....... It's really easy....surprisingly. 

Just run these commands from your terminal

```
sudo wget http://deb.playonlinux.com/playonlinux_jaunty.list -O  /etc/apt/sources.list.d/playonlinux.list
```That will update your source list so that you can download Playonlinux.

then do..

```
sudo apt-get update
```then

```
sudo apt-get install playonlinux
```This is for Ubuntu 9.04 (or kubuntu)

After you install it in the terminal it will be listed under "games" in your applications menu let it run its updates and then click install and choose "Fallout 3" it's that simple. Hope that helps.

---

### Post by jabazan on 2009-10-29
> **Sparticusx said:**
> This is how i got it working using Playonlinux ....... It's really easy....surprisingly. 

Just run these commands from your terminal

```
sudo wget http://deb.playonlinux.com/playonlinux_jaunty.list -O  /etc/apt/sources.list.d/playonlinux.list
```That will update your source list so that you can download Playonlinux.

then do..

```
sudo apt-get update
```then

```
sudo apt-get install playonlinux
```This is for Ubuntu 9.04 (or kubuntu)

After you install it in the terminal it will be listed under "games" in your applications menu let it run its updates and then click install and choose "Fallout 3" it's that simple. Hope that helps.

Yeah, i installed via playonlinux, but when i start fallout launcher.exe i do as regular, press play and wait for it to start, but i only get a black screen with the sound coming when the background pictures change, no theme or anything (as they say here). I LOVE <3 fallout 3, and really wanna have it on my computer. So... Plz help. 

Ps. I did not update the game, is this neccecary? If so, tell me howto.

---

### Post by NSLW on 2009-11-01
I think it's something wrong with your hardware configuration.

PlayOnLinux asked you if you would like to update game at the end. It would download patch automatically and it would update your game no matter what your language version is. You haven't red it or you didn't understand it.

---

### Post by cbdaqb on 2009-11-17
is it possible for someone to compile the wine version then send it to me? I am on mac os x trying to port this with an app called wineskin and my attempts at compiling with 1.1.30 have failed

---

### Post by NSLW on 2009-11-24
Fallout 3 works on vanilla Wine 1.1.33 (kudos to H. Verbeet)

---

### Post by Dr. I on 2009-12-06
Hello I am a n00b here. I have Playonlinux and I have problem.  When I get to installation,  it shows install fallout 3 media into your disk drive. I click forward and it shows the cdrom drives but says Error: unable to find the CD-Rom.  The funny thing is I can see it mounted in terminal and in disk browser.

What is going on.  

I get this error through wine:

@SheikYurbouti:~/wine-1.1.33$ wine '/home/Desktop/fallout/fallout3/FalloutLauncher.exe' 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\Desktop\\fallout\\fallout3\\FalloutLauncher.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\Desktop\\fallout\\fallout3\\FalloutLauncher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\Desktop\\fallout\\fallout3\\FalloutLauncher.exe" failed, status c0000135
 
well i did install winetricks -q vcrun2005 d3dx9 and after installation i still get the same error.  So Then decided to recompile with the patch and am stuck @:

@SheikYurbouti:~/wine-1.1.33$ make depend && make
make: *** No rule to make target `depend'.  Stop.

what do I need to do from here. 

I am sorry if I am all over the place.  Thanks

---

### Post by t.rei on 2010-07-16
Am getting the same thing:

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programme\\Steam\\steamapps\\common\\fallout 3\\FalloutLauncher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programme\\Steam\\steamapps\\common\\fallout 3\\FalloutLauncher.exe" failed, status c0000135
```*sigh*

MSVCP80.dll ???

---

### Post by vek on 2010-07-23
It might be worth installing the winetricks. (its just a script that you run in bash).  It lets you install all sorts of missing dlls automatically.

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Just gotta download the script and set it as executable (or just run it via sh)

The DLLs you're missing are probably called "vcrun2005" Winetricks will install it for you.

---

### Post by t.rei on 2010-07-24
I finally figured out that one needs to install something prior to dx9 .. it works pretty well now. :)

---

