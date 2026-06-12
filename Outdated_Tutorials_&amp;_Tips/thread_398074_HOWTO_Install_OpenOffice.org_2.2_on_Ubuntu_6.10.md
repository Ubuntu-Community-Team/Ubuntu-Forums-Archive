---
title: "HOWTO: Install OpenOffice.org 2.2 on Ubuntu 6.10"
date: 2007-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by jfinkels on 2007-03-31
Updated 6 April 2007.

Most of this information is taken from this thread, which I posted previously: [http://www.ubuntuforums.org/showthread.php?p=2349049](http://www.ubuntuforums.org/showthread.php?p=2349049)

Ubuntu 7.04 Feisty Fawn ships with OpenOffice.org 2.2, but what if you want to install Openoffice.org 2.2 on Ubuntu 6.10 Edgy Eft over the standard OpenOffice.org 2.0 that ships with it? It's very simple; read on to find out how.

**PURPOSE**: Every once in a while, somebody asks about how to install a more recent version of OpenOffice.org, which is _**VERY EASY TO DO**_. This HOWTO will covers an easy method for installing OpenOffice.org 2.2. 

I tested this on my Ubuntu 6.10 Dell Inspiron 9300, x86 processor.

**If you are a beginner** and would like detailed instructions, read on (these instructions are long and intended for absolute beginners). **If you just want to see the commands**, skip to the bottom, I wrote them out there for easy copy & paste action.

**NB**: I am assuming that you're system is up-to-date, i.e. you have installed all packages recommended by the update manager.

**Step 0 - Remove OpenOffice.org 2.0**
Remove all applications associated with the default OpenOffice.org 2.0 that is in the standard repositories for Ubuntu 6.10. Copy and paste the following command into the terminal to uninstall all OOo packages and those depending on them (if you are uncomfortable with this, follow the directions below the command):
```

sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-writer openoffice.org-xsltfilter  openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb

```
Alternately, to remove all those applications using a graphical package manager follow these directions:
[LIST=1]
[*]Press <Alt>+<F2> and type *gksudo synaptic*. This will open Synaptic Package Manager.
[*]Click the "Search" button in the menu bar.
[*]In the "Search:" field, type "openoffice" and in the "Look in:" field, select "Name". Press the "Search" button.
[*]For each package with a green box (meaning it is already installed) right click on the package name and select "Mark for Removal".
[*]Search for each of the following packages and mark them for removal as you did to the packages in the previous step (if they are not installed, don't worry about them): [LIST]
[*]ubuntu-desktop
[*]language-support-en
[*]thunderbird-locale-en-gb
[*]python-uno
[/LIST]
[*]Everything should be correctly uninstalled now.
[/LIST]

**Step 1 - Install JRE**
Install the Sun Java Runtime Environment 5 (JRE) (**NB**: This is non-free software! If you are concerned about keeping your Ubuntu free [as in speech], then you'll have to find yourself a different HOWTO, or different office software). OpenOffice.org uses it.

First, you need to enable the "multiverse" software repository, which provides access to packages whose use or source code may be restricted by copyright laws or other legal issues. It will all still be completely free [as in costless] for you to download and use. To enable the multiverse sowftware repository, click on **System** > **Administration** > **Software Sources**. Ensure that the checkbox next to "Software restricted by copyright or legal issues (multiverse)" is selected. (As a side note, you may want to enable the "universe" repository as well, which gives you access to many, many community-supported programs). Press the "Close" button and agree to "Reload" you're package list when prompted. You may "reload" your package list at any time by typing this into the terminal:
```

sudo aptitude update

```

Now you can install Java packages. Type the following code into the terminal:
```
sudo aptitude install sun-java5-bin sun-java5-jre
```
You'll have to install a couple of other packages on which the JRE depends. Press yes through all the goofy license agreements (or be a proactive, productive citizen and read them first).

**Step 2 - Install alien**
Install the program *alien*, which converts .rpm packages to .deb packages (i.e. it makes such packages usable in Debian-based Linux distributions such as Ubuntu). Type the following in the terminal:
```
sudo aptitude install alien
```
Agree to install all the dependencies for alien as well, if necessary.

**Step 3 - Download OpenOffice.org 2.2**
Download OpenOffice.org 2.2 from the official download website ([http://download.openoffice.org/2.2.0/index.html)](http://download.openoffice.org/2.2.0/index.html)). Click "Download OpenOffice.org". UNCHECK the little box that says "Include the Java JRE with this download". If you want to, I guess you can include it, but it's unnecessary because we installed it in step 1 :D. The download is pretty big (about 120MB) so it may take a while. Make a sandwich.

**Step 4 - Unpack and install OpenOffice.org 2.2**
Change to the directory in which the file *OOo_2.2.0_LinuxIntel_install_en-US.tar.gz* is saved. For example, if it is saved in your home directory, type the following in the terminal:
```
cd ~
```

Type the following code in your terminal to extract the contained files from the tarball archive:
```
tar xzvf OOo_2.2.0_LinuxIntel_install_en-US.tar.gz
```

Change to the directory that you just unpacked, with the long, goofy name:
```
cd OOF680_m14_native_packed-1_en-US.9134/
```

There should be three directories in this folder, *licenses/*, *readmes/*, and *RPMS/*. Change to the *RPMS/* directory:
```
cd RPMS/
```

Convert all the .rpm packages into .deb packages using alien (Ubuntu uses .deb packages to install programs, not .rpm packages). Type the following command into the terminal:
```
sudo alien --scripts --keep-version -d *.rpm
```
This might take a while. Make another sandwich. The *--scripts* option preserves pre- and post-installation scripts associated with the .rpm package (if you don't include it, alien will give you a warning). The *--keep-version* option prevents alien from adding one to the minor version number of the package (i.e. the package openoffice.org-core10-2.2.0-9134.i586.rpm, after being converted would have version number 2.2.0-9135), which is its default behavior. The *-d* parameter tells alien to convert the .rpm packages to .deb packages.

Finally install all the .deb packages. Type the following command into the terminal:
```
sudo dpkg -i *.deb
```
This will install the entire OpenOffice.org suite. This also might take a while, make a sandwich (or half, if you're getting full).

When all those packages are installed, change to the *desktop-integration* folder. Type the following in the terminal:
```

cd desktop-integration/

```

Install the OpenOffice.org menu items. Type the following in the terminal:
```

sudo dpkg -i openoffice.org-debian-menus_2.2-9119_all.deb

```

OpenOffice.org 2.2 suite is now installed system-wide! It is installed in the folder */opt/openoffice.org2.2/*. The actual binaries are in the folder */opt/openoffice.org2.2/program/*, so to start Writer, for example, type the following in the terminal:
```
/opt/openoffice.org2.2/program/swriter
```
The other programs are have similar appellations: *sbase*, *scalc*, *sdraw*, etc. The "s-" prefix is an artifact from StarOffice, from which OpenOffice is descended.

The entire suite and all its libraries are self-contained in the */opt/openoffice.org2.2/* folder. Technically, if you don't want the programs accessible to all users, you can simply move that folder to somewhere in your home directory (or wherever) by typing the following command in the terminal:
```
sudo mv /opt/openoffice.org2.2 ~
```
This is totally optional, though.

**Step 5 - Creating symbolic links (optional)**
To be able to start the programs contained in the suite, you probably want to be able to type a very short command instead of the very long one given above. To do this, we can use a symbolic link, which is something that points to a file located somewhere else in the file system. The syntax for a symbolic link looks like this:
```
ln -s *targetfilename* *symboliclinkname*
```
Link the command *swriter* in the directory */usr/bin/* (so that you can just type *swriter* at the command prompt to start Writer) to the actual binary for Writer, located at */opt/openoffice.org2.2/program/swriter* (or *~/openoffice.org2.2/program/swriter* if you moved the installation from its original location). Type the following into the terminal:
```
sudo ln -s /opt/openoffice.org2.2/program/swriter /usr/bin/swriter
```
Repeat this at your leisure for each program in the suite; just replace *swriter* with *sbase*, *scalc*, etc. in both places in the above command.

Success (hopefully)! Press <Alt>+<F2> and then type *swriter* to see if you linked correctly. OpenOffice.org 2.2 Writer should open. If you don't believe the splash screen that says in big letters "OpenOffice.org 2.2", you can choose *Help*>*About* and take a look at the version number.

[CENTER]~~~~~~~~~~[/CENTER]
**A couple extras**
[LIST]
[*]If the fonts on your toolbars are small, blurry, or ugly, you might be able to force OOo to use either GTK rules or Qt rules. Take a look at this thread for more information: [http://www.oooforum.org/forum/viewtopic.phtml?p=206806#206806](http://www.oooforum.org/forum/viewtopic.phtml?p=206806#206806)
[*]If you are having some problems with spell checking or language configuration for languages other than US English, take a look at this thread: [http://www.oooforum.org/forum/viewtopic.phtml?t=50862](http://www.oooforum.org/forum/viewtopic.phtml?t=50862)
[/LIST]



[CENTER]~~~~~~~~~~[/CENTER]

**For those who don't want to read all that**, here's just the commands for my installation of OOo2.2. Note that I am removing packages from a previous installation by this method, you need only worry about removing openoffice.org-* packages that are installed on your system. Note also that if the download fails or is slow or something, just go to [http://www.openoffice.org/](http://www.openoffice.org/) and download the file manually (because this is just one of the mirrors that OpenOffice.org uses to distribute their files).
```

sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-writer openoffice.org-xsltfilter openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb
wget http://openoffice.mirror.infinitaus.com/stable/2.2.0/OOo_2.2.0_LinuxIntel_install_en-US.tar.gz
sudo aptitude install sun-java5-jre sun-java5-bin alien
tar xzvf OOo_2.2.0_LinuxIntel_install_en-US.tar.gz
sudo alien -d OOF680_m14_native_packed-1_en-US.9134/RPMS/*.rpm
sudo alien --scripts -d OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core10-2.2.0-9134.i586.rpm
sudo dpkg -i OOF680_m14_native_packed-1_en-US.9134/RPMS/*.deb
sudo dpkg -i OOF680_m14_native_packed-1_en-US.9134/RPMS/desktop-integration/openoffice.org-debian-menus_2.2-9119_all.deb
sudo ln -s /opt/openoffice.org2.2/program/swriter /usr/bin/swriter
sudo ln -s /opt/openoffice.org2.2/program/sbase /usr/bin/sbase
sudo ln -s /opt/openoffice.org2.2/program/scalc /usr/bin/scalc
sudo ln -s /opt/openoffice.org2.2/program/smath /usr/bin/smath
sudo ln -s /opt/openoffice.org2.2/program/sdraw /usr/bin/sdraw
sudo ln -s /opt/openoffice.org2.2/program/simpress /usr/bin/simpress
sudo ln -s /opt/openoffice.org2.2/program/soffice /usr/bin/soffice
sudo ln -s /opt/openoffice.org2.2/program/spadmin /usr/bin/spadmin

```

[CENTER]~~~~~~~~~~[/CENTER]

**To uninstall OpenOffice.org 2.2**, simply uninstall all packages starting with *openoffice.org-* that are currently installed on your system. Follow the instructions at step 0 above, copied here for convenience:
```

sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-writer openoffice.org-xsltfilter  openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb

```

---

### Post by jahwire on 2007-04-02
When trying to install Sun JAVA, I got the following:

sudo aptitude install sun-java5-bin sun-java5-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java5-bin"
Couldn't find any package whose name or description matched "sun-java5-jre"
No packages will be installed, upgraded, or removed.

I am using Ubuntu 6.10 AMD64.

---

### Post by jfinkels on 2007-04-02
> **jahwire said:**
> When trying to install Sun JAVA, I got the following:

sudo aptitude install sun-java5-bin sun-java5-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java5-bin"
Couldn't find any package whose name or description matched "sun-java5-jre"
No packages will be installed, upgraded, or removed.

I am using Ubuntu 6.10 AMD64.

You may have to enable the "multiverse" software repository to get access to the Java packages. To do this, choose **System > Administration > Software Sources** from the Ubuntu main menu. After you type your password, check the boxes next to "Software restricted by copyright or legal issues". Software enabled by checking this box is not necessarily "free [as in liberty] and open source" software (i.e. it may have a license that copyrights the software or its source code), but it may still be free [as in costless] to download and use.

---

### Post by Athanasius on 2007-04-03
I found this very helpful.  The non-Ubuntuized OpenOffice works much faster for me.  The only thing is that first I copied the ubuntu icons and then 
```
dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```
to remove all traces of the old open office (I got this from [http://www.ubuntuforums.org/showpost.php?p=1945243&postcount=29](http://www.ubuntuforums.org/showpost.php?p=1945243&postcount=29)) as was noted in the earlier version of this tutorial.
Then I renamed the ubuntu icons to "images_industrial.zip" and replace it with the one in /opt/openoffice.org2.2/share/config then go to /home/ath/.openoffice.org2/user/config/imagecache and delete all the files.  

Start up OpenOffice and all should be well.

---

### Post by DizzyTech on 2007-04-03
So this uninstalls ubuntu-desktop?  Will it be restored later in the install? You have to have your install's original *-desktop package to upgrade Ubuntu to Feisty, or if you're paranoid like me, just so you have ubuntu-desktop installed.

---

### Post by jfinkels on 2007-04-03
> **DizzyTech said:**
> So this uninstalls ubuntu-desktop?  Will it be restored later in the install? You have to have your install's original *-desktop package to upgrade Ubuntu to Feisty, or if you're paranoid like me, just so you have ubuntu-desktop installed.

Yes, I'm afraid so: to my knowledge, if you want to uninstall OOo2.0, you will have to uninstall the *ubuntu-desktop* meta-package, (for those who don't know: a meta-package is a package which is empty and merely points to other packages to install). I suppose that if you want to upgrade to Feisty from Edgy, you might choose to reinstall *ubuntu-desktop* and then upgrade because Feisty comes with OOo2.2 anyway.

---

### Post by Athanasius on 2007-04-03
> **jahwire said:**
> When trying to install Sun JAVA, I got the following:

sudo aptitude install sun-java5-bin sun-java5-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java5-bin"
Couldn't find any package whose name or description matched "sun-java5-jre"
No packages will be installed, upgraded, or removed.[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Blackdown_Java_.28for_AMD64_systems_with_64-bit_Firefox.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Blackdown_Java_.28for_AMD64_systems_with_64-bit_Firefox.29)

I am using Ubuntu 6.10 AMD64.

You need to use Blackdown java because Sun doesn't have Java for 64 bit.  Here is a link for installation:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Blackdown_Java_.28for_AMD64_systems_with_64-bit_Firefox.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Blackdown_Java_.28for_AMD64_systems_with_64-bit_Firefox.29)

---

### Post by jahwire on 2007-04-04
When installing the JAVA package, I got into the license and could not press OK. Now, I get the following message when I try to install the package again:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I am new here... What should I do?

---

### Post by jahwire on 2007-04-04
When I type the following:
dpkg --configure -a

I get:
dpkg: requested operation requires superuser privilege

What is needed here? I know I am not a super user with Ubuntu yet, but I don't think this is referring to me personally!!

Please advice...

---

### Post by jfinkels on 2007-04-04
> **jahwire said:**
> When installing the JAVA package, I got into the license and could not press OK. Now, I get the following message when I try to install the package again:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I am new here... What should I do?

When you get to the Java license agreement, there's a little "OK" button on the bottom right? try pressing the left arrow key or the right arrow key to change which element is highlighted. I think by default the scroll bar on the right is highlighted (in order for you to scroll up and down with the up and down arrow keys) so try pressing left arrow to highlight the "OK" button. Then press enter and continue.

> **jahwire said:**
> When I type the following:
dpkg --configure -a

I get:
dpkg: requested operation requires superuser privilege

What is needed here? I know I am not a super user with Ubuntu yet, but I don't think this is referring to me personally!!

Please advice...

Just for kicks, "superuser privilege" means that you have to type the word "sudo" before typing the command. This allows the "_S_uper_U_ser" to "_DO_" the given command. The "superuser" or "root" user is the system administrator. If you want to change any system settings or do other important system actions, you'll have to login as the superuser or type "sudo" before doing it.

So to upgrade all possible packages, for example, type:
```

sudo aptitude upgrade

```
and type your password when prompted.

---

### Post by jahwire on 2007-04-04
At first I could not press the OK button with the Enter... That's why I got into trouble... Now I feel a bit silly... Of course it works.

I am 3 days old in Linux... Forgive me!!

Thanks... I am resuming installation now!

---

### Post by jahwire on 2007-04-04
The installation worked great....

A question about Ubuntu-desktop

The package is defined as so:
"This package depends on all of the packages in the Ubuntu desktop system
[B]It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.[/B]"

When I select to install it, it says that to be removed: "openOffice.org-debian-menus" and then to be installed... openOffice.org and plenty of other openOffice package...

I don't understand... Do I need it to insure proper upgrades? What will happen if I proceed with installation?

---

### Post by jfinkels on 2007-04-04
> **jahwire said:**
> The installation worked great....

A question about Ubuntu-desktop

The package is defined as so:
"This package depends on all of the packages in the Ubuntu desktop system
[B]It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.[/B]"

When I select to install it, it says that to be removed: "openOffice.org-debian-menus" and then to be installed... openOffice.org and plenty of other openOffice package...

I don't understand... Do I need it to insure proper upgrades? What will happen if I proceed with installation?

Choosing to install the package *ubuntu-desktop* will suggest installing all the other packages that come with the standard install of Ubuntu (i.e. when you install Ubuntu for the very first time, you have a few default packages installed, like Gaim, OpenOffice.org 2.0, etc.). If you choose to reinstall it after removing it as described in the first step of this HOWTO, *ubuntu-desktop* will suggest reinstalling the older version of OpenOffice.org, version 2.0. If you want to keep OpenOffice.org 2.0 uninstalled and OpenOffice.org 2.2 installed, then do not install ubuntu-desktop.

 By "ensure proper upgrades", I believe it means upgrading from Dapper to Edgy (Ubuntu 6.06 to Ubuntu 6.10) or Edgy to Feisty (Ubuntu 6.10 to Ubuntu 7.04, the upcoming release version). You don't really have to worry about your system not giving you upgrades to your packages if you uninstall *ubuntu-desktop*, unless you are doing a distribution upgrade. If I am wrong about this, can somebody give me the heads up?

By the way, welcome jahwire! I was new to Linux 6 months ago, my advice is ask lots of questions!!

---

### Post by Michaelt74 on 2007-04-04
Thanks for the tutorial, worked great!

---

### Post by jahwire on 2007-04-05
I see that Ubuntu version 7.04 is scheduled to be released in April. I even tried the AMD64 beta version since I had problem with my wireless connection. But that did not help with my wireless. (A long story!).  I do like the version 7...:guitar: :guitar: 

I would love to be able to upgrade to 7 when available without having to reinstall everything and hopefully keep my current wireless connection working. I don't mind using the 386 version. It rocks on my portable pretty much the same way for what I do.

For what you say, I might not be able to do so if I don't have ubuntu-desktop installed. Is there another package that would do the trick?

---

### Post by HokkaidoHillbilly on 2007-04-06
Ok, um, dumb 1 week old newbie question...

Is there anyway to make shortcuts in the Applications menu (i.e. similar to how it was prior to installation of 2.2) instead of having to start terminal every time?

---

### Post by HokkaidoHillbilly on 2007-04-06
Oops...never mind.  Deleted everything & re-installed according to [these directions]("http://http://www.digi-darkroom.com/showthread.php?p=210415") and everything's working perfectly now.

Thanks tho! :)

---

### Post by jfinkels on 2007-04-06
> **HokkaidoHillbilly said:**
> Oops...never mind.  Deleted everything & re-installed according to [these directions]("http://http://www.digi-darkroom.com/showthread.php?p=210415") and everything's working perfectly now.

Thanks tho! :)

Hmm... I don't know why your menu items weren't showing up following my method; installling the .deb package in the RPMS/desktop-integration/ folder should do it. The method you posted is pretty much the same. Oh well, I'm glad it finally worked for you! :)

Just for kicks, though: if you ever want to run a program without using a menu link and without having to open a terminal, you can press <Alt>+<F2>, which opens the "Run Program" dialog. Type the command for whatever program you want to run and voila! it will open. The menu launcher, desktop launchers, typing in the terminal, and typing in the "Run Program" dialog are all actually doing the same thing! They are all executing a command.

---

### Post by tigerstripedcat on 2007-04-06
Not working for AMD64?  (Incidently, this procedure doesn't work with 2.1 either so I must have something wrong with my setup.)


Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/openoffice.org-base
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of `NEEDED libvcl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libtl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsvt680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsvl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsfx680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libcomphelp4gcc3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libtk680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libutl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libstlport_gcc.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsvt680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libvcl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libtl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsvl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsfx680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libdbtools680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libcomphelp4gcc3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libstlport_gcc.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsvx680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsfx680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsb680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsvt680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libtk680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libvcl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libgo680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsvl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsot680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libutl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libtl680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libucbhelper3gcc3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libdbtools680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libcomphelp4gcc3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libso680li.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libvos3gcc3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libstlport_gcc.so' not recognized
dpkg-shlibdeps: warning: could not find any packages for libuno_sal.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libuno_sal (soname 3, path libuno_sal.so.3, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libuno_cppu.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libuno_cppu (soname 3, path libuno_cppu.so.3, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libuno_cppuhelpergcc3.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libuno_cppuhelpergcc3 (soname 3, path libuno_cppuhelpergcc3.so.3, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libuno_cppuhelpergcc3.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libuno_cppuhelpergcc3 (soname 3, path libuno_cppuhelpergcc3.so.3, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libuno_cppu.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libuno_cppu (soname 3, path libuno_cppu.so.3, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libuno_sal.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libuno_sal (soname 3, path libuno_sal.so.3, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libuno_cppuhelpergcc3.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libuno_cppuhelpergcc3 (soname 3, path libuno_cppuhelpergcc3.so.3, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libuno_cppu.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libuno_cppu (soname 3, path libuno_cppu.so.3, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libuno_sal.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libuno_sal (soname 3, path libuno_sal.so.3, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1

---

### Post by jonivey on 2007-04-08
I'm in Step 4, trying to change directory using the cd command.  However although I know my downloaded OOo 2.2 is in the desktop directory,  what is the proper syntax?
When I open a terminal window I see this:

jonivey@jonivey-desktop:~$ 

Does this mean I'm already in the desktop directory?
If not.........??????

---

### Post by jfinkels on 2007-04-08
> **jonivey said:**
> I'm in Step 4, trying to change directory using the cd command.  However although I know my downloaded OOo 2.2 is in the desktop directory,  what is the proper syntax?
When I open a terminal window I see this:

jonivey@jonivey-desktop:~$ 

Does this mean I'm already in the desktop directory?
If not.........??????

Hello again jonivey :D

Let me explain what the command-line prompt means. The first part, *jonivey*, is your username, the second part, *jonivey-desktop* is the "hostname" (basically your computer's nickname), the third part is your current directory, in this case just the tilde *~*. Whenever you see a directory name that includes a tilde like this, that's a shorthand for your "home directory" (analogous to My Documents in Microsoft Windows). You can see the full name of your current directory by using the command *pwd*, which _p_rints your _w_orking _d_irectory. The *$* at the end of the command prompt is just a signifier for the end of the 'locational' information and the start of where you type your commands.

Alrighty, now that that's out of the way: to see files and directories in your current directory, type *ls* (thats an L and an S) which will _l_i_s_t the contents of the current directory. If you are in your home folder (*~*) then you will see a folder called "Desktop". Type the following command to change to the "Desktop/" directory:
```

cd Desktop/

```

Starting to get it now? View the contents of this directory by using the *ls* command again. If you saved the OO2.2 package here, it will be listed. Then you can try the next few commands and see if they work. As always, post here if you have any problems.

By the way, this website ([http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)) has great introductory information if you're new to Linux!

---

### Post by jonivey on 2007-04-09
Thank you SO much for your patience with me and your detailed response.
I'll try to finish the OO02.2 install this PM.
Cordially,
Jon

---

### Post by jonivey on 2007-04-09
Sorry, forgot to mention:
I've visited psychocats.net and it looks promising so I bookmarked it to return later when things aren't so hectic.
On another subject, I downloaded Adobe:
AdobeReader_enu-7.0.9-1.i386.tar.gz
but in the terminal I got the following message:


Trying to install plugin for browser - firefox
Installing plugin in /usr/lib/firefox/firefox
cp: cannot create regular file `/usr/lib/firefox/plugins/nppdf.so': Permission denied
Could not copy the plugin file /home/jonivey/Desktop/AdobeReader/dir/Browser/intellinux/nppdf.so to /usr/lib/firefox/plugins/nppdf.so
Installation failed


Trying to install plugin for browser - mozilla
Installing plugin in /usr/lib/firefox/firefox
cp: cannot create regular file `/usr/lib/firefox/plugins/nppdf.so': Permission denied
Could not copy the plugin file /home/jonivey/Desktop/AdobeReader/dir/Browser/intellinux/nppdf.so to /usr/lib/firefox/plugins/nppdf.so
Installation failed


Do you want to perform manual installation ? [y/n] 

I should mention, by the way, that I created directory dir on the spur of the moment as a place to put Adobe.
Any suggestions on what's wrong?
P.S. All the Software Sources boxes are checked as far as Internet multiverse etc etc sources.

---

### Post by jfinkels on 2007-04-09
No probs, man. We're here to help :D

As for Adobe Reader, try this website ([http://ubuntu-tutorials.com/2006/11/23/how-to-install-adobe-reader-pdf-for-firefox-ubuntu-6061-610/)](http://ubuntu-tutorials.com/2006/11/23/how-to-install-adobe-reader-pdf-for-firefox-ubuntu-6061-610/)). For the most part, when you're just starting out, everything you need will be in the package manager, Synaptic. Also, there is a PDF reader already installed called "evince" that works just peachy, but if you really want/need Adobe, it's your computer; knock yourself out.

---

### Post by Jenske on 2007-04-09
Thanks for this very informative posting. I installed OOo 2.2 on my Ubuntu Dapper Drake (6.06) and it worked perfectly. Even the spelling checker -- I use Dutch -- worked perfectly. F.y.i. I already had version 2. 1 installed so OOo 2.2 "knew" I use the Dutch spelling checker.
Thanks

Jens (Belgium)

---

### Post by jonivey on 2007-04-11
Hi again. Thanks I'm beginning to get the hang of it. However I can't complete Step 4 of the OOo 2.2 install. Here's what I get:

jonivey@jonivey-desktop:~$ pwd
/home/jonivey
jonivey@jonivey-desktop:~$ ls
Desktop  Examples  Firefox_wallpaper.png  Hyatt Place  Yes
jonivey@jonivey-desktop:~$ cd Desktop/
jonivey@jonivey-desktop:~/Desktop$ ls

OOF680_m14_native_packed-1_en-US.9134
OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz



wmp11-windowsxp-x86-enu.exe
jonivey@jonivey-desktop:~/Desktop$ cd dir/
bash: cd: dir/: No such file or directory
jonivey@jonivey-desktop:~/Desktop$ cd OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz
bash: cd: OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz: Not a directory
jonivey@jonivey-desktop:~/Desktop$ tar bash: cd: OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz: Not a directory
tar: cd\:: Invalid blocking factor
Try `tar --help' or `tar --usage' for more information.
jonivey@jonivey-desktop:~/Desktop$ tar OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz
tar: Old option `L' requires an argument.
Try `tar --help' or `tar --usage' for more information.
jonivey@jonivey-desktop:~/Desktop$ tar usage
tar: Old option `g' requires an argument.
Try `tar --help' or `tar --usage' for more information.
jonivey@jonivey-desktop:~/Desktop$ tar help
tar: invalid option -- e
Try `tar --help' or `tar --usage' for more information.
jonivey@jonivey-desktop:~/Desktop$

Apparently I'm still doing something wrong.
Can anyone help?

---

### Post by jfinkels on 2007-04-11
Okey dokey, here we go:

> **jonivey said:**
> Hi again. Thanks I'm beginning to get the hang of it. However I can't complete Step 4 of the OOo 2.2 install. Here's what I get:

jonivey@jonivey-desktop:~/Desktop$ ls
OOF680_m14_native_packed-1_en-US.9134
OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz
wmp11-windowsxp-x86-enu.exe

Great! You've listed the files in your ~/Desktop directory.
> 
jonivey@jonivey-desktop:~/Desktop$ cd dir/
bash: cd: dir/: No such file or directory

I don't really know why you tried to change to a directory called "dir/" because we *know* it doesn't exist! It's not listed when you enter the command "ls", right? That's why you get the error message "No such file or directory". Error messages are your friend. They will tell you what you're doing wrong!
> 
jonivey@jonivey-desktop:~/Desktop$ cd OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz
bash: cd: OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz: Not a directory

You are trying to change directory to a file...that's impossible! You can only use "cd" with the name of a directory after it. "OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz" is a compressed package (sometimes called a "tarball"). This particular tarball contains the files for the OOo2.2 install, but it looks to me (from the results of typing "ls") that you have already extracted the files from this archive! They are in the directory "OOF680_m14_native_packed-1_en-US.9134". If you are using GNOME-terminal as your terminal emulator (which you most likely are) then when you list the files in a directory, you will see names of files and directories in different colors. For example, the tarball package may show up as red (signifying it is a package) and the directory I just spoke of may be blue (signifying it is a folder). If you are still having trouble figuring out which of your files is a directory you can try entering this command:
```

ls -l

```
That's a the 'list' command (ls) followed by a space, a dash, and the letter L, lowercase, ( -l). This will print a more detailed listing of your files, showing permissions, size, owner, and some other stuff. For example, when I type "ls -l", I might get something like this:
```

drwxr-xr-x 5 jeff jeff      4096 2006-11-30 14:46 OOF680_m14_native_packed-1_en-US.9134
-rw-r--r-- 1 jeff jeff 128789627 2007-02-12 18:33 OOo_2.2.0_LinuxIntel_install_en-US.tar.gz

```
The letter 'd' at the beginning of the first line tells me that this listing is a directory. The absence of the letter 'd' at the beginning of the second line tells me that this listing is a file. If you're still having trouble figuring out what's a directory and what's not, maybe you should stick with 'nautilus', the graphical file manager :).
> 
jonivey@jonivey-desktop:~/Desktop$ tar bash: cd: OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz: Not a directory
tar: cd\:: Invalid blocking factor
Try `tar --help' or `tar --usage' for more information.

I assume you tried to copy and paste the output of a previous command in the terminal...you generally should avoid doing that as much as possible. As you can see from the HOWTO, the program "tar" unpackages a file, as I explained above. I don't really know what you were trying to do here, but for now, stick with the commands I have given in the HOWTO.
> 
jonivey@jonivey-desktop:~/Desktop$ tar OOo_2.2.0_LinuxIntel_install_wJRE_en-US.tar.gz
tar: Old option `L' requires an argument.
Try `tar --help' or `tar --usage' for more information.
jonivey@jonivey-desktop:~/Desktop$ tar usage
tar: Old option `g' requires an argument.
Try `tar --help' or `tar --usage' for more information.
jonivey@jonivey-desktop:~/Desktop$ tar help
tar: invalid option -- e
Try `tar --help' or `tar --usage' for more information.

Apparently I'm still doing something wrong.
Can anyone help?
Okay, first: if the error message says "Try `tar --help' or `tar --usage' for more information.", type the command *exactly as written there*. There is no leeway for typing commands; they must be exact! A computer only does exactly what you tell it to do! So in general, to see the usage of a command and more information, type the following:
```

tar --help

```
Or if you want to see the help info for another program, type the name of that program followed by " --help" as above, like so:
```

ls --help
cd --help
mv --help

```
etc.

Okay moving on.

Again, as you can see from the commands listed in the HOWTO, typing the following command will extract files from the package:
```

tar xzvf OOo_2.2.0_LinuxIntel_install_en-US.tar.gz

```
To break this command down: "tar" is the name of the program (typing it orders the computer to run the program), "xzvf" is a series of 'options' which define a specific set of actions for the program to do (specifically, extract, unzip, use verbose output, and extract from a specific file, respectively), and "OOo_2.2.0_LinuxIntel_install_en-US.tar.gz" is the name of the file to extract. Do that and then move on to the next steps in the HOWTO (even though you've actually done it already, the practice can't hurt!).

Here's one final helpful hint in using the terminal. The program that allows you to type input in the terminal is called "bash" which is an acronym for the longer name of the program. It is a 'smart' program, so if you begin to type the name of a file, pressing <Tab> will fill in the rest of the name of the file if you have only typed a portion of it, or show you a list of possible completions to the file name. So instead of typing the long name of the file "OOo_2.2.0_LinuxIntel_install_en-US.tar.gz", you can just type "OOo", then press the <Tab> button, and bash will complete the name of the file for you! Isn't that nice.

Just ask if you need more help :D

---

### Post by jonivey on 2007-04-11
Hi jfinkels,

I'm deeply grateful that you've gone to all the trouble you have to explain the nitty gritty details.
And what is so cool about forums is that what you've written will remain posted so that other newbies can benefit, too. 
I'll try to finish the install soon.
By the way, you were puzzled about "dir". I did that deliberately because I THOUGHT I'd put the OOo 2.2 in that newly created directory.
Best wishes and may Linux become progressively more and more user friendly so that Microsoft will eventually shrink to nada ;).

Jon

---

### Post by jfinkels on 2007-04-11
> **jonivey said:**
> Hi jfinkels,

I'm deeply grateful that you've gone to all the trouble you have to explain the nitty gritty details.
And what is so cool about forums is that what you've written will remain posted so that other newbies can benefit, too. 
I'll try to finish the install soon.
By the way, you were puzzled about "dir". I did that deliberately because I THOUGHT I'd put the OOo 2.2 in that newly created directory.
Best wishes and may Linux become progressively more and more user friendly so that Microsoft will eventually shrink to nada ;).

Jon

We were all beginners once!

[http://en.wikipedia.org/wiki/Ubuntu_%28ideology%29](http://en.wikipedia.org/wiki/Ubuntu_%28ideology%29)

---

### Post by jonivey on 2007-04-12
:) :)
I have good news. The OOo 2.2 installation is ----I THINK-----complete.
HOO HOO!
But, I have 3 questions:
during the latter steps in Step 4 of the install, I neglected to do anything about the following 2 warnings:
Warning: Skipping conversion of scripts in package jre: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
jre_1.6.0-1_i386.deb generated
AND
Warning: Skipping conversion of scripts in package openoffice.org-core10: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
openoffice.org-core10_2.2.0-9135_i386.deb generated

Does it matter that I didn't do anything about these warnings?
SECOND QUESTION:
How exactly do I burn a CD, using the CD/DVD Creator, of the OOo 2.2? When I put a blank CD in the drive and click 'burn a data CD' , the program opens, but the 'Write to disc' option is grayed out.
THIRD QUESTION:
How do I stop all ----and I do mean, all----- of my input in OOo 2.2 Writer from being in red font and underlined?
The 'font' icon in the toolbar doesn't help, cuz when I select 'black' all input remains red.
(My original reason for uninstalling OOo 2.0 and installing 2.2 was to get rid of this problem, which apparently I caused inadvertently while trying to use AutoCorrect (name?) the one that's analagous to using the TAB key in bash to complete a long word. Or was it AutoComplete?)
I look forward to hearing enlightening words from any takers ;)
Thanks in advance, Linuxians. (Oops, did I just invent a word?:) )
I'm ok, honest. ;)

---

### Post by jfinkels on 2007-04-12
> **jonivey said:**
> :) :)
Warning: Skipping conversion of scripts in package jre: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
jre_1.6.0-1_i386.deb generated
AND
Warning: Skipping conversion of scripts in package openoffice.org-core10: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
openoffice.org-core10_2.2.0-9135_i386.deb generated

Did you copy the "alien" command exactly as I wrote it out? Make sure it has the "--scripts" option! If you use alien without the "--scripts" option, you will get this warning. It most likely won't make a difference, but it may cause you problems when you're using OOo later on. See the posts by Hagar de l'Est in this thread ([http://www.ubuntuforums.org/showthread.php?p=2349049)](http://www.ubuntuforums.org/showthread.php?p=2349049)).

Also, I wasn't going to tell you this before buuut...you shouldn't really be installing the Java Runtime Environment here; you should always be installing software using "sudo aptitude install ***" or by using the graphical package manager, "Synaptic" (until you're more experienced). I assume you simply forgot to uncheck the little box on the download page. Until you're older, make sure to follow the directions in the HOWTO *exactly*. 
> 
How exactly do I burn a CD, using the CD/DVD Creator, of the OOo 2.2? When I put a blank CD in the drive and click 'burn a data CD' , the program opens, but the 'Write to disc' option is grayed out.

For the most part, you can't really burn a disc that has a discrete copy of a program that will run on whatever computer you put it on (if that's what you're trying to do); most programs need to be installed on the filesystem because of library dependencies and other such stuff. However, I'm not so sure that it is impossible to make this particular installation of OpenOffice.org portable. But I haven't tried it so I wouldn't know. 

Regardless of all that, if you want to copy files to a blank disc, copy the files you want to burn to the Blank CD first, and then click "Write Disc". You can't write to a disc if you didn't tell it to write anything :P. Let me know if you need more help with burning.

> 
How do I stop all ----and I do mean, all----- of my input in OOo 2.2 Writer from being in red font and underlined?
The 'font' icon in the toolbar doesn't help, cuz when I select 'black' all input remains red.
(My original reason for uninstalling OOo 2.0 and installing 2.2 was to get rid of this problem, which apparently I caused inadvertently while trying to use AutoCorrect (name?) the one that's analagous to using the TAB key in bash to complete a long word. Or was it AutoComplete?)
I look forward to hearing enlightening words from any takers ;)
Thanks in advance, Linuxians. (Oops, did I just invent a word?:) )
I'm ok, honest. ;)

This is a problem I cannot solve for you, unfortunately. My best guess would be to check that your language settings are correct, maybe? Look in Tools > Options > Language Settings. If that doesn't work, ask the forums! (Which you maybe should have done in the first place, instead of reinstalling the entire program ;) but that's okay). Create a new thread asking for help.

---

### Post by Hagar Delest on 2007-04-15
> **jonivey said:**
> How do I stop all ----and I do mean, all----- of my input in OOo 2.2 Writer from being in red font and underlined?
The 'font' icon in the toolbar doesn't help, cuz when I select 'black' all input remains red.
You should be more precise. It can be a problem with your *Default* paragraph style, with the changes record feature that is activated (if there's also a vertical line in the margin). For information, here is some helpfull tip about the font icon : [Button to change font color at cursor?]("http://www.oooforum.org/forum/viewtopic.phtml?t=50200")

---

### Post by stchman on 2007-04-17
I have a procedure for updating Openoffice.org from the 2.0 version that Edgy has to the new 2.2 version.  It is actually quite easy.

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

I also have some openoffice tweaks in my Tweaks section.

---

### Post by Hagar Delest on 2007-04-17
> **stchman said:**
> I have a procedure for updating Openoffice.org from the 2.0 version that Edgy has to the new 2.2 version.  It is actually quite easy.

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)
If you don't add the parameter *--scripts* in the alien command, the install will be done but you may face problems afterwards (I know what I'm talking about, I experienced it with and without this).

