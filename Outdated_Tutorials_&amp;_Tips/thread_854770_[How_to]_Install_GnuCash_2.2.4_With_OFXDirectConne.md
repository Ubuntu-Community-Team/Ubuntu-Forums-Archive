---
title: "[How to] Install GnuCash 2.2.4 With OFXDirectConnect and HBCI Support"
date: 2008-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by undadecor on 2008-07-09
This guide should give you a working installation of GnuCash 2.2.4 with OFXDirectConnect and HBCI support.

We will go through five steps:
[LIST=1]
[*]Download .deb packages
[*]Remove conflicting packages
[*]Enable Feisty repository
[*]Install .deb packages
[*]Test installation
[/LIST]

**1.  Download .deb packages**
There are four .deb packages that you will need.  Download each of them to a location of your choice.
[LIST=1]
[*]The aqbanking wizard that will help you setup your OFXDirectConnect connection:  [http://tundrius.com/packages/aqbanking16-qt-wizard_2.2.3-3ubuntu1_i386.deb]("http://tundrius.com/packages/aqbanking16-qt-wizard_2.2.3-3ubuntu1_i386.deb")
[*]The aqbanking ofx plugin that will enable OFXDirectConnect:  [http://tundrius.com/packages/libaqbanking-ofx0_2.2.3-3ubuntu1_i386.deb]("http://tundrius.com/packages/libaqbanking-ofx0_2.2.3-3ubuntu1_i386.deb")
[*]The GnuCash common package:  [http://tundrius.com/packages/gnucash-common_2.2.4-1ubuntu1_all.deb]("http://tundrius.com/packages/gnucash-common_2.2.4-1ubuntu1_all.deb")
[*]The GnuCash package itself:  [http://tundrius.com/packages/gnucash_2.2.4-1ubuntu1_i386.deb]("http://tundrius.com/packages/gnucash_2.2.4-1ubuntu1_i386.deb")
[/LIST]

**2.  Remove conflicting packages**
There is one package that, if installed, will present a conflict with the packages we are about to install.  This is the package called libaqofxconnect4.  So if you have it, or if you are not sure, click on the "Applications" menu, then the "Accessories" submenu, and then on the application titled "Terminal".  Type the following command in and then hit Enter.
```
sudo apt-get remove libaqofxconnect4
```

**3.  Enable Feisty repository**
In order to install the dependency packages we must enable an additional repository.  To do this click on the "System" menu, then the "Administration" submenu, and then the "Software Sources" option.  Type in your root password, hit Enter.  A window titled "Software Sources" should open.  Click on the "Third-Party Software" tab.  Click on the "Add..." button at the bottom.  Type the following in the box that pops up.
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
```
Click the "Add Source" button.  Click the "Close" button on the "Software Sources" window.  An alert should pop up.  Click the "Reload" button on the popup.  Wait until it reloads and then closes the "Software Source" window.

**4.  Install .deb packages**
Note:  Make sure you install the package for gnucash-common before the package for gnucash.
[LIST=1]
[*]Double-click on the .deb package you downloaded called "**aqbanking16-qt-wizard_2.2.3-3ubuntu1_i386.deb**" and install it.
[*]Double-click on the .deb package you downloaded called "**libaqbanking-ofx0_2.2.3-3ubuntu1_i386.deb**" and install it.
[*]Double-click on the .deb package you downloaded called "**gnucash-common_2.2.4-1ubuntu1_all.deb**" and install it.
[*]Double-click on the .deb package you downloaded called "**gnucash_2.2.4-1ubuntu1_i386.deb**" and install it.
[/LIST]

**5.  Test installation**
Click on the menu "Applications", then on the submenu "Office", and then on the application "GnuCash Finance Management".  If this is your first time running GnuCash you should see a configuration wizard open.  When you are past the configuration wizard and at the main window of GnuCash, click on the menu "Tools" and then on the option "Online Banking Setup..."  Click "Forward" and then click "Start AqBanking Wizard".  If a menu pops up titled "Configuration" then your installation was probably successful.

Information for getting the OFXDirectConnect plugin configured for your specific bank is located here:
[http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2]("http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2") 
and here:
[http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings]("http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings")

**Changelog**
07/10/2008 - Fixed a typo

---

### Post by yhbin on 2008-07-23
Thanks for the "How to". For an Ubuntu newbie (like me) it was easier to follow than trying to recompile the program. 

I added the following to prevent Update Manager from overwriting and removing the OFX feature.  

```

echo "gnucash hold" | sudo dpkg --set-selections
echo "gnucash-common" | sudo dpkg --set-selections

```

---

### Post by megandy on 2008-07-27
Thank you for the manual. Unfortunately, I cannot add a new user in the aqbanking setup. When I try to do so, I get the following logging statements:

3:2008/07/27 16-42-02: (null)(11947): provider.c:  194: Deinit done
4:2008/07/27 16-42-02: (null)(11966):qt3_wizard.cpp:   47: Internationalisation is not available for your language
6:2008/07/27 16-42-02: (null)(11966):qbanking.cpp:  863: Internationalisation is not available for your language en_US.UTF-8
6:2008/07/27 16-42-02: (null)(11966):qbanking.cpp:  911: Registering cfg module plugin manager
6:2008/07/27 16-42-10: (null)(11966):qbselectbackend.cpp:  110: No long HTML description
3:2008/07/27 16-42-11: (null)(11966):qbcfgtabpageusers.cpp:  149: Selected backend: aqhbci
6:2008/07/27 16-42-13: (null)(11966):selectmode.cpp:   67: Selected 5
3:2008/07/27 16-42-13:gwen(11966): plugin.c:  320: Plugin "pintan" not found.
3:2008/07/27 16-42-13:aqhbci(11966):medium.c:  377: Plugin not found
3:2008/07/27 16-42-13: (null)(11966):userwizard.cpp:   76: Could not mount medium (-7)
3:2008/07/27 16-42-13: (null)(11966):qbcfgtabpageusers.cpp:  157: No user created (-9)


I think that the statement with "Plugin "pintan" not found." is important as I'm trying to add new user with pin/tan authentication.

Any ideas?

---

### Post by CFBauer on 2008-08-28
I ran into dependncy problems after following the steps above, the .debs couldn't find libaqbanking16.  The good news is libaqbanking20plugins and libaqbanking20plugins-qt are available, and I installed them.  

Unfortunately, there is no "Tools > Online banking setup" option, or a "Tools > HBCI setup" option.

I wonder if the problems is libaqofxconnect.  I tried removing it as mentioned in the guide but this did not solve my previously mentioned dependency problems.

---

### Post by CFBauer on 2008-08-28
Well I found libaqbanking16, the oder version of libaqbanking20 in the current repos. Then I followed the guide as described, but still now "Tools > Online Banking" or similar option.  I find this weird, since under "preferences" there's an online banking set of options.  Weird.

---

### Post by Jive Turkey on 2008-09-09
Thanks, it almost works.  I can set up the tool using the aqbanking wizard but when I run get balance from the actions menu I get this:
```
3:2008/09/09 18-48-00:(null)(3140):provider.c:  735: Port is: 443
3:2008/09/09 18-48-00:gwen(3140):directory_all.c:  299: Trying "/etc/gwen-public-ca.crt"
3:2008/09/09 18-48-00:gwen(3140):directory_all.c:  306: File "gwen-public-ca.crt" found in folder "/etc"
3:2008/09/09 18-48-00:(null)(3140):provider.c: 1168: Error parsing data: -1
3:2008/09/09 18-48-08:(null)(3140):provider.c:  194: Deinit done

```
...and gnucash says "Error executing backend's queue" and offers continue or abort buttons and neither gets the balance.
I've tried toggling/untoggling each option, not sure what the problem is, any ideas?

---

### Post by davescafe on 2008-09-13
I'm in the same situation. I followed these directions but when I try to download transactions or a balance, I receive the error, "error executing backend's queue".

---

### Post by Jive Turkey on 2008-09-15
Ok, just finished dancing around after getting this to work, I'm using a fresh install of x64 Hardy, and I've adapted this guide([http://wiki.gnucash.org/wiki/BuildGutsy]("http://wiki.gnucash.org/wiki/BuildGutsy")) to compile 2.2.6 from source, along with the required dependencies.

Here is what I did: 
1. get source packeges for:
    a. gwenhywfar-2.6.2 [http://sourceforge.net/projects/gwenhywfar]("http://sourceforge.net/projects/gwenhywfar")
    b. aqbanking-2.3.3 [http://sourceforge.net/projects/aqbanking]("http://sourceforge.net/projects/aqbanking")
    c. gnucash-2.2.6 [http://www.gnucash.org/pub/gnucash/sources/stable/gnucash-2.2.6.tar.bz2]("http://www.gnucash.org/pub/gnucash/sources/stable/gnucash-2.2.6.tar.bz2")

2. Run the following commands:
```
sudo apt-get install build-essential devscripts fakeroot checkinstall
sudo apt-get build-dep libgwenhywfar
```

3. Extract Each folder to its own directory
    a. for gwenhywfar, run these commands in a terminal 
```
cd /the/dir/to/gwen/src
./configure
fakeroot checkinstall -D --install=no

```
*watch for errors when you run ./configure,  there may be some missing dependencies, if configure complains go hunt down the packages you need with synaptic.  Once you get it to work install the .deb package you created with the checkinstall command, you will be prompted to answer y/n to create a doc file (i answered yes) and enter a description, the defaults(just hit enter) worked for me.
    b. for aqbanking:
    I think most of our problems are the result of this package, it has a non-free binary in it which is why we cant have working gnucash in the repos, I think a restricted version in the repos would be nice, but that may not be legal.
   Run:```
sudo apt-get build-dep libaqbanking
sudo apt-get install libssl-dev
sudo apt-get remove ofx libofx #we are going to get older ones in the next step
```
    From [http://wiki.gnucash.org/wiki/BuildGutsy]("http://wiki.gnucash.org/wiki/BuildGutsy")
    > Add a repository that carries libofx 0.8.x in my case it was: ftp.osuosl.org 
deb [http://ftp.osuosl.org/pub/ubuntu](http://ftp.osuosl.org/pub/ubuntu) gutsy main universe
Then force and lock version of libofx-dev to version 0.8.2 - Synaptic will do this (you may need to add libofx3 package)
Download source [http://sourceforge.net/projects/aqbanking](http://sourceforge.net/projects/aqbanking)
./configure --disable-chipcard-client --disable-chipcard-client-test --with-backends="aqhbci aqdtaus aqofxconnect" --with-frontends="cbanking g2banking qbanking"
make
sudo make install
  I actually just downloaded the apropriate packages libofx3_0.8.2.3 and libofx3_0.8.2.3-dev for my architecture from [http://ftp.osuosl.org/pub/ubuntu/pool/universe/libo/libofx/]("http://ftp.osuosl.org/pub/ubuntu/pool/universe/libo/libofx/")
   after enabling the suggested repository.  Configure gave me errors and I had to hunt down some seemingly random QT3 packages like qt designer (qt ui?).  Eventually it worked but checkinstall coughed up hairballs and wouldn't create a .deb. so I had to use "make install." and it worked.
    c. Lastly, gnucash:
```
sudo apt-get build-dep gnucash
cd /dir/with/gnucash/src
./configure --enable-hbci --enable-ofx --with-backends="aqhbci aqdtaus aqofxconnect" --with-frontends="cbanking g2banking qbanking"
##again watch for missing dependencies and resolve them.
fakeroot checkinstall -D --install=no
```
Install the .deb package you made and enjoy online banking w/ ofx directconnect!
I also locked my versions of libgwen, libofx, and gnucash in synaptic so they aren't steamrolled by hardy's premature adoption of aqbanking3 in a future update.

---

### Post by CFBauer on 2008-10-03
> **CFBauer said:**
> Well I found libaqbanking16, the oder version of libaqbanking20 in the current repos. Then I followed the guide as described, but still now "Tools > Online Banking" or similar option.  I find this weird, since under "preferences" there's an online banking set of options.  Weird.
Turns out it was just easier to update to gnucash 2.2.6 using the repository here:

[http://ppa.launchpad.net/gnucash/ubuntu](http://ppa.launchpad.net/gnucash/ubuntu)

Cheers.

---

