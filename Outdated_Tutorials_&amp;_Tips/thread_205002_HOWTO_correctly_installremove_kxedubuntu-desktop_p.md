---
title: "HOWTO: correctly install/remove k/x/ed/ubuntu-desktop packages"
date: 2006-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by user1397 on 2006-06-27
This how-to is for correctly installing and/or removing the x/k/ed/ubuntu-desktop meta packages.

NOTE: No matter what distribution you have installed (ubuntu/kubuntu/xubuntu/edubuntu), you can have all four meta packages at the same time, and switch between them all the time.

NOTE: Meta packages are just packages that point to many other packages.  So, if you remove the ubuntu-desktop package (with apt-get or synaptic) even though you have ubuntu installed, nothing will happen.  All the packages will remain there, just the pointer ubuntu-desktop package will be gone, but essentially nothing will be removed.  If installed with aptitude, like this guide, the meta package does get completely removed, along with all the packages it points to.

This is the best way to do it, because it is a lot easier to remove one of the desktop environments later using this method, if you don't want one of them anymore.

First of all, open a terminal:
gnome (ubuntu/edubuntu): Applications > Accessories > Terminal
kde (kubuntu): KMenu > System > Konsole
xfce (xubuntu): Applications > Terminal

[SIZE=5]**The Guide**[/SIZE]

[COLOR=DarkOrange]Ubuntu (Gnome):[/COLOR]
To install: 
```
sudo aptitude update&&sudo aptitude install ubuntu-desktop
```To remove it: ```
sudo aptitude remove ubuntu-desktop
```

[COLOR=Blue]Kubuntu (Kde):[/COLOR]
To install: 
```
sudo aptitude update&&sudo aptitude install kubuntu-desktop
```To remove it: ```
sudo aptitude remove kubuntu-desktop
```

[COLOR=Black]Xubuntu (Xfce):[/COLOR]
To install: 
```
sudo aptitude update&&sudo aptitude install xubuntu-desktop
```To remove it: ```
sudo aptitude remove xubuntu-desktop
```

[COLOR=SeaGreen]Edubuntu (Gnome also):[/COLOR]
To install: 
```
sudo aptitude update&&sudo aptitude install edubuntu-desktop
```To remove it: ```
sudo aptitude remove edubuntu-desktop
```NOTE: Again to emphasize, since we used aptitude to install these packages, **all packages will be removed**, not just the meta package.

Also, if you installed the following using **apt-get** (which is what synaptic package manager uses) instead of **aptitude**, you might want to try these guides to get rid of all extra packages that came bundled with the desktop environment packages:
To have pure gnome go _[here]("http://www.psychocats.net/ubuntu/puregnome.php")_
For pure kde go _[here]("http://www.psychocats.net/ubuntu/purekde.php")_
For pure xfce go _[here]("http://www.psychocats.net/ubuntu/purexfce.php")_

[SIZE=4]Helpful Stuff:[/SIZE]

To login using a different desktop environment, you would log out, choose options > session, and choose your desktop environment of choice.  You can make it your default or not if you want to.

