---
title: "HOWTO: Kiba-dock"
date: 2006-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by janbanan on 2006-09-23
I searched around for a nice dock for gnome and found Kiba-dock.
Did'nt find a good howto for installing so I'm posting one. I'm a noob and have'nt wrote any howto's before. So this is for noobs. I've collected this from other howto's.

you need Gtk, CAIRO, PANGO and the GCONF library.

In terminal

Start with:

sudo aptitude install build-essential automake cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev libglade2-dev

Then download sourcecode:

cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock

Go to the kiba folder:

cd ./kiba-dock

Now generate:

./autogen.sh

generate executable:

make

Install:

sudo make install

To start kiba-dock:

kiba-dock

But If you want It to load each time you start a session, do the following:

Move to home:

cd ~

Create and edit the file:

gedit dock.sh

Type this in the editor:

#!/bin/bash
cd ~/kiba-dock
kiba-dock

Now make It executable:

chmod +x dock.sh

Now add this script to the startup programs.

Tips:
When I got to the "./autogen.sh" and "make" part I got some errors.
You might have to use automake 1.9 and gconf2.13. I did this in synaptic package manager. Search for automake and do a complete removal of automake1.4 and then install automake1.9
Make a search for autoconf and do a complete removal of autoconf2.59a and install autoconf2.13.

Then I got it working at last.

And here's the result after some editing. Enjoy!

---

### Post by pau on 2006-09-28
Hi,

I am getting a problem...

```
melanos| ./autogen.sh                                                                                                          
autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.in: not using Gettext
autoreconf2.50: running: aclocal  --output=aclocal.m4t
autoreconf2.50: `aclocal.m4' is unchanged
autoreconf2.50: configure.in: tracing
autoreconf2.50: configure.in: not using Libtool
autoreconf2.50: running: /usr/bin/autoconf
autoreconf2.50: running: /usr/bin/autoheader
autoreconf2.50: running: automake --add-missing --copy
configure.in: 8: required file `./[config.h].in' not found
files/Makefile.am:9: variable `glade_DATA' not defined
autoreconf2.50: automake failed with exit status: 1
```


any hint of what's wrong??

---

### Post by screamboy on 2006-09-28
scream@screamboy:~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is created
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
automake: Makefile.am: installing `./INSTALL'
configure.in: 8: required file `./[config.h].in' not found
akamaru/Makefile.am:7: variable `GTK_LIBS' not defined
akamaru/Makefile.am:7: variable `CAIRO_LIBS' not defined
dock/Makefile.am:12: variable `GTK_LIBS' not defined
dock/Makefile.am:12: variable `GCONF_LIBS' not defined
dock/Makefile.am:12: variable `PANGO_LIBS' not defined
dock/Makefile.am:12: variable `SVG_LIBS' not defined
dock/Makefile.am:12: variable `CAIRO_LIBS' not defined
dock/Makefile.am:12: variable `GLITZ_LIBS' not defined
gset-kiba/Makefile.am:8: variable `GTK_LIBS' not defined
gset-kiba/Makefile.am:8: variable `GCONF_LIBS' not defined
gset-kiba/Makefile.am:8: variable `GLADE_LIBS' not defined
files/Makefile.am:9: variable `glade_DATA' not defined
autoreconf: automake failed with exit status: 1
scream@screamboy:~/kiba-dock$




shit :(

---

### Post by KillerKiwi on 2006-09-28
that thing is just ridiculaous ...

Video of it in action
[http://www.youtube.com/watch?v=gi6D0sD5GdU&mode=related&search=](http://www.youtube.com/watch?v=gi6D0sD5GdU&mode=related&search=)

---

### Post by jman2807 on 2006-09-29
I had the same problem as screamboy but then I did a completel removal of automake 1.4 and the autogen worked. However now the make gives me the following error: 

deps/kiba-render.Tpo"; exit 1; fi
kiba-render.c: In function ‘load_icon’:
kiba-render.c:82: error: ‘rsvg_resize_func’ undeclared (first use in this function)
kiba-render.c:82: error: (Each undeclared identifier is reported only once
kiba-render.c:82: error: for each function it appears in.)
make[2]: *** [kiba-render.o] Error 1
make[2]: Leaving directory `/home/jerrod/kiba-dock/dock'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jerrod/kiba-dock'
make: *** [all] Error 2