---

### Post by stchman on 2007-04-17
> **Hagar de l'Est said:**
> If you don't add the parameter *--scripts* in the alien command, the install will be done but you may face problems afterwards (I know what I'm talking about, I experienced it with and without this).


I have personally used this procedure on 5 different machines running Edgy and Openoffice runs beautifully.  I have only used Edgy.

So you are saying that I should use this command:

sudo alien --scripts -d *.rpm

What problems could you run into if not using the --scripts parameter?

Thanks

---

### Post by stchman on 2007-04-17
> **jfinkels said:**
> Yes, I'm afraid so: to my knowledge, if you want to uninstall OOo2.0, you will have to uninstall the *ubuntu-desktop* meta-package, (for those who don't know: a meta-package is a package which is empty and merely points to other packages to install). I suppose that if you want to upgrade to Feisty from Edgy, you might choose to reinstall *ubuntu-desktop* and then upgrade because Feisty comes with OOo2.2 anyway.

The method I used to uninstall Openoffice.org 2.0 in Ubuntu is this.

I started Synaptic package manager and did a search for openoffice.org.  I then sorted by installed.  There was a series of openoffice packages installed with 2.0-ubuntu-xxxx version after them.  I right clicked on all the green boxes and checked mark for complete removal.

Was OO2.0 not completely removed?

