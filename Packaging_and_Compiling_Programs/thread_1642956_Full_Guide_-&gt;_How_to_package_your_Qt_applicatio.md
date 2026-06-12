---
title: "Full Guide -&gt; How to package your Qt application and include it in ubuntu!"
date: 2010-12-11
forum: Packaging and Compiling Programs
---

### Post by hakermania on 2010-12-11
**THIS GUIDE IS OUTDATED**

Tutorial: How to package and upload an application for Ubuntu

In this tutorial, a Qt project will be used as an example named Wallpaper Changer (wallch). The purpose of it is to make it easier to the newbies (like me) on how they can package and upload their package into ubuntu for inclusion into the Ubuntu Software Center. Any corrections are welcome, because as I said I am a newbie and some errors are expected to exist. But that's what I did, after a lot of search in the internet and after a lot hanging around at the IRC channels #ubuntu-packaging and #ubuntu-motu ! So, if you notice an error or two, please don't hesitate to mention it!

You will need the following if you want to follow this tutorial with your own app:
[I]1. devscripts
2. debhelper
3. gnupg-agent
4. dput
5. lintian[/I]
6. Maybe something else, if while following this tutorial you realise that you need something more please let me know to add it.

Ok, let's start. We will consider that you have your project fully made and is working perfectly!


_**STEP 1:**_

Take your source code and place it in a folder named <project-name>-1.0 where <project-name> is the name you want to give to your package. I chose '-1.0' considering that this is the first application you make and that's why you need to use this tutorial. If you want to use another extension except from '-1.0' there is no problem, just remember to replace it if in the text following the string '1.0' appears.

_**STEP 2:**_

