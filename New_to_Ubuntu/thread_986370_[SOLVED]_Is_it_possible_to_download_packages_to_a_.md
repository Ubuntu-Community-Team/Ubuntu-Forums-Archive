---
title: "[SOLVED] Is it possible to download packages to a CD"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by LinuxFox on 2008-11-18
I notice the CD option in the Software Sources menu, and I wanted to know if it would be possible to download packages to a CD and use that as an option.  I want to do this just in case my internet is down and I want to install something I want to use or is important (for example SDL or GTK1.2 to run certain programs).

I've used APTonCD and it is quite useful for putting recently downloaded packages on CD, but it doesn't do all packages I install.

Is there a way to download packages to a CD?  Any answers would be appreciated.

---

### Post by jpoRS on 2008-11-18
You could probably burn the files to the disc after download, but I don't know for sure.

jim

---

### Post by LinuxFox on 2008-11-18
> **jpoRS said:**
> You could probably burn the files to the disc after download, but I don't know for sure.

jimI could try that, but I don't know how to download packages that are already installed without removing them and re-installing them again.  My system is working fine, I don't want to mess it up.

---

### Post by celsdogg on 2008-11-18
if you use apt you can specify download only with the -d flag. it then puts them in /var/cache/apt/archives

it would look like this: sudo apt-get install -d <package>

---

### Post by LinuxFox on 2008-11-18
> **celsdogg said:**
> if you use apt you can specify download only with the -d flag. it then puts them in /var/cache/apt/archives

it would look like this: sudo apt-get install -d <package>I just tried that with a SDL package.  I checked the archives and I didn't see it. :(

---

### Post by LinuxFox on 2008-11-18
Looks like I solved my problem about downloading packages.  Check it out, I found a "download only" option in Synaptic I never even noticed before.  I attached a picture, I hope it helps those who just want to "download only" I highlighted what I found.

Anyway, thanks for trying guys. :)  APTonCD reads the downloads, so there should be no problem making the CD.

---

### Post by metallicamike on 2008-11-18
also you can try the link to the source on the bottomof the description of the app in add remove, then  wen firefox opens make sure you set it to prompt you where to download the files. And DO NOT turn on the cd software source, it will not work and make your updates screw up

---

### Post by LinuxFox on 2008-11-18
> **metallicamike said:**
> also you can try the link to the source on the bottomof the description of the app in add remove, then  wen firefox opens make sure you set it to prompt you where to download the files. And DO NOT turn on the cd software source, it will not work and make your updates screw upIt's true you can download, but Ubuntu packages are easier. ;)  Most of the time the sites let you download the source to compile or a different package such as RPM.

Then some come zipped, which are easy. Just unzip and use the software.  I did this with Open Arena, works great! 8)

CD won't mess up, you can uncheck it in the Software Sources if you don't want to use it. ;)

---