And it may be becuase i am using autoconf 2.59a-7 but whenever I try to remove it and install 2.13 it always installs 2.59 again automatically. Anyway that i can force it to conf with version 2.13 or use another method to compile it? Thanks in advance.

---

### Post by liquilife on 2006-09-29
Same errors here as mentioned above. Has anyone gotten this to work using his method??
```
robbie@liquilife:~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is created
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
automake: Makefile.am: installing `./INSTALL'
configure.in: 8: required file `./[config.h].in' not found
akamaru/Makefile.am:7: variable `GTK_LIBS' not defined
akamaru/Makefile.am:7: variable `CAIRO_LIBS' not defined
dock/Makefile.am:12: variable `GTK_LIBS' not defined
dock/Makefile.am:12: variable `GCONF_LIBS' not defined
dock/Makefile.am:12: variable `PANGO_LIBS' not defined
dock/Makefile.am:12: variable `SVG_LIBS' not defined
dock/Makefile.am:12: variable `CAIRO_LIBS' not defined
dock/Makefile.am:12: variable `GLITZ_LIBS' not defined
gset-kiba/Makefile.am:8: variable `GTK_LIBS' not defined
gset-kiba/Makefile.am:8: variable `GCONF_LIBS' not defined
gset-kiba/Makefile.am:8: variable `GLADE_LIBS' not defined
files/Makefile.am:9: variable `glade_DATA' not defined
autoreconf: automake failed with exit status: 1

```

---

### Post by jman2807 on 2006-09-29
You probably have automack 1.4 installed. sudo synaptic and do a search for automake. Then do a complete removal of automake 1.4 and make sure that automake 1.9 is installed.

---

### Post by liquilife on 2006-09-29
Thanks, that was the trick! Hmm, it's running but with a black background. Once I hovered over the icons they disappeared as well which is just leaving me with a black box.

---

### Post by liquilife on 2006-09-29
Well, icons do not disappear but I can't seem to get a background to work for kiba-dock. The icon backgrounds are also not transparent. Everything is contained in black boxes. Anyone else having this issue?

---

### Post by pau on 2006-09-29
not for me... using automake 1.9 allows autogen.sh to be run but then make gives errors:

```
        then mv -f ".deps/kiba-render.Tpo" ".deps/kiba-render.Po"; else rm -f ".deps/kiba-render.Tpo"; exit 1; fi
kiba-render.c: In function ‘load_icon’:
kiba-render.c:82: error: ‘rsvg_resize_func’ undeclared (first use in this function)
```

Re black background and icons, I found a precompiled .deb on the net and installed it and got the problem you get now. I was hoping that compiling from source would fix it ...

---

### Post by jman2807 on 2006-09-29
I am getting the same errors as the above so last night i posted them on the beryl forums and got this response:

> 
no its not an automake/autoconf problem.
u probably have librsvg but no build in svg in cairo, some days ago i checked in the code if cairo has build in svg support, but this seems to be unneeded, i simply forgot to remove one check for the build in svg.
All should be fine now

He should update the source shortly.

Edit: I just got it to correctly compile however I am having some run time issues.

Edit Edit:

Alright I just got it fully working, a few pointers: If you install kiba dock and you run it  but you dont see any icons run the commands:
```

./utils/populate-dock.sh
make install-schemas

```
Then that should populate the dock, however, my dock came with an animated background which I dont like, so either right click on the kiba icon at the top and click preferences or if you dont see the icon then run: 
```

sudo gconf-editor

```
If you had to run the command then go to apps > kiba > style

There you can change all the settins, if you want complete transparency change all the dock alphas to 0 and the border alpha to 0. That should be about it.

---

### Post by liquilife on 2006-09-29
I have the transparencies all set at 0 and I still got the black background where the background image should be and the icons are still not transparent. Hmmm.

---

### Post by jman2807 on 2006-09-29
Are you running it under compiz? The gnome manager will draw black boxes around everything. I ran it under gnome just to check and got the exact replica of these effects...

---

### Post by liquilife on 2006-09-29
Ooh, no. I am running it under gnome. Hmm, guess that is my problem huh?

---

### Post by liquilife on 2006-09-29
Ok, so I went to the synaptic package manager and installed compiz. How would I run Kiba-Dock under compiz? I'm obviously missing something here :D