Remove from your source code any files that are not really useful for compiling the source (DO remove the Makefile, DO NOT remove the .pro file! You MUST remove any possible .o files, the executable, and the .pro.user file, while being in your source code folder, you can give 'make clean', this will delete most of the files that you don't need, if anyone left, delete it by hand). So, basically, put all your source code in a folder and clean it, keep only the very needed files for compilation plus the .pro file, which will be needed in the following steps.
[U][B]
STEP 3:[/B][/U]

Make 'make install' to work and fully install your application in your PC.
This isn't as scary as it seems to be. You must edit your .pro file in order to do this. First of all you must now that you must have the following files placed in the system: /usr/share/doc/<package-name>/changelog.gz  /usr/share/doc/<package-name>/copyright and some other files that will be explained soon. In order to place these files you can create in your source directory a folder named 'data'. There for example you can create some subdirecotires named 'man' doc' 'config' etc. then your .pro file (as I will show you how to edit it) will take these files from the 'data' folder and will place them into the system.
Analitically the files that have to be placed into the system are (I will analyze each one separately later):
/usr/share/doc/<package-name>/copyright
/usr/share/doc/<package-name>/changelog.gz
/usr/share/applications/<package-name>.desktop
/usr/share/man/man1/<package-name>.1.gz

So, in your 'data' folder you can create the folders man/ doc/ or anything else you think that you need to place inside the system (like a folder that you need to place at /usr/share/ which has your scripts etc.) Inside these folders you must place the pre-mentioned files. Let's see them analitically:
/usr/share/doc/<package-name>/copyright:
This is an example of this file:
```
This work was made for Debian by:

    Your full name <your real email> on Wed, 27 Oct 2010 19:47:13 +0300

Upstream Author(s):

    Your friend's name <your friend's real email>
    Your full name <your real email>

Copyright:

    <Copyright (C) 2010 Your full name>
    <Copyright (C) 2010 Your friend's name>

License:

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This package is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program. If not, see <http://www.gnu.org/licenses/>.

On Debian systems, the complete text of the GNU General
Public License version 3 can be found in "/usr/share/common-licenses/GPL-3".

The Debian packaging is:

    Copyright (C) 2011 Your full name <your real valid email>

and is licensed under the GPL version 3, see above.
```As GPL license 3 you can use every license you want or prefer. It is very important to place in your source code folder a file usually named COPYING that includes the License. GPL liceses can be found at [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)

Ok, let's procceed to the next file:
/usr/share/doc/<package-name>/changelog.gz:
This file is compressed via terminal using 'gzip -9 changelog'. So, before the file is zipped (if you want to edit it you can unzip it using unzip changelog.gz) was like this:
```
wallch (1.0-0ubuntu1) natty; urgency=low

  * Initial Release. (LP:: #677794)

 -- Your full name <your full email>  Thu, 28 Oct 2010 11:03:40 +0300
```As you see it says: LP: #677794
This means that you have to go to Launchpad and create a new project with your <project-name> and create a bug report named "needs-packaging". Changelog will close this bug report using its number as shown above! changelog file doesn't have to be inside the data/ folder. it will be automativally created at STEP 6, and then you can edit it as you can see above. Then , by editing the .pro file you will move it at usr/share/doc/<project-name>/ and you will 'gzip -9' it.

Ok, let's procceed to the next file /usr/share/applications/<package-name>.desktop
It is the shortcut of your application. This file will show the system what the program is (Utility, Internet tool etc) and will place it in the appropriate section at the Ubuntu Menu. This is an example of this file:
```
[Desktop Entry]
Version=1.0
Name=Wallpaper Changer
GenericName=Wallpaper Changer
Comment=Change your desktop wallpapers whenever you want!
Icon=/usr/share/WallpaperChanger/wallpaper.png
Exec=wallch
Terminal=false
Type=Application
Categories=Qt;Utility;

```I think all of the above are pretty easy to understand, the field categories: ( Categories=Qt;Utility; ) will place the application at the 'Accessories' field of the Ubuntu Menu with the icon (Icon=) /usr/share/WallpaperChanger/wallpaper.png and with the comment (when cursor moves above it) (Comment=) "Change your desktop wallpapers whenever you want!"

The next file /usr/share/man/man1/<package-name>.1.gz is the manpage of your program. It is compressed with 'gzip -9 <package-name>.1' but prior to this it was like this:
```
.TH WALLCH 1 "27 Oct 2010"
.SH NAME
\fBwallch\fP \- Wallpaper Changer for the GNOME Desktop

.SH SYNOPSIS
.B wallch
A program that changes your PC's look every once in a while
by changing your Desktop Wallpaper using your preferable
pictures and your preferable time! It supports 2 types of
notification: sound and simple and has a lot more functions!
.SH BUGS
If you find a bug, please report it at your full email or at your friends full email
.SH AUTHORS
You friends name (your friends email)
.TP
Your name (your full email)
```I know that this is a quite simple manpage but I don't have purpose to analyze it more.

(note: the manpage and the changelog must be zipped with 'gzip -9')

Ok, now your source code dir should contain: the COPYING file. It will contain your preferable lisence (like GPL3), an 'unistall' file. This file will be unix script. It will unistall the program(remove the manpages, the doc/<package-name> the .desktop file etc). A README file. It will contain everything you want. I recommend to write there that to install the program you must be root and type 'make install' (you can't do this yet but you will, after editing the .pro file). You must also refer to the unistall file and the COPYING. It is good to contain an email address that someone can contact. So the 3 files you need are: COPYING, unistall (this at your own option), and README. If you want you can have an AUTHORS file and more. But I think that these 3 are essential. As mentioned before, you will need a 'data' folder in your source code. There you can place the manpage, the folder that has go to /usr/share/doc/ and the files inside it, the shortcut file etc. Now, it's time to edit the .pro file that Qt provides you in order to place the files in the appropriate location of the system. That's an example on how you have to edit the .pro file:
```

######################################################################
# Automatically generated by qmake (2.01a) Sat Nov 6 23:20:34 2010
######################################################################

TEMPLATE = app
TARGET =
.... etc etc
...
...
..
. etc etc etc
(Here is at the end of the .pro file, so, at the end of the .pro file place the following (edit them so to be efficient with your package)
unix:configfiles.extra = chmod +x data/config/WallpaperChanger/Scripts/*; make clean; mv -f wallch-1 wallch
binfile.files += wallch
binfile.path = /usr/bin/
configfiles.files += data/config/*
configfiles.path = /usr/share/
docfiles.files += data/doc/*
docfiles.path = /usr/share/doc/
manfiles.files += data/man/*
manfiles.path = /usr/share/man/man1/
shortcutfiles.files += data/wallch.desktop
shortcutfiles.path = /usr/share/applications/
INSTALLS += configfiles
INSTALLS += docfiles
INSTALLS += manfiles
INSTALLS += shortcutfiles
INSTALLS += binfile

```Ok, so, let's see it line by line:
```
unix:configfiles.extra = chmod +x data/config/WallpaperChanger/Scripts/*; make clean; mv -f wallch-1 wallch
```this line is quite special. by using "unix:NAME.extra =" means that you need do something more. In this occasion to make all the scripts in the data folder executable and renamed the generated executable from wallch-1 to wallch (in the following steps you will see that this code will run after compiling the source code, so don't worry if you realise that in a previous step I said to remove the executable). You can place your own commands there. The other rows are quite understandable. You set the file and their destination. It is important to place here commands (like 'make clean') that will remove the uneeded files (.o files etc).

Ok, after this step is done, you'll have actually created you source tarball with a working Makefile!
You have your source code, a readme file, a Makefile etc! If you want you can now give 'make install' (while being root).
Your source code will be compiled and then the makefile will execute what the .pro file tells it. So, you executable will be first created and the Makefile will place it at /usr/bin/. Also the Makefile will place the manpages where they have to be, the shortcut file in its position etc! Also, if you have made an unistall file, by giving ./unistall you can unistall you application by removing all these files! So you are halfway now!

Ok, now, remove any uneeded file from your source code. Any executable .o file .pro.user file or anything else uneeded. The folder must be look like any else "extracted" tarball before giving 'make install' :)

_**STEP 4:**_

Create a tarball of your source directory, beside your source directory. The file must be <package-name>-1.0.tar.gz

_**STEP 5:**_

Go and have a GPG key! There are plently of instructions in the internet on how to get your GPG key. IMPORTANT: Once you get your GPG key, go and set it to your username in Launchpad! ([https://launchpad.net/~USERNAME/+editpgpkeys]("https://launchpad.net/%7EUSERNAME/+editpgpkeys")). So, to make you understand why this is important, to make a login to launchpad you'll need an OPENID, the same you'll need to login to REVU ([http://revu.ubuntuwire.com/](http://revu.ubuntuwire.com/) is the place where the packages go for review). So, you set your GPG key to launchpad and when you upload your package (signed with your GPG key) REVU will understand that it is yours. Simple.

_**STEP 6:**_

Once you have a working GPG key, and you have set it to launchpad, cd to your source directory and run:
```
dh_make -c gpl -s -f ../<package-name>-1.0.tar.gz
```Where <package-name>-1.0.tar.gz is the tarball you created at STEP 4. It will show you a name and an email address. Be sure that these 2 are your real name and your real address you that you have set to your GPG key. Hit enter when prompted.

_**STEP 7:**_

A <package-name>_1.0.orig.tar.gz will be created beside the <package-name>-1.0.tar.gz, and a /debian directory will be created inside your source code.
cd to the debian/ directory and give 'rm *ex *EX README*'. This will remove all the unecessary files. If you want, you can remove the copyright file, if you have placed them into the data/doc/ folder or somewhere else and then you place it from the .pro file at /usr/share/doc. changelog file must be there. See the example above to see how it has to be.

_**STEP 8:**_

Edit the control file. This is an important step. this is an example of a control file:
```
Source: wallch
Section: utils
Priority: optional
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
XSBC-Original-Maintainer: YOUR FULL NAME <YOUR REAL EMAIL>
Build-Depends: qt4-qmake, libqt4-dev, debhelper (>= 8)
Standards-Version: 3.9.1
Homepage: http://www.wallch.t35.com

Package: wallch
Architecture: any
Depends: sed (>=4.2.1), grep (>=2.6.3), mpg321, imagemagick, libnotify-bin, ${shlibs:Depends}, ${misc:Depends}
Description: Change Desktop Wallpapers automatically!
 You can select pictures from your hard drive and start 
 changing desktop wallpapers automatically, giving you 
 the opportunity to set the delay, the desktop or sound 
 notification. Also it allows you to select your own sound
 on sound notification, to start changing wallpapers on 
 start-up once or concurrently and also to enable the 
 Live Earth Wallpaper feature, which sets as Desktop 
 Background a wallpaper of the earth as it is now.
 Additionally, the program provides: History logging - when 
 pictures changed and with what options. Properties of 
 image - image size, dimensions, type etc. Deletion of image 
 from hard disk. Random image changing from the selected ones.
 Changing images on random time.
 The program is designed for Ubuntu Linux (GNOME Desktop)
```Note: The first line in description: "Change Desktop Wallpapers automatically!" will be shown outside of the program, below its name, the other description will be shown after clicking "more info". Note that the description must not be like an advertisement. It should not contain words like cool, fantastic etc.

_**STEP 9:**_

Create the debian/watch file. You must upload your source code in a site, like sourceforge, so to provide your tarball (created at step 4). This is how it is like:
```
version=3
http://sf.net/wall-changer/wallch-(.+)\.tar\.gz

```Note: version field MUST be 3.

_**STEP 10:**_

Edit the 'rules' file, if needed. A rules file can be very complicated, but in my situation is very simple, because in order to build the source I use debhelper. So, my rule file looks like this:
```
#!/usr/bin/make -f

%:
        dh $@

```Debhelper knows how to install Qt projects. So, if you have a working Makefile and you use debhelper in order to build your source (and you have included at the Build-Depends field of the control file), you don't need to do something else.

_**STEP 11:**_

Debuilding!
After you have done all the things needed, you have to debuild your source code!
cd to your source directory (which must be always clean from uneeded files) and give 'debuild'
If you don't get an error you will be very lucky. In case you get an error try to solve it and try again 'debuild'.
Once the debuild command run without outputing errors about your source code it will prompt for a password. It is the password with which you have set your GPG key, so it need it in order to sign the files. So, give it without any fear. All necessary files will be created beside your source code's folder.
[U][B]
STEP 12:[/B][/U]

Perform a check of your files!
While being in your source give 'lintian -I ../*deb ../*dsc ../*changes'. This will check these files for errors. Propably it will output some. Try to solve them and give again 'debuild'. When lintian doesn't outputs none error, check you .deb file. install it manually. Check if the program installs well and the files are in their position inside the system. Once you've done with checking, while being root give 'apt-get remove <package-name>' to remove your package.
Note: If you need to place some files in /home/$USER/.config/ you must place them at /usr/share first and then COPY and not MOVE them to /home/$USER/.config on first application run!

_**STEP 13:**_

This is the final step! In order to do this you must: a) Have signed your files with the GPG signature that you have set in the Launchpad b) Have a username in REVU with the same OPENID you use to login in Launchpad c) Internet connection
Ok, cd in your source code and give 'dput revu ../*changes' This will check the signature on each file separately and will upload the neseccary files to REVU. In 3-4 minutes you'll see your package on the Needs-Review section of revu. If you realise that you have an error in your package, or REVU says that you have errors in your package that have to be corrected, debuild again your package after doing the changes you were told to, and use 'dput -f revu ../*changes' to upload the changed package to REVu again. 


That's all, good luck!

---

### Post by alenn on 2012-07-04
is there any app for this. I'm trying to do all of this for a week and can't package my app

---

### Post by airglide on 2013-01-26
great guide, thank you very much,

maybe something isn't clear:

you want to run (to create a makefile)

```
qmake
```before giving

```
sudo make install
```

---

### Post by Malsasa on 2013-03-02
Hey TS, where is +reputation button for you? It is so good tutorial. Thank you. I have CTRL+S'ed this page. You have explained it step by step, every newbie need it. 

Keep you works easily readable :)

---