NOTE: If you install the k/x/ed/ubuntu-desktop package, there's a little bug where the splash screen (the boot-up and shut-down screen) gets taken over by any of the other desktop environments you have installed.  If you want your old splash screen back, just paste this into a terminal: ```
sudo update-alternatives --config usplash-artwork.so
```Choose usplash-default.so for the default brown ubuntu splash, or choose whichever one you like. Then paste this: ```
sudo dpkg-reconfigure linux-image-`uname -r`
```and you're all set.

To change your default display manager (login window), paste this if you have x/ed/ubuntu: ```
sudo dpkg-reconfigure gdm
``` or this if you have kubuntu:
```
sudo dpkg-reconfigure kdm
```and choose whichever one you would like.

---

### Post by rav on 2006-08-07
i tried to install kde and got this error please help me

RReading package lists... 0
%


Reading package lists... 10
0%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... Done


Reading extended state information... 0
%
Reading extended state information... 95
%

Reading extended state information       


Initializing package states... 0%
 


Initializing package states... Done

Couldn't find any package whose name or description matched "kubuntu-desktop"
The following packages have been kept back:
  base-config binutils binutils-static bogofilter bogofilter-bdb 
  bogofilter-common cpio eog evms evms-ncurses fetchmail firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnupg gthumb 
  gtk2-engines-pixbuf info irssi-text libcairo2 libcurl3 libevms-2.5 
  libfreetype6 libgd2-noxpm libgda2-3 libgda2-common libgimp2.0 libgnutls11 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libkpathsea3 libmagick6 
  libmysqlclient12 libmysqlclient14 libnspr4 libnss3 libperl5.8 
  libpoppler0c2 libpoppler0c2-glib libpq4 librpm4 libsasl2 libsasl2-modules 
  libsmbclient libssl0.9.7 libtasn1-2 libtiff4 libtotem-plparser0 linux-386 
  linux-image-386 linux-restricted-modules-386 
  linux-restricted-modules-common login mysql-common openoffice.org2 
  openoffice.org2-base openoffice.org2-calc openoffice.org2-common 
  openoffice.org2-core openoffice.org2-draw openoffice.org2-evolution 
  openoffice.org2-gnome openoffice.org2-impress openoffice.org2-java-common 
  openoffice.org2-l10n-en-us openoffice.org2-math openoffice.org2-writer 
  openssh-client passwd perl perl-base perl-modules pmount ppp python-pgsql 
  python-uno python2.4-pgsql rhythmbox rpm samba-common serpentine 
  smbclient ssh-askpass-gnome sudo tar totem totem-gstreamer ttf-opensymbol 
  unzip wget x-window-system-core xbase-clients xchat xchat-common 
  xorg-common xserver-common xserver-xorg xserver-xorg-core 
  xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati 
  xserver-xorg-driver-chips xserver-xorg-driver-cirrus 
  xserver-xorg-driver-cyrix xserver-xorg-driver-dummy 
  xserver-xorg-driver-fbdev xserver-xorg-driver-glide 
  xserver-xorg-driver-glint xserver-xorg-driver-i128 
  xserver-xorg-driver-i740 xserver-xorg-driver-i810 
  xserver-xorg-driver-imstt xserver-xorg-driver-mga 
  xserver-xorg-driver-neomagic xserver-xorg-driver-newport 
  xserver-xorg-driver-nsc xserver-xorg-driver-nv 
  xserver-xorg-driver-rendition xserver-xorg-driver-s3 
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage 
  xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis 
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga 
  xserver-xorg-driver-trident xserver-xorg-driver-tseng 
  xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-driver-vga 
  xserver-xorg-driver-via xserver-xorg-driver-vmware 
  xserver-xorg-input-acecad xserver-xorg-input-aiptek 
  xserver-xorg-input-calcomp xserver-xorg-input-citron 
  xserver-xorg-input-digitaledge xserver-xorg-input-dmc 
  xserver-xorg-input-dynapro xserver-xorg-input-elographics 
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen 
  xserver-xorg-input-kbd xserver-xorg-input-magellan 
  xserver-xorg-input-microtouch xserver-xorg-input-mouse 
  xserver-xorg-input-mutouch xserver-xorg-input-palmax 
  xserver-xorg-input-penmount xserver-xorg-input-spaceorb 
  xserver-xorg-input-summa xserver-xorg-input-tek4957 
  xserver-xorg-input-void xserver-xorg-input-wacom xutils 
0 packages upgraded, 0 newly installed, 0 to remove and 159 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Writing extended state information... 0%
Writing extended state information... Done

Reading package lists... 0%              
 
Reading package lists... 100%

Reading package lists... Done

Building dependency tree... 0%

Building dependency tree... Done

Reading extended state information... 0%

Reading extended state information       

Initializing package states... 0% 

Initializing package states... Done

---

### Post by user1397 on 2006-08-07
are you running breezy or dapper?

first follow this guide to get a good sources.list: [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

Then maybe you want to try this if you get a GPG error:

# go to apt folder
```
 cd /etc/apt
``` 
# Back up current sources.list
```
sudo cp sources.list sources.list_backup
``` 
# make an empty sources.list
```
 > sources.list