Thanks

---

### Post by stchman on 2007-04-17
> **Hagar de l'Est said:**
> If you don't add the parameter *--scripts* in the alien command, the install will be done but you may face problems afterwards (I know what I'm talking about, I experienced it with and without this).

I did it your way and OO installed and loads WAY faster.  Thanks.

---

### Post by jfinkels on 2007-04-17
> **stchman said:**
> The method I used to uninstall Openoffice.org 2.0 in Ubuntu is this.

I started Synaptic package manager and did a search for openoffice.org.  I then sorted by installed.  There was a series of openoffice packages installed with 2.0-ubuntu-xxxx version after them.  I right clicked on all the green boxes and checked mark for complete removal.

Was OO2.0 not completely removed?

Thanks

If you uninstalled all openoffice.org-* version 2.0 packages without having to uninstall any other packages because of dependency issues, then that's wonderful! I just included those few others because you *may* be required to uninstall them, depending on your own particular set of installed packages (I had to uninstall these after installing openoffice.org 2.2 on a fresh install). It should be completely uninstalled.

---

### Post by Hagar Delest on 2007-04-18
> **stchman said:**
> What problems could you run into if not using the --scripts parameter?
I've seen you were already convinced but just to try to be more precise about that, I've had problems with features that were simply just not effective or problems opening former files (at least a database IIRC). Sorry to be so vague, I noticed this for the 2.0 install so it's been quite a long time I last saw this.

