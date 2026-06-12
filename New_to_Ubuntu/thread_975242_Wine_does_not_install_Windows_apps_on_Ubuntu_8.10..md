---
title: "Wine does not install Windows apps on Ubuntu 8.10..."
date: 2008-11-08
forum: New to Ubuntu
---

### Post by resander on 2008-11-08
It did on Ubuntu 8.04. I successfully installed and used a Windows music application with GUI, images, animation and sound.

I installed Wine 1.0.1 on 8.10 using Applications->Add/Remove. The preinstalled (in Wine) Notepad Windows application worked, but got the following error when installing the music application:    

"End-of-central-directory signature not found.  Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive.  In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
note:   the .exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory...."

The Windows exe file is a self-extracting zip file, so I downloaded and installed 7zip and tried installing the music app again. Got a different error message output by 7zip:

"Error: exe file is not supported archive".

I also tried installing Visual C++ 6.0 (also a self-extracting exe file), but got the same error message, so it looks as if 7zip cannot do the unzipping or should not be used at all for this.

I downloaded lots of codecs, flash, java etc via Debian/Synaptic for Ubuntu 8.04, but I don't remember the details. It is quite possible I unknowingly downloaded zip support that helped Wine unzip and install Windows apps. Any idea what this might be? Or is the cause entirely different?

---

### Post by bodhi.zazen on 2008-11-08
Wine is not a drop in replacement for windows and in my experience takes a lot of attention and tweaking.

Your best source of information is winehq, search the database for your applicaion(s)

[http://www.winehq.org/](http://www.winehq.org/)

In addition wine is, IMO, very much in alpha or even pre-alpha development. Each "version" is nothing more then a snapshot and wine often goes through "regression" ie what works with one version of wine stops working with subsequent versions. For this reason, when you are following a how to you need to pay attention to host OS and the exact version of wine.

With that said, wine works fine for "simple" applications, but not so good for complex applications.

---

### Post by resander on 2008-11-08
I installed Wine version 1.0 on Ubuntu 8.04 and it could install Windows applications. 

According to winehq (at [www.wine.org](www.wine.org)) Wine version 1.0.1 is a maintenance version with only minor bug fixes to 1.0. It is unlikely these would stop the Fundamental function of installing Windows apps. And how could such a monumental clanger go undetected during testing? It is more likely the problem is the installer (me!), or in the installation infrastructure or lack of components needed by Wine. The unzip function called by .exe self-extracting file might not have been installed properly or gone missing (maybe some access paths have changed???).

I have seen other users having similar problems.

Hints would be most welcome.

---

### Post by Kellemora on 2008-11-08
Hi Resander

I've hit the same problem, only in Hardy 8.04 with some files I needed.

First of all, if a file is zipped, I explode it on a DOZE machine into a folder within the shared folder on the DOZE machine.
Don't try to explode it to a shared folder on your Linux box, nor try to move it from the Doze machine TO the Linux box.
Instead, go to your Linux box and Fetch the file from the shared folder on the Doze box.  (Don't know why but it save mucho problems doing it this way, probably permission problems).
AFTER you have placed the folder on your desktop or wherever on your Linux box, highlight and COPY that folder.
I will then go into the .wine folder, to the Drive_C folder and PASTE the folder into the Drive_C folder, often within a folder named NotInstalledPrograms.  I will then make the installation folder, however, in Wine you often cannot get to those folders and they become useless and need to be deleted later, since they are empty.
The problem is, the INSTALL program running in Wine will show your Linux Directory and NOT your Drive_C directory, so you are STUCK letting it install the program to the folder name IT CHOOSES.
Once you've done this, just look for the setup.exe file and you should be home free.
IF there is NO setup.exe file or Install.exe file, there's a good chance it won't run in WINE anyhow.
WINE seems to work BEST with programs that do NOT require installing or setup, they run from their own .exe file.  If so, make sure all the dependencies and .dll's are in the folder you run the .exe from.

Hope that helps!

TTUL
Gary

---

### Post by resander on 2008-11-09
Hi Kellemora,

Many Thanks for suggesting unzipping the installation file before doing the setup using Wine. That would work fine for .zip archives using utilities such as winzip or 7zip on a Windows PC.

The program I really need, Visual C++ version 6.0, has a setup.exe file that is already unpacked (it is not a self-extracting file actually). It is a tailor-made program that knows where to find the parts needed on the installation media and how to use them to make the application on the PC. Some of the parts no doubt are packed, but I don't know what/where they are and how they are packed. So cannot do any unpacking before handing over to Wine.

If anyone has managed to install Windows applications using Ubuntu 8.10 with Wine 1.0.1 please let me know how - and I will imitate!

---

### Post by resander on 2008-11-09
With a little bit of luck, figured it out...

Double-clicking on the setup.exe file opens the file with the Ubuntu Archiver. That's wrong.
It is necessary to right-click the .exe file and then select 'Open with "Wine Program loader"' from the popup menu. Don't remember doing that when on 8.04 and don't remember reading about it.

The install of the music application worked, the install of VC6 started but exited when clicking 'Next' on the wizard install menu (don't know why yet).

---

### Post by Kellemora on 2008-11-09
Hi Res

Some WinDOZE programs make machine calls outside of the API, usually this is games that do this most often, but also programs like QuickBooks and a few others.  
So, what it boils down to is if any program, large or small, short or tall, tries to make a call outside the API, it can't be run in Wine.

Just something to keep under your hat for when a seemingly simple program just flat out won't run in Wine!

TTUL
Gary

---

