---
title: "Dependencies Error"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by Future Warthog on 2012-04-02
Ok, I'm a beginner to Ubuntu and I have a problem.
LibreOffice locked up ans wouldn't let me use it, so I used the command:

sudo apt-get purge libreoffice-core

which it ran fine, and Libreoffice appeared to be gone for good. I installed OpenOffice, and it worked fine. But now I get this error message:

"An error occurred, please run package manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount >0'. This usually means that your installed packages have unmet dependencies."

So I tried the command line, and got this:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:3.4.5) but it is not installed
E: Unmet dependencies. Try using -f."

So I tried sudo apt-get -f install, but I got this:

Reading package List....Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0 B/16.9 MB of archives.
After this operation, 43.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 221598 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.4.5-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.4.5-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/mime/packages/openoffice.org.xml', which is also in package openoffice.org-debian-menus 3.3-9556
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.4.5-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone have any idea of my problem, and how to fix it?
It will NOT allow me to install/uninstall ANYTHING, from Ubuntu Software Center, or the command line.

I also recently installed the KDE desktop, could that have anything to do with?

-packpatfan

---

### Post by NikTh on 2012-04-02
Hello , 
can you please remove --purge completely Openoffice ? This package i think no longer supported by Ubuntu.
Run this command to fully remove it . Copy and paste to your terminal for accuracy. 
```
sudo apt-get purge openoffice.org-base-core openoffice.org-common  openoffice.org-core openoffice.org-style-human uno-libs3 ure  openoffice.org-thesaurus-en-au openoffice.org-thesaurus-en-us  openoffice.org-hyphenation openoffice.org-hyphenation-en-us  openoffice.org-l10n-common
```Then go to the site of LibreOffice , download it from there and follow the instructions to install it. 
[http://www.libreoffice.org/download/](http://www.libreoffice.org/download/)

Read the instructions --> [http://www.libreoffice.org/get-help/installation/linux/](http://www.libreoffice.org/get-help/installation/linux/)
Thanks

---

### Post by critin on 2012-04-02
Have you tried Synaptic Package manager to uninstall, fix broken packages or/and install?
Try uninstalling OO from there too and reinstalling whichever one you want.
If synaptic doesn't let you uninstall either, I have no suggestions.

---

### Post by Future Warthog on 2012-04-03
Well, I tried the command given, but this came up:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'openoffice.org-core' can't be removed
E: Unable to locate package openoffice.org-base-core
E: Couldn't find any package by regex 'openoffice.org-base-core'
E: Unable to locate package openoffice.org-style-human
E: Couldn't find any package by regex 'openoffice.org-style-human'
E: Unable to locate package openoffice.org-l10n-common
E: Couldn't find any package by regex 'openoffice.org-l10n-common'

I am trying to download LibreOffice, but I may have problems

---

### Post by dniMretsaM on 2012-04-03
Open up Synaptic, do a search for OpenOffice and purge everything related that you have installed. Do the same for LibreOffice. Then you can try installing Libre/OpenOffice again.

---

### Post by Future Warthog on 2012-04-03
Yay! Problem fixed. But now I have an even worse problem! Every time I try to open a new application, Ubuntu just about blows up. The Screen goes blank except for my background, and then it brings back some things, but not all. I had Pre-released updates and Unsupported updates selected. It doesn't happen when logged in as root.

[SIZE=4][COLOR=Red]**SOMEONE PLEASE HELP!**[/COLOR][/SIZE]

---

### Post by NikTh on 2012-04-04
> **packpatfan said:**
> Yay! Problem fixed. But now I have an even worse problem! Every time I try to open a new application, Ubuntu just about blows up. The Screen goes blank except for my background, and then it brings back some things, but not all. I had Pre-released updates and Unsupported updates selected. It doesn't happen when logged in as root.

[SIZE=4][COLOR=Red]**SOMEONE PLEASE HELP!**[/COLOR][/SIZE]

If problem with Openoffice/LibreOffice solved then please mark this thread as solved(from thread tools) and open a new thread with your new problem. Be as specific as you can to describe it.
It seems to be different.
Thanks

---

