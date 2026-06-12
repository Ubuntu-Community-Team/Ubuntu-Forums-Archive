---
title: "HOWTO: using debfoster in practice"
date: 2005-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu_demon on 2005-04-06
Hi,

This is not for the faint of heart so fresh baked noobs get away! :-D

This is my first HOWTO. I noticed I was explaining debfoster a lot and I wanted to have a link to it. debfoster is a very powerful tool once you are getting used to it. I've thought up five scenarios of use :

SCENARIO 1)You use it to keep track of what you did install
SCENARIO 2)You want to make your system clean,mean and lean.
SCENARIO 3)You have had problems with upgrading to hoary or you have entered a dependencies hell on accident.
SCENARIO 4)You want an internet gateway with a nice windowmanager that uses little resources.
SCENARIO 5)You want to remove all of kde and kubuntu and go back to ubuntu-desktop

apt-cache show debfoster :
> 
Description: Install only wanted Debian packages
 debfoster is a wrapper program for apt and dpkg.  When first run, it
 will ask you which of the installed packages you want to keep
 installed.
 .
 After that, it maintains a list of packages that you want to have
 installed on your system.  It uses this list to detect packages that
 have been installed only because other packages depended on them.  If
 one of these dependencies changes, debfoster will take notice, and
 ask if you want to remove the old package.
 .
 This helps you to maintain a clean Debian install, without old
 (mainly library) packages lying around that aren't used any more.



man debfoster :
> 
debfoster - weed unnecessary Debian packages

debfoster maintains a list of installed packages that were explicitly requested rather than installed as a dependency.  Arguments are entirely optional, debfoster can be invoked per se after each run of dpkg and/or apt-get.

Alternatively you can use debfoster to install and remove packages by specifying the packages on the command line.  Packages suffixed with a - are removed while packages without a suffix are installed.

If a new package is encountered or if debfoster notices that a package that used to be a dependency is now an orphan, it will ask you what to do with it.  If you decide to keep it, debfoster will just take note and continue.  If you decide that this package is not interesting enough it will be removed as soon as debfoster is done asking questions.  If your choises cause other packages to become orphaned more questions will ensue.


to install debfoster :
sudo apt-get install debfoster

EVERYTHING IN THIS HOWTO IS AT YOUR OWN RISK. You should understand what you are doing and also read the manpage($ man defoster) before doing any commands. If you do the following things the risk will be minimal.

-There is one very IMPORTANT thing. ALWAYS MAKE SURE THAT THE PACKAGE ubuntu-base IS MENTIONED IN YOUR KEEPERS FILE! Never choose to purge it when run debfoster from the commandline! This will render your system unusable.

-Be sure to to never remove the kernel you are currently running from your keepers file. Removing it probably won't succeed but if it will succeed (and you have no other kernels available in your grub menu then it will be a pain to boot the correct kernel)

-don't remove the grub package!

-Also be sure that you backup important configuration files that you have edited yourself!

-If you decide to do it and this is your only box. It would be handy to keep a live-cd aside in case you run into troubles

-it's nice if you leave debfoster in the keepers file otherwise it might try to remove itself :-D

SCENARIO 1)You use it to keep track of what you did install

to install debfoster type :
$ sudo apt-get install debfoster

to create the initial keepers file type :
$ sudo debfoster -q

to edit the keepers file type :
$ sudo pico /var/lib/debfoster/keepers

NEVER remove your current kernel (for example linux-686) and ubuntu-base

Also be sure that you backup important configuration files that you have edited yourself!

To force debfoster to remove all packages that aren't listed in this list or dependencies of packages that are listed in this list.It will also add all packages in this list that aren't installed. So it makes your system comply with this list. Do this :

$ sudo debfoster -f

from the manpage of debfoster :
> 
 -f, --force
Don&#8217;t ask anything and assume &#8216;no&#8217; as the answer to all questions. It also installs any packages that seem to be missing, thus forcing your
system to comply with the debfoster database. Can have &#8216;interesting&#8217; results if you&#8217;re not careful.


To keep track of what you installed additionally do once in a while :

$ sudo debfoster

type i for info, h for help, p for purge, y for remove and n for not remove

============================================================================================