---

### Post by pau on 2006-09-29
To make your life easier: Here you are a deb package of kiba

[HTML]http://forum.beryl-project.org/attachment.php?item=2024[/HTML]

to install it, just do

```
sudo dpkg -i kiba-dock_0.1reacocard2-1_i386.deb
```

It's funny... now I have a live background AND the black background ](*,)

---

### Post by teabeartom on 2006-09-29
After a lot of frustration and searching, I finally found a .deb for kiba-dock!  It installed FAST and everything works great!!!  Download it here:
[http://fred.cpp.googlepages.com/kiba-dock_0.1cvs20061018-1_i386.deb](http://fred.cpp.googlepages.com/kiba-dock_0.1cvs20061018-1_i386.deb)

Then, go ahead and install it.  It will put a menu entry under Applications --> Accessories called "Kiba-dock"  Start the program and you will see nothing, however, it created an icon in the system tray.

Right click the icon and go into the "Icon Manager"  Enter data for a program.  Then, close out of that and go into "Gset-kiba"  Here, you need to set a position for the dock and you can change around some physics if you'd like.  Then, right click on the system tray icon and restart kiba-dock.  Hopefully all should work!  This is all I know, and I got mine to work.  Good luck!

---

### Post by pau on 2006-09-30
Hi,

your deb yields the same result as mine: the dock is on a balck background and the icons too... how can I solve it?

---

### Post by Marsan on 2006-09-30
Got the same black boxes around the icons :(

---

### Post by Aetherius on 2006-09-30
Got it working fine after installing automake1.9 its a nice little app but it doesn't show up in the gconf-editor and i can't get rid of the annoying animated blue background

---

### Post by Marsan on 2006-09-30
I got xgl/beryl in so now kiba-dock is working as it should without any black boxes around the icons :D

---

### Post by pau on 2006-09-30
How do you set up beryl for an ati card??? I followed the instructions for compiz but it doesn't work at all!

---

### Post by calvinthomas on 2006-09-30
Sorry, fixed 

Calv

---

### Post by PriceChild on 2006-09-30
I've had big troubles getting this going... but have doen my own howto in the edgy forum: [http://www.ubuntuforums.org/showthread.php?p=1563769](http://www.ubuntuforums.org/showthread.php?p=1563769)

I've been told it works under Dapper also :)

---

### Post by bg1256 on 2006-09-30
Does this require Xgl?  

The computer I'm trying to install Kiba-dock on right now cannot run Xgl, so I may be SOL here.

Thanks.

---

### Post by BOBSONATOR on 2006-10-01
So do you need XGL to run this?!

---

### Post by Marsan on 2006-10-01
from the beryl-forum:

> Yes. Kiba-dock needs to have a composite manager running to have the nice transparent icones. I tried with xcompmgr but there seems to be some artifact. Works great with compiz.

---

### Post by calvinthomas on 2006-10-01
Has anyone managed to find a way so that this dock NEVER ends up having icons on top of each other, I thought setting it to rope did it but it seems that after some restarts it still ends with them jumbled with some on top of the other.

Also is it possible to put it in dock mode (rather than rope) and get them all on the same line?

Calv

---

### Post by routerstu on 2006-10-11
> **pau said:**
> To make your life easier: Here you are a deb package of kiba

[HTML]http://forum.beryl-project.org/attachment.php?item=2024[/HTML]

to install it, just do

```
sudo dpkg -i kiba-dock_0.1reacocard2-1_i386.deb
```

It's funny... now I have a live background AND the black background ](*,)

this one worked, so very cool :)

thanks!

---

### Post by mrgnash on 2006-10-14
Worked for me. Many thanks :)

---

### Post by routerstu on 2006-10-17
does anyone know how to change the background of kiba dock? ive tried changing setting, restarting but i keep getting blue with clear bars as shown in screenshot.

---

### Post by domino on 2006-10-17
> **routerstu said:**
> does anyone know how to change the background of kiba dock? ive tried changing setting, restarting but i keep getting blue with clear bars as shown in screenshot.

bring up Kiba Settings Editor --> Dock --> Colors. There you can change the color and dock transparency to left, middle, and right side of the dock.

