---
title: "install tarball"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by stubblepoo on 2008-07-10
when following this tutorial: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

i get as far as ./configure which fails as neither of the folders have a configue txt in them, they both have 'install' and 'makefile' in them, how do i install them?

---

### Post by roquefilipe on 2008-07-10
what error does ./configure report? 

To compile most tarballs its just matter of 

./configure   -check and prepare your system for dependencies, etc
make  - actual compiling
sudo make install -copy files to system directories

---

### Post by iaculallad on 2008-07-10
> **stubblepoo said:**
> when following this tutorial: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

i get as far as ./configure which fails as neither of the folders have a configue txt in them, they both have 'install' and 'makefile' in them, how do i install them?

First: Install the build-essential file:

```
sudo apt-get install build-essential
```

Extract the Tarball and:

cd Tarball_Extracted_Directory

```
./configure
./make
./install

```

NOTE: Usually, tarballs comes with Install file. Try to read the install file w/c comes with the extracted tarball.

---

### Post by rxtx on 2008-07-10
[This]("http://ubuntuforums.org/showthread.php?t=846921") thread might help you out.

The software may just need a "make" followed by "sudo make install" to do the trick.

Which package are you trying to install? Have you checked the install instructions or the README? :)

---

### Post by Paqman on 2008-07-10
Are you sure there isn't a .deb available? Compiling from source should be a last-ditch measure. If you absolutely *have* to compile something, make sure you use checkinstall so that you can remove it easily later.

---

### Post by stubblepoo on 2008-07-10
src/Main.cs ./src/Gib.cs ./src/AssemblyInfo.cs ./src/Functions.cs ./src/Theme.cs ./src/Preferences.cs ./src/NewTheme.cs ./src/About.cs ./src/ThemeBrowser.cs ./src/EditCategories.cs \
	&& mkdir build && mv "gib.exe" ./build/. && cp -r ./resources/* ./build/.
/bin/sh: mcs: not found
make: *** [gib.exe] Error 127
 

this is the error i get

---

### Post by bumanie on 2008-07-10
Copy and post the installation instructions - then someone may be able to help.

---

### Post by stubblepoo on 2008-07-15
kiran@kiran-laptop:~$ cd /usr/local/src/gib-0.2-src
kiran@kiran-laptop:/usr/local/src/gib-0.2-src$ sudo apt-get install build-essential
[sudo] password for kiran: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kiran@kiran-laptop:/usr/local/src/gib-0.2-src$ make
mcs  -target:exe -out:"gib.exe" -pkg:gtk-sharp -pkg:glade-sharp -r:System.dll ./src/Main.cs ./src/Gib.cs ./src/AssemblyInfo.cs ./src/Functions.cs ./src/Theme.cs ./src/Preferences.cs ./src/NewTheme.cs ./src/About.cs ./src/ThemeBrowser.cs ./src/EditCategories.cs \
	&& mkdir build && mv "gib.exe" ./build/. && cp -r ./resources/* ./build/.
/bin/sh: mcs: not found
make: *** [gib.exe] Error 127
kiran@kiran-laptop:/usr/local/src/gib-0.2-src$ 

 that is all

---

