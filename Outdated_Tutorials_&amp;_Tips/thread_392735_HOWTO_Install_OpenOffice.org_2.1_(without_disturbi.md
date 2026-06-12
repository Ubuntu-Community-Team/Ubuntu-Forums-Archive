---
title: "HOWTO: Install OpenOffice.org 2.1 (without disturbing 2.0)"
date: 2007-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by jfinkels on 2007-03-24
**HOWTO**: Install OpenOffice.org 2.1 on Ubuntu 6.10

I know, I know, I'm kind of late; Ubuntu 7.04 Feisty Fawn will ship with OpenOffice.org 2.2. Better late than never.

**PURPOSE**: Every once in a while, somebody asks about how to install a more recent version of OpenOffice.org, like OpenOffice.org version 2.1, which is the most recent official stable release, as stated on [http://www.openoffice.org](http://www.openoffice.org). _THIS IS VERY EASY TO DO_. This HOWTO will cover ONE WAY to install OpenOffice.org 2.1 (i.e. this is how I did it on my Ubuntu 6.10 Dell Inspiron 9300 with an x86 processor, and it works just peachy).

If you are a beginner and would like detailed instructions, read on (these instructions are long and intended for absolute beginners). If you just want to see the commands, skip to the bottom, I wrote them out there for easy copy & paste action.

**Step 0 - Remove OpenOffice.org 2.0**
Remove all applications associated with the default OpenOffice.org 2.0 that is in the standard repositories for Ubuntu 6.10 (and perhaps any remaining packages from a previous installation of OOo 2.1). Copy and paste the following command into the terminal to uninstall all OOo packages and those depending on them (if you are uncomfortable with this, follow the directions below the command):
```

sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-writer openoffice.org-xsltfilter openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb

```
To remove all those applications using a graphical package manager follow these directions:
[LIST=1]
[*]Press <Alt>+<F2> and type *gksudo synaptic*. This will open Synaptic Package Manager.
[*]Click the "Search" button in the menu bar.
[*]In the "Search:" field, type "openoffice" and in the "Look in:" field, select "Name". Press the "Search" button.
[*]For each package with a green box (meaning it is already installed) right click on the package name and select "Mark for Removal".
[*]Search for each of the following packages and mark them for removal as you did to the packages in the previous step: [LIST]
[*]ubuntu-desktop
[*]language-support-en
[*]thunderbird-locale-en-gb
[*]python-uno
[/LIST]
[*]Everything should be correctly uninstalled now.
[/LIST]

**Step 1 - Install JRE**
Install the Sun Java Runtime Environment 5 (JRE) (NB: This is non-free software. If you are concerned about keeping your Ubuntu free [as in speech], then you'll have to find yourself a different HOWTO). OpenOffice.org uses it. Type the following code into the terminal:
```
sudo aptitude install sun-java5-bin sun-java5-jre
```
You'll have to install a couple of other packages on which the JRE depends. Press yes through all the goofy license agreements (or be a proactive, productive citizen and read them first).

**Step 2 - Install alien**
Install the program *alien*, which converts .rpm packages to .deb packages (i.e. it makes such packages usable in Debian-based Linux distributions such as Ubuntu). Type the following in the terminal:
```
sudo aptitude install alien
```
Agree to install all the dependencies for alien as well, if needed.

**Step 3 - Download OpenOffice.org 2.1**
Download OpenOffice.org 2.1 from the official download website ([http://download.openoffice.org/2.1.0/index.html)](http://download.openoffice.org/2.1.0/index.html)). Click "Download OpenOffice.org". UNCHECK the little box that says "Include the Java JRE with this download". If you want to, I guess you can include it, but it's unnecessary because we installed it in step 1 :D. The download is pretty big (about 120MB) so it may take a while. Make a sandwich.

**Step 4 - Unpack and install OpenOffice.org 2.1**
Change to the directory in which the file *OOo_2.1.0_LinuxIntel_install_en-US.tar.gz* is saved. For example, if it is saved in your home directory, type the following in the terminal:
```
cd ~
```

Type the following code in your terminal to extract the contained files from the tarball archive:
```
tar xzvf OOo_2.1.0_LinuxIntel_install_en-US.tar.gz
```

Change to the directory that you just unpacked, with the long, goofy name:
```
cd OOE680_m6_native_packed-1_en-US.9095/
```

There should be three directories in this folder, *licenses/*, *readmes/*, and *RPMS/*. Change to the *RPMS/* directory:
```
cd RPMS/
```

Convert all the .rpm packages into .deb packages using alien (Ubuntu uses .deb packages to install programs, not .rpm packages). Type the following command into the terminal:
```
sudo alien -d *.rpm
```
This might take a while. Make another sandwich.

alien will give a warning about including scripts in the conversion of one of the packages. Convert the package in question with alien again, this time using the *--scripts* parameter:
```

sudo alien --scripts -d openoffice.org-core10-2.1.0-7-i586.rpm

```

Finally install all the .deb packages. Type the following command into the terminal:
```
sudo dpkg -i *.deb
```
This will install the entire OpenOffice.org suite. This also might take a while, make a sandwich (or half, if you're getting full).

Change to the *desktop-integration* directory. Type the following into the terminal:
```

cd desktop-integration/

```

Install the OpenOffice.org menu items. Type the following in the terminal:
```

sudo dpkg -i openoffice.org-debian-menus_2.1-5_all.deb

```

OpenOffice.org 2.1 suite is now installed system-wide! It is installed in the folder */opt/openoffice.org2.1/*. The actual binaries are in the folder */opt/openoffice.org2.1/program/*, so to start Writer, for example, type the following in the terminal:
```
/opt/openoffice.org2.1/program/swriter
```
The other programs are have similar appellations: *sbase*, *scalc*, *sdraw*, etc. The "s-" prefix is an artifact from StarOffice, from which OpenOffice is descended.

The entire suite and all its libraries are self-contained in the */opt/openoffice.org2.1/* folder. Technically, if you don't want the programs accessible to all users, you can simply move that folder to somewhere in your home directory (or wherever) by typing the following command in the terminal:
```
sudo mv /opt/openoffice.org2.1 ~
```

**Step 5 - Creating symbolic links (optional)**
To be able to start the programs contained in the suite, you probably want to be able to type a very short command instead of the very long one given above. To do this, we can use a symbolic link, which is something that points to a file located somewhere else in the file system. The syntax for a symbolic link looks like this:
```
ln -s *targetfilename* *symboliclinkname*
```
Link the command *swriter* in the directory */usr/bin/* (so that you can just type *swriter* at the command prompt to start Writer) to the actual binary for Writer, located at */opt/openoffice.org2.1/program/swriter* (or *~/openoffice.org2.1/program/swriter* if you moved the installation from its original location). Type the following into the terminal:
```
sudo ln -s /opt/openoffice.org2.1/program/swriter /usr/bin/swriter
```
Repeat this at your leisure for each program in the suite; just replace *swriter* with *sbase*, *scalc*, etc. in both places in the above command.

Success (hopefully)! Press <Alt>+<F2> and then type *swriter* to see if you linked correctly. OpenOffice.org 2.1 Writer should open. If you don't believe the splash screen that says in big letters "OpenOffice.org 2.1", you can choose *Help*>*About* and take a look at the version number.

[CENTER]----------[/CENTER]

**For those who don't want to read all that**, here's just the commands for my installation of OOo2.1.
```

sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-writer openoffice.org-xsltfilter openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb
wget http://ftp.ussg.iu.edu/openoffice/stable/2.1.0/OOo_2.1.0_LinuxIntel_install_en-US.tar.gz
sudo aptitude install sun-java5-jre sun-java5-bin alien
tar xzvf OOo_2.1.0_LinuxIntel_install_en-US.tar.gz
cd OOE680_m6_native_packed-1_en-US.9095/RPMS
sudo alien -d *.rpm
sudo alien --scripts -d openoffice.org-core10-2.1.0-7-i586.rpm
sudo dpkg -i *.deb
sudo ln -s /opt/openoffice.org2.1/program/swriter /usr/bin/swriter
sudo ln -s /opt/openoffice.org2.1/program/sbase /usr/bin/sbase
sudo ln -s /opt/openoffice.org2.1/program/scalc /usr/bin/scalc
sudo ln -s /opt/openoffice.org2.1/program/smath /usr/bin/smath
sudo ln -s /opt/openoffice.org2.1/program/sdraw /usr/bin/sdraw
sudo ln -s /opt/openoffice.org2.1/program/simpress /usr/bin/simpress

```

[CENTER]----------[/CENTER]

**To uninstall OpenOffice.org 2.1**, simply uninstall all packages on your system which have the prefix *openoffice.org-* by following the directions at Step 0, copied here for convenience:
```

sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-writer openoffice.org-xsltfilter openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb

```

---

### Post by Hagar Delest on 2007-03-28
There is already a nice How-to for that here : [Re: Help - Installing Open Office 2.1]("http://www.ubuntuforums.org/showpost.php?p=1945243&postcount=29").

Note that the --script option in the alien command is missing in your method, it can lead to bugs afterwards (but they don't prevent the installation).

Why do you say it leaves the 2.0 untouched ? As you use dpkg, it will upgrade and remove the previous version; as this is 2.1, it does leave some folders however.

---

### Post by jfinkels on 2007-03-29
> **Hagar de l'Est said:**
> There is already a nice How-to for that here : [Re: Help - Installing Open Office 2.1]("http://www.ubuntuforums.org/showpost.php?p=1945243&postcount=29").

Note that the --script option in the alien command is missing in your method, it can lead to bugs afterwards (but they don't prevent the installation).

Why do you say it leaves the 2.0 untouched ? As you use dpkg, it will upgrade and remove the previous version; as this is 2.1, it does leave some folders however.

You are right on both accounts; I fixed the how-to accordingly, thanks for your help. My mistakes. I see that you have posted essentially these directions on the OOo forums, so I trust you :).

---

### Post by Hagar Delest on 2007-03-29
> **jfinkels said:**
> I trust you :).
The most important is that it has been proved efficient for a large number of users. This is the fact to be trusted. I may make mistakes also ! 8-[ 

NB: if you want to get some attention, you can modify the thread for the 2.2 install. I installed it yesterday and it works fine.

---

### Post by berserker on 2007-03-29
Installed OO 2.2 using these instructions but now the toolbar fonts are small and blurry.  Anyone know how to change them?  Thanks!

---

### Post by Hagar Delest on 2007-03-30
See if this thread helps : [Linux user doesn't like UI]("http://www.oooforum.org/forum/viewtopic.phtml?p=206806#206806").

[quote="Ed"]It depends what desktop environment you're using. Under KDE it *does* use QT rules, and under GNome id *does* use GTK rules. If you're using any other environment, you can force it to use GTK or QT rules by adding ```
export OOO_FORCE_DESKTOP=gnome
``` or ```
export OOO_FORCE_DESKTOP=kde
``` int the startup script.

Unfortunately this requires manually editing text files, which is not really a suitable method for end users. There really needs to be a GUI option for this, but the developers seem to think that demanding that end users modify text files to get the right look is perfectly acceptable.[/quote]

---

### Post by berserker on 2007-03-30
> **Hagar de l'Est said:**
> See if this thread helps : [Linux user doesn't like UI]("http://www.oooforum.org/forum/viewtopic.phtml?p=206806#206806").

That worked.  Thank you!

---

### Post by jfinkels on 2007-03-31
> **Hagar de l'Est said:**
> if you want to get some attention, you can modify the thread for the 2.2 install. I installed it yesterday and it works fine.

I will definitely update this in the next couple of days, when I get a chance to make sure everything works fine with 2.2 and to change the howto. If you (or anyboy) have any more important suggestions (like the fix you gave to berserker above), I would be happy to include them.

---

### Post by Hagar Delest on 2007-03-31
Yes, you can point to this thread, especially the §3 about dictionaries configuration overriden during upgrade : [Tutorial for Spell check and Language configuration](http://www.oooforum.org/forum/viewtopic.phtml?t=50862).

---

### Post by Athanasius on 2007-03-31
I had the problem that only root could access the program; it has to be manually changed.

---

### Post by thommo on 2007-05-01
hi all, am I missing something here? 
the thread title is > HOWTO: Install OpenOffice.org 2.1 (without disturbing 2.0)
however step 0 of the process is to remove 2.0...

what the???

---

### Post by jfinkels on 2007-05-01
> **thommo said:**
> hi all, am I missing something here? 
the thread title is 
however step 0 of the process is to remove 2.0...

what the???

No, you read it correctly. I accidentally named the thread before realizing that in my installation, I had actually removed 2.0. That's why I added a Step 0. Unfortunately I was unable to change the title of the thread :)

You may want to look at this thread ( [http://ubuntuforums.org/showthread.php?t=398074](http://ubuntuforums.org/showthread.php?t=398074) ) as it concerns a more up-to-date version of OOo, plus it's named correctly.

---

### Post by rahimveron on 2007-07-09
Kudos once again to Ubuntu guys........I am lovin it!!!!!

---