A question for you.. I built from the cvs and and my Setting Editor is only v.0.1.1. I noticed you have v.1.2. Where did you get that version? I thought the cvs was the latest.

---

### Post by mozetti on 2006-10-17
> **routerstu said:**
> does anyone know how to change the background of kiba dock? ive tried changing setting, restarting but i keep getting blue with clear bars as shown in screenshot.

You can also change the type from "gnome-dock" (i think) to "gradient" and it will change from the diagonal lines to, well, a gradient.

---

### Post by domino on 2006-10-17
Okay. I ran alien on the rpm build which gave me the higher version of the setting editor. i have already gotten 3 Dock crashed since install the deb package and the icons dont want to behave. They're like kids that refuses to stay put.](*,) ](*,) 

Glad I have 2 versions on KD on this system.

---

### Post by routerstu on 2006-10-17
i tried uploading but i am using kiba-dock_0.1cvs20061018-1_i386.deb

anytime i make a change from gradient or gnome dock nothing changed.  does anyone have any other ideas?  maybe its the .deb i installed?  i can try to change color, or style, and nothing.  please help?

---

### Post by pormogo on 2006-10-19
I am having the same problem I can't seem to get rid of that background. I noticed if I look at the settings in gconf-editor it says none of the options have schemas attached.

The first time I used ./autogen.sh and built it. when I did this I wasn't able to change ANY options at all :( 

So I removed that (rm -r  on the directory where it was built) and installed  the .deb which is better but it seems like only some of the settings are still working I can't move the dock from bottom center nor can I get rid of that background :(

---

### Post by routerstu on 2006-10-22
this new .deb works great for dapper!!!!!!!!!!!!!!!!!!!!!!!