``` 
# update with your empty repositories list
```
sudo aptitude update
``` 
# revert to saved list
```
sudo cp sources.list_backup sources.list
``` 
# update again and this time you should get no errors
```
sudo aptitude update
```

---

### Post by Leigh on 2006-08-07
I'm interested in trying Kubuntu and Xubuntu, however, just a question regarding this guide. You advise typing ```
sudo aptitude update
``` before doing anything. I am currently running Breezy, will this command upgrade me to Dapper? I'd rather stay with my current set up if possible.

---

### Post by user1397 on 2006-08-08
> **Leigh said:**
> I'm interested in trying Kubuntu and Xubuntu, however, just a question regarding this guide. You advise typing ```
sudo aptitude update
``` before doing anything. I am currently running Breezy, will this command upgrade me to Dapper? I'd rather stay with my current set up if possible.No that command only updates the repository list, it is just like **sudo apt-get update**, but instead we're using aptitude and not apt.  I found aptitude to be more suitable for installing programs in the terminal, because it takes care of dependencies a whole lot better than apt.

The command for upgrading to dapper would be **sudo aptitude dist-upgrade**, but it is not that simple.  You would have to do some other stuff before performing that command to upgrade to dapper.  A good guide on that is here: [http://www.psychocats.net/ubuntu/dapper.php](http://www.psychocats.net/ubuntu/dapper.php)

---

### Post by duaneb on 2006-08-08
so how can I set xfce as the default?

---

### Post by user1397 on 2006-08-08
> **duaneb said:**
> so how can I set xfce as the default?at the login screen, choose options > session > xfce, and then it asks you if you want it to be the default.  Select yes and you're ready to go.

---

### Post by bhoughton on 2006-08-11
Went ahead and installed XFCE and KDE as posted above and set up the splash screen to be the Ubuntu default, all worked fine until this morning when I resumed from a hibernation and noticed that the startup is showing Xubuntu and their colors...

How do I change this back to the Ubuntu graphics?

---

### Post by user1397 on 2006-08-11
> **bhoughton said:**
> Went ahead and installed XFCE and KDE as posted above and set up the splash screen to be the Ubuntu default, all worked fine until this morning when I resumed from a hibernation and noticed that the startup is showing Xubuntu and their colors...

How do I change this back to the Ubuntu graphics?do you mean the splash screen (where that little bar progresses to the right and all the processes are starting up)?  Or the login screen (where you would type your username and password)? Or both?

---

### Post by bhoughton on 2006-08-11
Sorry, I mean the splash screen "where the little bar progresses to the right and all the processes are starting up".  

I was able to change the splash screen with the information provided above.

Thanks...

---

### Post by bhoughton on 2006-08-11
Crazy enough, after running the dpkg-reconfigure command this morning, here is my current splash issue...

- upon starting up, I see the default Ubuntu progress bar with list of items being processed
- upon loading the splash screen to log in, I am presented with the XFCE screen
- upon logging into Gnome and then logging out or restarting, the progress bar that started up with the default Ubuntu look appears to be the XFCE look

I have tried changing the splash with "sudo update-alternatives --config usplash-artwork.so" and see that (1) ubuntu is marked as default (*) and when I choose (1), it is still XFCE.  I notice that (2) XFCE is marked with a "+" symbol.  

This isn't a major problem, but it is slightly annoying.

I do have a splash screen option in my preferences (something I installed) but it doesn't have any installed to change yet.

Any thoughts would be greatly appreciated.

Regards...

---

### Post by user1397 on 2006-08-11
> **bhoughton said:**
> Crazy enough, after running the dpkg-reconfigure command this morning, here is my current splash issue...

- upon starting up, I see the default Ubuntu progress bar with list of items being processed
- upon loading the splash screen to log in, I am presented with the XFCE screen
- upon logging into Gnome and then logging out or restarting, the progress bar that started up with the default Ubuntu look appears to be the XFCE look

I have tried changing the splash with "sudo update-alternatives --config usplash-artwork.so" and see that (1) ubuntu is marked as default (*) and when I choose (1), it is still XFCE.  I notice that (2) XFCE is marked with a "+" symbol.  

This isn't a major problem, but it is slightly annoying.

I do have a splash screen option in my preferences (something I installed) but it doesn't have any installed to change yet.

Any thoughts would be greatly appreciated.

Regards...okay the + symbol indicates the default selection, so I guess that the xfce splash is the default one.  If you have picked the default ubuntu splash as your default it should work.  I think it might have to do more with your login screen, so follow my other command, the one about the default display manager, and see if that works for you.

---

### Post by skipo on 2006-08-13
I tried xubuntu but went back to ubuntu. Now when I log in I get the xubuntu login screen.

I tried the "sudo update-alternatives --config usplash-artwork.so" but that didn't help. It gave this message:

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.

Then I tried the "sudo dpkg-reconfigure linux-image-`uname -r`". Still the xubuntu login screen. Then I reconfigured the gdm, but I still get the xubuntu login screen.

How do I get the Ubuntu login screen back?

---

### Post by skipo on 2006-08-13
> **skipo said:**
> 
How do I get the Ubuntu login screen back?

Now when I think of it, there is gdmsetup that might do the trick... ;)

---

### Post by user1397 on 2006-08-13
> **skipo said:**
> Now when I think of it, there is gdmsetup that might do the trick... ;)also, try messing around with system > administration > login window

---

### Post by toykilla on 2006-08-14
Both KDE and Gnome desktops work, but now when i boot up i see the Kubuntu loading screen (where it shows all the services starting up). How can I change this back to Ubuntu loading screen?

---

### Post by user1397 on 2006-08-14
> **toykilla said:**
> Both KDE and Gnome desktops work, but now when i boot up i see the Kubuntu loading screen (where it shows all the services starting up). How can I change this back to Ubuntu loading screen?please read the bottom part of my guide to solve your problem, you can't miss it.

---

### Post by rpalyvoda on 2006-08-14
Hi,

I use right now Ubuntu, but I'd like to try again KDE which should have changed a lot since I last used it.

So, my stupid question is:

If I follow this how-to, what shall I get a clean KDE desktop, or something that looks a little bit like KDE but with all of my current Gnome programs (totem, nautilus etc).

Actually, I'm interested in trying a clean KDE, so may be it'd be better for me to install Kubuntu on a separate partition?

---

### Post by glennric on 2006-08-14
> **erik1397 said:**
> also, try messing around with system > administration > login window

"system > administration > login window" is merely the menu shortcut for starting gdmsetup.

---

### Post by user1397 on 2006-08-14
> **rpalyvoda said:**
> Hi,

I use right now Ubuntu, but I'd like to try again KDE which should have changed a lot since I last used it.

So, my stupid question is:

If I follow this how-to, what shall I get a clean KDE desktop, or something that looks a little bit like KDE but with all of my current Gnome programs (totem, nautilus etc).

Actually, I'm interested in trying a clean KDE, so may be it'd be better for me to install Kubuntu on a separate partition?your question is not stupid, its quite legitimate. 

now, if you install kde (kubuntu) over gnome (ubuntu) all of the gnome programs will appear along with the kde programs in the kubuntu main menu.  So, if you want a clean kde, i would say try the live cd of kubuntu (desktop cd they call it)  or like you said, try it on a different partition.

---

### Post by user1397 on 2006-08-14
> **glennric said:**
> "system > administration > login window" is merely the menu shortcut for starting gdmsetup.ahh, now i know something new.

---

### Post by pjrandew on 2006-09-19
I don't understand this command:

sudo dpkg-reconfigure linux-image-`uname -r`

Is `uname -r` as substitude for....?

---

### Post by user1397 on 2006-09-19
> **pjrandew said:**
> I don't understand this command:

sudo dpkg-reconfigure linux-image-`uname -r`

Is `uname -r` as substitude for....?no you dont substitue anything, you paste that exact command.

---

### Post by user1397 on 2006-10-23
***I have updated the guide, now it's a little easier to follow, i think.

---

### Post by phantom5 on 2006-10-26
I am a newbie to Linux and have been impressed with UBUNTU.  The Gnome desktop is fine but I would like to try the KDE desktop.  I followed your instructions using Aptitude and all seemed well.  I get the Kububtu splash screen and all services get the ok except for 'reloading postfix' which fails.  When I choose a KDE session from the login screen menu I get 'Could not start kstartconfig.  Check your installation'.  Have used your link and code to return to pure ubuntu then tried installing kubuntu again with the same result.  What am I doing wrong or am I missing something?

---

### Post by user1397 on 2006-10-26
> **phantom5 said:**
> I am a newbie to Linux and have been impressed with UBUNTU.  The Gnome desktop is fine but I would like to try the KDE desktop.  I followed your instructions using Aptitude and all seemed well.  I get the Kububtu splash screen and all services get the ok except for 'reloading postfix' which fails.  When I choose a KDE session from the login screen menu I get 'Could not start kstartconfig.  Check your installation'.  Have used your link and code to return to pure ubuntu then tried installing kubuntu again with the same result.  What am I doing wrong or am I missing something?i'm wondering if your kde was ever installed correctly.  how long did it take you to download and install kubuntu-desktop?

---

### Post by phantom5 on 2006-10-27
Thanks for quick reply.  It took quiet a few mins to download and install - sorry I cannot be more precise - and I answered a number of question screens along the way.  Many packages were downloaded and many of them appear on the applications/accessories menu plus odd entries in the system/preferences menu.  Is there some kind of configuration file I should have tweaked?  Why I say this is that all appears to be correct (as far as I can tell) but the kstartconfig could not be started.  Your help in trying to resolve this problem is much appreciated.

---

### Post by user1397 on 2006-10-27
> **phantom5 said:**
> Thanks for quick reply.  It took quiet a few mins to download and install - sorry I cannot be more precise - and I answered a number of question screens along the way.  Many packages were downloaded and many of them appear on the applications/accessories menu plus odd entries in the system/preferences menu.  Is there some kind of configuration file I should have tweaked?  Why I say this is that all appears to be correct (as far as I can tell) but the kstartconfig could not be started.  Your help in trying to resolve this problem is much appreciated.man a few minutes?  you must have a fast internet connection.  it usually would take me likeat least ...umm actually i forgot exactly how long it took, but it must have been around more than 30 minutes.  o well.  

no you shouldn't have to tweak any config file, all should work.  have you installed kubuntu again?  do you still want to try kubuntu?  if yes, follow my kubuntu installation advice.  also, try this in a terminal: ```
sudo apt-get install -f
```that might fix some problems. 

i really don't know what the kstartconfig thing is, it's not a package (i've searched for it myself in the ubuntu package search website, here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)** )**

---

### Post by phantom5 on 2006-10-29
Again, thanks for your help.  I have now returned to pure ubuntu using your code and your fix for the splash screen bug.  I would still like to try kubuntu so will follow your advice and have another try.  This time I will take note of how long it takes and will get back to you to let you know how I get on.

---

### Post by user1397 on 2006-10-29
> **phantom5 said:**
> Again, thanks for your help.  I have now returned to pure ubuntu using your code and your fix for the splash screen bug.  I would still like to try kubuntu so will follow your advice and have another try.  This time I will take note of how long it takes and will get back to you to let you know how I get on.
arite we'll see how it goes.

---

### Post by phantom5 on 2006-10-30
](*,)   Hi Eric - I tried installing kubuntu again but got the same result ie 'Could not start kstartconfig'.  The install took about 12 mins in total.  One of the screens that came up was to the effect that 'multiple display managers can run simultaneously if they are configured to manage different servers; to achieve this, configure the display managers accordingly, edit each of their init scripts in /etc/init.d, and disable the check for a default display manager'.  The next screen asked display manager to use as default and I selected the kdm.  Could this be where my problems are?  If so, how do I open the file to be able to edit it?  I apologise for the size of my post's but as a newbie I'm not sure what info you need to work out a possible solution.  Once again thanks for taking the time and trouble to help me.

---

### Post by user1397 on 2006-10-30
> **phantom5 said:**
> ](*,)   Hi Eric - I tried installing kubuntu again but got the same result ie 'Could not start kstartconfig'.  The install took about 12 mins in total.  One of the screens that came up was to the effect that 'multiple display managers can run simultaneously if they are configured to manage different servers; to achieve this, configure the display managers accordingly, edit each of their init scripts in /etc/init.d, and disable the check for a default display manager'.  The next screen asked display manager to use as default and I selected the kdm.  Could this be where my problems are?  If so, how do I open the file to be able to edit it?  I apologise for the size of my post's but as a newbie I'm not sure what info you need to work out a possible solution.  Once again thanks for taking the time and trouble to help me.hmm try in a terminal: ```
sudo dpkg-reconfigure kdm
```but this time select gdm.  then try logging into kde under options > sessions

---

### Post by phantom5 on 2006-10-31
> **erik1397 said:**
> hmm try in a terminal: ```
sudo dpkg-reconfigure kdm
```but this time select gdm.  then try logging into kde under options > sessions  Tried your suggestion but still no joy.  It's so frustrating as I can see dozens of 'k' programs such as konqueror, katapult and ksnapshot to name a few.  I seem to be locked into the ubuntu display manager and cannot change to kdm even though I select it from the login menu.  The default-display-manager file shows  /usr/bin/kdm  so I am at a total loss at what to try next.  Will leave kubuntu installed and keep trying to get it to run so any further suggestions would be greatfully received.  Thanks.
:???:

---

### Post by user1397 on 2006-10-31
> **phantom5 said:**
> Tried your suggestion but still no joy.  It's so frustrating as I can see dozens of 'k' programs such as konqueror, katapult and ksnapshot to name a few.  I seem to be locked into the ubuntu display manager and cannot change to kdm even though I select it from the login menu.  The default-display-manager file shows  /usr/bin/kdm  so I am at a total loss at what to try next.  Will leave kubuntu installed and keep trying to get it to run so any further suggestions would be greatfully received.  Thanks.
:???:you don't want to be able to change to kdm, the idea is to have gdm, and from within GDM, you can select options > sessions > kde.  you can make it the default or not, i suggest making it default only after you've tried it and you're satisfied with it.

---

### Post by phantom5 on 2006-11-02
> **erik1397 said:**
>  you can select options > sessions > kde.  
Thanks Eric - I have finally been able to get kde running!  I created a new user and was able to login as that user and run kde.  I cannot find the quote above, the only ref to sessions is in preferences > sessions so I think my basic setup must be a bit off.  I can at least play with kubuntu now so I may be able to sort the few niggles as I gain more knowledge.  Thanks for all your help.:D

---

### Post by user1397 on 2006-11-02
> **phantom5 said:**
> Thanks Eric - I have finally been able to get kde running!  I created a new user and was able to login as that user and run kde.  I cannot find the quote above, the only ref to sessions is in preferences > sessions so I think my basic setup must be a bit off.  I can at least play with kubuntu now so I may be able to sort the few niggles as I gain more knowledge.  Thanks for all your help.:D

no problem.  that quote is not found in gnome or kde, its in gdm itself (or kdm).  just try it.  log out of gnome or kde (whatever you're in right now), and in gdm (where you type your user name and password to log into ubuntu) you'll see an options button in the bottom-left (like this: [http://theblogjoint.com/wp-content/uploads/2006/05/gdm-options-small1.png](http://theblogjoint.com/wp-content/uploads/2006/05/gdm-options-small1.png) ) there you can go to sessions > kde, or gnome

---

### Post by phantom5 on 2006-11-04
Thanks Eric - I don't get that login screen when I first startup linux from the grub menu, I go strait into ubuntu.  If I logout as you suggest then I do get that login screen and am able to login as the other user and go into kde.  If I just try to change to kde but login as the default user the dreaded can't start kstartconfig info box appears!  :confused:

---

### Post by user1397 on 2006-11-04
> **phantom5 said:**
> Thanks Eric - I don't get that login screen when I first startup linux from the grub menu, I go strait into ubuntu.  If I logout as you suggest then I do get that login screen and am able to login as the other user and go into kde.  If I just try to change to kde but login as the default user the dreaded can't start kstartconfig info box appears!  :confused:
that's still weird though. have you considered filing a bug report on ubuntu's launchpad website about the kstartconfig thingie? just go here to make a launchpad account: [https://launchpad.net/+login](https://launchpad.net/+login), and then file a bug report here: [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)

also, the reason why you automatically are taken to ubuntu is that you set your login screen preferences to do that.  to change that if you want, in ubuntu go to system > administration > login window, and under security you'll find some box that says automatically log on when ubuntu starts or something.  (sorry im on windows right now.)

---

### Post by phantom5 on 2006-11-05
> **erik1397 said:**
> ...in ubuntu go to system > administration > login window, and under security you'll find some box that says automatically log on when ubuntu starts or something.
That worked fine Eric -I now go straight to the login screen.  As you say, it is a bit weird because as the default (first) user I cannot start a kde session, again the dreaded 'could not start kstartconfig', but as the second user I can choose to have either gnome or kde!  I will probably follow up your suggestion and report as a possible bug.  Again your help has been invaluable - thanks. :D

---

### Post by user1397 on 2006-11-06
> **phantom5 said:**
> That worked fine Eric -I now go straight to the login screen.  As you say, it is a bit weird because as the default (first) user I cannot start a kde session, again the dreaded 'could not start kstartconfig', but as the second user I can choose to have either gnome or kde!  I will probably follow up your suggestion and report as a possible bug.  Again your help has been invaluable - thanks. :Dmaybe your  original user account got corrupted somehow.  maybe you can delete the original account, and just stick with the new one (the one that works)  


just a suggestion.

---

### Post by phantom5 on 2006-11-08
> **erik1397 said:**
> maybe your  original user account got corrupted somehow.  maybe you can delete the original account, and just stick with the new one (the one that works)  


just a suggestion.

I will probably do that, Eric, that way at least I will be able to play with both gnome and kde.  Thanks.

---

### Post by Pathfinder_ on 2006-11-11
i have a question. Currently i have ubuntu installed, if i install kubuntu-desktop and remove ubuntu desktop will it be the same as installing kubuntu?

---

### Post by user1397 on 2006-11-11
> **Pathfinder_ said:**
> i have a question. Currently i have ubuntu installed, if i install kubuntu-desktop and remove ubuntu desktop will it be the same as installing kubuntu?technically yes.  although, you never know how "clean" it'll actually be, because little packages can always be floating around, but its not like it would matter much, so yes, it would be basically the same.

to remove gnome, you would have to follow the link i put called "pure kde"

---

### Post by Pathfinder_ on 2006-11-11
thanks for the info. :)

---

### Post by murthy on 2007-08-26
I have tried both Kubuntu and Ubuntu Feisty through installation CDs.  Now I am using Ubuntu, but would like to have Kubuntu also.  Is it possible to install Kubuntu over Ubuntu using the installation CD (and not from the internet, as web access is coslty for me)?  I have tried through synaptic, but it does not work.  Is the only way to reinstall using the Kubuntu CD?  I would really like to have the choice of both and the programmes from both.

---

### Post by user1397 on 2007-08-26
> **murthy said:**
> I have tried both Kubuntu and Ubuntu Feisty through installation CDs.  Now I am using Ubuntu, but would like to have Kubuntu also.  Is it possible to install Kubuntu over Ubuntu using the installation CD (and not from the internet, as web access is coslty for me)?  I have tried through synaptic, but it does not work.  Is the only way to reinstall using the Kubuntu CD?  I would really like to have the choice of both and the programmes from both.Just so you know, gnome programs work in kde, and vice versa.

But for your case, you could actually add your kubuntu feisty cd rom to your repositories list, and cancel all other entries.

To do that, insert the kubuntu cd, and go to system > administration > software sources, and try to find an "add cd rom" button, and add your cd.

Then untick every source except for the cd rom.

After that, open a terminal, and type ```
sudo aptitude install kubuntu-desktop
``` and it should install right from the cd.

After a quick reboot, you'll have the option of selecting either ubuntu or kubuntu from the main menu.

---

### Post by murthy on 2007-08-27
> **ubuntuman001 said:**
> Just so you know, gnome programs work in kde, and vice versa.

But for your case, you could actually add your kubuntu feisty cd rom to your repositories list, and cancel all other entries.

To do that, insert the kubuntu cd, and go to system > administration > software sources, and try to find an "add cd rom" button, and add your cd.

Then untick every source except for the cd rom.

After that, open a terminal, and type ```
sudo aptitude install kubuntu-desktop
``` and it should install right from the cd.

After a quick reboot, you'll have the option of selecting either ubuntu or kubuntu from the main menu.

Did as directed, but no result!  Following appears in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Any mistake?  Is there any way other than internet?
Thanks in advance.

---

### Post by user1397 on 2007-08-27
> **murthy said:**
> Did as directed, but no result!  Following appears in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Any mistake?  Is there any way other than internet?
Thanks in advance.o, my bad, try ```
sudo aptitude update
```before trying the install command.

---

### Post by murthy on 2007-08-28
> **ubuntuman001 said:**
> o, my bad, try ```
sudo aptitude update
```before trying the install command.

[SIZE="3"]Thanks for the prompt reply, but - did as directed again! Result?  ..same![/SIZE]
sudo aptitude update
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/main Translation-en_IN
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/restricted Translation-en_IN
Reading package lists... Done
[SIZE="3"]Then[/SIZE]:
sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
What now?

---

### Post by user1397 on 2007-08-28
> **murthy said:**
> [SIZE=3]Thanks for the prompt reply, but - did as directed again! Result?  ..same![/SIZE]
sudo aptitude update
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/main Translation-en_IN
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/restricted Translation-en_IN
Reading package lists... Done
[SIZE=3]Then[/SIZE]:
sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
What now?hmmm maybe aptitude isn't picking it up for some reason, so I guess you'll have to try apt-get instead.
```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```
note: this install will install kubuntu, but it will not be easily removable.

---

### Post by murthy on 2007-08-29
> **ubuntuman001 said:**
> hmmm maybe aptitude isn't picking it up for some reason, so I guess you'll have to try apt-get instead.
```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```
note: this install will install kubuntu, but it will not be easily removable.

[SIZE="3"]Sorry, this also did not install Kubuntu! (No problem about removing!)[/SIZE]
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/main Translation-en_IN
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/restricted Translation-en_IN
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop

---

### Post by user1397 on 2007-08-29
> **murthy said:**
> [SIZE=3]Sorry, this also did not install Kubuntu! (No problem about removing!)[/SIZE]
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/main Translation-en_IN
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/restricted Translation-en_IN
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktopokay, please post your sources.list file here
to open it, type in a terminal ```
gedit /etc/apt/sources.list
```and then just paste everything in that file into your next post.

---

### Post by murthy on 2007-08-30
> **ubuntuman001 said:**
> okay, please post your sources.list file here
to open it, type in a terminal ```
gedit /etc/apt/sources.list
```and then just paste everything in that file into your next post.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse



deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted

---

### Post by user1397 on 2007-08-30
> **murthy said:**
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse



deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restrictedhmm that file doesn't look right at all...I mean, you don't have any repositories listed there aside from the backports and the cd-rom...i guess it might have something to do with  doing it all through a GUI (software sources is a GUI to configure this file and other things)

I don't know what to tell you, except that perhaps the meta-package "kubuntu-desktop" is non-existant on an ubutnu desktop cd.

do you have the alternate cd?

---

### Post by murthy on 2007-08-31
> 
I don't know what to tell you, except that perhaps the meta-package "kubuntu-desktop" is non-existant on an ubutnu desktop cd.

do you have the alternate cd?

Thanks anyway for trying. Guess I will have to install through the internet only.  Seems that some method may be evolved by someone so that so much internet traffic is avoided ( - as also the cost), when the stuff is already available in the install CD.  
Ubuntu may please consider providing  Ubuntu, Kubuntu and Xubuntu material in a DVD and allow the choice of installation.  The repoistories provided in the installation CDs of both Ubuntu and Kubuntu may easily fit in a DVD and I hope the cost difference may not be much between a CD and DVD.

---

### Post by user1397 on 2007-08-31
> **murthy said:**
> Thanks anyway for trying. Guess I will have to install through the internet only.  Seems that some method may be evolved by someone so that so much internet traffic is avoided ( - as also the cost), when the stuff is already available in the install CD.  
Ubuntu may please consider providing  Ubuntu, Kubuntu and Xubuntu material in a DVD and allow the choice of installation.  The repoistories provided in the installation CDs of both Ubuntu and Kubuntu may easily fit in a DVD and I hope the cost difference may not be much between a CD and DVD.well, there *are* ubuntu DVDs available, see here: [http://cdimage.ubuntu.com/releases/feisty/release/](http://cdimage.ubuntu.com/releases/feisty/release/)
I don't know about the specific contents of the DVDs though, and I know that there are specific ubuntu and kubuntu DVDs.

---

### Post by murthy on 2007-09-01
> **ubuntuman001 said:**
> well, there *are* ubuntu DVDs available, see here: [http://cdimage.ubuntu.com/releases/feisty/release/](http://cdimage.ubuntu.com/releases/feisty/release/)
I don't know about the specific contents of the DVDs though, and I know that there are specific ubuntu and kubuntu DVDs.

Well, this link is for *[SIZE="3"]DVD download[/SIZE]* which returns me to square one (internet cost) - I was thinking in terms of Shipit CDs.  Thank you any way.

---

### Post by user1397 on 2007-09-01
> **murthy said:**
> Well, this link is for *[SIZE=3]DVD download[/SIZE]* which returns me to square one (internet cost) - I was thinking in terms of Shipit CDs.  Thank you any way.
Ah I see. You didn't specify you were talking about Shipit, so I naturally understood that you meant DVD downloads.  My bad.

I am gonna ask some questions to various members here though, and perhaps I will be able to solve your problem.

---

### Post by tylerious on 2009-11-04
I don't know how old this thread is, but I've been looking for a way to completely remove ubuntu-desktop and GNOME and all the other GUI programs... and these instructions do not work. From what I've read, this only works if aptitude was used to install ubuntu-desktop in the first place (which it wasn't).

Since I believe I've figured out how to actually do this, I wanted to share for the rest of the world and get these instructions in one place.

$ sudo apt-get install deborphan
$ sudo apt-get purge ubuntu-desktop
$ sudo apt-get purge `deborphan`

TWO NOTES:
First, one might want to run deborphan by itself before purging ubuntu-desktop to see if it points out any other orphans. This way you are aware of what else you might be removing. 
Second, note the ` ` marks around deborphan, not ' ' (single quotes)

I hope others find this helpful!

(I am using 9.04, btw).

---

