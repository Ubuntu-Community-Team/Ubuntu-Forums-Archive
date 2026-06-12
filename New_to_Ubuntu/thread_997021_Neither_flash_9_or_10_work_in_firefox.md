---
title: "Neither flash 9 or 10 work in firefox"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by waldschm on 2008-11-29
I've searched the forums and couldn't find a good answer so hopefully someone can help me out.

I tried install flash 9 (sudo apt-get install flashplugin-nonfree) and it installed just fine. However flash websites still ask me to download flash and about:plugins shows no flash plugin.

After that, I decided to uninstall 9 and try 10. I tried downloading the .deb file directly from adobe.com but when I attempt to install it says: "dependency is not satisfiable: libcairo2"

Any ideas? I need my youtube!

---

### Post by mikewhatever on 2008-11-29
Which versions of Ubuntu and Firefox do you have?

---

### Post by binbash on 2008-11-29
sudo apt-get install libcairo2 

THEN : 

remove flash player sudo apt-get remove flashplugin-nonfree then install it again.

---

### Post by Olivier2371 on 2008-11-29
Have you tried to look in the addons or plugins in firefox.

---

### Post by Cope57 on 2008-11-29
Make sure your **No-Script** is allowing those flash scripts to run if you have it installed. ;)

---

### Post by Funnnny on 2008-11-29
Maybe you're using 64bit version ?

---

### Post by kodman1113 on 2008-11-29
Have you tried Flash 8? It works for me so it might work for you as well.

---

### Post by cariboo on 2008-11-29
If you are using a 64bit version the new beta Linux only Flash plugin works perfectly.

Jim

---

### Post by waldschm on 2008-11-29
Hey guys, thanks for the quick replies. Sorry if I was a bit vague. I'm using Gutsy + firefox 2 without No-Script (all 32 bit).

Also binbash, I have libcairo installed already
~$ dpkg -s libcairo2
Package: libcairo2
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 832
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libcairo
Version: 1.4.10-1ubuntu4.4

Perhaps I need a different version?

I still don't understand why firefox is not recognizing the flash 9 plugin. Thanks for any help!

---

### Post by gandaran on 2008-11-29
if you are using gutsy you haven't any flash installed, that package is broken, all you have are empty flash folder installed, remove the package you installed and get the tar.gz package from adobe site [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
don't use the .deb package, this package is for newer ubuntu versions

---

### Post by waldschm on 2008-11-29
Thanks gandaran! Just curious, but do you know if there are any plans for a working version in the repository or at least a .deb for the sake of maintainability? Seems a little much to ask newbies to install flash from source.

---

### Post by gandaran on 2008-11-29
> **waldschm said:**
> Thanks gandaran! Just curious, but do you know if there are any plans for a working version in the repository or at least a .deb for the sake of maintainability? Seems a little much to ask newbies to install flash from source.

maybe this will still work, open synaptic and mark the flashplugin-nonfree for complete removal and click the apply button, next click the refresh/ reload button/option, now reinstall the flashplugin- nonfree again, not sure if this still works, it depends if the package is still maintained

---

### Post by gandaran on 2008-11-29
if none of that works you can easyly install the flash package manually
just download the tar.gz package to desktop, unpack/extract the contents, now just drop the libflashplayer.so file in /home/'user'/.mozilla/plugins folder, make the plugins folder, easy!
can also be installed in /usr/lib/mozilla/plugins

---

### Post by oldos2er on 2008-11-29
> **waldschm said:**
> Thanks gandaran! Just curious, but do you know if there are any plans for a working version in the repository or at least a .deb for the sake of maintainability? Seems a little much to ask newbies to install flash from source.

 It isn't source code, it's binaries. Once you've extracted the tar.gz, run ./flashplayer-installer from within its directory.

---

### Post by Eddie.bear on 2008-11-29
Try adding a soft link to the flash plugin shared object to /usr/lib/firefox/plugins


i.e first find libflashplayer.so (on one of my two ubuntu boxes it's in /usr/lib/adobe-flashplugin and on the other it's in /usr/lib/flashplugin-nonfree so have a look there).

Then run
#ln -s <the path you just found> /usr/lib/firefox/plugins/libflashplugin.so

Hopefully that will then work, if it doesn't there are also extension/ or plugin/ folders in various places connected to forefox, try 

$whereis firefox
and
$whereis mozilla

and put similar links in the plugins and/or extensions folders of the paths returned until it works.


Hope this helps

---

### Post by waldschm on 2008-11-29
Eddiebear, this is a fresh ubuntu install so no flash anywhere.

Gandaran and oldos2er, that makes sense but it's still too bad there isn't a convenient repository version.

So I tried reinstalling flashplugin-nonfree from the command line this time and it gave me this error:

[INDENT]```
Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed
```.[/INDENT]

I think since the package downloads direct from [http://fpdownload.macromedia.com/](http://fpdownload.macromedia.com/) that adobe must have released a new version and this package is simply not updated so the md5 doesn't match.

Update: I used the tar.gz file and it works, thanks for the help guys!

---

### Post by kev380 on 2008-12-04
> **gandaran said:**
> if you are using gutsy you haven't any flash installed, that package is broken, all you have are empty flash folder installed, remove the package you installed and get the tar.gz package from adobe site [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
don't use the .deb package, this package is for newer ubuntu versions

I have the same problem he has, but when i go to get the tar.gz thing it wont 
open, I click on it and my mouse does the load thing for half a second then it stops and nothing opens.

---

### Post by gandaran on 2008-12-04
> **kev380 said:**
> I have the same problem he has, but when i go to get the tar.gz thing it wont 
open, I click on it and my mouse does the load thing for half a second then it stops and nothing opens.
right click with the mouse the tar.gz file and choose extract here from the drop down menu

---

### Post by mcloser on 2008-12-05
> **gandaran said:**
> right click with the mouse the tar.gz file and choose extract here from the drop down menu

Thanks for the tip, I've had problems with other tars not openning 'automagically'.

in case anyone else is reading this thread for a flash solution, I had a ******* of a time getting it to work on my instance.  I even upgraded from 7.10 to 8.04 to force it, no luck.  finally I read somewhere that I should rip out every type of flash ( i.e. gnash and adobe flash ) and go back and reinstall the package.  in case any noobs dont know, go into package manger and select the gnash and flash for uninstall and proceed.  then go to the adobe site and download the flash.deb package and it will load.

after 25+ years with os2 and windows I know this would never be as hard on a windoze box but I can't help thinking that there are still way to many barriers to the average user to overcome.  the flash problem has kept me away from using Ubuntu as my my main OS for over a year now. and it is only through frustration that I managed to beat it into submission.

its kind of like getting xp to run on an old 486 laptop.  I've done it but it aint easy.

thanks to all the helpers out there making the Ubuntu experience easier for the lesser propeller heads out there !!!   

*  hava a snow flake - they're free !!

---

