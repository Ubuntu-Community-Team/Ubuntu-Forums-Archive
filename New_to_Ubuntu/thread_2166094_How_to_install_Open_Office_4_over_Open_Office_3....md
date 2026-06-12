---
title: "How to install Open Office 4 over Open Office 3..."
date: 2013-08-07
forum: New to Ubuntu
---

### Post by rrmtwo on 2013-08-07
Using 12.04 and have Open Office 3 installed.  Have tried many times and ways to install Open Office 4, but it never takes.  Help!

Thank You...

---

### Post by GwL3eNC on 2013-08-07
if you haven't done yet, download the oo4 deb file from [http://www.openoffice.org/download/index.html](http://www.openoffice.org/download/index.html),
normally it goes to your downloads folder.

After that open a terminal (CTRL+ALT+T or use the menu). From your home directory type

cd Downloads

If you are in type

sudo dpkg -i PACKTENAME.DEB

repalce PACKTENAME.DEB with the name of the OO4 deb file and press enter. If something goes wrong,
post the output here. Hopefully someone can help.

---

### Post by rrmtwo on 2013-08-07
> **GwL3eNC said:**
> if you haven't done yet, download the oo4 deb file from [http://www.openoffice.org/download/index.html](http://www.openoffice.org/download/index.html),
normally it goes to your downloads folder.

After that open a terminal (CTRL+ALT+T or use the menu). From your home directory type

cd Downloads

If you are in type

sudo dpkg -i PACKTENAME.DEB

repalce PACKTENAME.DEB with the name of the OO4 deb file and press enter. If something goes wrong,

post the output here. Hopefully someone can help.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Thanks for the reply, 

Do I put the whole .deb file name in as it's named on the download?   Apache_OpenOffice_4.0.0_Linux_x86_install-deb_en-US.tar.gz 

Thanks again

---

### Post by deadflowr on 2013-08-07
Firstly, You need to uninstall the earlier openoffice version(3).
So what method did you use to install it? deb or PPA.

then when that done.
Open the download folder and double click on the tar,gz file for openoffice.
Archive manager will open click "extract".
the files will extract whwereever you tell it to, by default that is the downloads folder(but you can place them anywhere.
Hit enter and let them get extracted.
You should get a folder (in the US it's en-us, but other places are different)
Inside the en-us(or whatever it's called) are more folders, look for the one called DEBS.
This is where the files you will need to install are.
There will be one folder called desktop-intregration and a bunch of openoffice-something.deb files.

If you went with the normal extraction and simply extracted the folder/files into the Downloads
in a terminal change the directory to the DEBS folder.
```
cd /home/user/Downloads/en-us/DEBS
```
then run
```
sudo dpkg -i *.deb
```
The * will install all packages with the .deb attached.
When the finishes installing, and hopefully it installs without errors, change directories again by running
```
cd desktop-integration
```
this puts you into the desktop integration folder in the DEBS folder.
run the dpkg -i *.deb command again and when finished, error-free, openoffice will be installed.

But it is super important that you uninstall any earlier version as they can cause problem during the install.

---

### Post by rrmtwo on 2013-08-08
Thank You...It worked!

---