SCENARIO 2)You want to make your system clean,mean and lean.

basically the same as scenario 1 but I want to add these comments :

ubuntu-base,ubuntu-desktop are the metapackages that all other packages depend on when you first install ubuntu.

This cleans your apt-get cache this can be a lot of space if you never do apt-get clean :
$ sudo apt-cache clean 


deborphan is also very nice.
$ sudo apt-get install deborphan

To find leftover configuration files :
$ deborphan --find-config 

To find all orphans (only remove things you are sure about!) :
$ deborphan -a

xdiskusage is nice if you want to easily see where the space on your harddrive goes
$ sudo apt-get install xdiskusage

$ sudo xdiskusage

==============================================================================================


SCENARIO 3)You have had problems with upgrading to hoary or you have entered a dependencies hell on accident.

First go read :

[www.ubuntuguide.org](www.ubuntuguide.org)
[www.ubuntulinux.org/wiki/guidetohoary](www.ubuntulinux.org/wiki/guidetohoary) 
[http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

Make sure your /etc/apt/sources.list is the same as the one on : [www.ubuntulinux.org/wiki/guidetohoary](www.ubuntulinux.org/wiki/guidetohoary) 

You should search the forums about your specific problem. Here's a relevant thread about upgrading to hoary :

[http://ubuntuforums.org/showthread.php?t=23624](http://ubuntuforums.org/showthread.php?t=23624)

So you have screwed up your box? The easiest way out of this mess is ofcourse reinstalling when hoary gets released. But that isn't fun. :)

Okay here we go :

Install debfoster by :
$ sudo apt-get install debfoster

edit your keepers file by :

$ sudo pico /var/lib/debfoster/keepers

It should look at like this (assuming you are on a 686 processor and using grub) :

```

ubuntu-base
linux-686
debfoster
grub

```

You should remove all other lines.

Now we go to init 1. To make sure we don't harm processes that are running.
$ sudo init 1

Also be sure that you backup important configuration files that you have edited yourself!

To force debfoster to remove all packages that aren't listed in this list or dependencies of packages that are listed in this list.It will also add all packages in this list that aren't installed. So it makes your system comply with this list. Do this :

$ sudo debfoster -f

from the manpage of debfoster :
> 
 -f, --force
Don&#8217;t ask anything and assume &#8216;no&#8217; as the answer to all questions. It also installs any packages that seem to be missing, thus forcing your
system to comply with the debfoster database. Can have &#8216;interesting&#8217; results if you&#8217;re not careful.


After this your system is compatible with the keepers file. 

Now install ubuntu-desktop and xserver-xorg by :

sudo apt-get install ubuntu-desktop xserver-xorg

To start your gdm / gnome again do this :

$ sudo init 2

if gdm doesn't start do :

$ startx

if it still doesn't start you should :

backup your /etc/X11/xorg.conf by :
suco cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

reconfigure your xserver by :
$ sudo dpkg-reconfigure xserver-xorg

try to start gdm/gnome again by :

$ startx

if it still doesn't start you should edit your xorg.conf by hand to solve the problem :
$ sudo pico /etc/X11/xorg.conf

or post in the forums for help and include your /var/log/Xorg.0.log

To keep track of what you installed additionally do once in a while :

$ sudo debfoster

type i for info, h for help, p for purge, y for remove and n for not remove

=============================================================================================

SCENARIO 4)You want an internet gateway with a nice windowmanager that uses little resources.

I've played enough with xfce4 to feel confident to use it as my only desktop-environment on my internet gateway/fileserver (using xfwm4 and vncserver

It's install size is only 771 mb in /. /home is mounted on a different partition.  I've also got installed J2SE and hugin lite (but not from packages). I "downgraded" my ubuntu-base / ubuntu-desktop configuration using debfoster.

I use it for:

-downloading
-working at my own pc from school using vncserver
-fileserver using samba

this is my /var/lib/debfoster/keepers :

```

amule
cgoban
debfoster
deborphan
firestarter
flashplayer-mozilla
gaim
gnugo
grub
grubconf
isag
linux-686
mozilla-firefox
nmap
prelink
python
raidtools2
samba
slocate
smbfs
ssh
swf-player
ubuntu-base
unrar
vncserver
xdiskusage
xfce4
xfce4-goodies
xfwm4
xserver-xorg

```

Okay here we go :

Install debfoster by :
$ sudo apt-get install debfoster

This is to create your initial keepers file :

$ sudo debfoster -q

Now edit your keepers file :

$ sudo pico /var/lib/debfoster/keepers

And change it to at least (IMO for this scenario) :

```

debfoster
deborphan
firestarter
gaim
grub
linux-686
mozilla-firefox
prelink
samba
slocate
smbfs
ssh
ubuntu-base
xfce4
xfce4-goodies
xfwm4
xserver-xorg

```

Also include your favorite applications.Be sure not to forget the ones you have already configured because all packages that are not listed will be removed completly (including configuration files). GNOME applications look really nice in XFCE4! I haven't checked kde applications but they should also work nicely.

Now we go to init 1. To make sure we don't harm processes that are running.
$ sudo init 1

Also be sure that you backup important configuration files that you have edited yourself!

To force debfoster to remove all packages that aren't listed in this list or dependencies of packages that are listed in this list.It will also add all packages in this list that aren't installed. So it makes your system comply with this list. Do this :

$ sudo debfoster -f

from the manpage of debfoster :
> 
 -f, --force
Don&#8217;t ask anything and assume &#8216;no&#8217; as the answer to all questions. It also installs any packages that seem to be missing, thus forcing your
system to comply with the debfoster database. Can have &#8216;interesting&#8217; results if you&#8217;re not careful.


After this your system is compatible with the keepers file. 

To start your xfce4 and enter init level 2 do this :

$ sudo init 2

if xfce4 doesn't start do :

$ startxfce4

if it still doesn't start you should :

backup your /etc/X11/xorg.conf by :
suco cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

reconfigure your xserver by :
$ sudo dpkg-reconfigure xserver-xorg

try to start xfce4 again by :

$ startxfce4

if it still doesn't start you should edit your xorg.conf by hand to solve the problem :
$ sudo pico /etc/X11/xorg.conf

or post in the forums for help and include your /var/log/Xorg.0.log

To keep track of what you installed additionally do once in a while :

$ sudo debfoster

type i for info, h for help, p for purge, y for remove and n for not remove

To configure samba and learn more about it please check [www.ubuntuguide.org](www.ubuntuguide.org)

see here for how to configure prelink :
[http://www.ubuntuforums.org/showthread.php?t=1971&highlight=prelink](http://www.ubuntuforums.org/showthread.php?t=1971&highlight=prelink)

==================================================================================

SCENARIO 5)You want to remove all of kde and kubuntu and go back to ubuntu-desktop

Install debfoster by :
$ sudo apt-get install debfoster

to build the keepers file without asking questions :

$ sudo debfoster -q 

and edit your keepers file by :

$ sudo pico /var/lib/debfoster/keepers

It should look at least like this (assuming you are on a 686 processor and using grub) :

```

ubuntu-base
ubuntu-desktop
linux-686
xserver-xorg
debfoster
grub

```

Also include your favorite applications.Be sure not to forget the ones you have already configured because all packages that are not listed will be removed completly (including configuration files).

You should remove kubuntu-desktop and all packages that start with the letter k that you know belong to kde and don't want anymore. If your kubuntu-desktop is broken and doesn't show up don't worry it's just a meta-package. Be sure to remove kdebase,kdm,kdelibs,kdelibs4 if they are mentioned in the keepers file. Also please keep all applications that are mentioned in the keepers file and that you do use. You should remove all other lines you are not sure of.

Now we go to init 1. To make sure we don't harm processes that are running.
$ sudo init 1

Also be sure that you backup important configuration files that you have edited yourself!

To force debfoster to remove all packages that aren't listed in this list or dependencies of packages that are listed in this list.It will also add all packages in this list that aren't installed. So it makes your system comply with this list. Do this :

$ sudo debfoster -f

from the manpage of debfoster :
> 
 -f, --force
Don&#8217;t ask anything and assume &#8216;no&#8217; as the answer to all questions. It also installs any packages that seem to be missing, thus forcing your
system to comply with the debfoster database. Can have &#8216;interesting&#8217; results if you&#8217;re not careful.


After this your system is compatible with the keepers file. 

To start your gdm / gnome again do this :

$ sudo init 2

if gdm doesn't start do :

$ startx

if it still doesn't start you should :

backup your /etc/X11/xorg.conf by :
suco cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

reconfigure your xserver by :
$ sudo dpkg-reconfigure xserver-xorg

try to start gdm/gnome again by :

$ startx

if it still doesn't start you should edit your xorg.conf by hand to solve the problem :
$ sudo pico /etc/X11/xorg.conf

or post in the forums for help and include your /var/log/Xorg.0.log

To keep track of what you installed additionally do once in a while :

$ sudo debfoster

type i for info, h for help, p for purge, y for remove and n for not remove

edit :
here's the website of debfoster :

[http://www.fruit.je/debfoster](http://www.fruit.je/debfoster)

here's a nice story about debfoster :

[http://ubuntu.wordpress.com/](http://ubuntu.wordpress.com/)

---

### Post by bored2k on 2005-04-06
Thanks, I wanted to know how to use it. I still haven't tested it 'cause its impossible for a human to read that fast LOL, but ill tell you once I test it.

---

### Post by ubuntu_demon on 2005-04-06
[QUOTE=bored2k]Thanks, I wanted to know how to use it. I still haven't tested it 'cause its impossible for a human to read that fast LOL, but ill tell you once I test it.[/QUOTE]
 okay :-D

---

### Post by underworld on 2005-04-08
Thanks for this HOWTO, I like to keep my system clean :wink:

Basically debfoster operates at the package level and I have now found a program, which finds cruft at the file level:

cruft - Find any cruft built up on your system

Has anyone exerience with this program? I have tried it out but don't know how to decide what to delete, don't wan't to break my system.

Greetings,
Daniel

---

### Post by ubuntu_demon on 2005-04-08
[QUOTE=underworld]Thanks for this HOWTO, I like to keep my system clean :wink:

Basically debfoster operates at the package level and I have now found a program, which finds cruft at the file level:

cruft - Find any cruft built up on your system

Has anyone exerience with this program? I have tried it out but don't know how to decide what to delete, don't wan't to break my system.

Greetings,
Daniel[/QUOTE]
 thnx for the tip! I didn't know cruft.

[http://packages.ubuntu.com/hoary/admin/cruft](http://packages.ubuntu.com/hoary/admin/cruft)

So it's still a pre-release. So you have to be really careful. Only remove stuff if you are absolutely sure. 

/usr/share/doc/cruft has a README and TODO file

So here we go :

$sudo pico /etc/cruft/explain/cruftexcludes

and put some directories in that you don't want to be included in the cruft search for example like this :
```

#!/bin/bash
find /home
find /usr/java
find /sys
find /.dev
find /var
find /usr/share/fonts
find /usr/share/icons

```

$sudo chmod +x /etc/cruft/explain/cruftexcludes

$sudo cruft

add stuff into your cruftexcludes that you are sure you want to keep and do sudo cruft again. After a while you should find some files that can be removed but only if you are absolutely sure.

I don't think you'll find much stuff that you can safely remove. So it isn't worth the hassle unless you are nerdish like me :-P

PS don't remove backups of configuration files. That won't safe much space and isn't worth it.

---

### Post by ubuntu_demon on 2005-04-09
I've added xdiskusage to scenario 2 :

xdiskusage is nice if you want to easily see where the space on your harddrive goes
$ sudo apt-get install xdiskusage

$ sudo xdiskusage

---

### Post by underworld on 2005-04-09
[QUOTE=demon666_nl]
xdiskusage is nice if you want to easily see where the space on your harddrive goes
[/QUOTE]

Filelight is also quite nice, show the disk usage in concentric segmented-rings: [filelight screenshoot](http://www.kde-apps.org/content/preview.php?preview=1&id=9887&file1=9887-1.png&file2=9887-2.png&file3=&name=Filelight).

Greetings,
Daniel

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=underworld]Filelight is also quite nice, show the disk usage in concentric segmented-rings: [filelight screenshoot](http://www.kde-apps.org/content/preview.php?preview=1&id=9887&file1=9887-1.png&file2=9887-2.png&file3=&name=Filelight).

Greetings,
Daniel[/QUOTE]
 thnx for the tip

It looks really nice. It would be great if there was a gnome equivalent because it depends on kdelibraries (if I only need them for this app then it's a bit unnecessary) and I can't use it to map my remote filesystems (samba)

---

### Post by bored2k on 2005-04-09
Hey demon666, as you know I went XFCE some minutes ago, and I'd like to cut off some of that GNOME fat, but, there are some gnome apps I still use like nautilus, anjuta, gaim, abiword and some more. Any pointers on how to -not- deleting something unwanted?

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=bored2k]Hey demon666, as you know I went XFCE some minutes ago, and I'd like to cut off some of that GNOME fat, but, there are some gnome apps I still use like nautilus, anjuta, gaim, abiword and some more. Any pointers on how to -not- deleting something unwanted?[/QUOTE]
 scenario2 and don't remove the application you want from the keepers file if they are not mentioned because they are not orphaned just find out the packagename using apt-cache and add them to your keepers file. Remove all bloat you don't use from the keepers file :)

---

### Post by underworld on 2005-04-11
[QUOTE=demon666_nl]
It looks really nice. It would be great if there was a gnome equivalent because it depends on kdelibraries (if I only need them for this app then it's a bit unnecessary) and I can't use it to map my remote filesystems (samba)[/QUOTE]

True. Didn't notice myself as I am a Ubuntu & Kubuntu user  ;-)

---

### Post by ubuntu_demon on 2005-04-11
Also if you are using debfoster and using grub don't remove this package ! (I have editted the howto)

---

### Post by mohaham on 2005-07-01
thanks for the great HOWTO..
can someone please post their keepers file, just to get an idea..

---

### Post by benplaut on 2005-07-01
so... what's the difference between this and aptitude?

---

### Post by ubuntu_demon on 2005-07-01
[QUOTE=benplaut]so... what's the difference between this and aptitude?[/QUOTE]
 This is packagemanagement for advanced users :-P

---

### Post by ubuntu_demon on 2005-10-06
here's the website of debfoster :

[http://www.fruit.je/debfoster](http://www.fruit.je/debfoster)

here's a nice story about debfoster :

[http://ubuntu.wordpress.com/2005/09/30/better-management-of-packages-while-uninstalling/](http://ubuntu.wordpress.com/2005/09/30/better-management-of-packages-while-uninstalling/)

---

### Post by corax on 2006-09-15
Hi, 
I didn't read through your HOW TO, only Scenario 2, i' m getting familiar with deborphan it finds me packages, i decide what to remove then aptitude purge removes. But there is an option you mentioned --find-config it finds me config files but i don't know where they are (it isn't listed). I checked all the switches for deborphan and i didn't find the right one :). Can you help me please ? THX

---

### Post by ubuntu_demon on 2006-09-22
> **corax said:**
> Hi, 
I didn't read through your HOW TO, only Scenario 2, i' m getting familiar with deborphan it finds me packages, i decide what to remove then aptitude purge removes. But there is an option you mentioned --find-config it finds me config files but i don't know where they are (it isn't listed). I checked all the switches for deborphan and i didn't find the right one :). Can you help me please ? THX
try gtkorphan it gives a graphical interface to deborphan. 

for a bit information :
$apt-cache show gtkorphan

to install it :
$sudo aptitude install gtkorphan

to view the manpage :
$man gtkorphan

to start it find it somewhere in the menu or :
$gksudo gtkorphan

If you search for 'gtkorphan' your will probably find a bit more information.

good luck! :)

Als this thread is really old and I wrote it during warty. This is my latest thread about package management. It's about fixing dependencies problems :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by goldaryn on 2006-11-04
this is exactly what I've been looking for..

thanks very much, it would have taken me a long to time to understand this without the how-to.. awesome. especially the minimalising bits!

ubuntu_demon, you're a hero!

g.

---

### Post by kempy1000 on 2010-06-08
I came across this from google, and wow its old!

Just wondering when you go to the debfoster website it says depreciated in favor of aptitude.

Does aptitude have a keepers file? or an equivalent?

Chris

---