---

### Post by stchman on 2007-04-18
> **Hagar de l'Est said:**
> I've seen you were already convinced but just to try to be more precise about that, I've had problems with features that were simply just not effective or problems opening former files (at least a database IIRC). Sorry to be so vague, I noticed this for the 2.0 install so it's been quite a long time I last saw this.

I am convinced.  The fonts in OO look way better as well.  I guess the --scripts is a must.  I have made the correction to my procedure (noting the forum here as a source) so that everyone can enjoy.

Everytime I convert one package into another I will use the --scripts parameter.

Thanks for the tip.  I have learned a great deal from this forum.

---

### Post by stchman on 2007-04-18
> **jfinkels said:**
> If you uninstalled all openoffice.org-* version 2.0 packages without having to uninstall any other packages because of dependency issues, then that's wonderful! I just included those few others because you *may* be required to uninstall them, depending on your own particular set of installed packages (I had to uninstall these after installing openoffice.org 2.2 on a fresh install). It should be completely uninstalled.


Yes I just use Synaptic.  There might be a package that OO2.0 needs left on the system, but the main OO files are gone.  I always use the "Mark for Complete Removal" option as this targets the dependencies that that particular package needs.  Now if that package has a dependency that other packages rely on it won't uninstall it.

---

### Post by jfinkels on 2007-04-19
> **stchman said:**
> Yes I just use Synaptic.  There might be a package that OO2.0 needs left on the system, but the main OO files are gone.  I always use the "Mark for Complete Removal" option as this targets the dependencies that that particular package needs.  Now if that package has a dependency that other packages rely on it won't uninstall it.

