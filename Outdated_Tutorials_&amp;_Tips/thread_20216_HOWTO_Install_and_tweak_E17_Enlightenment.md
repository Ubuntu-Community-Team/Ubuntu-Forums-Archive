---
title: "HOWTO: Install and tweak E17 Enlightenment"
date: 2005-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by bobmitch on 2005-03-15
[CENTER][LEFT][SIZE=4]**NOTE: 1(and maybe more)  of the mentioned repositories**[/SIZE][B][SIZE=4] doesn't exist at this current time.[/SIZE]
[/B][/LEFT]
[B]

QUICK AND DIRTY E17 HOWTO[/B][/CENTER]


Add the following line to **/etc/apt/sources.list**:

```
deb http://soulmachine.net/debian unstable/
```Add the following lines to **/etc/apt/preferences**
(If this file doesn`t exist, create it.)
(Don't know how necessary it is, but it worked for me.) :)

```
Package: enlightenment
Pin: version 0.17.0_pre10*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.17.0_pre10*
Pin-Priority: 999
```Create a file called **e17.deskto**p in **/usr/share/xsessions/**
Add the following lines to this file:

```
[Desktop Entry]
Encoding=UTF-8
Name=e17
Comment=
Exec=enlightenment
Icon=
Type=Application
```Using synaptic, install the following packages:

```
enlightenment        0.17.0_pre10-0cvs20050216
enlightenment-data    0.17.0_pre10-0cvs20050216
eutils            0.0.1-0cvs20050215
```E17 should now be available as a session from the gnome login screen. :)

Once in E17, the following commands are useful:

```
**enlightenment_remote -module-load flame**    - *Loads the flame module*. :D
**enlightenment_remote -module-load snow**    - *Loads the snow module*.
**e17setroot -s <imagename>**        - *Loads image, and scales to backdrop*.
(type e17setroot on it's own for other options)
```Once you have loaded a few backgrounds to test with, you can select them easily using the *emblem* E17 background selection tool, as all .eet files created with e17setroot are automatically stored in **$HOME/.e/e/background/**
(Just type **emblem** in the terminal)

[This]("http://lude.net/edocs/configuration.htm") is a great resource.

Hope this helps, apologies for any errors. :D

---

### Post by macewan on 2005-03-15
I was just getting ready to give it a try - thanks.


I'll be darned - [it worked](http://www.macewan.org/screenshots/engage.png). This is engage running right after an apt-get.

---

### Post by bored2k on 2005-03-15
It worked [yay @]

Now how do I edit the menus and the bar ? [like removing KDE terminal from favorite menus and adding mine, etc] ?

---

### Post by bobmitch on 2005-03-16
[QUOTE=bored2k]It worked [yay @]

Now how do I edit the menus and the bar ? [like removing KDE terminal from favorite menus and adding mine, etc] ?[/QUOTE]

This is a quick guide to menu/launcher editing - but I haven`t done extensive testing.  If all is well, I`ll add this to the howto.  It deals mainly with creating entries, but will show the path to removing entries as well, using the *.order* files.

First off, launch the application you want to create an 'icon' for.

Click the top left corner (but not the border!) with the left mouse button and select "Create Icon". Note that you need e_utils (which needs e17/libs/engrave) installed in order for this to work.  (You should have this package installed already if you followed the howto.)

An .eapp file will be created and moved to **~/.e/e/applications/all**.

Next, you need to add this .eapp file to the relevant **.order ** file.  These order files are what e17 parses when starting the apps, and are stored in the following directories:

```
**iBar:** ~/.e/e/applications/bar
**E17 menu:** ~/.e/e/applications/favourite
**Engage:** ~/.e/e/applications/engage

``` 

Here's and example iBar .order file:

```
firefox.eapp
xmms.eapp
engage.eapp
entice.eapp
evidence.eapp
``` 

Note that you can also create subdirectories for the menu. Simply make directories within **~/.e/e/applications/favourite ** and create **.order ** files in each one of them.

Here's an example: 
assuming that you have the following directories 

```
~/.e/e/applications/favourite/music
~/.e/e/applications/favourite/web
```

you can make a **~/.e/e/applications/.order ** which contains the following text:

```
terminal.eapp
music
web
```

This would create a menu that first shows the terminal icon and then has 2 directories - *music* and *web*. Following this system you'll also need to create .order files in those directories to select what .eapp files to have and in what order you want them to be in.


If you don`t want to create your own icons - the author of engage has a ton of them rolled already for your pleasure [here](http://aje.codewordt.co.uk/Files_files/applications.tar.gz) .

Note, that this has been heavily lifted from the site I linked to in the howto - but I`ve parsed it and packaged nicely for my fellow Ubuntians. :)

Good luck, and let us know if it works. :)

---

### Post by bored2k on 2005-03-16
[QUOTE=bobmitch]This is a quick guide to menu/launcher editing - but I haven`t done extensive testing.  If all is well, I`ll add this to the howto.  It deals mainly with creating entries, but will show the path to removing entries as well, using the *.order* files.

First off, launch the application you want to create an 'icon' for.

Click the top left corner (but not the border!) with the left mouse button and select "Create Icon". Note that you need e_utils (which needs e17/libs/engrave) installed in order for this to work.  (You should have this package installed already if you followed the howto.)

An .eapp file will be created and moved to **~/.e/e/applications/all**.

Next, you need to add this .eapp file to the relevant **.order ** file.  These order files are what e17 parses when starting the apps, and are stored in the following directories:

```
**iBar:** ~/.e/e/applications/bar
**E17 menu:** ~/.e/e/applications/favourite
**Engage:** ~/.e/e/applications/engage

``` 

Here's and example iBar .order file:

```
firefox.eapp
xmms.eapp
engage.eapp
entice.eapp
evidence.eapp
``` 

Note that you can also create subdirectories for the menu. Simply make directories within **~/.e/e/applications/favourite ** and create **.order ** files in each one of them.

Here's an example: 
assuming that you have the following directories 

```
~/.e/e/applications/favourite/music
~/.e/e/applications/favourite/web
```

you can make a **~/.e/e/applications/.order ** which contains the following text:

```
terminal.eapp
music
web
```

This would create a menu that first shows the terminal icon and then has 2 directories - *music* and *web*. Following this system you'll also need to create .order files in those directories to select what .eapp files to have and in what order you want them to be in.


If you don`t want to create your own icons - the author of engage has a ton of them rolled already for your pleasure [here](http://aje.codewordt.co.uk/Files_files/applications.tar.gz) .

Note, that this has been heavily lifted from the site I linked to in the howto - but I`ve parsed it and packaged nicely for my fellow Ubuntians. :)

Good luck, and let us know if it works. :)[/QUOTE]
 5 am here, Im trying to read this but all I can see on my screen are sleepy sheeps getting clubbed to death by penguins. zZzZzz

Will ASAP.

---

### Post by macewan on 2005-03-16
sweet - the bar is themeable(sp) also

mkdir ~/.e/apps/engage/themes/
cd ~/.e/apps/engage/themes/
wget http://edevelop.org/errand/packages/themes/gant/apps/engage/gant_engage-0.0.6.eet

now right click on engage, select config* & choose the gant theme-n-apply  =P~ 


 [http://www.macewan.org/screenshots/Engage.png](http://www.macewan.org/screenshots/Engage.png)

---

### Post by lizardking on 2005-03-17
**This HOW TO works also ion Warty?**

---

### Post by bobmitch on 2005-03-17
[QUOTE=lizardking]**This HOW TO works also ion Warty?**[/QUOTE]

I haven`t been able to test this - but I would have thought it would work *better* on Warty than Hoary at the moment.

NB.  I am on Hoary.

---

### Post by kleeman on 2005-03-17
Doesn't work on Warty I'm afraid to report. Dependency problems when synaptic tries to install the packages....Bummer it looks really interesting

---

### Post by bobmitch on 2005-03-17
[QUOTE=kleeman]Doesn't work on Warty I'm afraid to report. Dependency problems when synaptic tries to install the packages....Bummer it looks really interesting[/QUOTE]

I`m pretty surprised - do you have any esoteric stuff from universe installed?  As far as I know, the .deb package was made for a vanilla debian based system.

---

### Post by ichoudhury on 2005-03-17
I am getting the same thing in Warty like others....

When I select Enlightenment:

Depends: libe but it is not going to be installed
Depends: libevas2 but it is not going to be installed
Depends: libecore1 but it is not going to be installed
Depends: libedje0 but it is not going to be installed


When I select eutils:

Depends: libe but it is not going to be installed
Depends: libecore1 but it is not going to be installed
Depends: libeedje0 but it is not going to be installed
Depends: libengrave0 but it is not going to be installed
Depends: libesmart0 but it is not going to be installed
Depends: libevas2 but it is not going to be installed
Depends: libewl0 but it is not going to be installed


And if I try libe:

Depends: enlightenment but it is not going to be installed

Anybody solved this issue yet  :-({|=

---

### Post by kleeman on 2005-03-17
Not sure what you would call esoteric ;-) The dependency issues I get are identical to those above btw.

---

### Post by bobmitch on 2005-03-17
For those having dependency issues, try doing:

```
sudo apt-get update
```

Then retrying to install the packages, and report back success/failure.

---

### Post by kleeman on 2005-03-17
Did that already I thought but just to recheck I went through the directions exactly again and did the usual sudo apt-get update and tried to install enlightenment with the result:

enlightenment:
 Depends: libe but it is not going to be installed
 Depends: enlightenment-data but it is not going to be installed
 Depends: libevas2 but it is not going to be installed
 Depends: libecore1 but it is not going to be installed
 Depends: libedje0 but it is not going to be installed

tried 


enlightenment-data:
 Depends: enlightenment but it is not going to be installed


tried

eutils:
 Depends: libe but it is not going to be installed
 Depends: libecore1 but it is not going to be installed
 Depends: libedje0 but it is not going to be installed
 Depends: libengrave0 but it is not going to be installed
 Depends: libesmart0 but it is not going to be installed
 Depends: libevas2 but it is not going to be installed
 Depends: libewl0 but it is not going to be installed

---

### Post by kleeman on 2005-03-17
One other piece of info which might be significant: libe reports a conflict with libenlightenment - the other packages above have no conflicts. I could not find libenlightenment anywhere however....

---

### Post by darkoptix on 2005-03-17
I got it working in warty... 
I just needed some dependancies from hoary... I can't remember which ones, but  just got them from the debain packages site, installed, and then used synaptic to get enlightenment. However, I cannot get backgrounds working.

---

### Post by farruinn on 2005-03-18
Hey, thanks for letting me know about the repository and putting together the essential info here for us Ubuntuers.  This is highly preferred over CVS! :D
I'm gonna go rm -rf /usr/local right now I think...

---

### Post by dizzie on 2005-03-19
When i do : e17setroot -s <imagename>, i get 'sh edge_cc' not found

---

### Post by gab10 on 2005-03-20
I'm trying to get Enlightenment working under Warty...can anybody who has it working tell me how to get around that dependency problem?

---

### Post by m87 on 2005-03-22
[QUOTE=dizzie]When i do : e17setroot -s <imagename>, i get 'sh edge_cc' not found[/QUOTE]

THAT problem can be solved by installing some dev-packages (edje0-bin will do the trick), but you'll need Esetroot, therefore fsck yourself with eterm that WON'T install at first because you have to put on an OLDER version... happily ever after it did NOT work in my machine and therefore I decided to use one of the eet's from rasterman's site

kleeman's problem can be solved by - temporarily excluding the 'universe' repository | putting the already mentioned piece of code into /etc/apt/preferences - that should work [i don't know if you have that problem any more].

btw, enlightenment REALLY kicks a* and libraries like evas and edje should get more attention from the gtk folks... that's what i think.

anyway, does anybody know a replacement for GNOME's "run application" (yes, I'm talking 'bout alt+f2)

marco

---

### Post by kleeman on 2005-03-22
No go I'm afraid I get:

enlightenment:
 Depends: libe but it is not going to be installed
 Depends: enlightenment-data but it is not going to be installed
 Depends: libevas2 but it is not going to be installed
 Depends: libecore1 but it is not going to be installed
 Depends: libedje0 but it is not going to be installed

---

### Post by cutOff on 2005-03-23
Hi,

how do i change iBar theme?? where i get new themes??


Thanks

---

### Post by m87 on 2005-03-23
[QUOTE=kleeman]No go I'm afraid I get:

enlightenment:
 Depends: libe but it is not going to be installed
 Depends: enlightenment-data but it is not going to be installed
 Depends: libevas2 but it is not going to be installed
 Depends: libecore1 but it is not going to be installed
 Depends: libedje0 but it is not going to be installed[/QUOTE]

that's REALLY strange... have you tried excluding "universe" and apt-get update?

marco

---

### Post by kleeman on 2005-03-23
Yeah done both.

---

### Post by bobmitch on 2005-03-24
Using synaptic did you try doing a reload and a mark all upgrades followed by a smart upgrade?   Usually does the trick for those pesky not-gonna-install-or-upgrade-coz-I-dont-feel-like-it apt-get moment.

---

### Post by cutOff on 2005-03-24
[QUOTE=cutOff]Hi folks,

how do i change iBar theme?? where can i get new themes??

I have already looked in Rasterman's site but nothing I've seen.

Thanks[/QUOTE]
Anyone?  :-k

---

### Post by protocol on 2005-03-26
hmm... I seem to have a similar issue.  Four packages are conflicting over here.... its  libecore0 and libecore1, libevas0 and libevas2...and I tried apt-get update and retrying as well as apt-get -f install and same thing.  Get a "(Broken pipe) error.  Here it is:

```
Preconfiguring packages ...
(Reading database ... 117780 files and directories currently installed.)
Unpacking libevas0 (from .../libevas0_0.9.9.003-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libevas0_0.9.9.003-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libevas.so.1.0.0', which is also in package libevas2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libecore0 (from .../libecore0_0.9.9.003-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libecore0_0.9.9.003-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libecore.so.1.0.0', which is also in package libecore1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libevas0_0.9.9.003-1_i386.deb
 /var/cache/apt/archives/libecore0_0.9.9.003-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas?

---

### Post by bobmitch on 2005-03-27
No solution, but an explanation can be found [here.](http://shadoi.soulmachine.net/)

---

### Post by Slalomsk8er on 2005-03-31
[http://soulmachine.net/debian](http://soulmachine.net/debian) unstable-20050215/ is the new location in the repository but it looks like the package list is not fixed ([http://soulmachine.net/debian/unstable/*)](http://soulmachine.net/debian/unstable/*)).

```
W: Failed to fetch http://soulmachine.net/debian/unstable/libe_0.17.0_pre10-0cvs20050216_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/enlightenment-data_0.17.0_pre10-0cvs20050216_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libedb1_1.0.5-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libeet0_0.9.9-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libevas2_1.0.0_pre13-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libecore1_1.0.0_pre7-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libembryo0_0.9.1-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libedje0_0.5.0-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/enlightenment_0.17.0_pre10-0cvs20050216_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libengrave0_0.1.0-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libepeg0_0.9.0-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libepsilon0_0.3.0-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libesmart0_0.9.0-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libemotion0_0.0.1-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libetox0_0.9.0-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/libewl0_0.0.4-0cvs20050215_i386.deb
  404 Not Found

W: Failed to fetch http://soulmachine.net/debian/unstable/eutils_0.0.1-0cvs20050215_i386.deb
  404 Not Found
```
<edit>deb [http://mirror.my-space.ath.cx/](http://mirror.my-space.ath.cx/) unstable/ works for me :D</edit>

---

### Post by ichoudhury on 2005-03-31
If you installed e16, do you completely uninstall before attempting e17?  sudo apt-get install enlightenment installed e16 for me (because I removed the preferences files when it was constantly failing).  I removed Warty and installed Hoary and now I am stuck with e16  8-[

---

### Post by bobmitch on 2005-03-31
[QUOTE=ichoudhury]If you installed e16, do you completely uninstall before attempting e17?  sudo apt-get install enlightenment installed e16 for me (because I removed the preferences files when it was constantly failing).  I removed Warty and installed Hoary and now I am stuck with e16  8-[[/QUOTE]

Yes, remove E16 completely.  They are working towards using seperate namespaces for each project, but at the moment they are only version differences.

---

### Post by ichoudhury on 2005-03-31
> Yes, remove E16 completely. They are working towards using seperate namespaces for each project, but at the moment they are only version differences. 

Thanks for the msg.  I am actually posting this from the e17  :-({|= 

Basically I removed e16 (did not pick the complete option because I wasn't sure if that was going to remove any lib I may need later.  Anyway, I put the preferences file back as I saw what did happen by not having that last time (I got e16).  However, I commented out:

# deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/
 
and added the following

deb [http://mirror.my-space.ath.cx/](http://mirror.my-space.ath.cx/) unstable/

then ran

sudo apt-get update

and then

sudo apt-get install enlitenment

sudo reboot

Now I am in E17!   :shock:

---

### Post by bobmitch on 2005-04-01
Congrats!  Now all we have to do is pester the devs to get some nicer config tools and we're all set. :D

---

### Post by lwl on 2005-04-03
i have problems starting the engage module. it seems that this module is missing ... what should i do to fix the problem and have the module running ? 

p.s: i followed the steps in the howto

---

### Post by zeu on 2005-04-06
I still have problems with dependencies.. I tried everything that people suggested in this thread but no go..

Anyone have the repository url needed?

---

### Post by shimp999 on 2005-04-12
I followed the instructions on the 1st page and I get this error when I type sudo apt-get install enlightenment
```
Reading package lists... Done
Building dependency tree... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate
```

I'm on a fresh install of Ubuntu 5.04 Hoary.  Any clue what I should do about this?

Also, if I do apt-get install enlightenment-data, I get about the same message.

---

### Post by iomicifikko on 2005-04-12
[QUOTE=shimp999]I followed the instructions on the 1st page and I get this error when I type sudo apt-get install enlightenment
```
Reading package lists... Done
Building dependency tree... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate
```

I'm on a fresh install of Ubuntu 5.04 Hoary.  Any clue what I should do about this?

Also, if I do apt-get install enlightenment-data, I get about the same message.[/QUOTE]
 little update about repositories, give a look at [http://soulmachine.net/debian/](http://soulmachine.net/debian/) and u'll find that the dr17 tree is no more in the unstable directory but now in the unstable-20050215 directory so pay attention adding repositories.
anyway still same problems with dependencies and warty;( sigh.

byez

---

### Post by cirpo on 2005-04-12
when i try to install enlightenment17 i get the following error message:

>   WARNING: The following packages cannot be authenticated!
  libe enlightenment-data libevas2 libecore1 enlightenment
Install these packages without verification [y/N]? y
Err [http://soulmachine.net](http://soulmachine.net) unstable-20050215/ libe 0.17.0_pre10-0cvs20050216
  404 Not Found
Err [http://soulmachine.net](http://soulmachine.net) unstable-20050215/ enlightenment-data 0.17.0_pre10-0cvs20050216
  404 Not Found
Err [http://soulmachine.net](http://soulmachine.net) unstable-20050215/ libevas2 1.0.0_pre13-0cvs20050215
  404 Not Found
Err [http://soulmachine.net](http://soulmachine.net) unstable-20050215/ libecore1 1.0.0_pre7-0cvs20050215
  404 Not Found
Err [http://soulmachine.net](http://soulmachine.net) unstable-20050215/ enlightenment 0.17.0_pre10-0cvs20050216
  404 Not Found
Failed to fetch [http://soulmachine.net/debian/unstable/libe_0.17.0_pre10-0cvs20050216_i386.deb](http://soulmachine.net/debian/unstable/libe_0.17.0_pre10-0cvs20050216_i386.deb)  404 Not Found
Failed to fetch [http://soulmachine.net/debian/unstable/enlightenment-data_0.17.0_pre10-0cvs20050216_i386.deb](http://soulmachine.net/debian/unstable/enlightenment-data_0.17.0_pre10-0cvs20050216_i386.deb)  404 Not Found
Failed to fetch [http://soulmachine.net/debian/unstable/libevas2_1.0.0_pre13-0cvs20050215_i386.deb](http://soulmachine.net/debian/unstable/libevas2_1.0.0_pre13-0cvs20050215_i386.deb)  404 Not Found
Failed to fetch [http://soulmachine.net/debian/unstable/libecore1_1.0.0_pre7-0cvs20050215_i386.deb](http://soulmachine.net/debian/unstable/libecore1_1.0.0_pre7-0cvs20050215_i386.deb)  404 Not Found
Failed to fetch [http://soulmachine.net/debian/unstable/enlightenment_0.17.0_pre10-0cvs20050216_i386.deb](http://soulmachine.net/debian/unstable/enlightenment_0.17.0_pre10-0cvs20050216_i386.deb)  404 Not Found



any ideas?

---

### Post by iomicifikko on 2005-04-12
EDIT

ok,according to my researches that f***ing libpng is the only problem couse a few packages (not only libevas2) depend on it. all this about installing the 3 packs mentioned by bobmitch in his first message:enlightenment,enlightenment-data and eutils.

/EDIT



[QUOTE=iomicifikko]little update about repositories, give a look at [http://soulmachine.net/debian/](http://soulmachine.net/debian/) and u'll find that the dr17 tree is no more in the unstable directory but now in the unstable-20050215 directory so pay attention adding repositories.
anyway still same problems with dependencies and warty;( sigh.

byez[/QUOTE]
 always about warty, found the first (and i hope the only one) dep error:

libevas2:
  Depends on: libpng12-0 (>=1.2.8rel) but 1.2.5.0-7ubuntu1 will be installed

---

### Post by iomicifikko on 2005-04-12
[QUOTE=cirpo]when i try to install enlightenment17 i get the following error message:




any ideas?[/QUOTE]
 what did u exactly add in the repository list?

---

### Post by cirpo on 2005-04-12
my sources.list:
> 
#hoary------------------------------------
#############Ubuntu Hoary##############
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted

 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted


##############Ubuntu Security##############
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

 deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main
 deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted
 deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

# Mplayer + DVD CSS
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable-20050215/

#deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/
#deb [http://mirror.my-space.ath.cx/](http://mirror.my-space.ath.cx/) unstable/


---

### Post by iomicifikko on 2005-04-12
EDIT:
manually download all the files, then put all of them in /var/cache/apt/archives/, then sue synaptic in the same way as before, it will check that directory and it will find all the packages already downloaded so it will install them, byez;)
/EDIT


[QUOTE=cirpo]my sources.list:[/QUOTE]
 i think i know what is the problem sigh. the owner forgot to update his packages.gz file so all the files are linked at their old url .../unstable/....

u can do 2 things i think
1- wait a bit;)
2- manually download all the packages needed using your favourite browser and put them in the same directory to install it with "sudo dpkg -i file" (but im not sure dpkg automatically search for dependencies in directories, maybe there is an option, try also "man dpkg")

bye

---

### Post by kuleali on 2005-04-12
It worked! :)

---

### Post by 23meg on 2005-04-13
this doesn't work for me in Hoary; i get the following (usual) error in apt-get:

> Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment has no installation candidate 

and in Synaptic i get the Synaptic counterpart of this error. followed all steps, removed e16 completely, looked through the repository owner's blog, no luck.

---

### Post by iomicifikko on 2005-04-14
[QUOTE=23meg]this doesn't work for me in Hoary; i get the following (usual) error in apt-get:

 

and in Synaptic i get the Synaptic counterpart of this error. followed all steps, removed e16 completely, looked through the repository owner's blog, no luck.[/QUOTE]
 can u post your repositories list and the exact output error using synaptic?

---

### Post by jensyt on 2005-04-15
[QUOTE=23meg]this doesn't work for me in Hoary; i get the following (usual) error in apt-get:

 

and in Synaptic i get the Synaptic counterpart of this error. followed all steps, removed e16 completely, looked through the repository owner's blog, no luck.[/QUOTE]
I just got this working (and am in e17 right now). What you need to do is:

Change your sources.list from:
```
deb http://soulmachine.net/debian unstable/
```
to
```
deb http://soulmachine.net/debian unstable-20050215/
deb http://mirror.my-space.ath.cx/ unstable/
```
**Do everything as the original howto states; when you get errors, then look to the next step.**
Then, you'll still get some problems. To solve them, do this:
```
nano e17download
http://www.soulmachine.net/debian/unstable-20050215/enlightenment-data_0.17.0_pre10-0cvs20050216_i386.deb
http://www.soulmachine.net/debian/unstable-20050215/enlightenment_0.17.0_pre10-0cvs20050216_i386.deb
http://www.soulmachine.net/debian/unstable-20050215/libe_0.17.0_pre10-0cvs20050216_i386.deb
http://www.soulmachine.net/debian/unstable-20050215/libecore1_1.0.0_pre7-0cvs20050215_i386.deb
http://www.soulmachine.net/debian/unstable-20050215/libevas2_1.0.0_pre13-0cvs20050215_i386.deb
```
After you save that:
```

cd /var/cache/apt/archives/
sudo wget -i /path/to/e17download

```
After you've downloaded it all comes the fun part. 
```

sudo apt-get install enlightenment
sudo dpkg --force-overwrite -i libevas2_1.0.0_pre13-0cvs20050215_i386.deb
sudo dpkg --force-overwrite -i libecore1_1.0.0_pre7-0cvs20050215_i386.deb

```
You'll get errors after the first command, that's why the other two are there. (I may have the order wrong, if libevas depends on libecore, simply do libecore first.)

Log out and it should work!

EDIT: Though this should work, I'm having some problems with menu editing. It may be that one of the packages didn't properly install - so be careful to get everything, even if I didn't include it in the list.

---

### Post by Nikola on 2005-04-22
I've installed e17 but it doesn't start.
First everything is black, then turns into white screen with black box, here is screenshot:
[[IMG]http://img18.echo.cx/img18/2373/xnest2pj.th.png[/IMG]](http://img18.echo.cx/my.php?image=xnest2pj.png)

Anyone?

---

### Post by yoar on 2005-04-22
Here's what I have done to get dr17 working on my  system. Being a newb this may seem like attacking the issue with brute force in the form of a big club of ignorance by combining different installation methods. Forgive any technical omissions. 

1) added the preference file to /etc/apt 
2) added the e17.desktop file to ??/xsessions
3) added the following lines to my /etc/apt/sources.list

deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/
deb-src [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/

4) commented out all other lines in my /etc/apt/sources.list except the two lines I added to it above
5) in terminal apt-get update
6) apt-cache search "library name" for each of the following libraries to find the listed proper name. Then used apt-get install "library name" to install them in the order they appear. I added imlib2 because I had read that it was being used instead or in addition to imlib at various sites. Also the original list has "e" as the last app to install. It's not there don't look. List is from 
[E17 CVS Build Notes](http://www.enlightenment.org/index.php?id=35) :
 
imlib
imlib2
edb
eet
evas
ecore
epeg
epsilon
embryo
edje
esmart
emotion
etox
ewl

The following apps will build on the above libs: 
iconbar
entice
entrance
elicit

7) Unable to find the last app on the orginal list I used "apt-get install" to install the following:

enlightenment
enlightenment-data
eutils

8) logged off kde
9) cntrl-alt-backspace to restart X 
10) seen e17 was a session choice
11) it came up beautifully
12) uncommented my /etc/apt/sources.list file
13) apt-get update

Well the process worked for me... but may melt down systems if the proper sweet nothings are not screamed at the proper time. So your mileage may vary.

and remember... wireless hamsters are your friend.

---

### Post by codemills on 2005-04-24
enlightenment OWNZZZZ MEEE

STILL i am having lots of issues for installing other e17 apps . but till now i have managed to install enlightenment and enlightenment-data

OS:- ubuntu 5
wm:-  [http://enlightenment.freedesktop.org/](http://enlightenment.freedesktop.org/)

[[img]http://img234.echo.cx/img234/3103/e17desktop9ix.th.jpg[/img]](http://img234.echo.cx/my.php?image=e17desktop9ix.jpg)


the static screenshot fails to show what this window manager really is like .

---

### Post by yoar on 2005-04-24
I don't think I have seen the link to this site in this thread. But just in case....  [get-e.org](http://get-e.org//Documentation/User_Guide_pages/print.html)  This install procedure seems really current.  It also goes into how to customize different aspects. The most thorough site I have found on the topic. Just a another link in the knowledge of e.

---

### Post by codemills on 2005-04-24
[QUOTE=yoar]I don't think I have seen the link to this site in this thread. But just in case....  [get-e.org](http://get-e.org//Documentation/User_Guide_pages/print.html)  This install procedure seems really current.  It also goes into how to customize different aspects. The most thorough site I have found on the topic. Just a another link in the knowledge of e.[/QUOTE]

well. I am looking a simple installation of e17 for a linux newbie. I am Linux server admin by profession and playing with servers and installation just from bash commands is my meat and bread but this is not the case for newbie. so [http://get-e.org](http://get-e.org) is too hardcore as it involves installation from command line.

the installation using synpatic by adding soulmachine repos is the simplest one IMHO.

so i am looking to do this entirely from synaptic with some files to be added edited using command line.


although i have installed enlightenment. i still have lots of e17 things to be added but synaptic is giving errors like depends BLAH but cannot be installed. i am extremely pissed off why it cant.  ](*,) 

i will add a screenshot later and the code in my preferences file and  sources file.

---

### Post by raschen on 2005-04-24
I would have to agree with you codemills. That method on [http://get-org](http://get-org) is not easy. But it does have the most current build order that I have found. And you should be able to install the libraries via synaptic from soul machine's repositories in the mentioned order from get-e. If that is a path you wanted to follow....

Or you could even create a small script that a newb could fire off? Nothing easier than that for an install. That would automate the whole process after you iron out the issues your having.

As far as the depenency issues go... I think the 3 file install mentioned at the beginning of the thread is functional but not complete. Then again it's possible that when I installed I got newer code that could have addressed the dep problems. Who knows.

Best of luck!

---

### Post by Nikola on 2005-04-24
I finaly get it working.... WOW!
Now, can someone tell me how to use entrance in stead of gdm?
I've put: "/usr/sbin/entranced -nodaemon" in etc/X11/default-display-manager, but it douesn't start.

---

### Post by yoar on 2005-04-24
Nikola, have you configured entrance yet? Maybe you have... if not here's a link to the documentation. [Entrance](http://www.atmos.org/docs/entrance/index.html) 
It seems to be really in depth and detailed... whew... to much for me to chew on. Hope it helps though.

---

### Post by Nikola on 2005-04-24
OK, it works now. I had to add it to rc scripts:
```
update-rc.d entrance start 99 2 3 4 5 . stop 01 0 1 6 .
```

Looks awesome, but... I just can't use e17 in productive way! It looks awesome, but that's it. ANd lack of nice gui config tools drives me nuts. I'll keep it just to impress my friends when they come by, I'm back to XFce4 :-)
But this realy looks great.

---

### Post by Amidor on 2005-04-24
Great guide, though I get a wired error. I followed " bobmich" excellent
guide, but when the repositorys didn't work out I did what "jensyt" wrote. I
downloaded the packages with the script posted by "jensyt" thanx btw. And
then ran all the apt-get, and dkpg commands specified. But still I get this
error:


xlib:extension "XINERAMA" missing display ":0.0".
enlightenment: relocation error: /usr/lib/libedje.so.0: undefined symbol: evas_object_image_border_counter_fill_set

I googled a bit and saw that edje is some kind of graphics engine enlightenment uses. And if libedje is having issues, then E17 is having issues. 
That XINERAMA error is just wierding me out, that's supposed to be an extension that enables use of mutiple displays as one. I only have one display...gah...

Should I just reinstall the lib? Find another libedje, maybe newer or older. Or maybe I've just done a really simple error somewhere else that I've overlooked. 

Appreciate any help I receive.

xlib:extension "XINERAMA" missing display ":0.0".

---

### Post by yoar on 2005-04-25
[QUOTE=Amidor]
xlib:extension "XINERAMA" missing display ":0.0".
enlightenment: relocation error: /usr/lib/libedje.so.0: undefined symbol: evas_object_image_border_counter_fill_set
[/QUOTE]

Sounds like you might have a xienrama statement in your xorg.conf. If you are not running multiple displays or have it there for any other reason, I would recommend commenting it out. Should be located in /etc/X11/. Do you have a dual head video controller? I wonder if the unbuntu install would actually put that in the xorg.conf if a dual head controller was found? hmmm. But definitely check out the x server config file xorg.conf. 

if you post the contents of your xorg.conf... maybe an answer would appear for ya.

---

### Post by yoar on 2005-04-25
[QUOTE=Nikola]
Looks awesome, but... I just can't use e17 in productive way! It looks awesome, but that's it. ANd lack of nice gui config tools drives me nuts. I'll keep it just to impress my friends when they come by, I'm back to XFce4 :-)
But this realy looks great.[/QUOTE]

What do you mena by gui config tools? Left clicking on the desktop gives you tools to modify the clock, ibar, pager etc. For wallpaper changing you use emblem. There is no tool yet for changing themes yet... but it is still possible with a symlink command. 

I've actually got my menu's and ibar customized. All the e applications I have installed are working correctly and everything. I believe this is going to be my perm window manager. Applications start and respond so much faster in e17 than in kde or gnome, for me at least.  That is the big draw for me. It simply responds for me. 

Then again I've written a few litestep themes back in my windows era. So changing configs via text files is natural to me.  But good luck with with xfce, it's pretty tight.

---

### Post by Andy C on 2005-04-25
[QUOTE=Amidor]xlib:extension "XINERAMA" missing display ":0.0".
enlightenment: relocation error: /usr/lib/libedje.so.0: undefined symbol: evas_object_image_border_counter_fill_set

[QUOTE=yoar]if you post the contents of your xorg.conf... maybe an answer would appear for ya.[/QUOTE][/QUOTE]
I'm getting the same error as Amidor when I try to login using e17.  I can't find anything relating to XINERAMA in my xorg.conf, but here it is anyway...

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC LCD1760N"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"NEC LCD1760N"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Any ideas? :)


Andy.

---

### Post by Rob2687 on 2005-04-28
I keep getting this 404 error when I try apt-get install Enlightenment :(

I seems like its looking for the wrong file name or something...

```
Err http://mirror.my-space.ath.cx unstable-20050215/ libe 0.17.0_pre10-0cvs20050216
  404 Not Found
Err http://mirror.my-space.ath.cx unstable-20050215/ enlightenment-data 0.17.0_pre10-0cvs20050216
  404 Not Found
Err http://mirror.my-space.ath.cx unstable-20050215/ libevas2 1.0.0_pre13-0cvs20050215
  404 Not Found
Err http://mirror.my-space.ath.cx unstable-20050215/ libecore1 1.0.0_pre7-0cvs20050215
  404 Not Found
Err http://mirror.my-space.ath.cx unstable-20050215/ enlightenment 0.17.0_pre10-0cvs20050216
  404 Not Found
Failed to fetch http://mirror.my-space.ath.cx/unstable/libe_0.17.0_pre10-0cvs20050216_i386.deb  404 Not Found
Failed to fetch http://mirror.my-space.ath.cx/unstable/enlightenment-data_0.17.0_pre10-0cvs20050216_i386.deb  404 Not Found
Failed to fetch http://mirror.my-space.ath.cx/unstable/libevas2_1.0.0_pre13-0cvs20050215_i386.deb  404 Not Found
Failed to fetch http://mirror.my-space.ath.cx/unstable/libecore1_1.0.0_pre7-0cvs20050215_i386.deb  404 Not Found
Failed to fetch http://mirror.my-space.ath.cx/unstable/enlightenment_0.17.0_pre10-0cvs20050216_i386.deb  404 Not Found
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by km3k on 2005-04-28
I'm seeing the same thing as Andy C and Amidor with e17.

When attempting to start enlightenment, it kicks me back to the login menu. Like Andy C and Amidor, the .xsession-errors then contains

```
Xlib:  extension "XINERAMA" missing on display ":0.0".
enlightenment: relocation error: /usr/lib/libedje.so.0: undefined symbol: evas_o
bject_image_border_center_fill_set
``` 

And since it was asked for, here's my xorg.conf 

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "True"
        Option          "EnablePageFlip" "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Any ideas?

---

### Post by Nikola on 2005-04-28
Does anyone knows how to fix file selector dialog in e17? When I try to open something, file selector dialog is not sorted alphabeticaly, but it some random way. This drives me nuts!
Also, in entrance, I get nice golden cursor, but not when I'm in e17. I get some plain white cursor.

EDIT:
I found another repository, with some e17 app debs I didn't find in soulmachine repository.
Check it out here:
[http://gefechtsdienst.de/uman/files/dists/unstable/main/binary-i386/](http://gefechtsdienst.de/uman/files/dists/unstable/main/binary-i386/)

---

### Post by uidzer0 on 2005-05-03
How did you get entrace running on startup?

---

### Post by vassalle on 2005-05-05
hi.. ive tried installing E17 using all the information i can gather from this forum. However, i still couldnt get it to install, keep on getting this 404 error.. ive tried adding a combination of soulmachine and also the mirror.myspace repo but couldnt.. i tried browsing through it and finding what pages exists and dont,(which eventually turns out that the enlightenment.0.17-pre* was in [http://mirror.my-space.ath.cx/](http://mirror.my-space.ath.cx/) unstable-20050215/ instead of [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable-20050215/ which doesnt exists anymore..)
even so, when i put in the mirrorspace repo in my sources.list, i still get the 404 error.. gahh, really dont know what went wrong here.. i could even download the .deb package using firefox, but somehow i cant download it using either wget, apt-get or synaptic. i thought of downloading all the .deb files using firefox and doing a sudo dpkg -i, but kinda felt that was really unwise, so i didnt. Btw, im still a newbie in Linux, just used it for the last 2 months.. anyway, could anyone help me ? i really want to install this software.. thanks in advance!

---

### Post by Aasitus on 2005-05-05
Well, I did download all those .deb packages and proceeded to install them manually. They're i386 packages though, and I'm running amd64.. So I did dpkg --force-architecture -i packade.deb, I don't know if that's very clever though :p Well, I was able to install most of them, homewer, I got a kewl dependency problem.

I mean, 
enlightenment depends on enlightenment data and libe
libe depends of enlightenment
enlightenment-data depends on enlightenment

So, how exactly am I supposed to install those? :) And umm, even though this is in Warty forum, it looks like this guide is for/works for Hoary, so that's what I'm running. And it's indeed amd64, so I guess it just might not work :F It'd be nice to have a amd64 repo, I wouldn't want to compile all those packages myself

---

### Post by nerve on 2005-05-07
Has anybody find a repository that synaptic can read from to get these files? I've had the same 404 problems as everyone else, for the record.

---

### Post by vrln on 2005-05-09
[QUOTE=codemills]well. I am looking a simple installation of e17 for a linux newbie. I am Linux server admin by profession and playing with servers and installation just from bash commands is my meat and bread but this is not the case for newbie. so [http://get-e.org](http://get-e.org) is too hardcore as it involves installation from command line.

the installation using synpatic by adding soulmachine repos is the simplest one IMHO.

so i am looking to do this entirely from synaptic with some files to be added edited using command line.


although i have installed enlightenment. i still have lots of e17 things to be added but synaptic is giving errors like depends BLAH but cannot be installed. i am extremely pissed off why it cant.  ](*,) 

i will add a screenshot later and the code in my preferences file and  sources file.[/QUOTE]

First of all, hello to everyone here. As you can see this is my first post here. I just happened to notice a certain url is mentioned here heh - I'm one of the content team guys from [http://get-e.org](http://get-e.org). This post is not meant to be an advertisement btw, I just want to clear a few things.

We are much more than just a site about installation information. The install section on the user guide is less than ~20% of the whole guide. It's true that manual compiling notes are told first, but that's because that works for all distributions. There's also a distribution specific section, which points at various unofficial package repositories.

The real point of get-e.org however, is to be a users' portal - something like kde-look.org is to KDE. The user guide, after the initial brief installation section, explains (almost) everything there is to know about configuring E17 and using the most popular EFL (Enlightenment Foundation Libraries) based applications. It's written as a book, so I'd suggest reading it from the beginning using the printable monolithic version, which can be found at [http://get-e.org/User_Guide/English_pages/print.html](http://get-e.org/User_Guide/English_pages/print.html). We also have the guide translated into 6 languages (more coming soon). These are all maintained to be concurrent with the current development version in CVS.

Besides the user guide, we also have a FAQs section that has all the most common questions (and answers) - noticed some of those questions in this thread too (this FAQs section is meant to be read after the user guide of course). The real deal with the site however, is that we host themes for various E17/EFL related programs - this includes EAPP iconsets, E17 themes and both static and animated background EDJ files. In the future we're hoping to have some Evidence themes there too. The status page has the current development state "in a nutshell", so if your wondering why a certain feature doesn't exist yet, you might want to check that. Last but not least, we also have the obligatory screenshots section.

All in all, this site has just been started around 1-2 weeks ago, so this is hopefully just the beginning. The lude.net/edocs link that I noticed earlier in this thread no longer exists btw - that project has moved to this new site.

---

### Post by sud_crow on 2005-05-14
[QUOTE=Aasitus]Well, I did download all those .deb packages and proceeded to install them manually. They're i386 packages though, and I'm running amd64.. So I did dpkg --force-architecture -i packade.deb, I don't know if that's very clever though :p Well, I was able to install most of them, homewer, I got a kewl dependency problem.

I mean, 
enlightenment depends on enlightenment data and libe
libe depends of enlightenment
enlightenment-data depends on enlightenment

So, how exactly am I supposed to install those? :) And umm, even though this is in Warty forum, it looks like this guide is for/works for Hoary, so that's what I'm running. And it's indeed amd64, so I guess it just might not work :F It'd be nice to have a amd64 repo, I wouldn't want to compile all those packages myself[/QUOTE]
 Im also running AMD64 and im having this error:

> 
root@dhcppc1:/home/crow #  apt-get install enlightenment
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
El paquete enlightenment no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente
Sin embargo, los siguientes paquetes lo reemplazan:
  e16-data
E: El paquete enlightenment no tiene candidato para su instalación
root@dhcppc1:/home/crow #


Its says the package is not available or that its out of date, blah blah blah (the error is through previous posts).

How do i manage to skip this ?? do i have to manually download each pkg? and then run:

]$ sudo apt-get install pkg1 pkg2 pkg3 pkg4.... etc...

??

Or because its a 32bit compilation it wont work on Ubuntu 64bits? If this is the case, if i install it in the chroot enviroment, that way would work?

Help please... !

---

### Post by rickz on 2005-05-18
Hi all...

I got the same problem as Nicola before:

After a few problems I got installed the packages 

enlightenment & enlightenment.data

I tried a reboot and got a black screen, after a few seconds it becomes a white one.
If I want to apt-get install eutilis the package ist not found.

I`m a total noob in Linux but pherhaps anybody wants to help a noob,too :)

(Sorry for my bad English, I`am from Germany)


**edit**  I ALL GOT IT !!

---

### Post by clb137 on 2005-05-22
Hi ALL

Can anyone tell me WHERE I can down load E17?  '0.17.0_pre10-0cvs20050216'  I have looked at ALL the locations in this thread and the nearest I can get to it is 0.19.999???

is this the same version under a different file name??

thanks in advance

clinton

---

### Post by marti163 on 2005-06-02
I found this info while being confused by the same issue.

[http://shadoi.soulmachine.net/](http://shadoi.soulmachine.net/)

"One question I get repeatedly is: "Why did the version # go down?!" This was a decision made by Rasterman, the project lead. He makes snapshot releases on enlightenment.freedesktop.org now and this change was made to make that process easier. The final release version will still be 0.17."

So use the 16.99 or whatever it is.

---

### Post by clb137 on 2005-06-02
[QUOTE=marti163]I found this info while being confused by the same issue.

[http://shadoi.soulmachine.net/](http://shadoi.soulmachine.net/)

"One question I get repeatedly is: "Why did the version # go down?!" This was a decision made by Rasterman, the project lead. He makes snapshot releases on enlightenment.freedesktop.org now and this change was made to make that process easier. The final release version will still be 0.17."

So use the 16.99 or whatever it is.[/QUOTE]


Many thanks for your reply,

are you still using the desktop??  I ahve give it up for know and will down loads it a final or beta E17


clinton

---

### Post by clb137 on 2005-06-04
Hi ALL

If anyone is interested I have found an install script that will install the latest build via CVS, you must install CVS first, then as the process goes on, you may have to install more software as you get errors,

I have just finished and i now have the latest version running,

for more info please follow the link and download the 'get_e.sh' script from 

[http://www.rasterman.com/index.php?page=Files](http://www.rasterman.com/index.php?page=Files)

I am runnnig E17 while typeing this, I am going to try to config the background and themes

thanks

clinton bennett

---

### Post by smoon on 2005-06-04
[QUOTE=clb137]Hi ALL

If anyone is interested I have found an install script that will install the latest build via CVS, you must install CVS first, then as the process goes on, you may have to install more software as you get errors,

I have just finished and i now have the latest version running,

for more info please follow the link and download the 'get_e.sh' script from 

[http://www.rasterman.com/index.php?page=Files](http://www.rasterman.com/index.php?page=Files)

I am runnnig E17 while typeing this, I am going to try to config the background and themes

thanks

clinton bennett[/QUOTE]

I'm working on an Installation-Script for e17 and the EFL that automatically grabs the source from CVS and builds .debs from that. Basically it works, I just have some minor things to tweak. Maybe I'll add something like automatical dependency resolution to make it as easy as possible to compile, install, update and remove enlightenment and it's libraries. I'll put it online as soon as it is usable for anyone except me ;)

---

### Post by clb137 on 2005-06-05
[QUOTE=smoon]I'm working on an Installation-Script for e17 and the EFL that automatically grabs the source from CVS and builds .debs from that. Basically it works, I just have some minor things to tweak. Maybe I'll add something like automatical dependency resolution to make it as easy as possible to compile, install, update and remove enlightenment and it's libraries. I'll put it online as soon as it is usable for anyone except me ;)[/QUOTE]


HI,

Cool nice one looking forward to it, the above script does work though.  May be it can save you some time

good luck

clinton

---

### Post by bo_emperor on 2005-06-05
Hi. I downloaded an compiled e17 from cvs. I followed all the instructions, but when I try to strat engage, the only thing I get is a flickering grey bar at the bottom of my screen, that eventually crashes my GNOME and I have to restart X. Any ideas what it might be?

---

### Post by crane on 2005-06-05
This sure has been a lot of work for a desktop environment. :-?

---

### Post by clb137 on 2005-06-06
[QUOTE=bo_emperor]Hi. I downloaded an compiled e17 from cvs. I followed all the instructions, but when I try to strat engage, the only thing I get is a flickering grey bar at the bottom of my screen, that eventually crashes my GNOME and I have to restart X. Any ideas what it might be?[/QUOTE]


Not sure,  did you add e17 and make a preference file?

Create a file called e17.desktop in /usr/share/xsessions/
Add the following lines to this file:

Code:

[Desktop Entry] Encoding=UTF-8 Name=e17 Comment= Exec=enlightenment Icon= Type=Application

clinton

---

### Post by bo_emperor on 2005-06-06
[QUOTE=clb137]Not sure,  did you add e17 and make a preference file?

Create a file called e17.desktop in /usr/share/xsessions/
Add the following lines to this file:

Code:

[Desktop Entry] Encoding=UTF-8 Name=e17 Comment= Exec=enlightenment Icon= Type=Application

clinton[/QUOTE]
 Yes I did do that. E17 starts with no problem. But engage just won't run in gnome.

---

### Post by clb137 on 2005-06-06
[QUOTE=bo_emperor]Yes I did do that. E17 starts with no problem. But engage just won't run in gnome.[/QUOTE]

Hi,

Have look at this it may shed some light for you

[http://get-e.org/User_Guide/English_pages/4.2.html](http://get-e.org/User_Guide/English_pages/4.2.html)


clinton

---

### Post by godlike on 2005-06-08
Hey guys personally i found the easiest way to get it installed with no broken packages etc... was to use synaptic to install 
0) libstdc
 1) zlib1g_dev
 2) libjpeg62_dev
 3) libfreetype6
 4) libxext6
 5) x-dev
 6) libxext-dev
 7) libpng12-dev
 8) libtiff4-dev
 9) libungif4
10) libungif4-dev
11) libxi-dev
12) libx11-dev
13) libxinerama-dev
14) libxcursor-dev
15) libpcre3
16) libltdl3
17) libltdl3-dev
18) libxau6
19) libxau-dev
20) libimlib2
21) libimlib2-dev
22) libid3
23) libid3tag0-dev
24) libogg-dev
25) libextractor0
26) libextractor0-dev
27) xlibmesa-glu-dev
28) checkinstall

Then i just downloaded all the cvs files of the e17 site and copiled them all myself and used checkinstall to make and install the packages has been working fine for over a week now....

If anyone wants i686 packages of the cvs build lemmie know...

---

### Post by smoon on 2005-06-08
Ok, I began programming something in C again and stopped enhancing the e17install script, so I decided to put it online. Basically it works, though dependecy checking and resolution and better error handling would be nice. Anyway, here it is: [http://nooms.de/misc/e17install.sh](http://nooms.de/misc/e17install.sh).

It will create a directory ${HOME}/e17install where everything happens, commandline parameters are as follows:
```
 Options:
   -c     Continue even though an error occured.
   -h     Print this usage and exit.
   -i     Install already created .debs.
   -n     Don't update source from CVS.
```

Now that I see the "Don't update source from CVS"-switch: Maybe the script should check if there's some source already and overwrite this switch since it wouldn't make any sense in case there's nothing. (Just in case anyone wants to improve it ;))

Btw. I already use it to update my e17/efl installation regularly.

---

### Post by Merc248 on 2005-06-09
It errors out on the edb .deb compilation... here's the last few lines in the edb.log file (by the way, thanks for doing this :D)

```
test -z "edb.pc edb-config README edb.spec edb.oe edb-native.oe edb.bb edbXnative.bb debian/changelog" || rm -f edb.pc edb-c$rm -f config.h stamp-h1
rm -f libtool
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
make[2]: Leaving directory `/home/merc248/e17install/e17/libs/edb'
rm -f config.status config.cache config.log configure.lineno configure.status.lineno
rm -f Makefile
make[1]: Leaving directory `/home/merc248/e17install/e17/libs/edb'
dh_clean
 dpkg-source -b edb
dpkg-parsechangelog: error: cannot open ./edb/debian/changelog to find format: No such file or directory
dpkg-source: error: syntax error in parsed version of changelog at line 0: empty file
```

By the way, I installed automake-1.9... I had several choices, I'm going to try some of the other versions in a second.

EDIT #405: Automake 1.8 didn't work either.  I'm guessing it's not even executing it... I've no idea how I would insert it in the script either :x

Oh yeah, I tried autogen.sh and configure and that didn't help at all (it DID generate the changelog files for Debian, but didn't advance the install at all).

---

### Post by banjobacon on 2005-06-09
I get the same error as the previous poster.

---

### Post by DownloadTHIS on 2005-06-09
I am also getting the same error.

---

### Post by smoon on 2005-06-09
Ok, thanks to [subterrific](http://www.ubuntuforums.org/member.php?u=2990) it should work now. The newest version can be found at [http://nooms.de/misc/e17install.sh](http://nooms.de/misc/e17install.sh).

Please let me know if the problem is gone now. If so: Compiles engrave for anyone of you? I don't get this darn thing to compile...

---

### Post by luiska on 2005-06-10
Hi

Awesome install script! Have it working till embryo then I get the following error :

cp -f /usr/share/misc/config.sub config.sub
cp: `/usr/share/misc/config.sub' and `config.sub' are the same file
make: *** [clean] Error 1


Any ideas?

Although, just saw that this is for warty and I am doing this on hoary. When building from cvs though it should not make a difference?

Luiska

---

### Post by Merc248 on 2005-06-10
Same error on my end :(

---

### Post by smoon on 2005-06-10
[QUOTE=luiska]Hi

Awesome install script! Have it working till embryo then I get the following error :

cp -f /usr/share/misc/config.sub config.sub
cp: `/usr/share/misc/config.sub' and `config.sub' are the same file
make: *** [clean] Error 1


Any ideas?

Although, just saw that this is for warty and I am doing this on hoary. When building from cvs though it should not make a difference?

Luiska[/QUOTE]

No, it shouldn't make any difference. Honestly I've written and am using it on Hoary only. It should make no difference if you use it on Warty, Hoary, Debian testing/sid whatever.

I updated the script to fix the config.sub problem, could you please try it again? As we are at errors: I had some problems compiling evas since it doesn't link against some XOrg libs that do not exist within the XFree86 distribution. I've created a simple patch that you've to apply manually if evas does not compile: [http://nooms.de/misc/evas_xorg_configure.diff](http://nooms.de/misc/evas_xorg_configure.diff)

Use it this way: ```
cd ${HOME}/e17install/e17/libs/evas && patch -p0 < /path/to/evas_xorg_configure.diff
```

Hope it works now.

---

### Post by ploptor on 2005-06-10
Thank you for that install script.

But I need some help: I get an error while building iconbar. The Logs says:

main.o(.text+0x1a7): In function `main':
/root/e17install/e17/apps/iconbar/src/main.c:64: undefined reference to `ecore_x_window_prop_xy_set'
collect2: ld returned 1 exit status

And my C Skill is, well, limited.

---

### Post by smoon on 2005-06-10
[QUOTE=ploptor]Thank you for that install script.

But I need some help: I get an error while building iconbar. The Logs says:

main.o(.text+0x1a7): In function `main':
/root/e17install/e17/apps/iconbar/src/main.c:64: undefined reference to `ecore_x_window_prop_xy_set'
collect2: ld returned 1 exit status

And my C Skill is, well, limited.[/QUOTE]

Other users get this as well, I think something is messed up in the CVS source atm. I'll have a look on it though.

---

### Post by luiska on 2005-06-13
Hi

Found the repos and installed it with apt-get! Worked like a charm!

Check in Hoary Customizations and Tricks for same thread.

Luiska

---

### Post by clb137 on 2005-06-14
[QUOTE=smoon]Other users get this as well, I think something is messed up in the CVS source atm. I'll have a look on it though.[/QUOTE]

Hi there 

trying your script but i am getting this error please can you help

+ Building and Installing libraries.
   .debs for edb already built.
   .debs for eet already built.
   .debs for imlib2 already built.
   Building .deb of imlib2_loaders
   Missing dependencies, trying to resolve this issue.
   Package libedb1-dev is missing on your system, installing it...

** Unable to build a debian package of imlib2_loaders.
** Check /home/clinton/e17install/compile_logs/imlib2_loaders.log for details.
** An error occured. Exiting...

can post error file if you need it


thanks clinton

---

### Post by clb137 on 2005-06-14
[QUOTE=luiska]Hi

Found the repos and installed it with apt-get! Worked like a charm!

Check in Hoary Customizations and Tricks for same thread.

Luiska[/QUOTE]

where and what repos did u use?

clinton

---

### Post by smoon on 2005-06-14
[QUOTE=clb137]where and what repos did u use?

clinton[/QUOTE]
I think he means this: [http://www.ubuntuforums.org/showpost.php?p=209851&postcount=43](http://www.ubuntuforums.org/showpost.php?p=209851&postcount=43) from that thread: [http://www.ubuntuforums.org/showthread.php?t=30525](http://www.ubuntuforums.org/showthread.php?t=30525). The repository is for Hoary only since I've no Warty/Breezy installation where I can build packages for these Ubuntu releases. Maybe they work anyway, just try it and don't forget to report if it works for any other Ubuntu release than Hoary.

---

### Post by clb137 on 2005-06-14
Hi SMOOM

I have tried ur script again, this time after I manually installed some dev files and I got as far as the E package then i get this error

''dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package''

Taken from the install log.  I hpe that you can help.  I have already installed E17 using another script bu i could not get the utils installed therefore i could not change icons or customize the ibar etc

look forward to hearing from you thanks

clinton

---

### Post by clb137 on 2005-06-15
[QUOTE=smoon]I think he means this: [http://www.ubuntuforums.org/showpost.php?p=209851&postcount=43](http://www.ubuntuforums.org/showpost.php?p=209851&postcount=43) from that thread: [http://www.ubuntuforums.org/showthread.php?t=30525](http://www.ubuntuforums.org/showthread.php?t=30525). The repository is for Hoary only since I've no Warty/Breezy installation where I can build packages for these Ubuntu releases. Maybe they work anyway, just try it and don't forget to report if it works for any other Ubuntu release than Hoary.[/QUOTE]


Hi Smoom,

Yes the work no problem at all to get E17 installed and running;  This the best and the furthest I have been able to get witht the instalation. now I can get 'entangle to work, well at least it will start but it will not let me add any dir just gives me a solid line???

I have managed to get other thems and icons working, even the CPU hungry 'layered_sky' background, and boy does that look impressive

thanks for all your work it is a great help, maybe one day I will learn as much as you guys

thanks again

clinton

PS if you have any tip on how i could get my Ibar edited with  more icons and change some I would appriciate it 
thanks :)  :)  :)

---

### Post by Corey on 2005-06-15
[QUOTE=clb137]Hi SMOOM

I have tried ur script again, this time after I manually installed some dev files and I got as far as the E package then i get this error

''dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package''

Taken from the install log.  I hpe that you can help.  I have already installed E17 using another script bu i could not get the utils installed therefore i could not change icons or customize the ibar etc

look forward to hearing from you thanks

clinton[/QUOTE]

Got the same problem here :(

---

### Post by kamstrup on 2005-06-15
I get:
```
mikkel@bitsplitter:/media/space/programs/e17$ sh e17install.sh 
 + Checking for required programs.
   Package fakeroot is missing on your system, installing it...
Please enter the password to sudo: ** I ENTER MY PASSWORD **
   Package automake1.7 is missing on your system, installing it...
 + Done.
  
 + Updating alternatives to automake-1.7
 + Done.
  
 + Updating source from CVS-Repository.
 + This may take a while depending on your internet connection.
 + Honestly, we're grabbing something around 150 Megabytes now.
 Please standby
 Please standby
 + Done.
  
 + Building and Installing libraries.
   Building .deb of edb
   Installing .debs for edb
   Building .deb of eet
   Installing .debs for eet
   Building .deb of imlib2
   Missing dependencies, trying to resolve this issue.
   Package libttf-dev is missing on your system, installing it...
   Package libungif4-dev is missing on your system, installing it...
   Package | is missing on your system, installing it...

** sudo failed

** An error occured. Exiting...

mikkel@bitsplitter:/media/space/programs/e17$
```

---

### Post by smoon on 2005-06-15
[QUOTE=kamstrup]I get:
```
mikkel@bitsplitter:/media/space/programs/e17$ sh e17install.sh 
 + Checking for required programs.
   Package fakeroot is missing on your system, installing it...
Please enter the password to sudo: ** I ENTER MY PASSWORD **
   Package automake1.7 is missing on your system, installing it...
 + Done.
  
 + Updating alternatives to automake-1.7
 + Done.
  
 + Updating source from CVS-Repository.
 + This may take a while depending on your internet connection.
 + Honestly, we're grabbing something around 150 Megabytes now.
 Please standby
 Please standby
 + Done.
  
 + Building and Installing libraries.
   Building .deb of edb
   Installing .debs for edb
   Building .deb of eet
   Installing .debs for eet
   Building .deb of imlib2
   Missing dependencies, trying to resolve this issue.
   Package libttf-dev is missing on your system, installing it...
   Package libungif4-dev is missing on your system, installing it...
   Package | is missing on your system, installing it...

** sudo failed

** An error occured. Exiting...

mikkel@bitsplitter:/media/space/programs/e17$
```[/QUOTE]

This is a known issue, run the script with the -c switch or just use the repository: [http://www.ubuntuforums.org/showpost.php?p=209851&postcount=43](http://www.ubuntuforums.org/showpost.php?p=209851&postcount=43).

---

### Post by smoon on 2005-06-15
[QUOTE=Corey]Got the same problem here :([/QUOTE]

Same as above: The problem is already known and I wasn't able to fix it yet, so use the repository if you want to try e17.

---

### Post by smoon on 2005-06-15
[QUOTE=clb137]Hi Smoom,

Yes the work no problem at all to get E17 installed and running;  This the best and the furthest I have been able to get witht the instalation. now I can get 'entangle to work, well at least it will start but it will not let me add any dir just gives me a solid line???

I have managed to get other thems and icons working, even the CPU hungry 'layered_sky' background, and boy does that look impressive

thanks for all your work it is a great help, maybe one day I will learn as much as you guys

thanks again

clinton

PS if you have any tip on how i could get my Ibar edited with  more icons and change some I would appriciate it 
thanks :)  :)  :)[/QUOTE]

Entangle is in an early stage of development and dies on me regularly. Just don't use it ;). Instead you can follow the guide on [http://get-e.org](http://get-e.org) about "Editing the menu, IBar and Engage the manual way" at the middle at this page [http://get-e.org/User_Guide/English_pages/3.3.html](http://get-e.org/User_Guide/English_pages/3.3.html). You can also try to configure IBar using drag and drop - tried it, but only got entries removed, nothing added. Maybe you've more luck.

---

### Post by clb137 on 2005-06-15
> **smoon]Entangle is in an early stage of development and dies on me regularly. Just don't use it  said:**
> http://get-e.org[/url] about "Editing the menu, IBar and Engage the manual way" at the middle at this page [http://get-e.org/User_Guide/English_pages/3.3.html](http://get-e.org/User_Guide/English_pages/3.3.html). You can also try to configure IBar using drag and drop - tried it, but only got entries removed, nothing added. Maybe you've more luck.


hi there,

Yes I have managed to get it all working now, I just re-built the packages that i downloaded with your script and now it works a treat, the only thing that I have not yey figured out is how to 'remove' form the barr with Entange,

Yes i agree the maual method is good and it works,

Thanks for all your help, I do like this E17 it is the way to go, look forward to helping out when and where I can

clinton

---

### Post by AndyAWS on 2005-06-15
My 'Configuration' menu (and most of the others) are empty...is this normal?

Also I just installed Enlightenment last night from smoon's repo...and this morning it wanted to be upgraded, to the same version I installed...???

Is this an effect of locking the version or was there actually an upgrade since last night?

Last question...should I install 'e_utils' and where do I find it?

---

### Post by Fingel on 2005-06-15
Im suing Hoary, there seems to be a dependency problem with libc6 (enlightenment wouldn't be the first) I cant seem to get around,

---

### Post by clb137 on 2005-06-16
[QUOTE=Fingel]Im suing Hoary, there seems to be a dependency problem with libc6 (enlightenment wouldn't be the first) I cant seem to get around,[/QUOTE]


google search for it down load from debian and force the install if required



clinton

---

### Post by Seti on 2005-06-16
I just installed e17 (on MiniSlack 1.1, not Hoary) and have to say it was easier than I expected, after the time I tried to install in Hoary. Just downloaded the tarballs and used pkgtool. Done.
Enlightenment is definitely a DE that is going places. I think it is absolutely beautiful! Check my screenie of it [here](http://www.deviantart.com/view/19468633/) 
I really liked using it, even if some stuff was a bit strange. Like I couldn't figure out how to edit the menu. Plus, it didn't want to play nice with xcompmgr, which I had to disable. 
Otherwise, I was impressed by how light and fast it was, despite being so heavy on the eye-candy. All those little openGL tricks really make it sparkle.
In a couple of days I have some spare time; I'm gonna get it working right on Hoary this time.

---

### Post by kamstrup on 2005-06-16
I finally got e17 working using smoons (Kudos to you! You da man!) .debs. My first impression was "wow", but digging in quickly revealed some rough edges. To some extend expected - of course - since this is  in-develpment software, but also things more concerning.

My primary concern being the fact that the "dropshadows" are not real dropshadows. Windows does not shade each other. This looks a bit wierd when you have overlapping windows. It gives a somewhat "hackish" impression of e17 if you ask me...

---

### Post by clb137 on 2005-06-16
[QUOTE=Seti]I just installed e17 (on MiniSlack 1.1, not Hoary) and have to say it was easier than I expected, after the time I tried to install in Hoary. Just downloaded the tarballs and used pkgtool. Done.
Enlightenment is definitely a DE that is going places. I think it is absolutely beautiful! Check my screenie of it [here](http://www.deviantart.com/view/19468633/) 
I really liked using it, even if some stuff was a bit strange. Like I couldn't figure out how to edit the menu. Plus, it didn't want to play nice with xcompmgr, which I had to disable. 
Otherwise, I was impressed by how light and fast it was, despite being so heavy on the eye-candy. All those little openGL tricks really make it sparkle.
In a couple of days I have some spare time; I'm gonna get it working right on Hoary this time.[/QUOTE]


Hi Seti,

To edit the Ibar and other menus just follow this link

[http://get-e.org/User_Guide/English_pages/3.3.html](http://get-e.org/User_Guide/English_pages/3.3.html)

If you want to see what E17 can really do have a look at this link and scroll down to the *.AVI files download them and have a look

[http://www.rasterman.com/index.php?page=Files](http://www.rasterman.com/index.php?page=Files)

good luck,if you need any help i will try for you

clinton

---

### Post by clb137 on 2005-06-16
[QUOTE=kamstrup]I finally got e17 working using smoons (Kudos to you! You da man!) .debs. My first impression was "wow", but digging in quickly revealed some rough edges. To some extend expected - of course - since this is  in-develpment software, but also things more concerning.

My primary concern being the fact that the "dropshadows" are not real dropshadows. Windows does not shade each other. This looks a bit wierd when you have overlapping windows. It gives a somewhat "hackish" impression of e17 if you ask me...[/QUOTE]


Can you post an example?????

---

### Post by clb137 on 2005-06-16
HI,

A couple of shots of E17 in action for you to look at

---

### Post by ndhiet on 2005-06-17
Hi,

I'm newbie in Ubuntu, and know I've got trouble to apply your advice below:

[I]Using synaptic, install the following packages:

[CODE]
enlightenment		0.17.0_pre10-0cvs20050216
enlightenment-data	0.17.0_pre10-0cvs20050216
eutils			0.0.1-0cvs20050215[/CODE[/I]] 

*E17 should now be available as a session from the gnome login screen. :)*

when I type synaptic in terminal mode, it will proceed to Synaptic Package Manager (graphical), but when in SPM, I cannot impeletement your advice..
Can you give me more details guide?? step by step I hope...

Thanks in advance,
ndhiet

---

### Post by clb137 on 2005-06-17
[QUOTE=ndhiet]Hi,

I'm newbie in Ubuntu, and know I've got trouble to apply your advice below:

[I]Using synaptic, install the following packages:

[CODE]
enlightenment		0.17.0_pre10-0cvs20050216
enlightenment-data	0.17.0_pre10-0cvs20050216
eutils			0.0.1-0cvs20050215[/CODE[/I]] 

*E17 should now be available as a session from the gnome login screen. :)*

when I type synaptic in terminal mode, it will proceed to Synaptic Package Manager (graphical), but when in SPM, I cannot impeletement your advice..
Can you give me more details guide?? step by step I hope...

Thanks in advance,
ndhiet[/QUOTE]


Try this 

 http://www.ubuntuforums.org/showpos...51&postcount=43 from that thread: http://www.ubuntuforums.org/showthread.php?t=30525. 

This is from an earlier post in this thread, there is a lot of good reading in this thread have a good luck at it, if you need any more advice please get in touch

thanks


clinton

---

### Post by mojojojojo on 2005-06-20
Hello, iam new to the linux scene and Ubuntu is the first linux distro i have tried. Hehe. Ok well i followed everything as it said in the first post but i was doing the force version By the Package mnager, the protocol exited itself right after i pressed fore version. So someone suggested i try "sudo aptitude install program=version" in terminal. And here is what it gave me as logs:

```


mojojojo@BaD:~$ sudo aptitude install enlightenment=0.17.0_pre10-0cvs20050216
Password:
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Unable to find a version "0.17.0_pre10-0cvs20050216" for the package "enlightenment"
The following packages have been kept back:
  libimlib2
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
mojojojo@BaD:~$ sudo aptitude install enlightenment-data=0.17.0_pre10-0cvs20050216
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Unable to find a version "0.17.0_pre10-0cvs20050216" for the package "enlightenment-data"
The following packages have been kept back:
  libimlib2
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
mojojojo@BaD:~$ sudo aptitude install eutils=0.0.1-0cvs20050215 Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Unable to find a version "0.0.1-0cvs20050215" for the package "eutils"
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  eutils: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is installed.
          Depends: libe but it is not installable
          Depends: libecore0 but it is not installable
          Depends: libedb1 but it is not installable
          Depends: libedje0 but it is not installable
          Depends: libeet0 but it is not installable
          Depends: libengrave0 but it is not installable
          Depends: libesmart0 but it is not installable
          Depends: libevas0 but it is not installable
          Depends: libewl0 but it is not installable


```

Ok, so can anyone help? I think there are errors in there obviously. How can i fix this and install e17? Thanks very much

---

### Post by RobWeir on 2005-06-20
These packages are not for Ubuntu Hoary, and will not work on it.

---

### Post by smoon on 2005-06-20
[QUOTE=mojojojojo]Hello, iam new to the linux scene and Ubuntu is the first linux distro i have tried. Hehe. Ok well i followed everything as it said in the first post but i was doing the force version By the Package mnager, the protocol exited itself right after i pressed fore version. So someone suggested i try "sudo aptitude install program=version" in terminal. And here is what it gave me as logs:

(...)

Ok, so can anyone help? I think there are errors in there obviously. How can i fix this and install e17? Thanks very much[/QUOTE]

Use the instructions posted there: [http://www.ubuntuforums.org/showpost.php?p=209851&postcount=43](http://www.ubuntuforums.org/showpost.php?p=209851&postcount=43), there's more information in the whole thread: [http://www.ubuntuforums.org/showthread.php?t=30525](http://www.ubuntuforums.org/showthread.php?t=30525)

---

### Post by clb137 on 2005-06-21
[QUOTE=mojojojojo]Hello, iam new to the linux scene and Ubuntu is the first linux distro i have tried. Hehe. Ok well i followed everything as it said in the first post but i was doing the force version By the Package mnager, the protocol exited itself right after i pressed fore version. So someone suggested i try "sudo aptitude install program=version" in terminal. And here is what it gave me as logs:

```


mojojojo@BaD:~$ sudo aptitude install enlightenment=0.17.0_pre10-0cvs20050216
Password:
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Unable to find a version "0.17.0_pre10-0cvs20050216" for the package "enlightenment"
The following packages have been kept back:
  libimlib2
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
mojojojo@BaD:~$ sudo aptitude install enlightenment-data=0.17.0_pre10-0cvs20050216
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Unable to find a version "0.17.0_pre10-0cvs20050216" for the package "enlightenment-data"
The following packages have been kept back:
  libimlib2
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
mojojojo@BaD:~$ sudo aptitude install eutils=0.0.1-0cvs20050215 Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Unable to find a version "0.0.1-0cvs20050215" for the package "eutils"
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  eutils: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is installed.
          Depends: libe but it is not installable
          Depends: libecore0 but it is not installable
          Depends: libedb1 but it is not installable
          Depends: libedje0 but it is not installable
          Depends: libeet0 but it is not installable
          Depends: libengrave0 but it is not installable
          Depends: libesmart0 but it is not installable
          Depends: libevas0 but it is not installable
          Depends: libewl0 but it is not installable


```

Ok, so can anyone help? I think there are errors in there obviously. How can i fix this and install e17? Thanks very much[/QUOTE]



See the thread above,  have i=you installed via 'apt-get; ??? Once you have upadated your sources.conf file???

---

### Post by Malifick on 2005-06-25
hey there , cant seem to get synaptic to work with that line in /etc/apt/souces.list . 
is the server down over there or what , im really wanting to have e17 on my desktop .
 ](*,)  :-({|=

---

### Post by clb137 on 2005-06-26
[QUOTE=Malifick]hey there , cant seem to get synaptic to work with that line in /etc/apt/souces.list . 
is the server down over there or what , im really wanting to have e17 on my desktop .
 ](*,)  :-({|=[/QUOTE]


can u post  ur 'sources.list' file please


clinton

---

### Post by smoon on 2005-06-26
[QUOTE=Malifick]hey there , cant seem to get synaptic to work with that line in /etc/apt/souces.list . 
is the server down over there or what , im really wanting to have e17 on my desktop .
 ](*,)  :-({|=[/QUOTE]

The server is up and running and works just fine for me (just tested it). Please post your **/etc/apt/sources.list** just like clb137 said as well as your apt (synaptic) output.

---

### Post by tmh on 2005-06-28
Just a note that these instructions did not work for me in hoary.
The following, however, did work. The only real change was using the different repository listed there: [http://www.ubuntu-es.org/node/4724](http://www.ubuntu-es.org/node/4724)

And the repository: deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/

---

### Post by smoon on 2005-06-29
[QUOTE=tmh]Just a note that these instructions did not work for me in hoary.
The following, however, did work. The only real change was using the different repository listed there: [http://www.ubuntu-es.org/node/4724](http://www.ubuntu-es.org/node/4724)

And the repository: deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/[/QUOTE]

Hehe, but that's exactly the repository we're propagating here - isn't it? :)

Btw.: I created a new package today. The "anouncement" can be found there [http://www.ubuntuforums.org/showpost.php?p=233904&postcount=96](http://www.ubuntuforums.org/showpost.php?p=233904&postcount=96).

---

### Post by sapo on 2005-06-29
i got this error:
```

root@stfu:/home/sapo # apt-get install enlightenment
Reading package lists... Done
Building dependency tree... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment has no installation candidate

```

---

### Post by smoon on 2005-06-30
[QUOTE=sapo]i got this error:
```

root@stfu:/home/sapo # apt-get install enlightenment
Reading package lists... Done
Building dependency tree... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment has no installation candidate

```[/QUOTE]

Do you have the repository in your **/etc/apt/sources.list** and have done an `apt-get update'?

---

### Post by clb137 on 2005-06-30
[QUOTE=tmh]Just a note that these instructions did not work for me in hoary.
The following, however, did work. The only real change was using the different repository listed there: [http://www.ubuntu-es.org/node/4724](http://www.ubuntu-es.org/node/4724)

And the repository: deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/[/QUOTE]

that is the correct line anyway???????

not sure what did not work for you???


clinton

---

### Post by stevetorrefranca on 2005-07-14
hi,

eutils from soulmachine has dep problems to in hoary.  yes i have a lot of stuff from hoary universe too.

any idea how to fix this.

thank you!

steve

---

### Post by smoon on 2005-07-15
[QUOTE=stevetorrefranca]hi,

eutils from soulmachine has dep problems to in hoary.  yes i have a lot of stuff from hoary universe too.

any idea how to fix this.

thank you!

steve[/QUOTE]

Don't use the soulmachine repository. Use the one that is mentioned in the [Howto](http://www.ubuntuforums.org/showthread.php?t=46105).

---

### Post by brad457 on 2005-07-20
that install script doesn't work I get through a lot of libs and get stuck at this:

```

   Building .deb of epsilon

** Unable to build a debian package of epsilon.
** Check /root/e17install/compile_logs/epsilon.log for details.
** An error occured. Exiting...

```

When I check the log I find this:

```

found eof where expected first heading at /usr/lib/dpkg/parsechangelog/debian line 136.
dpkg-buildpackage: unable to determine source package

```

Any ideas?

---

### Post by pvphaneuf on 2005-08-03
I'm also using your HowTo to get e17 installed, but I get stumped on the first step (newb). I'm adding the repository to /etc/apt/sources.list and I always get this error when starting up synaptic

W: Couldn't stat source package list [http://soulmachine.net](http://soulmachine.net) unstable/ Packages (/var/lib/apt/lists/soulmachine.net_debian_unstable_Packages) - stat (2 No such file or directory)

Here is my sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

this is with the *deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/* taken out. Could you show me where to plug it in or any other info on what I may have wrong?

---

### Post by smoon on 2005-08-06
_Do not_ use the installscript nor the soulmachine repository, read that howto:
**[http://www.ubuntuforums.org/showthread.php?t=46105](http://www.ubuntuforums.org/showthread.php?t=46105)**

---

### Post by aussiedini on 2005-08-07
[QUOTE=bobmitch]This is a quick guide to menu/launcher editing - but I haven`t done extensive testing.  If all is well, I`ll add this to the howto.  It deals mainly with creating entries, but will show the path to removing entries as well, using the *.order* files.

First off, launch the application you want to create an 'icon' for.

Click the top left corner (but not the border!) with the left mouse button and select "Create Icon". Note that you need e_utils (which needs e17/libs/engrave) installed in order for this to work.  (You should have this package installed already if you followed the howto.)

An .eapp file will be created and moved to **~/.e/e/applications/all**.

Next, you need to add this .eapp file to the relevant **.order ** file.  These order files are what e17 parses when starting the apps, and are stored in the following directories:

```
**iBar:** ~/.e/e/applications/bar
**E17 menu:** ~/.e/e/applications/favourite
**Engage:** ~/.e/e/applications/engage

``` 

Here's and example iBar .order file:

```
firefox.eapp
xmms.eapp
engage.eapp
entice.eapp
evidence.eapp
``` 

Note that you can also create subdirectories for the menu. Simply make directories within **~/.e/e/applications/favourite ** and create **.order ** files in each one of them.

Here's an example: 
assuming that you have the following directories 

```
~/.e/e/applications/favourite/music
~/.e/e/applications/favourite/web
```

you can make a **~/.e/e/applications/.order ** which contains the following text:

```
terminal.eapp
music
web
```

This would create a menu that first shows the terminal icon and then has 2 directories - *music* and *web*. Following this system you'll also need to create .order files in those directories to select what .eapp files to have and in what order you want them to be in.


If you don`t want to create your own icons - the author of engage has a ton of them rolled already for your pleasure [here](http://aje.codewordt.co.uk/Files_files/applications.tar.gz) .

Note, that this has been heavily lifted from the site I linked to in the howto - but I`ve parsed it and packaged nicely for my fellow Ubuntians. :)

Good luck, and let us know if it works. :)[/QUOTE]
 Hi,
I tried this and the eapp file wasnt created. Any ideas?

---

### Post by dviflx on 2005-08-15
[QUOTE=brad457]that install script doesn't work I get through a lot of libs and get stuck at this:

```

   Building .deb of epsilon

** Unable to build a debian package of epsilon.
** Check /root/e17install/compile_logs/epsilon.log for details.
** An error occured. Exiting...

```

When I check the log I find this:

```

found eof where expected first heading at /usr/lib/dpkg/parsechangelog/debian line 136.
dpkg-buildpackage: unable to determine source package

```

Any ideas?[/QUOTE]

I've got an identical problem. It also occured when trying to build epeg, but managed to get round that by building the deb for libepeg on another machine. However, on this other machine, it segfaults all over the place after this step.

Any suggestions?

---

### Post by super on 2005-08-15
one answer and one question  :-P 

@aussiedini
e17 has recently been updated and no longer uses 'eapp's. it now uses eap's (same thing but with one less 'p') just change your icons and the names in the .order file and you should be fine.  :) 

@smoon, or other e17 wizards
i am having problems with some of the e17 configuration apps. whenever i run emblem, e_utils_eapp_edit, etc... i get the following error:

[FONT=Courier New]No usable themes found
Segmentation Fault[/FONT]

this only seems to occur with config tool because eclips, eclair, etc... all work fine. also evidence works fine but if i select the preferences option from the menu i get the same problem.

any ideas?  :?

---

### Post by Ma3lgwyn on 2005-09-02
I followed the instructions on the first page, and when I loaded Synaptic, I got this message:

> 
W: Couldn't stat source package list [http://soulmachine.net](http://soulmachine.net) unstable/ Packages (/var/lib/apt/lists/soulmachine.net_debian_unstable_Packages) - stat (2 No such file or directory


What've I done wrong? I'm running Hoary Hedgehog, fresh install....


OOps - my bad! I hadn't run apt-get update.... :blush:

Now I get another message though:
> 
enlightenment:

Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list




Sorry again.... I should've looked around before I posted! All fixed, thanks to
[http://www.ubuntuforums.org/showthread.php?t=46105](http://www.ubuntuforums.org/showthread.php?t=46105)

---

### Post by dviflx on 2005-09-02
Gave up with building it myself in the end, and just got them from apt - works a dream on both my server and my laptop, thanks guys.

Also confirmed for me that my Xorg crash is being exclusively caused by firefox. But I have more 'puters available for web browsing.

For the record, E17 is amazing - this is what a GUI should be like. Can't wait for this to be finished. And keep an eye on [Project Looking Glass](http://www.sun.com/software/looking_glass/)...

---

### Post by didit on 2005-09-03
everytime i log into E17, GUI for all gtk application looks very primitive. Yes, i know how to solve this, executing gnome-theme-manager or gnome-setting-daemon&, then it will give me my nice gtk theme back and icons. My question is how to starup automatically gnome-setting-daemon, so i dont execute in terminal everytime i use E17?
Thanks

Didit

---

### Post by cg18 on 2006-01-15
After reading all the pages and tried all your workarounds in vain for e17 install, i've found the way to do it, it's simple (for a newby like me) and fast:

[http://www.soulmachine.net/wiki/index.php?title=Enlightenment_on_Ubuntu_5.10_%28Breezy_Badger%29](http://www.soulmachine.net/wiki/index.php?title=Enlightenment_on_Ubuntu_5.10_%28Breezy_Badger%29)

Hope it works for anyone else.

PS. I duno if someone else had this problem, in the CONFIGURATION > CONFIGURATION PANEL menu just a window open but no icons or settings for configure appear into. It is incomplete my instalation or i need to add some files? Thanks in advance (the newby :) )

---

### Post by Alessandro - Linux newb on 2006-02-07
Ok, if you are still having problems with breezy, visit this site here for a complete guide etc,

[http://www.soulmachine.net/wiki/index.php?title=Enlightenment_on_Ubuntu_5.10_%28Breezy_Badger%29](http://www.soulmachine.net/wiki/index.php?title=Enlightenment_on_Ubuntu_5.10_%28Breezy_Badger%29)

ps, if for some reason the instruction 

"wget soulmachine.net/public.key && sudo apt-key add public.key"

doesnt work, just download it (the public key) to your home directory and try,

"sudo apt-key add public.key" on it,

hope this helps someone

---

### Post by dlai on 2006-02-18
hey everybody I'm looking for some help here... For some reason ibar and the menus resets everytime I restart enlightenment, do you have any idea what to do?

---

### Post by dlai on 2006-02-18
> i am having problems with some of the e17 configuration apps. whenever i run emblem, e_utils_eapp_edit, etc... i get the following error:

No usable themes found
Segmentation Faul
yeah it seems to be the same error here... very annoying... any solutions?

---

### Post by Cashel on 2006-02-25
Ack! Anyone have an updated URL ? The package maintainer maintains this loosely..

---

### Post by Kobra on 2006-02-26
*

---

### Post by nullspace on 2006-03-30
I am getting mass dependence errors. 

```
The following packages have unmet dependencies:
  edje0-bin: Depends: libecore0 but it is not going to be installed
             Depends: libedje0 but it is not going to be installed
             Depends: libevas0 but it is not going to be installed
  elicit: Depends: libecore0 but it is not going to be installed
          Depends: libedje0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libevas0 but it is not going to be installed
  emodules: Depends: libe but it is not going to be installed
            Depends: libecore0 but it is not going to be installed
            Depends: libevas0 but it is not going to be installed
            Depends: libesmart0 but it is not going to be installed
            Depends: libedje0 but it is not going to be installed
            Depends: emodule-calendar but it is not going to be installed
            Depends: emodule-cpu but it is not going to be installed
            Depends: emodule-emu but it is not going to be installed
            Depends: emodule-evolume but it is not going to be installed
            Depends: emodule-flame but it is not going to be installed
            Depends: emodule-mbar but it is not going to be installed
            Depends: emodule-mem but it is not going to be installed
            Depends: emodule-mount but it is not going to be installed
            Depends: emodule-net but it is not going to be installed
            Depends: emodule-rain but it is not going to be installed
            Depends: emodule-screenshot but it is not going to be installed
            Depends: emodule-slideshow but it is not going to be installed
            Depends: emodule-snow but it is not going to be installed
            Depends: emodule-tclock but it is not going to be installed
            Depends: emodule-uptime but it is not going to be installed
            Depends: emodule-weather but it is not going to be installed
            Depends: emodule-wlan but it is not going to be installed
            Conflicts: emodules-extra but 0.16.999.022-1 is to be installed
            Conflicts: evolume
  emodules-extra: Depends: libe but it is not going to be installed
  engage: Depends: libe but it is not going to be installed
          Depends: libecore0 but it is not going to be installed
          Depends: libedje0 but it is not going to be installed
          Depends: libemotion0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libevas0 but it is not going to be installed
          Depends: libewl0 but it is not going to be installed
  enlightenment: Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
                 Depends: libevas0 but it is not going to be installed
                 Depends: libe but it is not going to be installed
                 Depends: libevas0 (>= 0.9.9.025-0cvs20060330) but it is not going to be installed
                 Depends: libecore0 (>= 0.9.9.025-0cvs20060330) but it is not going to be installed
                 Depends: libedje0 (>= 0.5.0.025-0cvs20060330) but it is not going to be installed
  enscribe-efl: Depends: libecore0 but it is not going to be installed
                Depends: libedje0 but it is not going to be installed
                Depends: libesmart0 but it is not going to be installed
                Depends: libevas0 but it is not going to be installed
  enterminus: Depends: libecore0 but it is not going to be installed
              Depends: libevas0 but it is not going to be installed
  entice: Depends: libecore0 but it is not going to be installed
          Depends: libedje0 but it is not going to be installed
          Depends: libepsilon0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libevas0 but it is not going to be installed
  entropy: Depends: libecore0 but it is not going to be installed
           Depends: libedje0 but it is not going to be installed
           Depends: libemotion0 but it is not going to be installed
           Depends: libepsilon0 but it is not going to be installed
           Depends: libevas0 but it is not going to be installed
           Depends: libewl0 but it is not going to be installed
  epsilon0-bin: Depends: libecore0 but it is not going to be installed
                Depends: libedje0 but it is not going to be installed
                Depends: libepsilon0 but it is not going to be installed
                Depends: libevas0 but it is not going to be installed
  etk: Depends: libecore0 but it is not going to be installed
       Depends: libedje0 but it is not going to be installed
       Depends: libevas0 but it is not going to be installed
       Depends: libevas0 but it is not going to be installed
       Depends: libecore0 but it is not going to be installed
       Depends: libedje0 but it is not going to be installed
  eutils: Depends: libe but it is not going to be installed
          Depends: libecore0 but it is not going to be installed
          Depends: libedje0 but it is not going to be installed
          Depends: libemotion0 but it is not going to be installed
          Depends: libengrave0 but it is not going to be installed
          Depends: libepsilon0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libevas0 but it is not going to be installed
          Depends: libewl0 but it is not going to be installed
  evas0-bin: Depends: libevas0 but it is not going to be installed
             Depends: libxrender1 (>= 1:0.9.0.2) but 1:0.9.0-1 is to be installed
  evfs: Depends: libecore0 but it is not going to be installed
        Depends: libevas0 but it is not going to be installed
        Depends: libxml2 (>= 2.6.23) but 2.6.21-0ubuntu1 is to be installed
  evidence: Depends: libevas0 but it is not going to be installed
  examine: Depends: libecore0 but it is not going to be installed
           Depends: libedje0 but it is not going to be installed
           Depends: libemotion0 but it is not going to be installed
           Depends: libevas0 but it is not going to be installed
           Depends: libewl0 but it is not going to be installed
E: Broken packages

```

I have so far tried four different repositories
soulmachine
 deb [http://gefechtsdienst.de/uman/files/](http://gefechtsdienst.de/uman/files/) unstable main
deb [http://www.enlightenment.technatica.net/breezy/](http://www.enlightenment.technatica.net/breezy/) ./
deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/

all have problems weather they are broken, don't exist or have umet dependence issues. This is an offical cry for help.

---

### Post by patrick295767 on 2006-04-23
--

---

### Post by spector on 2006-04-24
I had same problem.

I have found the packages that you need in this repositories

deb [http://packages.vergenet.net/vergenet/](http://packages.vergenet.net/vergenet/) stable main

try adding this to your /etc/apt/soucers.list, make apt-get update and reinstalling the oackages you need.

Now I'm expirencing problem with the libewl0 package

engage: symbol lookup error: /usr/lib/libewl.so.0: undefined symbol: EPSILON_EVENT_DONE

I hobe being helpfully

---

### Post by patrick295767 on 2006-04-27
I installed it via the script provided in this thread. 
I made some modifications, and this worked on another breezy pc... 
  
That can maybe help you... I hope
(it's a script to launch)
  
```

#!/bin/bash
#########################
	apt-get -f -y install 
	apt-get -f -y install 
	apt-get -f -y install 
	apt-get clean
	apt-get clean
	date
	##################### .fvwm2rc = part II = e17 & engage ################"
	##apt-get -f -y install e17 should be installaed at the end
	## fbsetroot should be installed too
	
	echo "Installing e17 !! enlightenment "
	apt-get -f -y install enlightenment
	apt-get -f -y install gtk-theme-switch gtkgl-dev gtkter
	
	apt-get -f -y install libtool
	apt-get -f -y install libxxf86vm-dev
	apt-get -f -y install libxxf86vm-dev
	
	apt-get -f -y install flex
	apt-get -f -y install xlibmesa-dev
	apt-get -f -y install xlibmesa-gl-dev
	apt-get -f -y install libglu1-xorg-dev
	mkdir /root
        mkdir /root/miniram
	cd /root/miniram
	rm /root/miniram/dr17-2.sh
	wget http://patrick295767.sitesled.com/miniram/dr17-2.sh
	## I'll install some packages, download the easy_e17.sh, and install it ! :-)
	chmod +x dr17-2.sh
	./dr17-2.sh
	
	date
	##########################################################################
```


Greetings, Patrick

---

### Post by spector on 2006-05-27
Now I have installed it woith everything working.

I'm just having problem because every time i change the theme my E get crashed.

Some Ideas?

Thx

---

### Post by M@dMerC on 2006-06-06
i've installed E17 from the deb [http://soulmachine.net/breezy/](http://soulmachine.net/breezy/) unstable/  repo in this thread but i was wondering if anyone knows of a more up-to-date repo preferably for dapper as thats what im running lol thanx in advance ;)

---

### Post by Metroid48 on 2006-07-30
Hey, just tried this. I get errors when I start the package manager. It can't find the repositories.

Also, the "great resource" link doesn't work in the guide.

---

### Post by ramasdf123 on 2006-08-01
i am getting this msg


```
enlightenment:

Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


```

am i forgetting something?

i am sure i did everything the 1st page told me to do

---

### Post by commodore on 2006-08-04
I have the same problem that ramasdf123 has.

---

### Post by Razer(x) on 2006-08-13
this repo doesn't work

---

### Post by me_gustas on 2006-09-28
Non of the repos works. i tryed alla the repos listed in this thread. Can anybody help me? I realy want to try Enlightenmen. Thanx :)

---

### Post by Lut!n on 2006-09-28
try one of these
[http://www.get-e.org/Main/News/_articles/334.html](http://www.get-e.org/Main/News/_articles/334.html)
[http://www.ubuntuforums.org/showthread.php?t=228018&highlight=enlightenment+repo](http://www.ubuntuforums.org/showthread.php?t=228018&highlight=enlightenment+repo)

---

### Post by Lucidio on 2006-10-21
none of the repos works for me neither...!:(

---

### Post by Uncle Spellbinder on 2006-10-22
[***E17(Enlightenment-DR17) repo***](http://www.ubuntuforums.org/showthread.php?t=228018)

---

### Post by jmwinn21 on 2006-10-25
Tried the How-To and it worked great the first time. 
Thanks for the info.

---

### Post by RoadTripDK on 2006-10-30
Will the above procedure also work on a Ubuntu Edgy PPC64 install? I am particularly concerned about whatever is being added from the [http://soulmachine.net/](http://soulmachine.net/) site.

Ubuntu PPC newbie - just got the thermal controls to behave the other day, so I am first able to dig in to all the Ubuntu goooodness now.

---

### Post by ner0tic on 2006-11-06
> **Uncle Spellbinder said:**
> [***E17(Enlightenment-DR17) repo***](http://www.ubuntuforums.org/showthread.php?t=228018)

these repos didn't work for me are there any new ones?

---

### Post by froghopper on 2006-11-07
Follow the instructions here are [http://seerofsouls.com/ubuntu.html](http://seerofsouls.com/ubuntu.html) The debs were created 10 October. Worked faultlessly for me.

---

### Post by Bubs on 2006-11-12
SoS didn't work for me.

the command they gave doesn't work.

and when I try to install e17 in synaptic it gives me an error saying they need e16.99 which is uninstallable

---

### Post by Lut!n on 2006-11-18
That doesn't work because of the pin you put in /etc/apt/preferences, which make apt look only for packages named e17, whereas on all the up-to-date repos available the packages are named enlightenment 0.16.999.xxx
This howto is outdated and you shouldn't follow it as it leads to incomptabilities with existing repos (the soulmachine repo is no longer maintained). Remove your pin in /etc/apt/preferences, and then you can try this repo : [http://www1.get-e.org/Main/News/_articles/334.html](http://www1.get-e.org/Main/News/_articles/334.html). The packages are updated weekly for x86 arch and about twice a month for the PPC users (see [http://www1.get-e.org/Main/News/_articles/346.html](http://www1.get-e.org/Main/News/_articles/346.html) )

Cheers, 
Lut!n

---

### Post by SolarBear on 2006-12-06
Just a quick note to anybody interested in installing enlightenment : using the repo in the above article will redirect you to this one :

deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) dapper e17

Add this one to your /etc/apt/sources.list instead. Cheers !

---

### Post by Lut!n on 2006-12-06
As SolarBear said above, the repos have moved. to use them, first uninstall the following packages : enlightenment enlightenment-dbg enlightenment-dev enlightenment-data e17 e17-devel-extras emodules0-all and all the emodules.
Then add one of those lines to /etc/apt/sources.list : 

deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) dapper e17
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17

the src repos are also available : deb-src <same as above>

They are now available for x86 and amd64 (dapper, edgy) and ppc32 (edgy)
Enjoy !
Lut!n

---

### Post by Liolikas on 2006-12-09
Things changed a lot since the first post in this topic was written so maybe someone can write new up-to-date 
HOWTO: Install and tweak E17 Enlightenment ???  :confused:

---

### Post by jlc on 2006-12-15
> **Lut!n said:**
> As SolarBear said above, the repos have moved. to use them, first uninstall the following packages : enlightenment enlightenment-dbg enlightenment-dev enlightenment-data e17 e17-devel-extras emodules0-all and all the emodules.
Then add one of those lines to /etc/apt/sources.list : 

deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) dapper e17
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17

the src repos are also available : deb-src <same as above>

They are now available for x86 and amd64 (dapper, edgy) and ppc32 (edgy)
Enjoy !
Lut!n

Anyone know were the key is?

---

### Post by tcrroadie on 2006-12-15
I simply ignored the message relating to the key and E17 installed just fine. 

After adding the repository to your apt source list just try installing Enlightenment.

aptitude update

aptitude install e17

---

### Post by tcrroadie on 2006-12-15
JLC, 

I did some searching and I believe I found the soluition to your question.  

I took this from Get-E.org. Link is here.

[http://www4.get-e.org/Main/News/_articles/365.html]("http://www4.get-e.org/Main/News/_articles/365.html")
> 
The repo are signed, so as for the previous repo, you can find the key at [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc), and then add it to the keyring using `apt-key add`. The repos are now available for AMD64 arch, for edgy and dapper. :)

I am at work right now, so I am unable to test.  I'll try it later and try to get back.

Kris

---

### Post by Lut!n on 2006-12-15
Oops. my mistake. I gave the infos, assuming you were already using the repos.
tcrroadie  is right, that's exactly the way to get the key. The news he pointed on get-e.org is the reference on how to use those repos :)

---

### Post by dyntryx on 2006-12-19
I had some weird dependency problems which I've since **resolved**.  However, I'll post the information here as a resource for anyone with a similar issue.
**READ:** _I already solved this issue; reading this post is unnecessary unless you are having problems and think you may be in a similar situation!_

If you're still reading...
**READ:** *I provide no guarantee and/or warranty for the information provided here.  I will take no liability in damages occurring due to following these instructions.  You, the user of the system, accept all liability for anything that happens AT ALL.* :neutral:
**NOTE:** * These instructions were written regarding (K)Ubuntu Edgy.  They may need changing for other releases of the *Ubuntu distro.  I do not recommend following this guide unless you're sure you know what you're doing.*

If you're still reading even now, I wish you luck... :twisted:

Firstly, let me just say that I had previously installed the Enlightenment package provided by Hawkwind at [http://seerofsouls.com](http://seerofsouls.com).  But, I decided I wanted to use the newest version from the repository listed at get-e.org.  If you have done this as well, issue these commands first:
```
sudo apt-get remove emodules0-all enlightenment
```
Nextly, using the Adept Package Manager (yes, the interface), search for installed packages using the filter "e17" and then "enlightenment".  Remove any you find.

Now, after this I tried to install e17 using the repository from get-e.org.  I had this in my sources.list:
```
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
```
Also I had imported the gpg key to diminish messages of the unverified source*:
```
wget http://lut1n.ifrance.com/repo_key.asc
sudo apt-key add repo_key.asc
```
I made sure to comment out the repositories provided by seerofsouls.com.  Of course, issue this command:
```
sudo apt-get update
```

So, I did this to install the new Enlightenment package:
```
sudo apt-get install e17
```
I didn't record the errors and I'd rather not try to reproduce them ;), but the issue is with libexml1_0.1.1+cvs20061112-1_i386.deb.  You may also see a problem with emodules0-language, which is related to the dependency on libexml1.  If you see either of these, this is how I fixed it, so you may try this as well.

Firstly, I issued the recommended command:
```
sudo apt-get -f install
```

Unfortunately this did not help, as I still got the same dependency issues.  So, I searched for help and only found [one other person]("http://forum.ubuntu-fr.org/viewtopic.php?pid=594229#p594229")with this issue at the [French Ubuntu Forums]("http://forum.ubuntu-fr.org/").  No help there, as they didn't resolve it and my French is bad anyway. :rolleyes:

So, what I tried next was commenting out the get-e.org repository as such:
```
#deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
```
Then I re-added the SeerOfSouls repositories:
```
deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy e17
deb-src [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy e17
deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
deb-src [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
```

If you don't want annoying messages, import the gpg keys for these repositories*:
```
wget http://seerofsouls.com/keys/hawkwind.asc
sudo apt-key add hawkwind.asc
wget http://seerofsouls.com/keys/philip.asc
sudo apt-key add philip.asc
```

Update as always when changing your sources.list:
```
sudo apt-get update
```

Finally, I did this command:
```
sudo apt-get -f install
```

After switching the repositories, the problem resolved itself.  How this occurred, I cannot be certain.  I should assume the installation completed using packages from both repositories.  None-the-less, this definitely DID get e17 running with the themes, etc. provided from get-e.org's listed repository.  Viewing "about" under Enlightenment does suggest that I am running the latest packaged version.  This post is actually written under the Enlightenment desktop environment.  Hope I've helped someone.

Cheers. :KS

*Guide Notes:*
See [http://seerofsouls.com/ubuntu.html]("http://seerofsouls.com/ubuntu.html") for information on enabling that repository.
See [http://www4.get-e.org/Main/News/_articles/365.html]("http://www4.get-e.org/Main/News/_articles/365.html") for information on enabling that repository.

* Yes, I understand the need for the GPG keys to provide secure repositories. :p

---

### Post by Beamerboy on 2006-12-24
I am getting errors with this in Dapper:

The following packages have unmet dependencies:
  e17: Depends: enlightenment-theme (>= 0.16.999) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
e17 [Not Installed]

Score is -1

I can't find enlightenment-theme in the repos.  Anyone got any ideas?

Paladine

---

### Post by Triple Threat on 2006-12-26
> **Beamerboy said:**
> I am getting errors with this in Dapper:

The following packages have unmet dependencies:
  e17: Depends: enlightenment-theme (>= 0.16.999) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
e17 [Not Installed]

Score is -1

I can't find enlightenment-theme in the repos.  Anyone got any ideas?

Paladine

I am getting the same problem. I am trying to figure it out. I have noticed on other repositories that enlightenment-theme is only suggested NOT DEPENDED UPON. I believe the problem lies in the fact that it is a virtual theme consisting of four or so other packages - all of which are themes (like enlightenment-theme-gunmetal or something of that nature)

My question is this: I have installed the other packages that are apart of this virtual one. couldnt i just create a dummy package called enlightenment-theme and install it to make the installerl shut up?

Either way, I believe this is a package development bug and I'd like to know when they will fix it if it really is a bug.

---

### Post by Triple Threat on 2006-12-26
one more thing. I am using Edgy not Dapper like the person above me.

---

### Post by autocrosser on 2006-12-26
Yes--I'm running into the same problem--anyone found the answer yet?

---

### Post by Lut!n on 2006-12-26
I'm working on it ;)
Fix will be commited soon, don't worry. Anyways, this isn't a big problem as e17 is only a metapackage, so you can install all the pkges which it depends on separately (except of course enlightenment-theme for the moment ;) )

EDIT : seems to work fine now

---

### Post by Triple Threat on 2006-12-26
I second that... it seems to be working. Just reload your repositories and you're good to go!

---

### Post by autocrosser on 2006-12-27
Thank you--that works very well--I'd hand-installed some of the themes already, but it's nice to have more choices

Any information on how to set-up some of the apps? I've started to look around & was wondering about other peoples experiences/input/thoughts--

---

### Post by rctxtreme on 2007-01-02
I'm a total noob... please tell me how to install E17, I tried editing sources.list with the text editor but it's read  only...

---

### Post by autocrosser on 2007-01-03
In a Terminal:

sudo gedit /etc/apt/sources.list

you need root permissions to modify that file.

---

### Post by rctxtreme on 2007-01-03
When I tried refreshing the repo index in synpatic it says that the soulmachine.net repo is 404 not found. I'll remove it for now.

---

### Post by BLTicklemonster on 2007-01-09
How do I get xmodmap to work in e17? I want my mouse buttons to work.

---

### Post by trippinnik on 2007-02-03
Ok, I got e17 working (I had to use another repo though) but does anyone know how to have Enlightenment not make GTK apps look so bad?  I'll try running it instead of metacity, and kill the panel too, but it seems like i shouldn't have to do that.  Enlightenment has everything and it's so fast while still being slick.  I am pretty impressed with it.

---

### Post by BLTicklemonster on 2007-02-03
Still wondering how to get xmodmap and locomo to work...

---

### Post by Lut!n on 2007-02-04
You can run gnome-settings-daemon or add this (for exemple) to the ~/.gtkrc-2.0 file :
```
gtk-font-name = "Bitstream Vera Sans 7"
gtk-theme-name = "Human"
gtk-icon-theme-name = "Human"
```
to have the gtk look'n'feel ;)

For lomoco, if you want to autorun it, you can use the /etc/rc.local script

---

### Post by BLTicklemonster on 2007-02-04
Hmmm

```
sudo gedit /etc/rc.local
```

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exec locomo
exec xmodmap

exit 0

```


???????

---

### Post by Lut!n on 2007-02-04
you don't need 'exec'. Besides, I think it's lomoco, not locomo ;)
I don't know about xmodmap, maybe xmodmap <your conffile> would work :)

---

### Post by dragnazz5.0 on 2007-02-09
well im trying to get this working but i cant even make a file named e17.desktop in /usr/share/xsessions.  i thought i would have permissions to do so but i guess i was wrong and i cant for the life of me figure out how to do it.

---

### Post by BLTicklemonster on 2007-02-09
> **dragnazz5.0 said:**
> well im trying to get this working but i cant even make a file named e17.desktop in /usr/share/xsessions.  i thought i would have permissions to do so but i guess i was wrong and i cant for the life of me figure out how to do it.
```

cd /usr/share/xsessions
```

then

```

sudo gedit e17.desktop
```

I think.

---

### Post by BLTicklemonster on 2007-02-09
> **Lut!n said:**
> you don't need 'exec'. Besides, I think it's lomoco, not locomo ;)
I don't know about xmodmap, maybe xmodmap <your conffile> would work :)

Yeah, the spelling always messes with me on that. I just posted that as a query, but never tried it. Thanks I'll try that.

---

### Post by SRX on 2007-07-29
when ever i go to start e-gnome it takes me to the normal gnome session 

can someone please help me

---

### Post by somesnapper on 2007-11-06
I cant even edit deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/ access denied. Is there a specific way to do it? I'm logged in as user with in the root group.

---

### Post by smartboyathome on 2007-11-07
> **somesnapper said:**
> I cant even edit deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/ access denied. Is there a specific way to do it? I'm logged in as user with in the root group.

You have to use su to become root (from the terminal), and then you will be able to edit it (using gedit /etc/apt/sources.list).

---

### Post by j0nn0 on 2008-01-19
Well, it looks like the repositories on soulmachine have been removed.  A better recommendation (imho) is the Geubuntu project, install described at:

[http://geubuntu.wikispaces.com/Installing+Geubuntu+7.10+from+packages]("http://geubuntu.wikispaces.com/Installing+Geubuntu+7.10+from+packages")

with some interesting info and screen shots at:

[http://www.linux.com/feature/123494]("http://www.linux.com/feature/123494")

---

### Post by richardh9936 on 2008-05-24
[SIZE="3"]The e17 repositories seem to have moved in the two years since this thread began.

In May 2008, the e17 repositories that other forums prefer are

DUNNEWIND ([http://e17blog.tuxfamily.org/e17blog_en.php/post/2007/08/22/HowTo-Install-Enlightenment-on-Ubuntu-Gutsy-Gibbon]("http://e17blog.tuxfamily.org/e17blog_en.php/post/2007/08/22/HowTo-Install-Enlightenment-on-Ubuntu-Gutsy-Gibbon"))
Installation date: 	October 10 2007
Version installed: 	enlightenment 1:0.16.999.041+cvs20071001-1gutsy1
Gutsy repository used: 	e17.dunnewind.net
Installation on: 	i386 architecture

and ALPHAGEMINI []("xms.alphagemini.org")
 and you will need [Falko's]("http://xsm.alphagemini.org/E17/repository/") instructions.

Falko recommends installing e17 and emodules-all.  apt may claim that the packages are broken, but the issue is that the packages require more recent library packages than are available from HARDY.  Good news - they are available from INTREPID.  Bad news - you will need some fancy footwork to get them.  Here are my steps, assuming you have opened a terminal and sudo -s -H already:

1. Follow Falko's instructions, including using apt-get install alphagemini-keyring
2. Make a backup copy of /etc/apt/sources.list (maybe call it sources.hardy)
3. Edit /etc/apt/sources.list and replace all instances of hardy with intrepid   Save and exit your editor.
4. Make a backup copy of /etc/apt/sources.list (maybe call it sources.intrepid)
5. apt-get update
6. apt-get install e17 emodules-all
7. Restore sources.hardy to sources.list
8. apt-get update        to restore the automatic updating procedures to HARDY and we're all back to normal.
9. log off.
10. On the log-in screen, change session to enlightenment (probably best to say just for this session, in case it all turns to custard.)
11. log in.
12. Ta-Da.... you should see the Enlightenment splash screen.

---

### Post by richardh9936 on 2008-05-24
[SIZE="3"]
I've corrected the text above and tested it on my laptop.  All ok as at 2008-07-06 08:30 UCT.

I still recommend you read Falko's page at [xms.alphagemini.org]("http://xms.alphagemini.org")
[/SIZE]

---