[http://forum.beryl-project.org/topic-5577-deb-package-for-ubuntu-dapper](http://forum.beryl-project.org/topic-5577-deb-package-for-ubuntu-dapper)

---

### Post by giropizza on 2006-10-26
I installed the package and it works perfectly but I have a problem.
I use edgy and the bar is bottom-centered: the problem is that I have the icon on the very bottom of the screen. I want to make it little upper becouse now is on the bar and so if I have many windows open and I go on the bar the kiba-dock cover them.
Sorry for my english, I hope tha t someone understand the problem anc can solve it.

Thanks in advance

---

### Post by JedTheHead on 2006-10-28
This dock is great (once you explore all the crazy settings and tire of flipping it around your desktop ;)  Question though:  It seems to "activate" or rather, react to the mouse, about an inch above the actual icons.  So it goes a little nuts if I am working in the bottom of a window above it.  Anyone know what setting I am missing to control the "active area"?

Thanks!

---

### Post by amr2205 on 2006-11-21
After some adjustments, finally get kiba-dock working. Thanks for this how-to. Note: I use the new deb for kiba-dock.

---

### Post by Don_DiZzLe on 2006-11-23
which deb might that be?

Btw, does anyone how I can make a desktop file and where to put it so kiba can be accessed from system > preferences so i dont have to start kiba with inputting kiba-dock in the terminal?

---

### Post by steevk on 2006-11-23
To those who have transparency problems:

You need XGL installed to get the transparency effect. I prefer Beryl, but it's up to you...

---

### Post by macewan on 2006-11-29
compiz seems to be quicker than beryl at the moment and with kiba-dock there just isn't any comparison. with compiz it's smooth and quick to respond, but with beryl it crawls.

---

### Post by steevk on 2006-11-29
> **macewan said:**
> compiz seems to be quicker than beryl at the moment and with kiba-dock there just isn't any comparison. with compiz it's smooth and quick to respond, but with beryl it crawls.

See, it's all individual. I couldn't get Compiz to install, but beryl runs quite smoothly, even with all of the water effects on...


I have a feeling this is going to turn into something as large as emacs/vi...

---

### Post by Alex6969 on 2006-11-30
is there a way that i can position the dock between my two monitors?

I also cannot get the back ground to be trnasparent.

---

### Post by bg1256 on 2006-12-02
> **macewan said:**
> compiz seems to be quicker than beryl at the moment and with kiba-dock there just isn't any comparison. with compiz it's smooth and quick to respond, but with beryl it crawls.

With my beryl, kiba and beryl run fast and smooth.  Maybe it depends more on your system specs than compiz or beryl.

I have beryl and aiglx running, and kiba dock runs fine. Once in awhile, it gets buggy, but not too bigt a deal.

---

### Post by MockY on 2007-01-31
Installed kiba-dock with the latest .deb that is located in this thread. I'm running Beryl on 6.10 as well. The problem is that I can't change anything, in the properties that is. Everything goes back to the way it was before when I close the window. I can't get the ugly blue to disappear.  Any suggestions?

[Screenshot]("http://www.sotd.se/dock.png")

---

### Post by MockY on 2007-02-01
It is now solved. I uninstalled it again and downloaded the cvs from their official website [http://www.kiba-dock.org/](http://www.kiba-dock.org/)

---

### Post by Izobalax on 2007-02-09
Question:

I have Beryl running on Dapper. I wish to install this deb package given in this thread. However, I need to get rid of the current install of kiba-dock which doesn't work. How do I remove this so I can try this thread's deb package?

Many thanks. 

/izo

---

### Post by blade5256 on 2007-02-13
Im having a few problems here...first of ill start by saying i got it working SORTA....i go into Terminal and type kiba-dock and hit enter the dock comes up which i wanted but its coming up with all the windows i have open...which i guess thats what its suppose to do? but if i close my Terminal the dock closes all by its self...whats is that about? and when i go to change change the model it also closes and i get this in the Terminal:


(kiba-dock:28184): GConf-CRITICAL **: gconf_client_get_int: assertion `err == NULL || *err == NULL' failed
Segmentation fault (core dumped)


and when i open the dock back up the changes are made....whats going on?

---

### Post by ultragamer on 2007-02-17
when i run kiba-dock i get this error: salaam@salaam-desktop:~$ kiba-dock
** Message: Cant copy /usr/share/applications/epiphany.desktop to /home/salaam/.kiba-dock/epiphany.desktop and when i close terminal kiba-dock closes

---

### Post by Andy0 on 2007-02-26
See PriceChilds how-to

The cvs server is down :( well atleast for anonymous right now

---

### Post by amaan on 2007-03-01
i'm having trouble running kiba-dock, i get a whole bunch of diagonal blue lines where the dock is, don't know what it is...?

please help, i've downloaded and installed just about every version of kiba-dock out there, and each time has been different variations of the same blue lines :(

check out screenshot

---

### Post by bg1256 on 2007-03-05
The blue lines are just the default background!  Just open the configuration and change the colors! 


I'm also getting an error during install:

```
cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
```

renders the following:

```
PAM authenticate error: Authentication failure
cvs checkout: authorization failed: server metascape.afraid.org rejected access to /cvsroot for user anonymous
cvs checkout: used empty password; try "cvs login" with a real password

```

---

### Post by bugz0r on 2007-03-24
I get the same thing, what shoudl I do?

---

### Post by Woolz on 2007-04-02
After you install Kiba-Dock you must hit alt-F2 and type in populate-dock.sh  click the option to run in terminal. After that go to applications system tools and start kiba dock.  Right click the kiba icon go to profiles and choose dock. Then go into terminal and type sudo chmod 777 -R /etc/gconf. go back to kiba icon right click and choose restart kiba. It should be transparent. Tested on 3 computers and it works.

---

### Post by TheCleaner on 2007-04-03
> **amaan said:**
> i'm having trouble running kiba-dock, i get a whole bunch of diagonal blue lines where the dock is, don't know what it is...?

please help, i've downloaded and installed just about every version of kiba-dock out there, and each time has been different variations of the same blue lines :(

check out screenshot


I had the same thing happen, but got the .deb file from here:

[http://ubuntuforums.org/showthread.php?t=312789](http://ubuntuforums.org/showthread.php?t=312789)

Then installed it and had the same problem and was like "COME ON!".  But if you then right click on the Kiba-Dock icon on your launch bar and choose profiles and choose a profile it will work ok at that point and you can modify the profile from there.

Hope that helps.

---

### Post by riverguardian on 2007-06-23
The best way is to get Trevino's repositories via [http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/) and download the necessary things.

---

### Post by BlahMan_of.Doom on 2007-06-29
Here's a guide that I just did on amd64 Feisty (x86_64), and it works like a charm. it'll work for any other too.
[http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html](http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html)

You compile your own source, and it's not from Trevino's repos's so it works :D

---