I think Synaptic will, as apt-get and aptitude do, warn you of dependency issues even if you just "Mark for Removal". When you "Mark for Complete Removal", that's the same as doing an "aptitude purge", which *I think* just deletes configuration files associated with the program in addition to uninstalling it.

---

### Post by liberalist on 2007-04-27
Thank you very much for your explanation how to install OpenOffice.org updates. It is really helpful.

---

### Post by rautamiekka on 2007-05-02
When I try to install, it complains with this output:

```
jouni@jouni-kubuntu:~/Desktop/RPMS/desktop-integration$ sudo dpkg -i openoffice.org-debian-menus_2.2-9134_all.deb
dpkg: regarding openoffice.org-debian-menus_2.2-9134_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.2-9134_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org-debian-menus_2.2-9134_all.deb
```

What to do to fix this ?

---

### Post by jfinkels on 2007-05-02
> **rautamiekka said:**
> When I try to install, it complains with this output:

```
jouni@jouni-kubuntu:~/Desktop/RPMS/desktop-integration$ sudo dpkg -i openoffice.org-debian-menus_2.2-9134_all.deb
dpkg: regarding openoffice.org-debian-menus_2.2-9134_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.2-9134_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org-debian-menus_2.2-9134_all.deb
```

What to do to fix this ?

