---
title: "Cannot install Libre Office 3.6.2.2"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by m3ideh on 2012-10-12
The readme on how to install LibreOffice 3.6.2.2 says this:

"This directory contains a subdirectory called "DEBS". Change directory to the "DEBS" directory.

Right-click within the directory and choose "Open in Terminal" "

however when I open the DEBS folder and right-click i don't see any option called 'open in terminal'

also, it asked me to do all this in 'file manager' and to 'change directories' and stuff like that

I dont know what changing the directory is and is the file manager the home folder?

BTW i HAVE gotten rid of the old version of Libre Office first.





-Im using ubuntu 12.04 through Dual-Boot on my windows 7 Laptop

--system specs--

-nvidia gt540m 2gb
-2nd gen i5 2.9 ghz
-8gb RAM
-750gb hard drive

please help me out since i have work that needs to be done

thanks for your helps in advance

[EDIT]

here are the contents of the readme file:
(down below)









======================================================================
LibreOffice 3.6 ReadMe
======================================================================


For latest updates to this readme file, see [http://www.libreoffice.org/welcome/readme.html](http://www.libreoffice.org/welcome/readme.html)

This file contains important information about the LibreOffice software. You are recommended to read this information very carefully before starting installation.

The LibreOffice community is responsible for the development of this product, and invites you to consider participating as a community member. If you are a new user, you can visit the LibreOffice site, where you will find lots of information about the LibreOffice project and the communities that exist around it. Go to [http://www.libreoffice.org/](http://www.libreoffice.org/).

Is LibreOffice Really Free for Any User?
----------------------------------------------------------------------

LibreOffice is free for use by everybody. You may take this copy of LibreOffice and install it on as many computers as you like, and use it for any purpose you like (including commercial, government, public administration and educational use). For further details see the license text packaged with this LibreOffice download.

Why is LibreOffice Free for Any User?
----------------------------------------------------------------------

You can use this copy of LibreOffice free of charge because individual contributors and corporate sponsors have designed, developed, tested, translated, documented, supported, marketed, and helped in many other ways to make LibreOffice what it is today - the world's leading Open Source productivity software for home and office.

If you appreciate their efforts, and would like to ensure that LibreOffice continues to be available far into the future, please consider contributing to the project - see [http://www.documentfoundation.org/contribution/](http://www.documentfoundation.org/contribution/) for details. Everyone can make a contribution of some kind.

----------------------------------------------------------------------
Notes on Installation
----------------------------------------------------------------------

LibreOffice requires a recent version of Java Runtime Environment (JRE) for full functionality. JRE is not part of the LibreOffice installation package, it should be installed separately.

System Requirements
----------------------------------------------------------------------

As a general rule, you are recommended to install LibreOffice via the installation methods recommended by your particular Linux distribution (such as the Ubuntu Software Center, in the case of Ubuntu Linux). This is because it is usually the simplest way to obtain an installation that is optimally integrated into your system. Indeed, LibreOffice may well be already installed by default when you originally install your Linux operating system.

This "stand-alone" LibreOffice installer is provided for users in need of previews, having special needs, and for out-of-the-ordinary cases.

* Linux Kernel version 2.6.18 or higher;
* glibc2 version 2.5 or higher;
* gtk version 2.10.4 or higher;
* Pentium compatible PC (Pentium III or Athlon recommended);
* 256 MB RAM (512 MB RAM recommended);
* Up to 1.55 GB available hard disk space;
* X Server with 1024x768 resolution (higher resolution recommended), with at least 256 colors;
* Gnome 2.16 or higher, with the gail 1.8.6 and the at-spi 1.7 packages (required for support for assistive technology [AT] tools), or another compatible GUI (such as KDE, among others).

There is a wide variety of Linux distributions, and there may be different installation options (KDE vs Gnome, etc.) available from the same Linux vendor. Some distributions ship with their own &#8220;native&#8221; version of LibreOffice, which may have different features from this community-supplied version of LibreOffice. In many cases, you can install the community-supplied LibreOffice alongside a native version. However, you may prefer to remove the &#8220;native&#8221; version before installing this community-supplied version. For details on how to do that, please consult the user help resources provided by your particular Linux vendor.

It is a recommended best practice to back-up your system and data before you remove or install software.

Please make sure you have enough free memory in the temporary directory on your system, and please ensure that read, write and run access rights have been granted. Close all other programs before starting the installation process.

Installation of LibreOffice on Debian/Ubuntu-based Linux systems
----------------------------------------------------------------------

If you have a previous version of LibreOffice already installed, then you will need to de-install it before proceeding further. For instructions on how to install a language pack (after having installed the US English version of LibreOffice), please read the section below entitled Installing a Language Pack.

When you unpack the downloaded archive, you will see that the contents have been decompressed into a sub-directory. Open a file manager window, and change directory to the one starting with "LibO_", followed by the version number and some platform information.

This directory contains a subdirectory called "DEBS". Change directory to the "DEBS" directory.

Right-click within the directory and choose "Open in Terminal". A terminal window will open. From the command line of the terminal window, enter the following command (you will be prompted to enter your root user's password before the command will execute):

sudo dpkg -i *.deb

The above dpkg command does the first part of the installation process. To complete the process, you also need to install the desktop integration packages. To do this, change directory to the "desktop-integration" directory that is within the "DEBS" directory, using the following command:

cd desktop-integration

Now run the dpkg command again:

sudo dpkg -i *.deb

The installation process is now completed, and you should have icons for all the LibreOffice applications in your desktop's Applications/Office menu.

Installation of LibreOffice on Fedora, Suse, Mandriva and other Linux systems using RPM packages
----------------------------------------------------------------------

If you have a previous version of LibreOffice already installed, then you will need to de-install it before proceeding further. For instructions on how to install a language pack (after having installed the US English version of LibreOffice), please read the section below entitled Installing a Language Pack.

When you unpack the downloaded archive, you will see that the contents have been decompressed into a sub-directory. Open a file manager window, and change directory to the one starting with "LibO_", followed by the version number and some platform information.

This directory contains a subdirectory called "RPMS". Change directory to the "RPMS" directory.

Right-click within the directory and choose "Open in Terminal". A terminal window will open. From the command line of the terminal window, enter the following command (you will be prompted to enter your root user's password before the command will execute):

For Fedora-based systems: su -c 'yum install *.rpm'

For Mandriva-based systems: sudo urpmi *.rpm

For other RPM-based systems (Suse, etc.): rpm -Uvh *.rpm

The above command does the first part of the installation process. To complete the process, you also need to install the desktop integration packages. To do this, change directory to the "desktop-integration" directory that is within the "RPMS" directory, using the following command:

cd desktop-integration

Now run the installation command again:

For Fedora-based systems: su -c 'yum install *freedesktop*.rpm'

For Mandriva-based systems: sudo urpmi *mandriva*.rpm

For SUSE-based systems: rpm -Uvh *suse*.rpm

For other RPM-based systems: rpm -Uvh *freedesktop*.rpm

The installation process is now completed, and you should have icons for all the LibreOffice applications in your desktop's Applications/Office menu.

Notes Concerning Desktop Integration for Linux Distributions Not Covered in the Above Installation Instructions
----------------------------------------------------------------------

It should be easily possible to install LibreOffice on other Linux distributions not specifically covered in these installation instructions. The main aspect for which differences might be encountered is desktop integration.

The desktop-integration directory also contains a package named libreoffice3.3-freedesktop-menus-3.3.1.noarch.rpm (or similar). This is a package for all Linux distributions that support the Freedesktop.org specifications/recommendations ([http://en.wikipedia.org/wiki/Freedesktop.org](http://en.wikipedia.org/wiki/Freedesktop.org)), and is provided for installation on other Linux distributions not covered in the aforementioned instructions.

Installing a Language Pack
----------------------------------------------------------------------

Download the language pack for your desired language and platform. They are available from the same location as the main installation archive. From the Nautilus file manager, extract the downloaded archive into a directory (your desktop, for instance). Ensure that you have exited all LibreOffice applications (including the QuickStarter, if it is started).

Change directory to the directory in which you extracted your downloaded language pack.

Now change directory to the directory that was created during the extraction process. For instance, for the French language pack for a 32-bit Debian/Ubuntu-based system, the directory is named LibO_, plus some version information, plus Linux_x86_langpack-deb_fr.

Now change directory to the directory that contains the packages to install. On Debian/Ubuntu-based systems, the directory will be DEBS. On Fedora, Suse or Mandriva systems, the directory will be RPMS.

From the Nautilus file manager, right-click in the directory and choose the command "Open in terminal". In the terminal window you just opened, execute the command to install the language pack (with all of the commands below, you may be prompted to enter your root user's password):

For Debian/Ubuntu-based systems: sudo dpkg -i *.deb

For Fedora-based systems: su -c 'yum install *.rpm'

For Mandriva-based systems: sudo urpmi *.rpm

For other RPM-using systems (Suse, etc.): rpm -Uvh *.rpm

Now start one of the LibreOffice applications - Writer, for instance. Go to the Tools menu and choose Options. In the Options dialog box, click on "Language Settings" and then click on "Languages". Dropdown the "User interface" list and select the language you just installed. If you want, do the same thing for the "Locale setting", the "Default currency", and the "Default languages for documents".

After adjusting those settings, click on OK. The dialog box will close, and you will see an information message telling you that your changes will only be activated after you exit LibreOffice and start it again (remember to also exit the QuickStarter if it is started).

The next time you start LibreOffice, it will start in the language you just installed.

----------------------------------------------------------------------
Problems During Program Startup
----------------------------------------------------------------------

Difficulties starting LibreOffice (e.g. applications hang) as well as problems with the screen display are often caused by the graphics card driver. If these problems occur, please update your graphics card driver or try using the graphics driver delivered with your operating system. Difficulties displaying 3D objects can often be solved by deactivating the option "Use OpenGL" under 'Tools - Options - LibreOffice - View - 3D view'.

----------------------------------------------------------------------
Shortcut Keys
----------------------------------------------------------------------

Only shortcut keys (key combinations) not used by the operating system can be used in LibreOffice. If a key combination in LibreOffice does not work as described in the LibreOffice Help, check if that shortcut is already used by the operating system. To rectify such conflicts, you can change the keys assigned by your operating system. Alternatively, you can change almost any key assignment in LibreOffice. For more information on this topic, refer to the LibreOffice Help or the Help documention of your operating system.

----------------------------------------------------------------------
File Locking
----------------------------------------------------------------------

File locking is enabled by default in LibreOffice. On a network that uses the Network File System protocol (NFS), the locking daemon for NFS clients must be active. To disable file locking, edit the soffice script and change the line "export SAL_ENABLE_FILE_LOCKING" to "# export SAL_ENABLE_FILE_LOCKING". If you disable file locking, the write access of a document is not restricted to the user who first opens the document.

Warning: The activated file locking feature can cause problems with Solaris 2.5.1 and 2.7 used in conjunction with Linux NFS 2.0. If your system environment has these parameters, we strongly recommend that you avoid using the file locking feature. Otherwise, LibreOffice will hang when you try to open a file from a NFS mounted directory from a Linux computer.

----------------------------------------------------------------------
Graphic Performance
----------------------------------------------------------------------

By default, LibreOffice favours nice-looking graphics over speed. If you experience slow graphics, switching off 'Tools - Options - LibreOffice - View - Use Anti-Aliasing' may help.

----------------------------------------------------------------------
Important Accessibility Notes
----------------------------------------------------------------------

For more information on the accessibility features in LibreOffice, see [http://www.libreoffice.org/accessibility/](http://www.libreoffice.org/accessibility/)

----------------------------------------------------------------------
User Support
----------------------------------------------------------------------

The main support page [http://www.libreoffice.org/support/](http://www.libreoffice.org/support/) offers various possibilities for help with LibreOffice. Your question may have already been answered - check the Community Forum at [http://www.documentfoundation.org/nabble/](http://www.documentfoundation.org/nabble/) or search the archives of the 'users@libreoffice.org' mailing list at [http://www.libreoffice.org/lists/users/](http://www.libreoffice.org/lists/users/). Alternatively, you can send in your questions to [email]users@libreoffice.org[/email]. If you like to subscribe to the list (to get email responses), send an empty mail to: [email]users+subscribe@libreoffice.org[/email].

Also check the FAQ section at [http://www.libreoffice.org/faq/](http://www.libreoffice.org/faq/).

----------------------------------------------------------------------
Reporting Bugs & Issues
----------------------------------------------------------------------

Our system for reporting, tracking and solving bugs is currently BugZilla, kindly hosted at [https://bugs.freedesktop.org/](https://bugs.freedesktop.org/). We encourage all users to feel entitled and welcome to report bugs that may arise on your particular platform. Energetic reporting of bugs is one of the most important contributions that the user community can make to the ongoing development and improvement of LibreOffice.

----------------------------------------------------------------------
Getting Involved
----------------------------------------------------------------------

The LibreOffice Community would very much benefit from your active participation in the development of this important open source project.

As a user, you are already a valuable part of the suite's development process and we would like to encourage you to take an even more active role with a view to being a long-term contributor to the community. Please join and check out the contributing page at [http://www.libreoffice.org/contribution/](http://www.libreoffice.org/contribution/)

How to Start
----------------------------------------------------------------------

The best way to start contributing is to subscribe to one or more of the mailing lists, lurk for a while, and gradually use the mail archives to familiarize yourself with many of the topics covered since the LibreOffice source code was released back in October 2000. When you're comfortable, all you need to do is send an email self-introduction and jump right in. If you are familiar with Open Source Projects, check out our To-Dos list and see if there is anything you would like to help with at [http://www.libreoffice.org/develop/](http://www.libreoffice.org/develop/).

Subscribe
----------------------------------------------------------------------

Here are a few of the mailing lists to which you can subscribe at [http://www.libreoffice.org/contribution/](http://www.libreoffice.org/contribution/)

* News: [email]announce@documentfoundation.org[/email] *recommended to all users* (light traffic)
* Main user list: [email]users@global.libreoffice.org[/email] *easy way to lurk on discussions* (heavy traffic)
* Marketing project: [email]marketing@global.libreoffice.org[/email] *beyond development* (getting heavy)
* General developer list: [email]libreoffice@lists.freedesktop.org[/email] (heavy traffic)

Joining one or more Projects
----------------------------------------------------------------------

You can make major contributions to this important open source project even if you have limited software design or coding experience. Yes, you!

We hope you enjoy working with the new LibreOffice 3.6 and will join us online.

The LibreOffice Community

----------------------------------------------------------------------
Used / Modified Source Code
----------------------------------------------------------------------

Portions Copyright 1998, 1999 James Clark. Portions Copyright 1996, 1998 Netscape Communications Corporation.

---

### Post by newb85 on 2012-10-12
Welcome to the forums!

First of all, when inserting quotes (like the contents of the readme file), please surround them with quote tags like this:

[noparse]> Quoted Text Here[/noparse]

It makes threads a lot easier to read.  (You can also do this by highlighting the quoted text and clicking the little quote-bubble icon above the composition area.)

On to your question:  What .deb files are included in the DEBS folder?  Are they the different components of LO?  You should be able to right-click on the files and open them with the Software Center.

---

### Post by Peter Maunder on 2012-10-13
Have you nautilus-open-terminal installed on your system? You will find it using the ubuntu software centre or synaptic. 

Then the right click will give you the 'Open in Terminal' option with Nautilus. I thought it was now a default with Ubuntu 12.04.

3.6.2.2  installed fine on my three systems. 
Cheers Peter

---

### Post by m3ideh on 2012-10-13
> **newb85 said:**
> Welcome to the forums!

First of all, when inserting quotes (like the contents of the readme file), please surround them with quote tags like this:



It makes threads a lot easier to read.  (You can also do this by highlighting the quoted text and clicking the little quote-bubble icon above the composition area.)

On to your question:  What .deb files are included in the DEBS folder?  Are they the different components of LO?  You should be able to right-click on the files and open them with the Software Center.

oh sorry about that, thanks for the welcome and the advice!

i cant open them in Ubuntu Software Center because when I do it comes up with this:

> Dependency is not satisfiable: libobasis3.6-core01


and what do you mean when you say this:

> What .deb files are included in the DEBS folder?  Are they the different components of LO?

I cant exactly go through and name all the files in the deb folder but heres a screenshot:

[ATTACH]225496[/ATTACH]


And how do I tell if they are different components of LibreOffice?

sorry for all the questions but i would be extremely thankful if you could answer them.

---

### Post by m3ideh on 2012-10-13
> **Peter Maunder said:**
> Have you nautilus-open-terminal installed on your system? You will find it using the ubuntu software centre or synaptic. 

Then the right click will give you the 'Open in Terminal' option with Nautilus. I thought it was now a default with Ubuntu 12.04.

3.6.2.2  installed fine on my three systems. 
Cheers Peter


Well I got the nautilus-open-terminal program and then I was able to follow the instructions on the readme file, but when I got to the last part of the installation (which was installing the 'desktop integration'), I got this error message:

[ATTACH]225497[/ATTACH]

I thought that it was just a minor problem but now I cant seem to find Libre Office anywhere; so I don't know if it even installed or not!

---

### Post by Peter Maunder on 2012-10-13
On my system LibreOffice 3.6.2.2 can be found in the
 

 /opt/libreoffice3.6/  folder  
 and the programs as  
 /opt/libreoffice3.6/program/soffice or /swriter /scalc   /sbase  /sdraw etc.
 

 For me the launch Icons are in Applications/Office, I don't use unity.
 

 My advice would be either to use synaptic or the 'ubuntu software centre' to manage LibreOffice through the official Ubuntu PPA My official PPA version is currently at level 3.5.4.2.


   
   OR if you must have the latest version of LibO to download, unpack and then use 'sudo dpkg -i *.deb' on the folders.

---

### Post by Pilot6 on 2012-10-13
You should have removed old Libreoffice before installed the new one. Libreoffice is installed, but debian menus not. Remove Libreoffice from Software Center (all applications) and then install Debian menus deb again.

---

### Post by Linux_junkie on 2012-10-13
Please follow the instructions on the post under Kubuntu forums to install LibreOffice 3.6  Reply 2 in the thread

[http://www.kubuntuforums.net/showthread.php?60410-When-I-can-expect-LibreOffice-3-6-in-the-repos](http://www.kubuntuforums.net/showthread.php?60410-When-I-can-expect-LibreOffice-3-6-in-the-repos)

oops! I missed the most important command to install LibreOffice.

```
sudo apt-get install libreoffice
```

After you add the PPA of LibreOffice and update.

---

### Post by m3ideh on 2012-10-13
> **Pilot6 said:**
> You should have removed old Libreoffice before installed the new one. Libreoffice is installed, but debian menus not. Remove Libreoffice from Software Center (all applications) and then install Debian menus deb again.


Well I got rid of everything I saw in the software center that had the word 'libre' in it, but Libreoffice still exists on my computer (just Libre office, not writer or any other of the programs in Libre office)

[ATTACH]225522[/ATTACH]
(see how none of the programs are clickable)


but in the software center, Libreoffice doesn't exist apparently!
(see below)

[ATTACH]225523[/ATTACH]


thanks for all the help guys so far though!

---

### Post by m3ideh on 2012-10-13
> **Linux_junkie said:**
> Please follow the instructions on the post under Kubuntu forums to install LibreOffice 3.6  Reply 2 in the thread

[http://www.kubuntuforums.net/showthread.php?60410-When-I-can-expect-LibreOffice-3-6-in-the-repos](http://www.kubuntuforums.net/showthread.php?60410-When-I-can-expect-LibreOffice-3-6-in-the-repos)

oops! I missed the most important command to install LibreOffice.

```
sudo apt-get install libreoffice
```After you add the PPA of LibreOffice and update.


i did what it said on the forum but it didnt work, NOTHING shows up after i clearly installed it.

thanks anyway though

---

### Post by m3ideh on 2012-10-13
DONT WORRY GUYS!

I fixed the problem, Libre office was at vers. 3.5 in the software center this morning but now all of a sudden its at vers. 3.6

I downloaded it, installed it and now everything is fine again.

I think it might have been because of the instructions that you guys offered or maybe the people behind LibreOffice just suddenly decided to update the software that was on the software center.

either way, thanks a heap guys for all the support!

:)

---

