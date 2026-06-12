---
title: "[SOLVED] Where are the cached package files stored ?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by bhadotia on 2008-05-14
Some of my friends who have ubuntu do not have a wi-fi card , so that they are not able to connect to our University's network (internet). When they need to install packages we have to manually download them and then transfer them to their pcs.

So if I have a package installed that my friend also needs ,where can   the cached file for that package be found.

---

### Post by forestpixie on 2008-05-14
/var/cache/apt/archives

---

### Post by sisco311 on 2008-05-14
> **bhadotia said:**
> Some of my friends who have ubuntu do not have a wi-fi card , so that they are not able to connect to our University's network (internet). When they need to install packages we have to manually download them and then transfer them to their pcs.

So if I have a package installed that my friend also needs ,where can   the cached file for that package be found.

/var/cache/apt/archives

---

### Post by bhadotia on 2008-05-15
Thanks guys.

---

### Post by NITROCARIO on 2010-12-23
I have found the files in my friend's PC from the location /var/cache/apt/archives/ and I also copied them on my Usb stick but when I install it on my PC they do not get installed install the Software Centre gives a message that please connect to Internet. So how can I install the files without internet connection?

The files are:

chromium-browser_8.0.552.224~r68599-0ubuntu0.10.10.1_i386.deb
chromium-browser-inspector_8.0.552.224~r68599-0ubuntu0.10.10.1_all.deb
chromium-codecs-ffmpeg_0.6+svn20100904r58574+58998-0ubuntu1_i386.deb

==============================================================================
Found a way to install the files
==============================================================================

Goto **System > Administrator > Synaptic Package Manager**; enter your password; in search menu search for file you want to install; mark it for installation and it will select all the files required for installation; then goto file menu and select generate package dowload script and save it with any name of your choice; now copy that file to usb and then goto your friends home; then open that file and then goto /var/cache/apt/archives/ on your friends pc where the files got downloaded and find each and every file and copy it into a newly created folder and then finally copy the generated script into that folder too.

When you return back to your home open synaptic package manager and goto file menu and click on add downloaded packages and browse for that folder in which you saved the files and then open it and install them :D

---

### Post by karthick87 on 2010-12-23
```
cd /var/cache/apt/archives/
```
```
sudo dpkg -i *.deb
```

---

### Post by NITROCARIO on 2010-12-28
> **NITROCARIO said:**
> I have found the files in my friend's PC from the location /var/cache/apt/archives/ and I also copied them on my Usb stick but when I install it on my PC they do not get installed install the Software Centre gives a message that please connect to Internet. So how can I install the files without internet connection?

The files are:

chromium-browser_8.0.552.224~r68599-0ubuntu0.10.10.1_i386.deb
chromium-browser-inspector_8.0.552.224~r68599-0ubuntu0.10.10.1_all.deb
chromium-codecs-ffmpeg_0.6+svn20100904r58574+58998-0ubuntu1_i386.deb

==============================================================================
Found a way to install the files
==============================================================================

Goto **System > Administrator > Synaptic Package Manager**; enter your password; in search menu search for file you want to install; mark it for installation and it will select all the files required for installation; then goto file menu and select generate package dowload script and save it with any name of your choice; now copy that file to usb and then goto your friends home; then open that file and then goto /var/cache/apt/archives/ on your friends pc where the files got downloaded and find each and every file and copy it into a newly created folder and then finally copy the generated script into that folder too.

When you return back to your home open synaptic package manager and goto file menu and click on add downloaded packages and browse for that folder in which you saved the files and then open it and install them :D

But this process is very time consuming if you have any other way which saves time and energy then please inform me. :)

---

### Post by corncob on 2010-12-28
> **NITROCARIO said:**
> But this process is very time consuming if you have any other way which saves time and energy then please inform me. :)

I never did this myself but is there anything wrong with copying the .deb files to a CD and then going to System > Synaptic > Edit > Add CD-Rom?  Or, if its just a one time thing with a package or two, double click it in the file browser and let the package manager install it.

---

### Post by bhadotia on 2011-04-30
> **NITROCARIO said:**
> I have found the files in my friend's PC from the location /var/cache/apt/archives/ and I also copied them on my Usb stick but when I install it on my PC they do not get installed install the Software Centre gives a message that please connect to Internet. So how can I install the files without internet connection?

The files are:

chromium-browser_8.0.552.224~r68599-0ubuntu0.10.10.1_i386.deb
chromium-browser-inspector_8.0.552.224~r68599-0ubuntu0.10.10.1_all.deb
chromium-codecs-ffmpeg_0.6+svn20100904r58574+58998-0ubuntu1_i386.deb

==============================================================================
Found a way to install the files
==============================================================================

Goto **System > Administrator > Synaptic Package Manager**; enter your password; in search menu search for file you want to install; mark it for installation and it will select all the files required for installation; then goto file menu and select generate package dowload script and save it with any name of your choice; now copy that file to usb and then goto your friends home; then open that file and then goto /var/cache/apt/archives/ on your friends pc where the files got downloaded and find each and every file and copy it into a newly created folder and then finally copy the generated script into that folder too.

When you return back to your home open synaptic package manager and goto file menu and click on add downloaded packages and browse for that folder in which you saved the files and then open it and install them :D
First copy all the files from your friends computer to your usb and paste them in your computer in the /var/cache/apt/archives/ directory. This is done so that you also copy all the dependencies for the package you are trying to install.
You will need to copy the files using administrative previliges, so either use the command line:
```
sudo cp <path_to_the_files_on_the_usb/*> /var/cache/apt/archives/
```
or use nautilus with previliges:
```
gksudo nautilu
```
> **karthick87 said:**
> ```
cd /var/cache/apt/archives/
```
```
sudo dpkg -i *.deb
```
Dude that does not make any sense..

---