This means that apparently openoffice-org-debian-menus provides a package called openoffice.org-unbundled which conflicts with openoffice.org-core (which you have already installed if you followed the directions as I gave them). To be honest, I don't know why you're getting this error...fortunately, though, the menu items are not really necessary. Also, you can install menu items on your own! Here's how:

**[SIZE="4"]HOW TO INSTALL MENU ITEMS FOR PROGRAMS IN OOO2.2[/SIZE]**
-----
[LIST=1]
[*]Go to "System > Preferences > Menu Layout"
[*]Select the "Office" sub-menu on the left-hand side of the interface.
[*]Select "New Item" from the right-hand side of the interface.
[*]Name this launcher "OpenOffice.org Word Processor"
[*]The command will be "/opt/openoffice.org2.2/program/swriter"
[*]If you want to choose an icon for this launcher, click on the box at left that says "No Icon" and select an icon. I'm sure the OpenOffice.org default icons are there somewhere, I just don't know where.
[*]Press "OK" and this menu item will be added. You should now be able to move this launcher wherever you want within the menu hierarchy.
[*]Repeat this process for each of the other apps for which you want menu items (i.e. scalc, sdraw, etc.)
[/LIST]

---

### Post by sadiini on 2007-05-02
[QUOTE=jfinkels;2382405]Updated 6 April 2007.

