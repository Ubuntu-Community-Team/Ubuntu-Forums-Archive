---
title: "How to install Pixel 1.0 Demo for Ubuntu 8.04 [64-bit]"
date: 2008-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxed on 2008-10-11
Name: Pixel
Version: 1.0 Beta 7 Build 699

Pixel is a RGB, CMYK and HDR image editing, photo retouching, graphics manipulating and animation program available for many operating systems formerly known as Pixel32.  Pixel image editor has been developed by Pavel Kanzelsberger (Banská Bystrica, Slovakia) since 1997 (current version since 2003 after few rewrites) and is still in heavy development.  If you are looking for a good Photoshop alternative for Linux you will definitely want to check out Pixel.

The official Pixel website (kanzelsberger.com) offers a free downloadable demo of Pixel for 32-bit and 64-bit systems.  However 64-bit systems require a few extra steps in order to get it running successfully.  The demo is currently only available as a .tar.bz2 archive so this guide will walk you through creating and installing a Pixel deb package on 64-bit systems.  As a time saver you may want to simply copy and paste the text from the code boxes below directly into your terminal window.

Before continuing you will need to download the following files.  Make sure to download them to your desktop as the steps below assume that these files can be found in your desktop folder.

[_Pixel demo_](http://www.kanzelsberger.com/download.php?id=a3fc72f9e89216dc2f7d038a80f4776a)
[_libopenexr6 32-bit_](http://mirrors.kernel.org/ubuntu/pool/main/o/openexr/libopenexr6_1.6.1-3ubuntu1_i386.deb)
[_libaspell15 32-bit_](http://mirrors.kernel.org/ubuntu/pool/main/a/aspell/libaspell15_0.60.5-1ubuntu2_i386.deb)
[_libilmbase6 32-bit_](http://mirrors.kernel.org/ubuntu/pool/universe/i/ilmbase/libilmbase6_1.0.1-2_i386.deb)


[list=1]
[*]First off, install the ia32-libs package if it's not already installed.
```

sudo apt-get install ia32-libs

```
[*]Change to your Desktop folder.
```

cd /home/YourUserName/Desktop

```
[*]Type the following (one line at a time):
```

mkdir -p ./pixel/usr/lib
mkdir -p ./pixel/DEBIAN
mkdir -p ./pixel/usr/share/applications
mkdir -p ./pixel/usr/lib32
tar -xf pixeldemo-1.0.699-linux.x86-64cmpt.tar.bz2 --directory=./pixel/usr/lib
dpkg-deb --extract libaspell15_0.60.5-1ubuntu2_i386.deb libaspell
dpkg-deb --extract libopenexr6_1.6.1-3ubuntu1_i386.deb libopenexr
dpkg-deb --extract libilmbase6_1.0.1-2_i386.deb libilmbase
cp -P ./libopenexr/usr/lib/* ./pixel/usr/lib32
ln -s /usr/lib32/libIlmImf.so.6.0.0 ./pixel/usr/lib32/libIlmImf.so.4
cp -P ./libaspell/usr/lib/libaspell.so.* ./pixel/usr/lib32
cp -P ./libilmbase/usr/lib/* ./pixel/usr/lib32

```
[*]Now we need to create the control file for deb package.  Type the following:
```

gedit ./pixel/DEBIAN/control

```
[*]Copy the following text and paste it into gedit.  You may want to replace the name and email address on the Maintainer line with your own name and email.
```

Package: Pixel
Version: 1.0b7.699-1
Architecture: all
Maintainer: Your Name <yourname@yourdomain.com>
Installed-Size: 35328
Section: graphics
Priority: extra
Description: A cross-platform image editor.
  Pixel image editor has been developed by Pavel Kanzelsberger
  (Banská Bystrica, Slovakia) since 1997 (current version since
  2003 after few rewrites) and is still in heavy development.
  Final stable product will be released in 2008.

```
[*]Click save and close gedit.
[*]Now we're going to create an applications menu entry for Pixel.  Type the following:
```

gedit ./pixel/usr/share/applications/pixel.desktop

```
[*]Copy ALL of the following text and paste it into gedit.
```

[Desktop Entry]
Version=1.0
Name=Pixel
Comment=Image editor
GenericName=Image editor
Exec=/usr/lib/Pixel/pixel
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/usr/lib/Pixel/pixel32.png
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
MimeType=image/gif;image/jpeg;image/png;
StartupNotify=true

```
[*]Click save and close gedit.
[*]Type the following to build the package.
```

dpkg-deb --build pixel

```
[*]You can now click on the pixel.deb package to install it or type the following:
```

sudo dpkg -i pixel.deb

```
[*]Before running Pixel for the first time you need to make sure that all of the required libraries are installed.  Type the following:
```

ldd /usr/lib/Pixel/pixel

```
[*]Scroll through the list of libraries and make sure that none of them say 'not found'.  As long as none say 'not found' you should now be able to open Pixel from your Applications > Graphics menu.
[/list]


If any libraries are listed as 'not found' then you'll need to manually install the missing library in your /usr/lib32 folder.  [_You can perform a package contents search here._](http://packages.ubuntu.com/search?suite=hardy&section=all&arch=any&searchon=contents&keywords=libnss3.so.1d)  Enter the name of the missing library and then search for a package that contains it.  When you've found the correct package download the i386 version and use file-roller to extract the missing library from the package into your /usr/lib32 folder.


**To uninstall this package simply type the following:**
```

sudo apt-get remove pixel

```

---

### Post by corvx on 2008-12-19
does this work for intrepid 64-bit?

edit:
I tested this on intrepid, when I run the .deb everything seems to run smoothly, and it even says it was installed, but then no files are created, at least not where they were supposed to be created, for example i can't "ldd /usr/lib/Pixel/pixel", and when run directly by clicking pixel.deb, the "Install Package Button" becomes available again, instead of the reinstall one.

---

### Post by NickWilsdon on 2009-01-21
I've just followed these instructions and successfully installed the full (paid) 64 bit version of Pixel on 8.10 Intrepid. 

All seems to be working - thanks linuxed!

@corvx

I also noticed the package only says "install" rather than "reinstall" but there was an output from ldd /usr/lib/Pixel/pixel

---

### Post by red_team316 on 2009-05-03
I'd like to say that this works fine on 64-bit Jaunty 9.04 also.

Too bad Pixel still hasn't released 1.0 final still, it was supposed to be released on April 30th :(

---

### Post by FaceLeg on 2009-05-08
Great guide, thanks.  Worked for me: Jaunty 64.

EDIT: yeah great guide - Pixel froze 3 minutes into my first play, heh.

---

### Post by Mikael P. on 2009-07-06
Thanks for that guide! Worked fine on my 64 bit 9.04 jaunty.

---

### Post by aspergerian on 2009-09-15
The original downloads are on my desktop. 

I entered:

sudo apt-get install ia32-libs


And got this response: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

Teresa

---

### Post by aspergerian on 2009-09-15
I'm trying to install onto a HP Mini netbook running Hardy Heron. 


> **aspergerian said:**
> 
sudo apt-get install ia32-libs

Generated this response: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs


---

### Post by Mikael P. on 2009-09-15
But it's available in synaptic. Can't you install from there?

---

### Post by linuxed on 2009-09-15
Here's a list of mirrors for the ia32-libs package.  Just download the package and then click on it to begin the installation.

[http://packages.ubuntu.com/hardy-updates/amd64/ia32-libs/download](http://packages.ubuntu.com/hardy-updates/amd64/ia32-libs/download)

Alternatively, you might want to double check your sources.list file and make sure that none of the source urls are commented out.
```

sudo gedit /etc/apt/sources.list

```
Remove the "#" symbol from any line that contains a url, click save and close gedit.  Then type:
```

sudo apt-get update

```

---

### Post by dsmithnc on 2009-11-19
Thanks so much for those clear and concise directions.  I took a flyer and installed Pixel on Karmic 64bit and everything worked as advertised.  Now I just have to learn the program.

One question, is there a way to access smb shares in Pixel.  Karmic sees my network drives with no problem, but I can't see them in the file manager in Pixel.  Not a deal breaker but would be nice.

And I do realize this is the Ubuntu Forum and not Pixel.  I guess the question was more rhetorical than anything else.

Thanks again,

Dick SMith

---