Most of this information is taken from this thread, which I posted previously: [http://www.ubuntuforums.org/showthread.php?p=2349049](http://www.ubuntuforums.org/showthread.php?p=2349049)

Ubuntu 7.04 Feisty Fawn ships with OpenOffice.org 2.2, but what if you want to install Openoffice.org 2.2 on Ubuntu 6.10 Edgy Eft over the standard OpenOffice.org 2.0 that ships with it? It's very simple; read on to find out how.

**PURPOSE**: Every once in a while, somebody asks about how to install a more recent version of OpenOffice.org, which is _**VERY EASY TO DO**_. This HOWTO will covers an easy method for installing OpenOffice.org 2.2. 

I am estonian and we have our localized version in *deb format.  

Take look at [http://l10n.openoffice.org/languages.html](http://l10n.openoffice.org/languages.html) and may be You have it too. :) 
Who knows?

---

### Post by rocketbomb on 2007-05-07
> **jfinkels said:**
> This means that apparently openoffice-org-debian-menus provides a package called openoffice.org-unbundled which conflicts with openoffice.org-core (which you have already installed if you followed the directions as I gave them). To be honest, I don't know why you're getting this error...fortunately, though, the menu items are not really necessary. Also, you can install menu items on your own! Here's how:

**[SIZE="4"]HOW TO INSTALL MENU ITEMS FOR PROGRAMS IN OOO2.2[/SIZE]**
-----
[LIST=1]
[*]Go to "System > Preferences > Menu Layout"
[*]Select the "Office" sub-menu on the left-hand side of the interface.
[*]Select "New Item" from the right-hand side of the interface.
[*]Name this launcher "OpenOffice.org Word Processor"
[*]The command will be "/opt/openoffice.org2.2/program/swriter"
[*]If you want to choose an icon for this launcher, click on the box at left that says "No Icon" and select an icon. I'm sure the OpenOffice.org default icons are there somewhere, I just don't know where.
[*]Press "OK" and this menu item will be added. You should now be able to move this launcher wherever you want within the menu hierarchy.
[*]Repeat this process for each of the other apps for which you want menu items (i.e. scalc, sdraw, etc.)
[/LIST]

I can't find the "Menu layout". There is only menu & toolbar in the menu.

---

### Post by jfinkels on 2007-05-07
> **rocketbomb said:**
> I can't find the "Menu layout". There is only menu & toolbar in the menu.

Another way to get to the menu layout editor is by opening it from the terminal. Go to the terminal ("Applications > Accessories > Terminal") and enter the following:
```

alacarte

``` 
"alacarte" is the name of the menu editor. It should open.

---

### Post by peter_from_hobart on 2007-05-11
Dear wonderful folk at Christian UBUNTU forums

Thank you for telling us newbies the commands to use.

It looks quite complicated so I will try it when I am feeling better.

Yours Sincerely & with Best Wishes,
pew

from the beautiful city of Hobart,Tasmania, Australia

Here is my totally free website:

[http://pewtas.googlepages.com](http://pewtas.googlepages.com)

--------------------------

---

### Post by Screaming Monkey on 2007-05-22
Thank you so much for this howto jfinkels.  It worked like a dream.

---

### Post by gottatrieit on 2007-05-31
I would like to thank you also, jfinkels, for this tutorial.
I have been using Ubuntu for about six months to a year (I think!)  I really don't remember when I originally installed it!
I've been "playing" around with Linux for at least three years, my first attempt at a Linux system was the purchase of SuSe 8,2.  I had problems with it, mostly a lack of knowledge on my part, and went back to microstuff.
To make a long story short, I used this tutorial to install OOo2.2 onto my Dapper machine.  It took a bit of work on my part to get it o:Dnto the system, but all in all, by following your steps and circumventing one or two, it works great!
The one I remember going "around" was the step involving the installation of the code: "cd OOF680_m14_native_packed-1_en-US.9134/".  I had opened the tar archive and it was in my downloads file, so I just pasted it into the terminal.
Again, thank you.

  And as I say about Linux: gottatrieit   You just gotta!  ):P

---

### Post by jfinkels on 2007-05-31
> **gottatrieit said:**
> I would like to thank you also, jfinkels, for this tutorial.
I have been using Ubuntu for about six months to a year (I think!)  I really don't remember when I originally installed it!
I've been "playing" around with Linux for at least three years, my first attempt at a Linux system was the purchase of SuSe 8,2.  I had problems with it, mostly a lack of knowledge on my part, and went back to microstuff.
To make a long story short, I used this tutorial to install OOo2.2 onto my Dapper machine.  It took a bit of work on my part to get it o:Dnto the system, but all in all, by following your steps and circumventing one or two, it works great!
The one I remember going "around" was the step involving the installation of the code: "cd OOF680_m14_native_packed-1_en-US.9134/".  I had opened the tar archive and it was in my downloads file, so I just pasted it into the terminal.
Again, thank you.

  And as I say about Linux: gottatrieit   You just gotta!  ):P

OpenOffice.org may have updated the files, that may be a reason for the different name. I'll look into it.

---

### Post by skeeterflea on 2007-06-20
Thhhhhank you!

---

### Post by HugoRune on 2007-06-25
Hi

I tried to install the newest openoffice using this tutorial

I am stuck at the first step with an error message, and unsure what to do.

I have a presentation due in a few days and am really afraid of breaking my system right now, that is also why I did not upgrade to feisty.

I am fighting with some bugs in openoffice that I hope this update will solve, but I have to admit that updating openoffice is not as easy as I thought it would be

(by the way, is this really the only way to do it, or am I doing this wrong? isn't there some sort of installer for this?)

Is it save to remove thunderbird-locale-en-gb, or will this break thunderbird? Do I also have to remove thunderbird-locale-jp? What happens if I remove "language-support-en", do the english language menus go away? What about "ubuntu-desktop", don't I need that?

```
$ sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-writer openoffice.org-xsltfilter  openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "openoffice.org-xsltfilter"
Couldn't find any package whose name or description matched "openoffice.org-testtool"
Couldn't find any package whose name or description matched "openoffice.org-emailmerge"
Couldn't find any package whose name or description matched "openoffice.org-onlineupdate"
Couldn't find any package whose name or description matched "openoffice.org-pyuno"
Couldn't find any package whose name or description matched "openoffice.org-kde-integration"
Couldn't find any package whose name or description matched "openoffice.org-javafilter"
Couldn't find any package whose name or description matched "openoffice.org-gnome-integration"
Couldn't find any package whose name or description matched "openoffice.org-graphicfilter"
Couldn't find any package whose name or description matched "openoffice.org-core01"
Couldn't find any package whose name or description matched "openoffice.org-core02"
Couldn't find any package whose name or description matched "openoffice.org-core03"
Couldn't find any package whose name or description matched "openoffice.org-core03u"
Couldn't find any package whose name or description matched "openoffice.org-core04"
Couldn't find any package whose name or description matched "openoffice.org-core04u"
Couldn't find any package whose name or description matched "openoffice.org-core05"
Couldn't find any package whose name or description matched "openoffice.org-core05u"
Couldn't find any package whose name or description matched "openoffice.org-core06"
Couldn't find any package whose name or description matched "openoffice.org-core07"
Couldn't find any package whose name or description matched "openoffice.org-core08"
Couldn't find any package whose name or description matched "openoffice.org-core09"
Couldn't find any package whose name or description matched "openoffice.org-core10"
The following packages are BROKEN:
  openoffice.org-help-de openoffice.org-help-en-gb openoffice.org-help-ja openoffice.org-kde openoffice.org-l10n-de openoffice.org-l10n-en-us openoffice.org-l10n-ja
  openoffice.org-style-crystal openoffice.org-thesaurus-de openoffice.org-thesaurus-de-ch
The following packages will be REMOVED:
  language-support-en openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-default openoffice.org-style-industrial openoffice.org-thesaurus-en-us openoffice.org-writer python-uno
  thunderbird-locale-en-gb ubuntu-desktop
0 packages upgraded, 0 newly installed, 23 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 281MB will be freed.
The following packages have unmet dependencies:
  openoffice.org-l10n-de: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
  openoffice.org-l10n-ja: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
  openoffice.org-thesaurus-de-ch: Depends: openoffice.org-core (>= 1.9) but it is not installable
  openoffice.org-l10n-en-us: Depends: openoffice.org-common (= 2.0.4-0ubuntu5) but it is not installable or
                                      language-support-en but it is not installable
  openoffice.org-help-en-gb: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
                             Depends: openoffice.org-writer but it is not installable
                             Depends: openoffice.org-core (>= 2.0.4~rc3) but it is not installable or
                                      language-support-en but it is not installable
  openoffice.org-thesaurus-de: Depends: openoffice.org-core (>= 1.9) but it is not installable
  openoffice.org-kde: Depends: openoffice.org-core (= 2.0.4-0ubuntu5) but it is not installable
  openoffice.org-help-de: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
                          Depends: openoffice.org-writer but it is not installable
  openoffice.org-help-ja: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
                          Depends: openoffice.org-writer but it is not installable
  openoffice.org-style-crystal: Depends: openoffice.org-common (= 2.0.4-0ubuntu5) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
language-support-en [1:6.06+20060529 (edgy, edgy, now)]
openoffice.org-common [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-core [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-help-en-us [2.0.4-0ubuntu1 (edgy, edgy, now)]
openoffice.org-java-common [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-l10n-common [2.0.4-0ubuntu1 (edgy, edgy, now)]
openoffice.org-l10n-en-gb [2.0.4-0ubuntu1 (edgy, edgy, now)]
openoffice.org-l10n-en-za [2.0.4-0ubuntu1 (edgy, edgy, now)]
openoffice.org-style-default [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-style-industrial [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-thesaurus-en-us [1:2.0.3-2ubuntu1 (edgy, edgy, now)]
openoffice.org-writer [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
python-uno [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
thunderbird-locale-en-gb [1:1.5.0.2ubuntu1-3 (edgy, edgy, now)]

Leave the following dependencies unresolved:
kubuntu-desktop recommends openoffice.org
openclipart-openoffice.org recommends openoffice.org | openoffice.org2
Score is -1036

Accept this solution? [Y/n/q/?]            
```

---

### Post by jfinkels on 2007-06-25
> **HugoRune said:**
> Hi

I tried to install the newest openoffice using this tutorial

I am stuck at the first step with an error message, and unsure what to do.

I have a presentation due in a few days and am really afraid of breaking my system right now, that is also why I did not upgrade to feisty.

I am fighting with some bugs in openoffice that I hope this update will solve, but I have to admit that updating openoffice is not as easy as I thought it would be

(by the way, is this really the only way to do it, or am I doing this wrong? isn't there some sort of installer for this?)

Is it save to remove thunderbird-locale-en-gb, or will this break thunderbird? Do I also have to remove thunderbird-locale-jp? What happens if I remove "language-support-en", do the english language menus go away? What about "ubuntu-desktop", don't I need that?

```
$ sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-writer openoffice.org-xsltfilter  openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "openoffice.org-xsltfilter"
Couldn't find any package whose name or description matched "openoffice.org-testtool"
Couldn't find any package whose name or description matched "openoffice.org-emailmerge"
Couldn't find any package whose name or description matched "openoffice.org-onlineupdate"
Couldn't find any package whose name or description matched "openoffice.org-pyuno"
Couldn't find any package whose name or description matched "openoffice.org-kde-integration"
Couldn't find any package whose name or description matched "openoffice.org-javafilter"
Couldn't find any package whose name or description matched "openoffice.org-gnome-integration"
Couldn't find any package whose name or description matched "openoffice.org-graphicfilter"
Couldn't find any package whose name or description matched "openoffice.org-core01"
Couldn't find any package whose name or description matched "openoffice.org-core02"
Couldn't find any package whose name or description matched "openoffice.org-core03"
Couldn't find any package whose name or description matched "openoffice.org-core03u"
Couldn't find any package whose name or description matched "openoffice.org-core04"
Couldn't find any package whose name or description matched "openoffice.org-core04u"
Couldn't find any package whose name or description matched "openoffice.org-core05"
Couldn't find any package whose name or description matched "openoffice.org-core05u"
Couldn't find any package whose name or description matched "openoffice.org-core06"
Couldn't find any package whose name or description matched "openoffice.org-core07"
Couldn't find any package whose name or description matched "openoffice.org-core08"
Couldn't find any package whose name or description matched "openoffice.org-core09"
Couldn't find any package whose name or description matched "openoffice.org-core10"
The following packages are BROKEN:
  openoffice.org-help-de openoffice.org-help-en-gb openoffice.org-help-ja openoffice.org-kde openoffice.org-l10n-de openoffice.org-l10n-en-us openoffice.org-l10n-ja
  openoffice.org-style-crystal openoffice.org-thesaurus-de openoffice.org-thesaurus-de-ch
The following packages will be REMOVED:
  language-support-en openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-default openoffice.org-style-industrial openoffice.org-thesaurus-en-us openoffice.org-writer python-uno
  thunderbird-locale-en-gb ubuntu-desktop
0 packages upgraded, 0 newly installed, 23 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 281MB will be freed.
The following packages have unmet dependencies:
  openoffice.org-l10n-de: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
  openoffice.org-l10n-ja: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
  openoffice.org-thesaurus-de-ch: Depends: openoffice.org-core (>= 1.9) but it is not installable
  openoffice.org-l10n-en-us: Depends: openoffice.org-common (= 2.0.4-0ubuntu5) but it is not installable or
                                      language-support-en but it is not installable
  openoffice.org-help-en-gb: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
                             Depends: openoffice.org-writer but it is not installable
                             Depends: openoffice.org-core (>= 2.0.4~rc3) but it is not installable or
                                      language-support-en but it is not installable
  openoffice.org-thesaurus-de: Depends: openoffice.org-core (>= 1.9) but it is not installable
  openoffice.org-kde: Depends: openoffice.org-core (= 2.0.4-0ubuntu5) but it is not installable
  openoffice.org-help-de: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
                          Depends: openoffice.org-writer but it is not installable
  openoffice.org-help-ja: Depends: openoffice.org-l10n-common (>= 2.0.4~rc3) but it is not installable
                          Depends: openoffice.org-writer but it is not installable
  openoffice.org-style-crystal: Depends: openoffice.org-common (= 2.0.4-0ubuntu5) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
language-support-en [1:6.06+20060529 (edgy, edgy, now)]
openoffice.org-common [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-core [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-help-en-us [2.0.4-0ubuntu1 (edgy, edgy, now)]
openoffice.org-java-common [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-l10n-common [2.0.4-0ubuntu1 (edgy, edgy, now)]
openoffice.org-l10n-en-gb [2.0.4-0ubuntu1 (edgy, edgy, now)]
openoffice.org-l10n-en-za [2.0.4-0ubuntu1 (edgy, edgy, now)]
openoffice.org-style-default [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-style-industrial [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
openoffice.org-thesaurus-en-us [1:2.0.3-2ubuntu1 (edgy, edgy, now)]
openoffice.org-writer [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
python-uno [2.0.4-0ubuntu5 (edgy-security, edgy-security, now)]
thunderbird-locale-en-gb [1:1.5.0.2ubuntu1-3 (edgy, edgy, now)]

Leave the following dependencies unresolved:
kubuntu-desktop recommends openoffice.org
openclipart-openoffice.org recommends openoffice.org | openoffice.org2
Score is -1036

Accept this solution? [Y/n/q/?]            
```

Hello HugoRune!

I'm afraid I was somewhat short-sighted when writing this tutorial and thought only about the US English versions of packages. In your specific case, please remove the following packages as well (i.e. add them to the long list of packages to remove given in the first step):```
openoffice.org-help-de openoffice.org-help-en-gb openoffice.org-help-ja openoffice.org-kde openoffice.org-l10n-de openoffice.org-l10n-en-us openoffice.org-l10n-ja openoffice.org-style-crystal openoffice.org-thesaurus-de openoffice.org-thesaurus-de-ch

```

Removing those packages should not cause any problems. Also, don't worry about the "packages not found" warnings; that just means that those packages aren't installed on your system (so they can't possible be uninstalled!).

As for these questions:> 
Is it save to remove thunderbird-locale-en-gb, or will this break thunderbird? Do I also have to remove thunderbird-locale-jp? What happens if I remove "language-support-en", do the english language menus go away? What about "ubuntu-desktop", don't I need that?
I think it should be fine to remove thunderbird-locale-en-gb, you might just have to deal with different spellings for some words (i.e. colour -> color, etc.). 

If aptitude doesn't specifically request that you remove thunderbird-locale-jp, then leave it in for now. Let me know if that causes any problems.

Although I am not certain by far, I think you should be okay remove "language-support-en". It is a metapackage, which means its only purpose is to point to other packages to be installed. If aptitude asks you to remove this or says it is broken, that means you are removing some package(s) that it points to. I'm not sure what will happen. Hopefully you know Japanese :D.

"ubuntu-desktop" is another metapackage, which means it merely 'points' to other packages to be installed. Uninstalling a program to which ubuntu-desktop points will in turn uninstall ubuntu-desktop. However, this will cause no further effect on your system. (It is said that ubuntu-desktop should be installed when you upgrade your system across versions, like 6.10 -> 7.04, but I'm not sure about what happens if you don't have it installed...you should be fine for now).

---

### Post by Madmoose on 2007-07-04
This method could be used to install any of the new updates from OO0.  Just need to copy the names of the new files! Thanks!


Moose

---

### Post by battaz on 2007-07-15
I am attempting to follow this posted how-to, and I am now on step 4.  I have just input the code:

cd desktop-integration/

after inputting the following code:

sudo dpkg -i openoffice.org-debain-menus_2.2-9119_all.deb

and I receive the following response:

dpkg: error processing openoffice.org-debain-menus_2.2-9119_all.deb (--install): cannot access archive:  No such file or directory
Errors were encountered while processing:
openoffice.org-debain-menus_2.2-9119_all.deb

I'm not sure what to do here.  I followed the thread of this post, and I attempted to use the "System > Preferences > Menu Layout" you recommended.  When I choose "New Item", all I have is the Directory Properties.  There is nowhere for me to input a command.
Is there anyway I can fix this problem, or perhaps skip this step and simply move on?

Thanks for any help you can offer.

---

### Post by rautamiekka on 2007-07-16
Heh, you have typed -debain- but it should be -debian-

---

### Post by Hagar Delest on 2007-07-16
Right. In such cases with long names, you should use the TAB key to complete the name : type the command and the beginning of the file name, then hit TAB, the name will be completed automatically (full completion depends on presence of other files with the same beginning).

---

### Post by battaz on 2007-07-16
Thanks for the help on my last post.  It worked.  Now, I've come across another problem.  I'm hoping everyone can be as much help here as well.

I've input the following code:

/opt/openoffice.org2.2/program/swriter

And now, I'm getting this error in my terminal:

[Java framework] Invalid value for bootstrap variable: UNO_JAVA_JFW_VENDOR_SETTINGSjavaldx failed!
/opt/openoffice.org2.2/program/soffice.bin: symbol lookup error: /opt/openoffice.org2.2/program/libsvt680li.so: undefined symbol: ,ZN8TextViewlldragDropEndERKN3com3sun4star12datatransfer3dnd19DragSourceDropEventE

I'm hoping that I am almost finished, and I can start writing again.  Anyway, thanks again for any help you can offer.

---

### Post by jfinkels on 2007-07-16
> **battaz said:**
> Thanks for the help on my last post.  It worked.  Now, I've come across another problem.  I'm hoping everyone can be as much help here as well.

I've input the following code:

/opt/openoffice.org2.2/program/swriter

And now, I'm getting this error in my terminal:

[Java framework] Invalid value for bootstrap variable: UNO_JAVA_JFW_VENDOR_SETTINGSjavaldx failed!
/opt/openoffice.org2.2/program/soffice.bin: symbol lookup error: /opt/openoffice.org2.2/program/libsvt680li.so: undefined symbol: ,ZN8TextViewlldragDropEndERKN3com3sun4star12datatransfer3dnd19DragSourceDropEventE

I'm hoping that I am almost finished, and I can start writing again.  Anyway, thanks again for any help you can offer.

Try this:```
sudo aptitude reinstall sun-java6-bin sun-java6-jre python-uno
```
Then this:```
cd /opt/openoffice.org2.2/program
```
Then```
./swriter
```

If that doesn't work, come back.

---

### Post by battaz on 2007-07-17
I input the commands as you posted them, and now I'm getting this error:

[Java framework] Invalid value for bootstrap variable: UNO_JAVA_JFW_VENDOR_SETTINGSjavaldx failed!
/opt/openoffice.org2.2/program/soffice.bin: symbol lookup error: /opt/openoffice.org2.2/program/libsvt680li.so: undefined symbol: ,ZN8TextViewlldragDropEndERKN3com3sun4star12datatransfer3dnd19DragSourceDropEventE

Any help would be greatly appreciated, and thanks for all of your help so far.

---

### Post by jfinkels on 2007-07-17
> **battaz said:**
> I input the commands as you posted them, and now I'm getting this error:

[Java framework] Invalid value for bootstrap variable: UNO_JAVA_JFW_VENDOR_SETTINGSjavaldx failed!
/opt/openoffice.org2.2/program/soffice.bin: symbol lookup error: /opt/openoffice.org2.2/program/libsvt680li.so: undefined symbol: ,ZN8TextViewlldragDropEndERKN3com3sun4star12datatransfer3dnd19DragSourceDropEventE

Any help would be greatly appreciated, and thanks for all of your help so far.

...I'm afraid I don't know how to solve this problem. It seems to be a Java problem, and there's nothing I can really do from here.

---

### Post by battaz on 2007-07-18
Okay, thanks for all of your help.  I suppose I will start looking for some other word processor.

---

### Post by jfinkels on 2007-07-18
> **battaz said:**
> Okay, thanks for all of your help.  I suppose I will start looking for some other word processor.

Try abiword.```
sudo aptitude install abiword
```

In fact, you can install the entire gnome-office suite of applications by doing:```
sudo aptitude install gnome-office
```

I prefer this because it doesn't depend on java, which has a "restrictive" license (i.e. contrary to the ideals of Ubuntu).

---

### Post by ishwar on 2007-11-20
thanx a million.

this thread is one of the perfect place for begginers.. i installed Oo following u r suggestion on my dapper everything went well.. awesome..

i found a zipped deb package of Oo 2.3 from the open office website.. i think it can decrease considerable amount of hassle.  

thank u for all your valuable postings:guitar:

---

### Post by helpdeskdan on 2007-12-30
2.3's out now.  Just uninstall using:
sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-writer openoffice.org-xsltfilter  openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb

Download:
[http://ftp-atl.osuosl.org/pub/openoffice/stable/2.3.1/OOo_2.3.1_LinuxIntel_install_en-US_deb.tar.gz](http://ftp-atl.osuosl.org/pub/openoffice/stable/2.3.1/OOo_2.3.1_LinuxIntel_install_en-US_deb.tar.gz)

And install via the deb via these instructions:
[http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html](http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html)

(scroll down to update)

do a sudo killall gnome-panel when you are done, and everything works great - even the menus!

---

### Post by helpdeskdan on 2007-12-30
Oh, and thanks - I had a terrible time figuring out the uninstall!

---

