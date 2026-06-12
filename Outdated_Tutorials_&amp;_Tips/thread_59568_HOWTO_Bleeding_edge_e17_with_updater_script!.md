---
title: "HOWTO: Bleeding edge e17 with updater script!"
date: 2005-08-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Nightblade on 2005-08-24
[SIZE=3]**Introduction** [/SIZE]

Hello!
This howto is for people who want to use the Enlightenment e17 WM and that being from CVS.
I suggest removing all previous versions of Enlightenment before using this.

I will also give you a quick introduction to customizing, modules and so on. I've based this HOWTO on the script availible from the winged.it dev, this script being a improved version of Rastermans (the official E founder) own get-e script. 
Enlightenment Window Manager (WM) is for everyone who likes eye-candy, simple stuff and speed. It's pretty hard to setup since it has quite some bugs, but if you work it out it's really comfortable!

[SIZE=3]**Dependencies** [/SIZE]

Ok, so I figured this must be in here since it won't work without it lol. ;) Install all deps by running:
```
sudo apt-get install gcc-3.4 g++-3.4 libx11-dev libpng12-dev libtiff4-dev libfreetype6-dev libssl-dev zlib1g-dev xlibmesa-dev xlibmesa-gl-dev libxine-dev libtag1-dev libxml2-dev automake autogen libsqlite3-dev libtagc0-dev
```

Also install your graphicsdrivers dev package. nvidia-glx-dev is what I use.

Accept any new packages that wants to get installed along with this. 
NOTE! All packages might not be used, but I wasn't sure what packages that actually was needed, so this is more a "accurate guess". This should get it installed though.

[SIZE=3]**Getting e17** [/SIZE]

So, first of we need the script to get e17 obviousley. It's located [here](http://dev.winged.it/download/enlightened_stuff/enlightenment_updater_script)  ; get the latest version of it, current is 0.3.3. Now, I'm gonna assume you want a folder in your home-dir for the e17 source, you can put it wherever you feel it will fit ;). 

```
$ cd ~
``` 

```
$ mkdir e17cvs
``` 

Now, get the script in there:

```
$ mv location/of/script ~/e17cvs/
``` 


Now, we need to configure the script for our needs. 

```
$ gedit ~/e17cvs/get_e.sh
``` 

I enabled most application support but that's because I like to mixture with development stuff.  For you I recommend to leave it as it is unless you reeally want something in there. 
Time to run the script!

```
$ cd ~/e17cvs
``` 

```
$ sh get_e.sh
``` 

It will ask you for your password, just type it in, this isn't a evil hacker script that steals your password and then sets up a ssh on your comp and allows entrance for the author. lol that was a pretty neat hack idea ;) Anyway, this process will take QUITE some time, like an hour or two, depending on your connection and speed of your computer. Might even take longer. Worth noting is that you wont have to redo this special thing unless they update ALL of cvs which I find hard to believe they will in a soon future and all at once. Later when you update Enlightenment it will only re-download and re-build what has been committed changes to,

At the end the script will display what has been built.

Now, log out and make sure there's a entry for Enlightenment where you pick what window-manager to use. If there isn't, just go back to gnome and open up a terminal:

```
$ sudo gedit /usr/share/xsessions/enlightenment.desktop
``` 

And add:

```
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Enlightenment Window Manager - www.enlightenment.org
Type=XSession
Exec=/usr/bin/enlightenment
TryExec=/usr/bin/enlightenment
```

Creds to whoever made that fix in the first place in another thread in this forum. Think it was Smoon.

So, now, logout and log into Enlightenment. You will see the E Sun followed by the default desktop. It's really neat ;)

Take your time, look around, familirize yourself with it. 
When you've done this, it's time to configure!

[SIZE=3]**Gnome and KDE menus** [/SIZE]

Ok, first off, what do we miss in here? That's right, our menus from gnome and KDE! Even though I don't use it too much I'll show you how to get them over. We're going to use a application called e17genmenu. This applications generates all your menus to Enlightenment. 
*NOTE*! It didn't work properly for me, some menu entries got messed up when being brought to Enlightenment from Gnome and some just wasn't there, but overall I got what I wanted so I'm satisfied :). And no, it doesn't ruin the menus in gnome, it basicly copies them and translates them into E. 

You will be able to access these menus from the usual menu and favourites. 

Time to acutally preform all this!

Surf to [this](http://sourceforge.net/projects/e17genmenu) site and get a copy of e17genmenu. 

```
$ cd /location/for/download
$ tar -xzf e17genmenu*
$ cd e17genmenu*
$ ./autogen.sh
$ make
$ sudo make install
``` 

Now, use the acutal program:

```
e17genmenu -g
``` 
That's for gnome.

```
e17genmenu -k
```
And that's for KDE!

If you want certain icon themes for your menu that you already have, use the extension --gnome-theme=<themename> or --kde-theme=<themename> after the -g or -k. After this you can customize your menu as you like by using Entangle (availible in left-click -> Configuration). You can also add stuff and remove stuff from the bar you have and so on.
[SIZE=3]
**Customizing the interface** [/SIZE]

Ok! You might want to move stuff around on the desktop which isn't hard at all, and very well-done. Use the left-click -> Gadgets -> Edit Mode for that, you can resize and move all modules practicly wherever you want. Worth noting is that everything on the desktop are modules, which means you can remove/disable everything without any hazzle. You can find more options too under the modules configuration in left-click->Modules->Name.

[SIZE=3]**Extra modules** [/SIZE]

Time to load some extra modules that come with the CVS! As always, worth noting is that the whole CVS is under heavy-development so there's no certainty at all that everything will work buggfree.

There are a few usefull modules that aren't loaded by default:

flame - flame extension for your desktop, pure eyecandy
snow - snow extension for your desktop, pure eyecandy
notes - keep notes on your desktop
monitor - monitor CPU, network and memory
engage - and OSX style application bar

To load these you run:

```
$ enlightenment_remote --module-load <modulename>
``` 

And they will pop up in the Modules menu!

Also there are a few other external modules, 3rd party, but I will leave that for you to find. Look in forums and so on, [www.edevelop.org](www.edevelop.org). 

[SIZE=3]**Themes and backgrounds** [/SIZE]

The last part of this how-to in its current state. Themes is a great part of E, so is backgrounds. E supports animated backgrounds. Look for themes and backgrounds on [www.get-e.org](www.get-e.org) and [www.edevelop.org](www.edevelop.org). To install and use themes & backgrounds you must put them in your E folder. Like this:

```
$ mv /location/to/theme ~/.e/e/themes/
``` 

And for backgrounds:

```
$ mv /location/to/background ~/.e/e/backgrounds/
```

To change themes, use the left-click -> Themes menu. To change backgrounds, use Emblem, located in left-click -> Configuration -> Background Selector. Worth noting is that you have to click on the big picture of the background to set it as background.


[SIZE=3]**Final notes** [/SIZE]

We've reached the end! 
Anyway, I strongly recommend running this script at least once a day, since there are at least one commit to the cvs per day. 


Hope this guide helps you guys! Feedback appreaciated.

[SIZE=3]**Updates** [/SIZE]

08-26-2005: More dependencies.
08-25-2005: Update, changed the order of the update info. Lol. Neat update ;)
08-25-2005: Major update! Added the dependencies.
08-24-2005: Added note about emblem and themes.

---

### Post by Stormy Eyes on 2005-08-24
You may want to mention that this script requires that you execute **sudo apt-get install build-essential cvs** at the very least in order to run. Also, will this work with automake 1.4? I thought e17cvs wanted a later version.

I'm trying it out now, so I'll post again if I notice any other issues.

---

### Post by Stormy Eyes on 2005-08-24
You also need to execute **sudo apt-get install automake autogen**.

---

### Post by Stormy Eyes on 2005-08-24
OK. Running this script on Hoary with the packages I mentioned earlier installed yields the following result:

```
=== Building: e17/apps/e... ===

make: *** No rule to make target `clean'.  Stop.

 => Autofoo: e17/apps/e

Running aclocal...
aclocal: configure.in: 18: macro `AM_ENABLE_SHARED' not found in library
aclocal: configure.in: 19: macro `AM_PROG_LIBTOOL' not found in library
```

I will install libtool with apt-get and try again.

---

### Post by Stormy Eyes on 2005-08-24
OK, this bastard's building now. I'll post again tomorrow, when I've had time to actually try it out.

EDIT: So much for a smooth build. It failed while building EVAS, with the following output:

```
gcc -g -O2 -o .libs/evas_software_x11_test evas_test_main.o evas_software_x11_main.o  ../../src/lib/.libs/libevas.so -lm -L/usr/X11R6/lib -lX11 -lXext
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeQueryVersion'
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[4]: *** [evas_software_x11_test] Error 1
make[4]: Leaving directory `/home/matthew/src/e17cvs/e17/libs/evas/src/bin'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/matthew/src/e17cvs/e17/libs/evas/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/matthew/src/e17cvs/e17/libs/evas/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matthew/src/e17cvs/e17/libs/evas'
make: *** [all-recursive-am] Error 2
```

Perhaps I'm missing X.org development packages.

---

### Post by SFN on 2005-08-24
Oh sweet!

I just installed last night from Smoon's repo and it's great. Then I saw Smoon's announcement that he wouldn't be keeping the repo up. ](*,) 

I'll be trying this shortly.

---

### Post by Stormy Eyes on 2005-08-24
You might want to wait until I've finished, in case I see any other issues. I had to change the $PREFIX from /usr/local to /usr, which might not work.

---

### Post by SFN on 2005-08-24
> You might want to wait until I've finished 

Dude, you're killing me, here.

Oh......alright.

---

### Post by Stormy Eyes on 2005-08-24
OK, I couldn't find any xserver-xorg development packages, and changing the prefix from /usr/local to /usr didn't help. I'm still getting this output when building EVAS:

```
gcc -g -O2 -o .libs/evas_software_x11_test evas_test_main.o evas_software_x11_main.o  ../../src/lib/.libs/libevas.so -lm -L/usr/X11R6/lib -lX11 -lXext
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeQueryVersion'
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
```

Don't bother trying to run this right now; the code itself might be broken.

---

### Post by SFN on 2005-08-24
Hmmmmm. Yep. Sounds best to wait.

Thanks for the info.

---

### Post by usererror on 2005-08-24
i am also curious to know what results you have!

---

### Post by rjstevens3 on 2005-08-24
i installed:

build essentials, automake, autogen, libtool

then i ran the script and it downloads everything and then says it will build modules, but there is no output and no modules are created...

I checked for enlightenment in /usr/bin and its not there. anyone have a fix? i'm going to mess around with the script.

RJ

---

### Post by AndyAWS on 2005-08-24
[QUOTE=Stormy Eyes]OK, I couldn't find any xserver-xorg development packages, and changing the prefix from /usr/local to /usr didn't help. I'm still getting this output when building EVAS:

```
gcc -g -O2 -o .libs/evas_software_x11_test evas_test_main.o evas_software_x11_main.o  ../../src/lib/.libs/libevas.so -lm -L/usr/X11R6/lib -lX11 -lXext
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeQueryVersion'
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
```

Don't bother trying to run this right now; the code itself might be broken.[/QUOTE]

I'm not that up on compiler commmands but if I look in /usr/X11R6/lib I don't see lX11 or lXext, I do however see libX11 and libXext, or does 'l' mean 'lib' to the compiler?

---

### Post by Stormy Eyes on 2005-08-24
[QUOTE=AndyAWS]I'm not that up on compiler commmands but if I look in /usr/X11R6/lib I don't see lX11 or lXext, I do however see libX11 and libXext, or does 'l' mean 'lib' to the compiler?[/QUOTE]

I think it means "link against", but I'd have to RTFM and right now I'm more interested in my wife's swaying bottom. Goodnight.

---

### Post by AndyAWS on 2005-08-24
Check this post about an evas source patch

[http://www.ubuntuforums.org/showthread.php?p=207121&highlight=patch#post207121](http://www.ubuntuforums.org/showthread.php?p=207121&highlight=patch#post207121)

---

### Post by SFN on 2005-08-24
Hmmm

"wife's swaying bottom"

"evas source patch"


I think we all know how this is going to turn out.

---

### Post by Stormy Eyes on 2005-08-24
[QUOTE=AndyAWS]Check this post about an evas source patch

[http://www.ubuntuforums.org/showthread.php?p=207121&highlight=patch#post207121](http://www.ubuntuforums.org/showthread.php?p=207121&highlight=patch#post207121)[/QUOTE]

No good. That patch doesn't exist at the location provided.

---

### Post by SFN on 2005-08-24
> I think we all know how this is going to turn out. 

Or not.

---

### Post by jerrybme on 2005-08-25
Hmm, I changed the script to point to /usr instead of /usr/local as my current e17 stuff is in /usr/bin & /usr/lib. It compiled acouple of apps but choked on e:
```
=== Building: e17/apps/e... ===


 => Autofoo: e17/apps/e

Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.in: installing `./install-sh'
configure.in: installing `./mkinstalldirs'
configure.in: installing `./missing'
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used
src/bin/Makefile.am: installing `./depcomp'
EXTRA_DIST: variable `files_DATA' is used but `files_DATA' is undefined
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used

```

---

### Post by Nightblade on 2005-08-25
Ooops sorry, I'll have a look at dependencies when I get home. I ran the script without any problems but then again I have quite some dev packages on this comp.

---

### Post by rjstevens3 on 2005-08-25
maybe i'm the only one who didn't figure this out right away, but in order to run the script over agian and build stuff you have edit the script and change rebuild to "yes". also, i've had to add xft2 dev package and libjpeg along with the others. i ran into the same problem with evas, so i added some xfree86 libs since that seems to be what its lookig for... hoping this helps

RJ

Ok, after some research it looks like people get the query problems when they try to build something that wants xfree86 on a system with xorg. some vtk guys found a fix, namely

"I just needed to changed it to :
/usr/X11R6/lib/libXext.so;/usr/X11R6/lib/libXxf86vm.so"

I've been trying to find the makefile for evas to change this, but no luck. i hope someone fixes/finds a better way while i finally get some sleep ](*,) (quite possible most overused smiley, but how appropriate)

---

### Post by AndyAWS on 2005-08-25
I made it through compiling all of the libs, without making any changes, then I hit this on the first app.

```
=== Building: e17/apps/e... ===

make: *** No rule to make target `clean'.  Stop.

 => Autofoo: e17/apps/e

Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.in: installing `./install-sh'
configure.in: installing `./mkinstalldirs'
configure.in: installing `./missing'
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used
src/bin/Makefile.am: installing `./depcomp'
EXTRA_DIST: variable `files_DATA' is used but `files_DATA' is undefined
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used
```

---

### Post by Nightblade on 2005-08-25
> **rjstevens3]maybe i'm the only one who didn't figure this out right away, but in order to run the script over agian and build stuff you have edit the script and change rebuild to "yes". also, i've had to add xft2 dev package and libjpeg along with the others. i ran into the same problem with evas, so i added some xfree86 libs since that seems to be what its lookig for... hoping this helps

RJ

Ok, after some research it looks like people get the query problems when they try to build something that wants xfree86 on a system with xorg. some vtk guys found a fix, namely

"I just needed to changed it to :
/usr/X11R6/lib/libXext.so said:**
> (*,) (quite possible most overused smiley, but how appropriate)

If you pick yes there it will rebuild everything even if it isn't updated, otherwise it'll only rebuild what has been updated..

---

### Post by Stormy Eyes on 2005-08-25
[QUOTE=Nightblade]Ooops sorry, I'll have a look at dependencies when I get home. I ran the script without any problems but then again I have quite some dev packages on this comp.[/QUOTE]

What X11 dev packages do you have installed?

---

### Post by AndyAWS on 2005-08-25
> If you pick yes there it will rebuild everything even if it isn't updated, otherwise it'll only rebuild what has been updated..

Yes, but it looks like you should leave rebuild set to yes until you successfully build everything at least once, otherwise when you rerun the script and there are no updates it won't attempt to rebuild the failed items...does that sound correct?

It seemed to make a difference for me in getting the libs built, although I still haven't made it through building e17/apps/e.

---

### Post by Nightblade on 2005-08-25
[QUOTE=Stormy Eyes]What X11 dev packages do you have installed?[/QUOTE]
libx11-dev

---

### Post by Stormy Eyes on 2005-08-25
[QUOTE=Nightblade]libx11-dev[/QUOTE]

OK. I'll apt-get that tonight and try again. Thanks.

---

### Post by Nightblade on 2005-08-25
[QUOTE=Stormy Eyes]OK. I'll apt-get that tonight and try again. Thanks.[/QUOTE]
 Sorry, I should've though about deps. Looking up them now, will return later with them,

---

### Post by Stormy Eyes on 2005-08-25
[QUOTE=Nightblade]Sorry, I should've though about deps. Looking up them now, will return later with them,[/QUOTE]

I remember it being mentioned as a TODO item on either your site or in the script itself. Don't worry. You could just update your HOWTO with the packages I mentioned along with libX11-dev.

---

### Post by Nightblade on 2005-08-25
Ok! Major update now, THINK this will fix the dependencies problems.

---

### Post by Stormy Eyes on 2005-08-25
[QUOTE=Nightblade]Ok! Major update now, THINK this will fix the dependencies problems.[/QUOTE]

Dumb question: is there a reason you specified gcc-3.4 and g++-3.4 and not just build-essential?

---

### Post by Nightblade on 2005-08-25
[QUOTE=Stormy Eyes]Dumb question: is there a reason you specified gcc-3.4 and g++-3.4 and not just build-essential?[/QUOTE]
I did a library trace and put whatever I found linked to E into that dep thingy :)

---

### Post by Stormy Eyes on 2005-08-25
[QUOTE=Nightblade]I did a library trace and put whatever I found linked to E into that dep thingy :)[/QUOTE]

Ah. That makes sense.

---

### Post by Nightblade on 2005-08-25
[QUOTE=Stormy Eyes]Ah. That makes sense.[/QUOTE]
I hope so ;)

Anyway, can anyone confirm that the deps work with building e17?

---

### Post by darkmatter on 2005-08-25
Also, gcc-3.4 or higher is needed for the weather module to compile correctly, as the tempurature display requires UTF-8, and a compiler that supports UTF-8 needs to be used if the module is to build successfully.

---

### Post by Nightblade on 2005-08-25
[QUOTE=darkmatter]Also, gcc-3.4 or higher is needed for the weather module to compile correctly, as the tempurature display requires UTF-8, and a compiler that supports UTF-8 needs to be used if the module is to build successfully.[/QUOTE]
I did put that in deps ;)

---

### Post by darkmatter on 2005-08-25
[QUOTE=Nightblade]I did put that in deps ;)[/QUOTE]

Yeh, I know. Just offering some extra information for Stormy Eyes, as he had asked why the 3.4 compilers were specified. ;-)

---

### Post by Nightblade on 2005-08-25
[QUOTE=darkmatter]Yeh, I know. Just offering some extra information for Stormy Eyes, as he had asked why the 3.4 compilers were specified. ;-)[/QUOTE]
 Okay :) Anyway, anyone tried it yet?

---

### Post by kpettersen on 2005-08-25
I am getting a lot farther than last night.  But it is now failing when building 'enterminus':

=== Building: e17/libs/exml... ===

make: *** No rule to make target `clean'.  Stop.

 => Autofoo: e17/libs/exml

get_e.sh: line 522: ./autogen.sh: No such file or directory

Looks like the exml directory is not being created, and nothing built in it.

KP

---

### Post by KageKeeper on 2005-08-25
I am failing the build of what looks like evas with this error:

```
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[4]: *** [libevas.la] Error 1
make[4]: Leaving directory `/home/rob/e17cvs/e17/libs/evas/src/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/rob/e17cvs/e17/libs/evas/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rob/e17cvs/e17/libs/evas/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/e17cvs/e17/libs/evas'
make: *** [all-recursive-am] Error 2
``` 

What is -lGL?

---

### Post by foxy123 on 2005-08-25
so if I've got E17 installed from Smoog's repos, should I uninstall it before running this script?

---

### Post by rjstevens3 on 2005-08-25
ok i made it this point after adding a bunch of dev libs:

==Building: e17/apps/e...===

make: *** No rule to make target `clean'. Stop

 => Autofoo: e17/apps/e

Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
src/modules/randr/Makefile.am:9: variable `files_Data' not defined

i have no idea what to do about that one...

---

### Post by Stormy Eyes on 2005-08-25
OK, I installed all of the dependencies, but it still barfs at the same point when building evas:

```

gcc -g -O2 -o .libs/evas_software_x11_test evas_test_main.o evas_software_x11_main.o  ../../src/lib/.libs/libevas.so -lm -L/usr/X11R6/lib -lX11 -lXext
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeQueryVersion'
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status

```

---

### Post by kpettersen on 2005-08-25
Okay, e17 up and running.  There were a lot of dependencies to add.  Mostly the development stuff needed for different portions of e17 that a normal Ubuntu install doesn't include.  I removed ( said "no" ) to eterminus and most of the other experimental or older items in the get_e.sh file.

KP

---

### Post by Stormy Eyes on 2005-08-25
[QUOTE=KageKeeper]What is -lGL?[/QUOTE]

Probably an OpenGL library. Did you apt-get all the required packages listed at the beginning of the howto?

---

### Post by rjstevens3 on 2005-08-25
i think i need some more stuff from cvs, but i get refused when i try to connect. any ideas?

---

### Post by kpettersen on 2005-08-25
Looks like there is no -g option in e17genmenu now......anybody run that yet?

---

### Post by gorkhal on 2005-08-25
ok this is where I got stuck

```

=== Building: e17/libs/edje... ===

make: *** No rule to make target `clean'.  Stop.

 => Autofoo: e17/libs/edje

Running aclocal...
aclocal: configure.in: 0: macro `AM_PATH_GTK' not found in library

```

installed more gtk dev packages...no luck

really appreciate it if someone could point in the right direction...thanks... :)

---

### Post by AndyAWS on 2005-08-25
ANOTHER DEPENDANCY ==>  [COLOR=DarkGreen] libsqlite3-dev[/COLOR]

I think it was enage that needed it....

---

### Post by jerrybme on 2005-08-25
Just finished running. All apps compiled fine. Thanks!

---

### Post by AndyAWS on 2005-08-25
DEPENDANCY ==>  [COLOR=DarkGreen]libtagc0-dev[/COLOR]

Required by [COLOR=DarkGreen]eclair[/COLOR]

---

### Post by KageKeeper on 2005-08-25
[QUOTE=Stormy Eyes]Probably an OpenGL library. Did you apt-get all the required packages listed at the beginning of the howto?[/QUOTE]

Yes sir I did. :)

And OpenGL works for me as well. So I am not sure what libs I am missing. Anyone have any suggestions?

---

### Post by Nightblade on 2005-08-26
First off, sometimes CVS is broken, usually fixes in an hour or so.

For all ppl with lGL problems, install your dev package for your graphicsdrivers. nvidia-glx-dev for example.

---

### Post by KageKeeper on 2005-08-26
[QUOTE=Nightblade]First off, sometimes CVS is broken, usually fixes in an hour or so.

For all ppl with lGL problems, install your dev package for your graphicsdrivers. nvidia-glx-dev for example.[/QUOTE]

Well, that fixed that issue..

Now during the build of esmart I get:

```
configure: error: Cannot find ltdl.h. Please make sure you have the libltdl-dev package installed.
``` 

I did an apt-get and there is no libltfl-dev pakage nor can I find one on synaptic.....

---

### Post by rjstevens3 on 2005-08-26
you can apt or synaptic libltdl3-dev

---

### Post by AndyAWS on 2005-08-26
I am currently to the point where 'enterminus' builds, then when the script moves on to 'ewler' I get e17/libs/exml doesn't exist.

Looking at the CVS tree, all of the exml files are in the Attic with a note from 3 days ago that the "Root for this project has been corrupted, re-adding."

As far as I can tell the only thing that depends on 'exml' is 'ewler'.

Is that correct? I'd like to be sure before I go through the script again.

---

### Post by Nightblade on 2005-08-26
[QUOTE=AndyAWS]I am currently to the point where 'enterminus' builds, then when the script moves on to 'ewler' I get e17/libs/exml doesn't exist.

Looking at the CVS tree, all of the exml files are in the Attic with a note from 3 days ago that the "Root for this project has been corrupted, re-adding."

As far as I can tell the only thing that depends on 'exml' is 'ewler'.

Is that correct? I'd like to be sure before I go through the script again.[/QUOTE]
 Can't give you a better answer then that you're probably right. :)

---

### Post by AndyAWS on 2005-08-26
Then I'll run through it again later tonight and post the results here.

Just curious, has anyone here successfully built EWLER ?

---

### Post by movies1978 on 2005-08-26
Hi Guys,
someone post hoary debs somewhere. This would safe us all the compile hassle. 
I know it is a cvs build, but we could call the packet something like : 
E17-CVS260805.deb
I would love to test it, but lazieness is my problem ;-)

Mathias

---

### Post by Stormy Eyes on 2005-08-26
[QUOTE=movies1978]Hi Guys,
someone post hoary debs somewhere. This would safe us all the compile hassle. 
I know it is a cvs build, but we could call the packet something like : 
E17-CVS260805.deb
I would love to test it, but lazieness is my problem ;-)

Mathias[/QUOTE]

Smoon was doing that for a while, but can no longer maintain them now that he's moved to Arch Linux. So, if you want Enlightenment 0.17 before Rasterman and company are ready to release it to the public, man up and use CVS. Be grateful that Nightblade's taken the trouble to hack a script that automates most of the build process. :)

---

### Post by Nightblade on 2005-08-26
Actually I didn't hack the script, the guy at winged.it did that and deserve all cred for that. ;)

---

### Post by Kyral on 2005-08-26
Got a problem. Starts compiling then I get

 ```
=== Building: e17/libs/edje... ===

make: *** No rule to make target `clean'.  Stop.

 => Autofoo: e17/libs/edje

Running aclocal...
aclocal: configure.in: 0: macro `AM_PATH_GTK' not found in library

``` 

I have NO idea what this is....

---

### Post by rjstevens3 on 2005-08-26
[QUOTE=Kyral]Got a problem. Starts compiling then I get

 ```
=== Building: e17/libs/edje... ===

make: *** No rule to make target `clean'.  Stop.

 => Autofoo: e17/libs/edje

Running aclocal...
aclocal: configure.in: 0: macro `AM_PATH_GTK' not found in library

``` 

I have NO idea what this is....[/QUOTE]
 "Running aclocal...
aclocal: configure.in: 0: macro `AM_PATH_GTK' not found in library"

i had that same problem for a while. i had automake 1.7 installed, but the system was using 1.4 anyways. i had to dpkg -r automake1.4 to solve that. and then it worked. i also took the advice from the enlightenment build notes and combined my aclocal dirs to one place and symlinked the other.

my new problem is that the script can't find a makefile.in that i checked is there...

---

### Post by SFN on 2005-08-26
[QUOTE=Kyral]Got a problem. Starts compiling then I get

 ```
=== Building: e17/libs/edje... ===

make: *** No rule to make target `clean'.  Stop.

 => Autofoo: e17/libs/edje

Running aclocal...
aclocal: configure.in: 0: macro `AM_PATH_GTK' not found in library

``` 

I have NO idea what this is....[/QUOTE]

I just got that, myself. Do:

```
sudo apt-get install libgtk1.2-dev
``` 

and you're on to the next issue.

Slowly but surely we're getting there.

---

### Post by KageKeeper on 2005-08-26
Is there a way to continue the script when it exits for an error without removing everthing that has been downloaded/compiled first?

I try to rerun, but it never works correctly.

---

### Post by SFN on 2005-08-26
[QUOTE=KageKeeper]Is there a way to continue the script when it exits for an error without removing everthing that has been downloaded/compiled first?

I try to rerun, but it never works correctly.[/QUOTE]

Sort of. You need to edit the script Do:

```
sudo /path/to/nano get_e.sh
``` 

Locate the lines that say

> ## Rebuild all, even if CVS doesn't have updated files ("yes" or "no")
REBUILD_ALL="no"

and change

REBUILD_ALL="no"

to

REBUILD_ALL="yes"

You'll still have to re-run the script and everything will be rebuilt from scratch but you won't have to do it by hand.

---

### Post by KageKeeper on 2005-08-26
[QUOTE=SFN]Sort of. You need to edit the script Do:

```
sudo /path/to/nano get_e.sh
``` 

Locate the lines that say



and change

REBUILD_ALL="no"

to

REBUILD_ALL="yes"

You'll still have to re-run the script and everything will be rebuilt from scratch but you won't have to do it by hand.[/QUOTE]

Ahh. Thanks! That may speed some things up. I have downloaded the CVS about 5 seperate times now..hehe.

Thanks!

---

### Post by gorkhal on 2005-08-26
[QUOTE=rjstevens3]"Running aclocal...
aclocal: configure.in: 0: macro `AM_PATH_GTK' not found in library"

i had that same problem for a while. i had automake 1.7 installed, but the system was using 1.4 anyways. i had to dpkg -r automake1.4 to solve that. and then it worked. i also took the advice from the enlightenment build notes and combined my aclocal dirs to one place and symlinked the other.

my new problem is that the script can't find a makefile.in that i checked is there...[/QUOTE]

An alternative solution is to remove the references to 'AM_PATH_GTK' from either 

~/e17cvs/e17/libs/edje/configure.in
or
~/e17cvs/e17/libs/edje/acinclude.m4

when compiling edje...
'AM_PATH_GTK' is not used at all, the enlightened devs just make a passing reference to it, but aclocal gets confused and starts looking for it, so for those who have the required devs, its ok, but for those who dont, we get the bad error message.

but its probably easier to install libgtk1.2-dev as SFN suggested, then compile, since other packages have the similar problem as well.

---

### Post by Kyral on 2005-08-26
I installed libgtk2.0-dev :P And its working, until I slammed into the flex depend on something.

[b]ADD FLEX TO THE DEPEND LIST!!

[/b]Edit: And Bison

---

### Post by KageKeeper on 2005-08-26
Ok. New one I think.

Building evfs, get this error:

```
/usr/bin/ld: cannot find -lfam
``` 

Which I think means it needs libfam-dev.

But, for libfam-dev, I am told it depends on libfam0c102 and if I try to install that, it wants to remove a TON of things.

Any suggestions?

Should I just not build evfs?

---

### Post by rjstevens3 on 2005-08-26
anyone else having trouble with Enscribe? i've been getting a missing makefile error for a while now, so i'm just going to skip it.

---

### Post by SFN on 2005-08-26
[QUOTE=KageKeeper]Ok. New one I think.

Building evfs, get this error:

```
/usr/bin/ld: cannot find -lfam
``` 

Which I think means it needs libfam-dev.

But, for libfam-dev, I am told it depends on libfam0c102 and if I try to install that, it wants to remove a TON of things.

Any suggestions?

Should I just not build evfs?[/QUOTE]

Unless somebody comes up with an answer sooner, hang tight for a bit. It looks like I'm close to being done and right now I don't have libfam0c102 installed. Once I finish, I can tell you what I've got.

---

### Post by KageKeeper on 2005-08-26
[QUOTE=SFN]Unless somebody comes up with an answer sooner, hang tight for a bit. It looks like I'm close to being done and right now I don't have libfam0c102 installed. Once I finish, I can tell you what I've got.[/QUOTE]

Alright, will do. Thanks :)

---

### Post by SFN on 2005-08-26
It would appear that I am attempting to redefine the concept of "close to being done". Still going.

In the meantime, what I've added as a result of being asked to by the script (or at least guessing what the script was looking for) is:

libtool
libjpeg62-dev
libgtk1.2-dev
libltdl3-dev
flex

I've also upgraded automake from 1.4 to 1.9. I probably didn't need to go that high as it was asking for 1.5 but there's no 1.5 in the Ubuntu repos and 1.6 failed. Rather than go one at a time, I just went straight up to 1.9.

The script is still running right now. Hopefully I'll have more news soon.

If anybody else has better info regarding the packages I installed - such as I didn't need one and could have gotten away with another - please, by all means, let me/us know.

---

### Post by zenrox on 2005-08-26
so far i am epslion  hoping for the best
 :---)

---

### Post by KageKeeper on 2005-08-26
Did you elect to build evfs?

---

### Post by SFN on 2005-08-26
[QUOTE=KageKeeper]Did you elect to build evfs?[/QUOTE]

Yep. I took everything. I figured if I'm going to test it, I might as well really test it.

Of course, it helps that I have a PC that I use for testing everything. If it chokes, it chokes. I just reinstall.

---

### Post by zenrox on 2005-08-26
/quote 
Did you elect to build evfs?
 
yes

---

### Post by KageKeeper on 2005-08-26
[QUOTE=SFN]Yep. I took everything. I figured if I'm going to test it, I might as well really test it.

Of course, it helps that I have a PC that I use for testing everything. If it chokes, it chokes. I just reinstall.[/QUOTE]

Hmm...then why am I choking on not finding -lfam?

Baffling..

---

### Post by rjstevens3 on 2005-08-26
I finally got this to work without enscribe. i'm using e17 now! i'm running into the same issue as someone else with no -g option in e17genmenu...

---

### Post by Kyral on 2005-08-26
Yanno doing this by hand (almost) is giving me a new appreciation for Apt :razz:

---

### Post by SFN on 2005-08-26
[QUOTE=Kyral]Yanno doing this by hand (almost) is giving me a new appreciation for Apt :razz:[/QUOTE]

Yeah. If only I'd never seen e17. My life would be so much more peaceful. Now I'll do anything for that E monkey.

---

### Post by Kyral on 2005-08-26
I've seen it, I've installed it from Smoon's repo. Its NICE. I'm hoping to config it enough so that I can stop using GNOME :P

---

### Post by SFN on 2005-08-26
[QUOTE=Kyral]I've seen it, I've installed it from Smoon's repo.[/quote]
Me too. I'm like a crackhead now.
> Its NICE. I'm hoping to config it enough so that I can stop using GNOME :P
I tried that with both fluxbox and xfce4. I just kept finding that there were things I missed from Gnome. I'll probably keep both Gnome and Elnightenment.

It's failed twice on me now. Once on enscribe and once on enterminus. Just a text editor and a terminal but I'm going all Veruca Salt on this. I want it NOW!

One minute till closing - I'm going home. Going to start it all again later tonight. I'll be sure and report in.

---

### Post by darkmatter on 2005-08-26
[QUOTE=SFN]One minute till closing - I'm going home. Going to start it all again later tonight. I'll be sure and report in.[/QUOTE]

And if all else fails, I have a copy of smoons install script. :smile: 

Must obey my addiction... ](*,)

---

### Post by gorkhal on 2005-08-26
Needed to add: ** giblib1 and giblib-dev **

when building SCROT....I was almost there...so close

---

### Post by DJ_Max on 2005-08-26
[QUOTE=SFN]Me too. I'm like a crackhead now.
[/QUOTE]
I thought I was the only one.  :smile: It failed on engrave, since I didn't read the entire thread, I needed a new version of automake. But I'm using E17 right now, and I must complete the install. I think this will replace GNOME on my desktop.

---

### Post by KageKeeper on 2005-08-26
Grr. Ok. I am getting mildly frustrated, only because I do not know why I am having issues..  ](*,) 

So, building eterminus and I get:

```
make[1]: Leaving directory `/home/rob/e17cvs/e17/proto/enterminus'
~/e17cvs
get_e.sh: line 511: pushd: e17/libs/exml: No such file or directory
``` 

So. Yes, I have all the deps that are listed as well as what others have listed. 

So. Yeah. Help?

EDIT: And e17/libs/exml does not exist. Is it being built in the wrong order?

---

### Post by gorkhal on 2005-08-26
woohooo posting from enlightenment...boy its fast...no application taskbar though...or did i miss it???

THis is beautiful. 

Found the flame module, FLAME ON!!!

btw i did not install any of the experimental/deprecated modules. too many problems there.

---

### Post by darkmatter on 2005-08-26
[QUOTE=gorkhal]woohooo posting from enlightenment...boy its fast...no application taskbar though...or did i miss it???[/QUOTE]

```
$ enlightenment_remote -module-load ibox
```

will solve your problem. It displays icons of iconified and minimized apps. ;-)

EDIT: Almost forgot...
```
$ enlightenment_remote -module-load engage
```

gives you an animated (like the OS X dock) replacement for ibar that also will display running apps + a systray.

A nice feature is that mouse-wheel over the icon of an application will raise the instance into focus - works great for mutiple windows.

---

### Post by AndyAWS on 2005-08-26
Engage includes a taskbar/systemtray:
```
enlightenment_remote -module-load engage --tray
```[Engage Users Guide](http://www.get-e.org/User_Guide/English/_pages/4.2.html) 

[get-e.org](http://www.get-e.org)  is a great source of info for e17

---

### Post by darkmatter on 2005-08-26
[QUOTE=AndyAWS]systemtray:[/QUOTE]

Unfortunately, it clashes with all the wondeful eye-candy (works well enough, just butt ugly)

I prefer a minimal gnome-panel for notifications and a few essential applets (volume control for example)

---

### Post by DJ_Max on 2005-08-26
[QUOTE=KageKeeper]Grr. Ok. I am getting mildly frustrated, only because I do not know why I am having issues..  ](*,) 

So, building eterminus and I get:

```
make[1]: Leaving directory `/home/rob/e17cvs/e17/proto/enterminus'
~/e17cvs
get_e.sh: line 511: pushd: e17/libs/exml: No such file or directory
``` 

So. Yes, I have all the deps that are listed as well as what others have listed. 

So. Yeah. Help?

EDIT: And e17/libs/exml does not exist. Is it being built in the wrong order?[/QUOTE]
 If you look in the CVS repo. [http://cvs.sourceforge.net/viewcvs.py/enlightenment/e17/libs/](http://cvs.sourceforge.net/viewcvs.py/enlightenment/e17/libs/)

You see there's a directory, but nothing is in it. So it may not be implemented in the CVS yet.

---

### Post by AndyAWS on 2005-08-26
```
welcome.c: In function `open_welcome':
welcome.c:27: error: too many arguments to function `ewl_text_font_set'
welcome.c:38: error: too many arguments to function `ewl_text_font_set'
welcome.c: In function `open_credits':
welcome.c:117: error: too many arguments to function `ewl_text_font_set'
make[2]: *** [welcome.o] Error 1
make[2]: Leaving directory `/home/ag/e17cvs/misc/enotes/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ag/e17cvs/misc/enotes'
make: *** [all] Error 2
```

 ](*,)  Dead again....setting BUILD_ENOTES = "no"  ](*,) ```


sh get_e.sh
```

waiting

---

### Post by KageKeeper on 2005-08-26
[QUOTE=DJ_Max]If you look in the CVS repo. [http://cvs.sourceforge.net/viewcvs.py/enlightenment/e17/libs/](http://cvs.sourceforge.net/viewcvs.py/enlightenment/e17/libs/)

You see there's a directory, but nothing is in it. So it may not be implemented in the CVS yet.[/QUOTE]

Ahh. Good to know. I guess that would explain that.

Thanks.

---

### Post by KageKeeper on 2005-08-26
```
ewl_text_test.c: In function `__trigger_cb_mouse_in':
ewl_text_test.c:27: error: structure has no member named `parent'
ewl_text_test.c:28: error: structure has no member named `parent'
ewl_text_test.c: In function `__trigger_cb_mouse_out':
ewl_text_test.c:38: error: structure has no member named `parent'
ewl_text_test.c:39: error: structure has no member named `parent'
make[3]: *** [ewl_text_test.o] Error 1
make[3]: Leaving directory `/home/rob/e17cvs/e17/libs/ewl/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rob/e17cvs/e17/libs/ewl/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/e17cvs/e17/libs/ewl'
make: *** [all] Error 2
``` 

 ](*,)  ](*,)  ](*,) 

*pulls hair out* 

Anyone want to take a stab at this?

---

### Post by darkmatter on 2005-08-26
[QUOTE=KageKeeper]](*,)  ](*,)  ](*,) 

*pulls hair out* 

Anyone want to take a stab at this?[/QUOTE]

If anyone wants a copy of smoons install script, all you have to do is ask... ;-)

---

### Post by KageKeeper on 2005-08-26
[QUOTE=darkmatter]If anyone wants a copy of smoons install script, all you have to do is ask... ;-)[/QUOTE]

At this point, I will try it. As long as I can get it to work *sobs* 

I do not know why it is being reticent, but it is. *chuckles*

---

### Post by SFN on 2005-08-26
I've started the script again. While I'm waiting, I'll tell you a story.

When I was 19, I started coming down with these nasty headaches. Blinding stuff. Not migraines. No nausea. No weird eyesight stuff. Just the headache but the most excrutiating pain ever. I'd have at least one a day for months on end, then one day they stopped. After a few weeks, they started up again. This pattern has repeated ever since. I'm 41 now. 

A number of years later I found out the types of headaches I had were being identified as cluster headaches. They think it's what Gary Gilmore suffered from.

About a year ago, a neurologist diagnosed me with rheumatoid arthritis in my cervical vertibrae (4-7 specifically). He connected it to some nerve problems I was having in my arms, good amounts of back pain, some intense dizzy spells and, possibly, could be one for the medical journals, the cluster headaches!

Over the past couple of weeks, the arthritis has been flaring up. When I woke up today, I had all of my symptoms at once. The headache, the nerve pain in the arms, the dizziness, the pain in the back - everything. I've been heavily medicated all day but had to go to work.

Obviously, I didn't make my job a huge priority as I've been trying to install e17 all day. When I got off work though, I decided that I wouldn't bother with this anymore. The pain was still there and I really couldn't deal with a keyboard and a mouse. But here I am. I've gone with codeine and Merlot. Such is the power of e17.

Anywho, the script is done. Failure again. This time with ewl. Enscribe and enterminus it sounds like I can live without but from what I'm seeing over at elightenment.org:

> EWL provides a complete widget library built on all the other components of the EFL. And more!

Sounds like I need that. Anybody have any ideas on this?

---

### Post by AndyAWS on 2005-08-26
I have the same problem with EWL...the thing is that EWL compiled fine all of the other times I ran the script, so I think sometime in the last couple hours the source code must have been updated, and broke. I don't know how else to explain it.

The only change I made since last time was BUILD_ENOTES = "no"

---

### Post by SFN on 2005-08-26
[QUOTE=AndyAWS]The only change I made since last time was BUILD_ENOTES = "no"[/QUOTE]

And it's working now?

---

### Post by AndyAWS on 2005-08-26
No I cannot get EWL to build at the moment, however I am posting this from E17   :) 

It seems that my previous build was good (except for enotes), so I have a working E17 build ATM.

Now it's bedtime...I'll play around with it tomorrow.

Honestly the problem with EWL looks like broken code. Things like that will happen a lot just try later and hope the code has been fixed. I'm going to try a rebuild tomorrow to see for myself.

---

### Post by AndyAWS on 2005-08-27
[QUOTE=KageKeeper]```
ewl_text_test.c: In function `__trigger_cb_mouse_in':
ewl_text_test.c:27: error: structure has no member named `parent'
ewl_text_test.c:28: error: structure has no member named `parent'
ewl_text_test.c: In function `__trigger_cb_mouse_out':
ewl_text_test.c:38: error: structure has no member named `parent'
ewl_text_test.c:39: error: structure has no member named `parent'
make[3]: *** [ewl_text_test.o] Error 1
make[3]: Leaving directory `/home/rob/e17cvs/e17/libs/ewl/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rob/e17cvs/e17/libs/ewl/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/e17cvs/e17/libs/ewl'
make: *** [all] Error 2
``` 

 ](*,)  ](*,)  ](*,) 

*pulls hair out* 

Anyone want to take a stab at this?[/QUOTE]


Looking here [http://cia.navi.cx/stats/project/e/](http://cia.navi.cx/stats/project/e/) 
there was an update to ewl_text_test.c earlier tonight.

---

### Post by atrus325 on 2005-08-27
Seems like this topic has been going on for a while, but I figured I'd chime in anyway.

So far, Ubuntu is the only distro I've actually gotten e17 working on (also tried on Gentoo and *blech* Fedora), but I didn't use CVS at all.. i just downloaded the requred modules from: [http://enlightenment.freedesktop.org/](http://enlightenment.freedesktop.org/) and compiled and made each manually.

I haven't spent much time on the Gentoo install, which compiled perfectly until I got to the enlightenment module itself, which crashed shortly into the process.

But in Ubuntu, that method worked without a hitch, provided I did it in the correct order.  There are some basic instructions at the site.

J.

---

### Post by DJ_Max on 2005-08-27
[QUOTE=AndyAWS]No I cannot get EWL to build at the moment, however I am posting this from E17   :) 

It seems that my previous build was good (except for enotes), so I have a working E17 build ATM.

Now it's bedtime...I'll play around with it tomorrow.

Honestly the problem with EWL looks like broken code. Things like that will happen a lot just try later and hope the code has been fixed. I'm going to try a rebuild tomorrow to see for myself.[/QUOTE]
 Same with me, it fails with that ewl problem people have been having. But you have to remeber, this is from the CVS, and like me, they will sometimes leave code segments broken. Otherwise it works fine.

---

### Post by gorkhal on 2005-08-27
[QUOTE=darkmatter]```
$ enlightenment_remote -module-load ibox
```

will solve your problem. It displays icons of iconified and minimized apps. ;-)

EDIT: Almost forgot...
```
$ enlightenment_remote -module-load engage
```

[/QUOTE]

thanks!!! only one problem with Ibox...apps like Opera dont have their icons show up...i think its only for some preset apps.

engage seems pretty nice...but needs lots more work.

---

### Post by finn on 2005-08-27
[QUOTE=DJ_Max]Same with me, it fails with that ewl problem people have been having. But you have to remeber, this is from the CVS, and like me, they will sometimes leave code segments broken. Otherwise it works fine.[/QUOTE]


Hmm... i've got the same ewl problem.  Anybody around here know how to hack the script to grab yesterday's ewl source rather than todays broken stuff?

---

### Post by darkmatter on 2005-08-27
[QUOTE=gorkhal]thanks!!! only one problem with Ibox...apps like Opera dont have their icons show up...i think its only for some preset apps.

engage seems pretty nice...but needs lots more work.[/QUOTE]

Left-click the open space in the left area of the titlebar or right-click anywhere in the titlebar. select 'create icon' frome the menu. choose an icon to use using the eapp editor which opens to choose the desired icon, give the name you want displayed and enter the command to be executed. Save and restart E.

Now the given app will have an eap to represent it when iconified. (and to be added to the menu)

---

### Post by darkmatter on 2005-08-27
[QUOTE=SFN]The pain was still there and I really couldn't deal with a keyboard and a mouse. But here I am. I've gone with codeine and Merlot. Such is the power of e17.
[/QUOTE]

That's something I understand far to well. A year ago, I was diagnosed with a VERY serious illness. But here I am, hacking away at my keyboard, trying to have my dream of an Enlightenment-centric, Ubuntu based distro bear fruit.

I'm not sure if it's an addiction to E 17, or a stubborn desire to achive some form of immortality... :roll:

---

### Post by gorkhal on 2005-08-27
[QUOTE=darkmatter]Left-click the open space in the left area of the titlebar or right-click anywhere in the titlebar. select 'create icon' frome the menu. choose an icon to use using the eapp editor which opens to choose the desired icon, give the name you want displayed and enter the command to be executed. Save and restart E.

Now the given app will have an eap to represent it when iconified. (and to be added to the menu)[/QUOTE]

Wow was completely unaware of this, I have been enlightened...time to take a better look at the manual. :smile:

---

### Post by darkmatter on 2005-08-27
[QUOTE=gorkhal]Wow was completely unaware of this, I have been enlightened...time to take a better look at the manual. :smile:[/QUOTE]

[http://www.get-e.org/User_Guide/English/_pages/3.3.html](http://www.get-e.org/User_Guide/English/_pages/3.3.html) ;-)

You can also use [e17genmenu](http://sourceforge.net/projects/e17genmenu) to automagically generate eaps (and menu structure) from the .desktop files in /usr/share/applications. The results aren't perfect (it has problems with some of the files - like those with spaces in the names), but it's a good starting point.

---

### Post by darkmatter on 2005-08-27
Additionally, for those who are having problems with dependencies, here is the command to fetch  the additional packages needed prior to installing E 17 (minus the compilers):
```
$ apt-get install cvs autoconf automake1.7 gettext libtool libfreetype6-dev libjpeg62-dev libpng3-dev libtiff4-dev libungif4-dev libbz2-dev libltdl3-dev pkg-config libxine-dev libgtk1.2-dev build-essential flex bison byacc
```

Of particular note is automake 1.7, this version MUST be used to successfully compile E 17!!!

Perhaps the OP can update the HOWTO to include any of these that may be missing from his list. ;-) 

More info on building E 17 at [get-e](http://www.get-e.org) and from [https://vogelweith.homeftp.net/Linux/e17_en.php](https://vogelweith.homeftp.net/Linux/e17_en.php)

EDIT: Ubuntu has problems with fonts in the themes Blue Eyed and Clean. This is caused by the version of Freetype in Ubuntu. We only have freetype2.1.7 at present, to fix this we need a backport of freetype2.1.8 or above. Additionally, gcc3.4 or higher is needed for the weather module to build correctly (requires UTF-8 support)

---

### Post by sapo on 2005-08-27
thanx for the guide...

i m installing it right now.. but its more than half an hour downloading stuff from cvs  :-#

---

### Post by darkmatter on 2005-08-27
[QUOTE=sapo]but its more than half an hour downloading stuff from cvs  :-#[/QUOTE]

Dialup??? :-P

---

### Post by sapo on 2005-08-27
[QUOTE=darkmatter]Dialup??? :-P[/QUOTE]

nope.. adsl 500k =x

---

### Post by sapo on 2005-08-27
edit: fixed that.. now i got another error:

gcc: cannot find /usr/lib/libGL.so no such file or directory

But i have this file there  ](*,)

---

### Post by gorkhal on 2005-08-27
[QUOTE=darkmatter]Additionally, for those who are having problems with dependencies, here is the command to fetch  the additional packages needed prior to installing E 17 (minus the compilers):
[/QUOTE]

you also need giblib-dev for SCROT. Also you have to remove the previous automake version for the new version (1.7) to take effect. At least thats what happened in my case.

---

### Post by gorkhal on 2005-08-27
[QUOTE=darkmatter]Additionally, for those who are having problems with dependencies, here is the command to fetch  the additional packages needed prior to installing E 17 (minus the compilers):
[/QUOTE]

you also need giblib-dev for SCROT. Also you have to remove the previous automake version for the new version (1.7) to take effect. At least thats what happened in my case.

---

### Post by Nightblade on 2005-08-27
Install nvidia-glx-dev.

---

### Post by darkmatter on 2005-08-27
[QUOTE=gorkhal]Also you have to remove the previous automake version for the new version (1.7) to take effect.[/QUOTE]

Or you can just specify which version to use during the build process. ;-)

---

### Post by DJ_Max on 2005-08-27
[QUOTE=darkmatter]Or you can just specify which version to use during the build process. ;-)[/QUOTE]
 Yeah, I thought that was a viable option. Seeing as I have all the version available for Ubuntu.

---

### Post by rjstevens3 on 2005-08-27
there is a new version of e17genmenue on sourceforge. 3.0.2 has been released today and it worked with my gnome menues without typing -g. 

1. download
2. sh autogen.sh
3. make
4. sudo make install (optional)
5. e17genmenue (or ./e17genmenue is skipped step 4)

and its done!!

---

### Post by darkmatter on 2005-08-27
Does the new e17genmenu fix the problem with .desktop files that have spaces in the name?

---

### Post by darkmatter on 2005-08-27
[QUOTE=Nightblade]Install nvidia-glx-dev.[/QUOTE]

Only if you use an nvidia graphics card.

---

### Post by rjstevens3 on 2005-08-27
new e17genmenu out version 3.0.2 get it from source forge

---

### Post by darkmatter on 2005-08-27
Yep, got the new version already. :smile:

Still doesn't answer my question, though. (I don't want to mess up my work with my menus)

---

### Post by AndyAWS on 2005-08-27
e17genmenu is 3.0.3 now.

But I get a segmentation fault when running it.

---

### Post by finn on 2005-08-27
[QUOTE=Nightblade]

```
$ sudo gedit /usr/share/xsessions/enlightenment.desktop
``` 

And add:

```
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Enlightenment Window Manager - www.enlightenment.org
Type=XSession
Exec=/usr/bin/enlightenment
TryExec=/usr/bin/enlightenment
```
[/QUOTE]

The above code needs to actually be:
```
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Enlightenment Window Manager - www.enlightenment.org
Type=XSession
Exec=/usr/local/bin/enlightenment
TryExec=/usr/local/bin/enlightenment
```
Unless you want to run the old version of enlightenment you installed last week :)

Also there was another dependency which hasn't been mentioned before, libgtk2.0-0
```
sudo apt-get install libgtk2.0-0
```

Hope that helps

---

### Post by KageKeeper on 2005-08-27
Well. I think CVS is broke more. Heh.

I have not been able to compile ebd now.

*shrugs*

Anyone else have luck getting everything compiled from today's CVS?

---

### Post by finn on 2005-08-27
[QUOTE=KageKeeper]Well. I think CVS is broke more. Heh.

I have not been able to compile ebd now.

*shrugs*

Anyone else have luck getting everything compiled from today's CVS?[/QUOTE]
Yep, I compiled twice successfully this morning (about 3hours ago)

---

### Post by KageKeeper on 2005-08-28
[QUOTE=finn]Yep, I compiled twice successfully this morning (about 3hours ago)[/QUOTE]

*grumbles* Well, I would LOVE to know what I am doing wrong then.  :grin:

---

### Post by darkmatter on 2005-08-28
[QUOTE=KageKeeper]*grumbles* Well, I would LOVE to know what I am doing wrong then.  :grin:[/QUOTE]

CVS is in an extraordinary amount of flux lately (Raster and the rest of the crew must have ingested WAY to much sugar).

I'd recommend keeping tabs on CVS as well as the other E-specific RSS feeds, as well as browsing the changelogs, just to make sure that everything is working before fetching the files.

Besides,*AHEM*[size=1] I think building daily is a little much, people [/size]*AHEM*

---

### Post by KageKeeper on 2005-08-28
So. Using fresh CVS.

Dies during epsilon build: 

```
/usr/local/lib/libedje.so: undefined reference to `evas_smart_below_get_set'
/usr/local/lib/libedje.so: undefined reference to `evas_smart_above_get_set'
collect2: ld returned 1 exit status
make[3]: *** [epsilon] Error 1
make[3]: Leaving directory `/home/rob/e17cvs/e17/libs/epsilon/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rob/e17cvs/e17/libs/epsilon/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/rob/e17cvs/e17/libs/epsilon/src'
make: *** [all-recursive] Error 1
``` 

Thoughts? Suggestions?

---

### Post by darkmatter on 2005-08-28
[QUOTE=KageKeeper]So. Using fresh CVS.

Dies during epsilon build: 

```
/usr/local/lib/libedje.so: undefined reference to `evas_smart_below_get_set'
/usr/local/lib/libedje.so: undefined reference to `evas_smart_above_get_set'
collect2: ld returned 1 exit status
make[3]: *** [epsilon] Error 1
make[3]: Leaving directory `/home/rob/e17cvs/e17/libs/epsilon/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rob/e17cvs/e17/libs/epsilon/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/rob/e17cvs/e17/libs/epsilon/src'
make: *** [all-recursive] Error 1
``` 

Thoughts? Suggestions?[/QUOTE]

I've found that the best cure to an 'impossible' situation is a manual build.

It will definitely take longer, but also allows more feedback.

Plus, I've never failed to build E manually, though at times I've had the automated scripts die on me.

---

### Post by KageKeeper on 2005-08-28
[QUOTE=darkmatter]I've found that the best cure to an 'impossible' situation is a manual build.

It will definitely take longer, but also allows more feedback.

Plus, I've never failed to build E manually, though at times I've had scripts die on me.[/QUOTE]

Is there a good source for the proper order with which to build manually?

---

### Post by darkmatter on 2005-08-28
[QUOTE=KageKeeper]Is there a good source for the proper order with which to build manually?[/QUOTE]

[*Here...*](https://vogelweith.homeftp.net/Linux/e17_en.php) 


[*...and Here.*](http://www.ubuntuforums.org/showthread.php?t=30525);-)

Also, check the CVS commit feeds at e-develop, as well as checking the changelogs before compiling. It'll save you a migrane. :razz:

---

### Post by gorkhal on 2005-08-28
[QUOTE=darkmatter]
Besides,*AHEM*[size=1] I think building daily is a little much, people [/size]*AHEM*[/QUOTE]

Truer words have never been spoken...in fact shame on you people who continue to build...give it a rest...

oh screw the pretense....I have built it 3 times already today...and more times yesterday and I plan to build more tomorrow...this MUST STOP!!...

I need help...:sad:

---

### Post by foxy123 on 2005-08-28
[QUOTE=gorkhal]Truer words have never been spoken...in fact shame on you people who continue to build...give it a rest...

oh screw the pretense....I have built it 3 times already today...and more times yesterday and I plan to build more tomorrow...this MUST STOP!!...

I need help...:sad:[/QUOTE]
A stupid question - is it worth it? I mean if the CVS version is much better than Smoog's build?

---

### Post by darkmatter on 2005-08-28
[QUOTE=foxy123]A stupid question - is it worth it? I mean if the CVS version is much better than Smoog's build?[/QUOTE]

The CVS has several additions and improvements. But, if you don't wan't to go through the trouble of compiling, then don't bother. The updates are only small improvements.

---

### Post by KageKeeper on 2005-08-28
All right. I hate to be a pest, but...

I am doing the manual build now. Checked the CVS commits and see nothing changed that would do this. During the make of edje I get this:

```
../../src/lib/.libs/libedje.so: undefined reference to `evas_smart_below_get_set'
../../src/lib/.libs/libedje.so: undefined reference to `evas_smart_above_get_set'
collect2: ld returned 1 exit status
make[3]: *** [edje] Error 1
make[3]: Leaving directory `/home/rob/cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rob/cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/cvs/e17/libs/edje'
make: *** [all] Error 2
``` 

Anyone know why? What may be causing that? I have already built evas and that compiled fine.

Thoughts?

---

### Post by darkmatter on 2005-08-28
[QUOTE=KageKeeper]All right. I hate to be a pest, but...

I am doing the manual build now. Checked the CVS commits and see nothing changed that would do this. During the make of edje I get this:

```
../../src/lib/.libs/libedje.so: undefined reference to `evas_smart_below_get_set'
../../src/lib/.libs/libedje.so: undefined reference to `evas_smart_above_get_set'
collect2: ld returned 1 exit status
make[3]: *** [edje] Error 1
make[3]: Leaving directory `/home/rob/cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rob/cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/cvs/e17/libs/edje'
make: *** [all] Error 2
``` 

Anyone know why? What may be causing that? I have already built evas and that compiled fine.

Thoughts?[/QUOTE]

Stupid question, but did you run ldconfig after building evas?

---

### Post by Stormy Eyes on 2005-08-28
[QUOTE=darkmatter]Stupid question, but did you run ldconfig after building evas?[/QUOTE]

Not if he was using the script, unless the script calls ldconfig after each build.

---

### Post by darkmatter on 2005-08-28
[QUOTE=Stormy Eyes]Not if he was using the script, unless the script calls ldconfig after each build.[/QUOTE]

He had stated in his post that he was trying the MANUAL build, which is why I asked... ;-)

---

### Post by KageKeeper on 2005-08-28
[QUOTE=darkmatter]Stupid question, but did you run ldconfig after building evas?[/QUOTE]

Not a stupid question, but yes, I ran sudo ldconfig after building evas.

---

### Post by elpresidente on 2005-08-28
Attempted fr0om script and came to this. I searched for some indication of how to fix this but came up with nothing.

```
=== Building: e17/libs/engrave... ===

make: *** No rule to make target `clean'.  Stop.

 => Autofoo: e17/libs/engrave

Running aclocal...
Running autoheader...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7017: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running autoconf...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7017: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running libtoolize...
Running automake...
Makefile.am:2: require version 1.5, but have 1.4-p6
src/bin/Makefile.am:1: require version 1.5, but have 1.4-p6
``` 

Any suggestions as to what I should do?

---

### Post by regeya on 2005-08-28
I wonder how many years E17 will be "bleeding edge"?

I wonder if it'll make the decade mark?

I don't remember what the first E17/EFM announcement was, or when, but the oldest I could find was *more* than five years ago, and I could have sworn I'd read about e17 code in '99, which would make it more like 6 years, which means we're more than halfway to the decade point.

Can't wait until 2009, when the next e17 rewrite goes pre-alpha!

---

### Post by KageKeeper on 2005-08-28
[QUOTE=elpresidente]Attempted fr0om script and came to this. I searched for some indication of how to fix this but came up with nothing.

```
=== Building: e17/libs/engrave... ===

make: *** No rule to make target `clean'.  Stop.

 => Autofoo: e17/libs/engrave

Running aclocal...
Running autoheader...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7017: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running autoconf...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7017: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running libtoolize...
Running automake...
Makefile.am:2: require version 1.5, but have 1.4-p6
src/bin/Makefile.am:1: require version 1.5, but have 1.4-p6
``` 

Any suggestions as to what I should do?[/QUOTE]

Do a:

```
sudo apt-get install automake1.5
``` 

And you should be ok I think.

---

### Post by elpresidente on 2005-08-28
[QUOTE=KageKeeper]Do a:

```
sudo apt-get install automake1.5
``` 

And you should be ok I think.[/QUOTE]

Just tried it and got:

```
Package automake1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package automake1.5 has no installation candidate
```

---

### Post by KageKeeper on 2005-08-29
[QUOTE=elpresidente]Just tried it and got:

```
Package automake1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package automake1.5 has no installation candidate
```[/QUOTE]

Oops...I meant automake1.7

Same command, but 1.7. That is what is required anyway.


Sorry.

---

### Post by elpresidente on 2005-08-29
[QUOTE=KageKeeper]Oops...I meant automake1.7

Same command, but 1.7. That is what is required anyway.


Sorry.[/QUOTE]

```
Reading package lists... Done
Building dependency tree... Done
automake1.7 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
``` 

Hmmm. Doesn't quite make sense to me.

---

### Post by SFN on 2005-08-29
](*,) Well, I'm out. I've already spent way too much time on this and it still isn't working.

Trying e17 before really hooked me and I'm looking forward to it being available via a repository but this is too time consuming. I've got a grandchild coming in a couple of months and it just doesn't look like this will get built by then.

---

### Post by KageKeeper on 2005-08-29
*chuckles*

Ok, what does everyone think of this. I have tried to build the CVS two different ways. 

1.) Manually.

2.) The script in this thread.

Both ways I get an error, the same error, however it is in two different packages.

When I build manually I get this error while building **edje** :

```
gcc -g -O2 -o .libs/edje edje_main.o  ../../src/lib/.libs/libedje.so
../../src/lib/.libs/libedje.so: undefined reference to `evas_smart_below_get_set'
../../src/lib/.libs/libedje.so: undefined reference to `evas_smart_above_get_set'
collect2: ld returned 1 exit status
make[3]: *** [edje] Error 1
make[3]: Leaving directory `/home/rob/cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rob/cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/cvs/e17/libs/edje'
make: *** [all] Error 2
``` 

When I use the script in this thead, using the same CVS pull, I build edje successfully but fail on the next package **epsilon**.

Heres the kicker: **IT FAILS WITH THE SAME DARN ERROR!**  

Yep. So if that is not baffling, I don't know what is.

I am half tempted to erase everything and start alllll over from scratch.

---

### Post by darkmatter on 2005-08-29
[QUOTE=KageKeeper]*chuckles*

Ok, what does everyone think of this. I have tried to build the CVS two different ways. 

1.) Manually.

2.) The script in this thread.

Both ways I get an error, the same error, however it is in two different packages.

When I build manually I get this error while building **edje** :

```
gcc -g -O2 -o .libs/edje edje_main.o  ../../src/lib/.libs/libedje.so
../../src/lib/.libs/libedje.so: undefined reference to `evas_smart_below_get_set'
../../src/lib/.libs/libedje.so: undefined reference to `evas_smart_above_get_set'
collect2: ld returned 1 exit status
make[3]: *** [edje] Error 1
make[3]: Leaving directory `/home/rob/cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rob/cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/cvs/e17/libs/edje'
make: *** [all] Error 2
``` 

When I use the script in this thead, using the same CVS pull, I build edje successfully but fail on the next package **epsilon**.

Heres the kicker: **IT FAILS WITH THE SAME DARN ERROR!**  

Yep. So if that is not baffling, I don't know what is.

I am half tempted to erase everything and start alllll over from scratch.[/QUOTE]

That is rather odd. I'll look into it later once I get home and I'll see if I can come up with a solution. (No access to Linux at my current location)

---

### Post by mega on 2005-08-30
Someone needs to update this howto with directions for a bare machine

I started to attempt to run the script, but now I'm finding LOTS of dependencies I'm missing

things like what nvidia glx package works with the nvidia drivers from nvidia
jpeg headers
right now I'm getting errors about missing AM_PATH_GTK


the howto seems ok, but it's based on a machine that has too many packages installed, it's missing way too many from the directions

---

### Post by AndyAWS on 2005-08-30
Nightshade has been steadily adding dependencies as we let him know about them. If there are still some missing then perhaps you could post a list here to help him out.

The script has been working great for me, as long as I don't try to build evfs, elation, ewler or enotes. (elation might work but I haven't tried).

Remember some of the 'extra' apps just plain don't work, and at anytime there may be broken code in the cvs from the many daily updates.

---

### Post by mega on 2005-08-30
I have no idea what packages they are, asside from the jpeg library I mentioned

I have not found a fix for the current error

I also had to install the nvidia-glx dev package, and then re-install the nvidia drivers from nvidia.com, xorg would no longer start with the nvidia-glx ubuntu packages

---

### Post by AndyAWS on 2005-08-30
A couple tips that helped me:

Leave REBUILD_ALL = "yes" until you actually get through a successful build, otherwise you will most likely get missing libraries (that were never built).

Leave PREFIX="/usr/local" even if you originally had enlightenment under "/usr/". Actually almost anything that is installed from source should go under /usr/local/, it helps keep things isolated from package installs. I had no problems at all leaving the PREFIX as is, once I had all of the proper libraries installed.

Forget ENOTES for sure, the source code is broke and does not compile. Same for EWLER unless it's been updated in the last 2 days. EXPRESS, ELATION and EVFS I haven't tried yet. ERSS builds for me but runs buggy, ETERM and ENTERMINUS both seem to work for me. Also I chose not to build ENTRANCE so I can't say how that works. Everything else builds fine as of last night (haven't tried an update today).

---

### Post by AndyAWS on 2005-08-30
[QUOTE=mega]I have no idea what packages they are, asside from the jpeg library I mentioned

I have not found a fix for the current error

I also had to install the nvidia-glx dev package, and then re-install the nvidia drivers from nvidia.com, xorg would no longer start with the nvidia-glx ubuntu packages[/QUOTE]


When you find that you need to install a package, post the package name here, install it, and try again...yes it's time consuming, but in the end it's worth it...remember this is pre-alpha stuff, it's expected to be a bit of a pain. It initially took me about 3 nights (2 or 3 tries per night) to get everything I needed and successfully build. Now it's smooth sailing (so far).

And I'm not sure why installing any -dev package would break drivers, xorg or anything else...-dev's are only libraries used when compiling. :-?

---

### Post by AndyAWS on 2005-08-30
Unless installing the nvidia-glx-dev caused other files to be updated as well.

Anyway, if you've worked through that problem then the next would be finding out what library AM_PATH_GTK is from. Best to look back through the compiler output to see what was happening when you get the error.

Also set DEBUG_SCRIPT="yes" in the get_e.sh script, that might give you more info, I'm not sure, I set it to yes just because it looked like a good idea.

---

### Post by KageKeeper on 2005-08-30
Well, I *finally* got everything to build.

I had to completely redo my ubuntu install. I think I had something that was bunking it up.

I have not been able to get eterminus or eterm to successfully build as well as the ones already listed, ewler and evfs.

But hey, everything else is build, including entrance. I am not using entrance just because I do not fully undertstand how to configure it and such, but that will come in time I am sure. :D

---

### Post by SFN on 2005-08-30
[QUOTE=SFN]Me too. I'm like a crackhead now.[/QUOTE]

Yeah, OK. I couldn't take it anymore. Got it working, though.

I ran the script again. Same problems. So I tried setting all the BUILD statements to "no" except for BUILD_WM which I set to "yes", then ran it again. That worked so I set BUILD_WM to "no" and set the next one to yes and re-ran it. That worked too. On down the line until each of the pieces were built. 

I have to assume that means there's something funky in the script but I could be way off base.

At that point there was only one problem. In the HOWTO, it says:

[QUOTE=Nightblade]Now, log out and make sure there's a entry for Enlightenment where you pick what window-manager to use. If there isn't, just go back to gnome and open up a terminal:

```
$ sudo gedit /usr/share/xsessions/enlightenment.desktop
``` 

And add:

```
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Enlightenment Window Manager - www.enlightenment.org
Type=XSession
Exec=/usr/bin/enlightenment
TryExec=/usr/bin/enlightenment
```
[/QUOTE]

Those last two lines should read:

```
Exec=/usr/local/bin/enlightenment
TryExec=/usr/local/bin/enlightenment
```

I'm now writing this from within the womb of e17. Heaven, I tell you. Just got some tweaking to do.

---

### Post by SFN on 2005-08-30
Also, under Extra Modules the HOWTO says:

> 
To load these you run:

```
$ enlightenment_remote --module-load <modulename>
``` 


That should read:

> 
To load these you run:

```
$ enlightenment_remote -module-load <modulename>
``` 


---

### Post by Weav on 2005-08-30
I am trying to install cvs and enlightenment after executing sh get_e.sh ,however i get an error about 5 minutes in:
```

checking jpeglib.h usability... no
checking jpeglib.h presence... no
checking for jpeglib.h... no
configure: error: "Cannot find jpeglib.h. Make sure your CFLAGS environment variable contains include lines for the location of this file"

```
Anyone have any ideas? Thanks

---

### Post by AndyAWS on 2005-08-30
You need to install the jpeg library dev....I'm not sure (not at my Ubuntu computer ATM) but I think the package is called [COLOR=Red]libjpeg62[/COLOR] and [COLOR=Red]libjpeg62-dev[/COLOR]

---

### Post by darkmatter on 2005-08-30
[QUOTE=AndyAWS]Anyway, if you've worked through that problem then the next would be finding out what library AM_PATH_GTK is from.[/QUOTE]

The AM_PATH_GTK error he is experiencing is a reference to automake. Chances are he has the wrong version installed (1.5 is what is needed), so he is getting errors for undefined references during the build process.

---

### Post by Weav on 2005-08-30
[QUOTE=AndyAWS]You need to install the jpeg library dev....I'm not sure (not at my Ubuntu computer ATM) but I think the package is called libjpeg-dev[/QUOTE]
ok cool thanks it worked, but when i went to run the sh file it says it was merely "ipdating" and not installing all these things like before.
And now when i log onto enlightenment it is still e16, is it possible to completely remove all of enlightenment and just start over?

Thanks!

---

### Post by AndyAWS on 2005-08-30
In the get_e script change REBUILD_ALL="yes"

That will make it rebuild everything.

---

### Post by Weav on 2005-08-30
[QUOTE=AndyAWS]In the get_e script change REBUILD_ALL="yes"

That will make it rebuild everything.[/QUOTE]
ok i changed that which led to more errors  :-x 
```

./configure: line 5578:  5105 Segmentation fault      ( eval echo "$as_me:$LINENO: \"$ac_try\"" ) 1>&5
./configure: line 5578:  5106 Segmentation fault      ( eval $ac_try ) 2>&5
./autogen.sh: line 16:  4006 Segmentation fault      ./configure "$@"

```
Any ideas? Sorry to pester you guys all the time... ](*,)

---

### Post by AndyAWS on 2005-08-30
Don't worry about pestering...how do you think I managed to get it to work?  ;-) 

Seg faults are bad, might be broken source code...which lib/app was it building at the time?

---

### Post by AndyAWS on 2005-08-30
Also I'm not sure if it's OK to install E17 when you already have e16 installed...does anyone know for sure it that would work or if there's anything 'special' that would need to be done?

---

### Post by darkmatter on 2005-08-30
[QUOTE=AndyAWS]Also I'm not sure if it's OK to install E17 when you already have e16 installed...does anyone know for sure it that would work or if there's anything 'special' that would need to be done?[/QUOTE]

It will work, but only if E 16 is version 16.8+. They changed the install path in that version so that it doesn't conflict with E 17.

I think the version of E 16 in the repos is only 16.7, so it would have to be removed UNLESS E 17 and it's components are installed to a different path with:

```
 ./configure --prefix=<pathtoinstall>
```

---

### Post by Weav on 2005-08-30
[QUOTE=AndyAWS]Don't worry about pestering...how do you think I managed to get it to work?  ;-) 

Seg faults are bad, might be broken source code...which lib/app was it building at the time?[/QUOTE]
Um i don't quite remember it had been going for a good time, but i do have e16 installed and when i try to boot up into enlightenment it only boots up into e16.6

---

### Post by Weav on 2005-08-30
[QUOTE=darkmatter]It will work, but only if E 16 is version 16.8+. They changed the install path in that version so that it doesn't conflict with E 17.

I think the version of E 16 in the repos is only 16.7, so it would have to be removed UNLESS E 17 and it's components are installed to a different path with:

```
 ./configure --prefix=<pathtoinstall>
```[/QUOTE]
ok ya its not then do i need to do apt-get uninstall enlightenment?

I would rather just like to totally get rid of e16 and start anew and then maybe i won't be getting source errors

---

### Post by darkmatter on 2005-08-30
[QUOTE=Weav]ok ya its not then do i need to do apt-get uninstall enlightenment?

I would rather just like to totally get rid of e16 and start anew and then maybe i won't be getting source errors[/QUOTE]

Just uninstall dr16 and its components in synaptic, as it is easier to find and purge left over configuration files that way. 

make uninstall e 17 and all its libraries and additional applications from their respective source directories (If installed), then make clean and begin the build process again.

---

### Post by Weav on 2005-08-30
[QUOTE=darkmatter]Just uninstall dr16 and its components in synaptic, as it is easier to find and purge left over configuration files that way. 

make uninstall e 17 and all its libraries and additional applications from their respective source directories (If installed), then make clean and begin the build process again.[/QUOTE]
WoW i'm still sorta a Linux n00b so i went to synaptic manager and unchecked and did a complete removal of enlightenment, however i did not find dr16 and don't know how to make clean or make uninstall???

Thanks again!

---

### Post by darkmatter on 2005-08-30
[QUOTE=Weav]WoW i'm still sorta a Linux n00b so i went to synaptic manager and unchecked and did a complete removal of enlightenment, however i did not find dr16 and don't know how to make clean or make uninstall???

Thanks again![/QUOTE]

The Enlightenment listed in the synaptic repositories is dr16... ;-) 

As for the make clean, I'm to lazy to type. :roll:  Here: [https://vogelweith.homeftp.net/Files/rebuild_e17.sh](https://vogelweith.homeftp.net/Files/rebuild_e17.sh) 
or, do the following for each source directory:

```
$ cd ~/cvs/e17/<libs_or_apps>/<name_of_the_apps_or_libs> 
$ sudo make uninstall 
$ make clean 
$ aclocal 
$ ./autogen.sh 
$ make  
$ sudo make install 
$ sudo ldconfig
```

Note: If the script doesn't work and you need to manually rebuild, do the above for each source directory in the INSTALL ORDER given here: [https://vogelweith.homeftp.net/Linux/e17_en.php#x1-80002](https://vogelweith.homeftp.net/Linux/e17_en.php#x1-80002)

---

### Post by CuRoi on 2005-08-31
[QUOTE=darkmatter]The AM_PATH_GTK error he is experiencing is a reference to automake. Chances are he has the wrong version installed (1.5 is what is needed), so he is getting errors for undefined references during the build process.[/QUOTE]

I had that same error, so I've gone poking around with automake.

- Automake1.5 is no longer in the repos, so I tried 1.6.
- Ran into some compatibility issues with part of the system using 1.6, and part of it using 1.4. So I removed 1.4, and fixed the symlinks in /usr/bin/aclocal and /usr/bin/automake to point to the 1.6 versions. 
- This is the first time I've tried messing with automake versions, and keep running into problems. Now I get: ```
automake: src/lib/Makefile.am: Assembler source seen but `CCAS' not defined in `configure.in'
automake: src/lib/Makefile.am: Assembler source seen but `CCASFLAGS' not defined in `configure.in'
automake: src/lib/Makefile.am: Assembler source seen but `CCAS' not defined in `configure.in'
automake: src/lib/Makefile.am: Assembler source seen but `CCASFLAGS' not defined in `configure.in'
``` when the script is working on e17/libs/imlib2.

When changing automake versions, are there other things I need to do beyond a simple apt-get install?

TIA!

---

### Post by darkmatter on 2005-08-31
[QUOTE=CuRoi]I had that same error, so I've gone poking around with automake.

- Automake1.5 is no longer in the repos, so I tried 1.6.
- Ran into some compatibility issues with part of the system using 1.6, and part of it using 1.4. So I removed 1.4, and fixed the symlinks in /usr/bin/aclocal and /usr/bin/automake to point to the 1.6 versions. 
- This is the first time I've tried messing with automake versions, and keep running into problems. Now I get: ```
automake: src/lib/Makefile.am: Assembler source seen but `CCAS' not defined in `configure.in'
automake: src/lib/Makefile.am: Assembler source seen but `CCASFLAGS' not defined in `configure.in'
automake: src/lib/Makefile.am: Assembler source seen but `CCAS' not defined in `configure.in'
automake: src/lib/Makefile.am: Assembler source seen but `CCASFLAGS' not defined in `configure.in'
``` when the script is working on e17/libs/imlib2.

When changing automake versions, are there other things I need to do beyond a simple apt-get install?

TIA![/QUOTE]

Sorry, my brain was asleep when I made that post *bad penguin* :roll: . Here's my original, and it's automake1.7
[http://www.ubuntuforums.org/showpost.php?p=320625&postcount=112](http://www.ubuntuforums.org/showpost.php?p=320625&postcount=112)

As for the version to be used, it should be specified in the autogen.sh for the individual apps/libs, so it should be fine.

---

### Post by CuRoi on 2005-08-31
*edit* brainfart

Thanks darkmatter, that worked wonderfully.

//learn_to_read_the_thread
Post-automake, I came accross another dependency issue with misc/scrot that needed giblib1 and giblib-dev. 
//doh

Hrmmm:
configure: error: Library requirements (gtk+-2.0 >= 2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them

Ahhh:
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by darkmatter on 2005-08-31
[QUOTE=CuRoi]Thanks darkmatter, that worked wonderfully.[/quote]
Glad to hear it. :smile: 

[QUOTE=CuRoi]Post-automake, I came accross another dependency issue with misc/scrot that needed giblib1 and giblib-dev. FYI[/QUOTE]

I figured as much...

---

### Post by Ratur on 2005-08-31
[QUOTE=Stormy Eyes]OK, I installed all of the dependencies, but it still barfs at the same point when building evas:

```

gcc -g -O2 -o .libs/evas_software_x11_test evas_test_main.o evas_software_x11_main.o  ../../src/lib/.libs/libevas.so -lm -L/usr/X11R6/lib -lX11 -lXext
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeQueryVersion'
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status

```[/QUOTE]

I have exactly the same problem than you.

Did you manage to resolve it ?

---

### Post by Swad on 2005-08-31
Anyone tried this repository?  Does it work?  Are there any issues?

deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/

Current version there is 16.999.013 from Aug. 25th.

---

### Post by mrcsparker on 2005-08-31
I just put together a e17 build tool. It is basically a slightly modified version of jhbuild - 

[http://ecvsbuild.berlios.de](http://ecvsbuild.berlios.de)

Because it uses jhbuild, it does things like bootstrap your system, handle dependencies, has an optional gtk2 frontend, and will let you know if it is checking out code/compiling/installing from your notification area.

It should be able to run next to a current jhbuild installation without messing with it.

I have built e17 cvs on my breezy box, but there is no reason that it shouldn't work with warty ot hoary.

---

### Post by foxy123 on 2005-08-31
[QUOTE=Swad]Anyone tried this repository?  Does it work?  Are there any issues?

deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/

Current version there is 16.999.013 from Aug. 25th.[/QUOTE]
most of the stuff is built against newer version of libc6. I guess it should work in Breezy...

---

### Post by Swad on 2005-08-31
Ah--well I haven't made any move to breezy yet, so... I guess I might try one of these scripts.

---

### Post by DJ_Max on 2005-08-31
Ok, I got past the problem I had before, seems someone fixed the file that was giving people problems. But when it comes to e17/libs/engrave it says it needs automake 1.9!! Wish I would have known that before I uninstalled it.

---

### Post by rpgcyco on 2005-08-31
I'm getting the following error, like someone else here. I get it while compiling evas.

```
gcc: /usr/lib/libGL.so: No such file or directory
```

I'm not using the supplied NVIDIA drivers, so does anybody know how I can compile E17 using the officially packaged drivers?

According to the release notes of [7664](http://www.nvidia.com/object/linux_display_ia32_1.0-7664.html), the OpenGL headers are now installed by default, but I'm not sure that's even relevant.

- Rpg Cyco

---

### Post by Weav on 2005-09-01
```

$ cd /location/for/download
$ tar -xzf e17genmenu*
$ cd e17genmenu*
$ ./autogen.sh
$ make
$ sudo make install

```

When i follow those instructions after i do "make" it gives me this repeating error about perl not being able to work:
"perl: warning: Falling back to the standard locale ("C")."

Then at the end it spews this tou:
```

In file included from order.c:25:
eaps.h:8:21: Engrave.h: No such file or directory
make[2]: *** [order.o] Error 1
make[2]: Leaving directory `/home/steve/Downloads/e17genmenu-3.0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steve/Downloads/e17genmenu-3.0.3'
make: *** [all-recursive-am] Error 2

```
Any ideas? Thanks

---

### Post by AndyAWS on 2005-09-02
It looks like make is looking for Engrave, which should be there if you made it through the e17 install.

e17genmenu3.0.3 compliled for me but gives a seg fault when run.

As for the perl errors, I have no idea.

---

### Post by zzzneo on 2005-09-04
How do you solve the freetype version problem?

```
checking for freetype-config... /usr/bin/freetype-config
checking for freetype - version >= 9.8.0... *** An old version of freetype (9.5.3) was found.
*** You need a version of freetype newer than 9.8.0.
***
*** If you have already installed a sufficiently new version, this error
*** probably means that the wrong copy of the freetype-config shell script is
*** being found. The easiest way to fix this is to remove the old version
*** of freetype, but you can also set the FREETYPE_CONFIG environment to point to the
*** correct copy of freetype-config. (In this case, you will have to
*** modify your LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf
*** so that the correct libraries are found at run-time)
no
configure: error: Freetype isn't installed

```

---

### Post by Xgkkp on 2005-09-07
It has been mentioned many times that you need the nvidia-glx-dev file for nvidia cards, but what should I have If I am using ATI?

---

### Post by rjstevens3 on 2005-09-07
[QUOTE=Xgkkp]It has been mentioned many times that you need the nvidia-glx-dev file for nvidia cards, but what should I have If I am using ATI?[/QUOTE]

I don't think that you need them. i have an intel intergrated graphics card in my laptop and i built e17 just fine without nvidia-glx-dev.

---

### Post by manobes on 2005-09-07
I had the exact same freetype problem.  Does anybody have a workaround?

---

### Post by leonardovcr on 2005-09-07
Just dropping by to say that version 4.0.0 of e17genmenu has been released.
Grab it [here](http://sourceforge.net/projects/e17genmenu).
I haven't tested it though...

Edit1.
Oh, and some fixes have been made to the get_e script. Check it [here](http://dev.winged.it/download/enlightened_stuff/enlightenment_updater_script) .

---

### Post by kevcart3 on 2005-09-16
Hi everyone, I was just trying to figure out everything I needed to do to get E17 working in Breezy using CVS. I'm not having much luck, Here's my error so far:

Running aclocal...
aclocal: configure.in: 17: macro `AM_ENABLE_SHARED' not found in library
aclocal: configure.in: 18: macro `AM_PROG_LIBTOOL' not found in library


I know this guide is for Hoary, but I am trying to figure out a good way to get this to work in Breezy, and I figured compiling from cvs would be the best solution. Any ideas on what is causing this error?

Thanks in advance.

---

### Post by sinaen on 2005-09-16
Maybe you should wite what dependencies for the rest of us that also want this to work, if there are more than the ones described in the howto at the beginnning

[QUOTE=kpettersen]Okay, e17 up and running.  There were a lot of dependencies to add.  Mostly the development stuff needed for different portions of e17 that a normal Ubuntu install doesn't include.  I removed ( said "no" ) to eterminus and most of the other experimental or older items in the get_e.sh file.

KP[/QUOTE]

---

### Post by sinaen on 2005-09-16
anyone got this error? i haveread throug the whole 20 pages of your conversation but i dont remember anything about this

make[2]: Leaving directory `/home/sinaen/e17cvs/e17/apps/eclair'
make[1]: Leaving directory `/home/sinaen/e17cvs/e17/apps/eclair'
~/e17cvs
get_e.sh: line 515: pushd: e17/libs/exml: No such file or directory

ill be glad if you can help me

---

### Post by Nightblade on 2005-09-16
[QUOTE=sinaen]anyone got this error? i haveread throug the whole 20 pages of your conversation but i dont remember anything about this

make[2]: Leaving directory `/home/sinaen/e17cvs/e17/apps/eclair'
make[1]: Leaving directory `/home/sinaen/e17cvs/e17/apps/eclair'
~/e17cvs
get_e.sh: line 515: pushd: e17/libs/exml: No such file or directory

ill be glad if you can help me[/QUOTE]
 Usually fixes itself after a while.

---

### Post by dukeleto on 2005-09-16
Hi all,
I'm rather tempted to try e17, but would like to keep my gnome available.
How does it work at the moment: do you choose between e17 and gnome at the login screen? As long as it leaves me the choice, that's fine!
Thanks,
Olivier

---

### Post by gorkhal on 2005-09-16
[QUOTE=dukeleto]Hi all,
I'm rather tempted to try e17, but would like to keep my gnome available.
How does it work at the moment: do you choose between e17 and gnome at the login screen? As long as it leaves me the choice, that's fine!
Thanks,
Olivier[/QUOTE]

Yup the login screen lets you choose between your installed desktop environments, just make sure you follow the Howto correctly

---

### Post by dukeleto on 2005-09-16
you mean I will be able to choose, and have access to my *unmodified* gnome?
That's great! away I go for compile time then!
Thanks,
olivier

---

### Post by sinaen on 2005-09-16
[QUOTE=Nightblade]Usually fixes itself after a while.[/QUOTE]

LOL, then i try again, and again, and again again, if i must ;)

---

### Post by sinaen on 2005-09-16
[QUOTE=sinaen]LOL, then i try again, and again, and again again, if i must ;)[/QUOTE]
 ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  tried at least 4 times now ;/ still the same problem

---

### Post by rjwood on 2005-09-17
please, can someone  tell me how to do this!!;

| /etc/ld.so.conf paths don't contain e17 libs' path.               |
| Add /usr/local/lib to /etc/ld.so.conf please.

I'm a real newbie
I know I know  I probably should not try but, I have the time and I want to learn...
thanks---i'll chek back later.

---

### Post by sinaen on 2005-09-17
[QUOTE=rjwood]please, can someone  tell me how to do this!!;

| /etc/ld.so.conf paths don't contain e17 libs' path.               |
| Add /usr/local/lib to /etc/ld.so.conf please.

I'm a real newbie
I know I know  I probably should not try but, I have the time and I want to learn...
thanks---i'll chek back later.[/QUOTE]


sudo gedit /etc/ld.so.conf 

then put in the line
/usr/local/lib 
under the ones in the file, then save, then youre on to the next level

---

### Post by rjwood on 2005-09-17
can anybody please tell me how to solve this problem. should I just
sudo apt-get remove automake1.4 ???? thanks in advance
forgot to quote with question
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
Makefile.am:2: require version 1.5, but have 1.4-p6
src/bin/Makefile.am:1: require version 1.5, but have 1.4-p6
rob@basement:~/e17cvs$

rob@basement:~$ sudo apt-get install automake1.7
Reading package lists... Done
Building dependency tree... Done
automake1.7 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rob@basement:~$

and btw can I do that in another terminal while the first terminal is waiting????

---

### Post by foxy123 on 2005-09-17
[QUOTE=rjwood]can anybody please tell me how to solve this problem. should I just
sudo apt-get remove automake1.4 ???? thanks in advance
forgot to quote with question
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
Makefile.am:2: require version 1.5, but have 1.4-p6
src/bin/Makefile.am:1: require version 1.5, but have 1.4-p6
rob@basement:~/e17cvs$

rob@basement:~$ sudo apt-get install automake1.7
Reading package lists... Done
Building dependency tree... Done
automake1.7 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rob@basement:~$

and btw can I do that in another terminal while the first terminal is waiting????[/QUOTE]
I had a similar problem with another app. The only way was to uninstall 1.4 and install a newer version.

---

### Post by rjwood on 2005-09-17
thanks everyone for all the help. I got it working
not really that crazy about it but, maybe I just need some time with it.
thanks again for the great---how to.

---

### Post by juantxorena on 2005-09-18
OK, I have readed the entire post, I tried to solve, I've installed a lot of libs-dev. But I got this error when the script it's compiling ewl:
 ```
ewl_config.c: In function `ewl_config_config_read':
ewl_config.c:209: error: `PF_MODIFIED' undeclared (first use in this function)
ewl_config.c:209: error: (Each undeclared identifier is reported only once
ewl_config.c:209: error: for each function it appears in.)
ewl_config.c:210: error: `PF_SYSTEM' undeclared (first use in this function)
ewl_config.c: In function `ewl_config_defaults_set':
ewl_config.c:388: error: `PF_MODIFIED' undeclared (first use in this function)
ewl_config.c:389: error: `PF_SYSTEM' undeclared (first use in this function)
make[3]: *** [ewl_config.lo] Error 1
make[3]: Leaving directory `/home/juantxorena/e17cvs/e17/libs/ewl/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/juantxorena/e17cvs/e17/libs/ewl/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/juantxorena/e17cvs/e17/libs/ewl'
make: *** [all] Error 2

``` 
Please help, anyone

---

### Post by DJ_Max on 2005-09-18
Samething happened to me. But, it's a CVS version, it's not meant to work all the time. There's nothing you can do but wait until they update it.

---

### Post by leonardovcr on 2005-09-19
Ewl is compiling OK now...

Guys, I've noticed something strange... if I head to the 'start menu' and click on About Enlightenment, it shows me that the version installed is 0.16.999.013.

Shouldn't it be 0.17? I've compiled it straight from the CVS...

---

### Post by dlpfmVfH on 2005-09-20
does this script work on breezy to....

or do I have to change some stuff...

I would really like to help out, and maybe build deps for breezy that can go into some repository for all breezy folks out there.

Because at the moment enlightenment in breezy is outdated even the dr16 is outdated...

any response is appreciated...

---

### Post by Tomasz on 2005-09-20
On breezy current, everything goes fine until this
```

=== Building: e17/libs/evas... ===


 => Autofoo: e17/libs/evas

Running aclocal...
aclocal: configure.in: 118: macro `AM_PATH_GTK' not found in library

```

Any ideas?

---

### Post by DJ_Max on 2005-09-20
[QUOTE=leonardovcr]Ewl is compiling OK now...

Guys, I've noticed something strange... if I head to the 'start menu' and click on About Enlightenment, it shows me that the version installed is 0.16.999.013.

Shouldn't it be 0.17? I've compiled it straight from the CVS...[/QUOTE]
 No, e17 hasn't been released, if you read the documents on the site, I forget where, it'll tell you.

This script should work on breezy, granted you have the correct dependecies.

---

### Post by juantxorena on 2005-09-20
ewl is not compiling:
```
/bin/sh: line 1: 26081 Violación de segmento  edje_cc -v -id ../../data/themes/default/bits/images default.edc ../../data/themes/default.edj
make[3]: *** [default.edj] Error 139
make[3]: Leaving directory `/home/juantxorena/e17cvs/e17/libs/ewl/data/themes'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/juantxorena/e17cvs/e17/libs/ewl/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/juantxorena/e17cvs/e17/libs/ewl'
make: *** [all] Error 2
``` 
Violación de segmento = Segment violation.
What happens?

---

### Post by leonardovcr on 2005-09-20
[QUOTE=DJ_Max]No, e17 hasn't been released, if you read the documents on the site, I forget where, it'll tell you.

This script should work on breezy, granted you have the correct dependecies.[/QUOTE]
Well, that's strange... I could swear that, when I compiled it on another machine, it showed me 0.17.something.

---

### Post by dlpfmVfH on 2005-09-21
[QUOTE=DJ_Max]No, e17 hasn't been released, if you read the documents on the site, I forget where, it'll tell you.

This script should work on breezy, granted you have the correct dependecies.[/QUOTE]

I tried the script on Breezy, installed almost all dev files I could possibly found,
and it still not working, something about makefile.in missing, about depencies, 1,50 is needed but 1,46c is used.... 

But I can't figure out why....rerun the script it stops on something else...
it could be that the cvs was in the middle of some update the moment I grabbed the packages...

build E17 cvs from scratch without the script...and no problems...
just used the Get E guide for the build order...and installed with checkinstall..
had to do one sudo ldconfig with emotion....so it could find all it needs...

---

### Post by DJ_Max on 2005-09-21
[QUOTE=aboe]I tried the script on Breezy, installed almost all dev files I could possibly found,
and it still not working, something about makefile.in missing, about depencies, 1,50 is needed but 1,46c is used.... 
[/QUOTE]
It requires a certain version of automake you probably don't have installed.

---

### Post by dlpfmVfH on 2005-09-22
installed every automake, and compiling without the script worked fine...
I have enlightenment running at the moment....
but can't figure out what went wrong in the script....

maybe it is the sudo ldconfig before compiling emotion....

And I build it with checkinstall...so I got some nice deb files...
except I was lazy about the information and naming schemes...hahaha
so every deb has the same version numbering and description...
just saying it was a cvs build on 21 september 2005....

but it runs...and that is the main point...

---

### Post by juantxorena on 2005-09-22
The same error as above:
```
/bin/sh: line 1: 10325 Violación de segmento  edje_cc -v -id ../../data/themes/default/bits/images default.edc ../../data/themes/default.edj
make[3]: *** [default.edj] Error 139
make[3]: Leaving directory `/home/juantxorena/e17cvs/e17/libs/ewl/data/themes'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/juantxorena/e17cvs/e17/libs/ewl/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/juantxorena/e17cvs/e17/libs/ewl'
make: *** [all] Error 2
``` 
I downloaded everithing again, just in case.
What went wrong?

---

### Post by volvoguy on 2005-09-24
[QUOTE=sinaen]Maybe you should wite what dependencies for the rest of us that also want this to work, if there are more than the ones described in the howto at the beginnning[/QUOTE]
 I didn't keep track of all of them unfortunately, but here are the three I wrote down when I realized that might be a good idea. :o)

flex
bison
byacc

I don't know if they're explicitly required, but they were mentioned at a few different points where my builds failed, so I installed them and continued just fine. I'm using Breezy BTW. This script has kept things up to date for nearly a week, but the last 24 hours or so there are some things that are failing to build. I'm assuming it's e17's "bleeding edgedness" because the errors don't mention anything about missing software or dependencies. Considering it's alpha code, I'm assuming the bugs will work themselves out eventually. 

Aaron

---

### Post by Ampersand on 2005-09-24
Got the cvs of E17 installed, I get an error about not being able to set up the IPC socket when I log in or try to load modules. None of the menus in Eclair work (although folders can be dragged on and played). Is there a fix for these other than waiting for them to be fixed in the CVS? Also, is it possible to get Entrance working instead of GDM?

Other than that, it's looking good. Thanks to everyone who postedf dependancies. (:

---

### Post by Ampersand on 2005-09-25
The IPC socket problem was because the .ecore directory was owned by root. One other question, does the anonymous CVS server on sourceforge update continuously, or at a certain time each day? I believe it's updated later than the subscriber one.

---

### Post by linkunderscore on 2005-09-26
```
ES_PDA=1 -DMEDIUMRES_PDA=2 -DHIRES_PDA=3 -DSLOW_PC=4 -DMEDIUM_PC=5 -DFAST_PC=6 -DE17_PROFILE=FAST_PC \
../../data/init/init.edc \
../../data/init/init.edj
make[4]: *** [init.edj] Segmentation fault
make[4]: Leaving directory `/home/link/e17cvs/e17/apps/e/data/init'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/link/e17cvs/e17/apps/e/data/init'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/link/e17cvs/e17/apps/e/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/link/e17cvs/e17/apps/e'
make: *** [all-recursive-am] Error 2


```

seems to be a common problem...this is really starting to piss me off. >:|

sadlkjhgas'dsgfasdfasdf
:confused:

---

### Post by DJ_Max on 2005-09-26
[QUOTE=linkunderscore]```
ES_PDA=1 -DMEDIUMRES_PDA=2 -DHIRES_PDA=3 -DSLOW_PC=4 -DMEDIUM_PC=5 -DFAST_PC=6 -DE17_PROFILE=FAST_PC \
../../data/init/init.edc \
../../data/init/init.edj
make[4]: *** [init.edj] Segmentation fault
make[4]: Leaving directory `/home/link/e17cvs/e17/apps/e/data/init'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/link/e17cvs/e17/apps/e/data/init'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/link/e17cvs/e17/apps/e/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/link/e17cvs/e17/apps/e'
make: *** [all-recursive-am] Error 2


```

seems to be a common problem...this is really starting to piss me off. >:|

sadlkjhgas'dsgfasdfasdf
:confused:[/QUOTE]

Do you really expect a CVS version of software to work? It hasn't been packaged for a reason. This is one of them.

---

### Post by wbiggers on 2005-09-27
I went through and manually build E17 - awesome!  Then wanted to try out the script so I didn't have to dedicate several hours every time I wanted to update.  However, when I ran the script, I go the following error over and over:

        perl: warning: Setting locale failed.
        perl: warning: Please check that your locale settings:
                LANGUAGE = "en",
                LC_ALL = (unset),
                LANG = "en
            are supported and installed on your system.
        perl: warning: Falling back to the standard locale ("C").

Seemed odd because I didn't get any of that when I went through manually.

Did some searching and found lots of locale information related to perl at [http://www.sunsite.ualberta.ca/Documentation/Misc/perl-5.6.1/pod/perllocale.html](http://www.sunsite.ualberta.ca/Documentation/Misc/perl-5.6.1/pod/perllocale.html)

Unfortunately, I'm not savy enough to really understand what it all means.  Someone with knowledge of perl - could you interpret the information for the rest of us?

I figure it isn't all that bad - the perl messages are warnings but they don't stop the process.  They just tell us that Perl is defaulting back to a basic locale called "C".  But it would be nice to stop all the warning messages (and hopefully speed up the process a bit by keeping the system from having to search for locales over and over and over and ....

---

### Post by sinaen on 2005-09-29
[QUOTE=volvoguy]I didn't keep track of all of them unfortunately, but here are the three I wrote down when I realized that might be a good idea. :o)
flex
bison
byacc
I don't know if they're explicitly required, but they were mentioned at a few different points where my builds failed, so I installed them and continued just fine. I'm using Breezy BTW. This script has kept things up to date for nearly a week, but the last 24 hours or so there are some things that are failing to build. I'm assuming it's e17's "bleeding edgedness" because the errors don't mention anything about missing software or dependencies. Considering it's alpha code, I'm assuming the bugs will work themselves out eventually. 
Aaron[/QUOTE]

Well it seems like i also had run into these problems, so i already had them installed. but its a good thing to have a list somewhere that you can watch what preparations you should make when trying to build e17 from cvs. the first page howto is one sure thing to place it, update the message there. if youre the one who wrote it for example.

---

### Post by sinaen on 2005-09-29
I haven't tried to build for a while now, but now when i tested it again, the script is exiting on an very early basis

cd . && /bin/sh /home/sinaen/e17cvs/e17/libs/eet/missing --run aclocal-1.7
aclocal: configure.in: 127: macro `AM_CHECK_DOXYGEN' not found in library
make: *** [aclocal.m4] Error 1

thats a real hassle,

did a
apt-cache search aclocal
libguile-dev - Development headers and static library for libguile
sinaen@Yoshi:~/e17cvs$ sudo apt-get install libguile-dev
Reading package lists... Done
Building dependency tree... Done
libguile-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so now what, ill think ill try a manual build, for now, or install the e16 release,

and i also am thinking of developing a real tourettes syndrome, atleast when im by the computer trying to get e17 cvs to compile and work.

---

### Post by sinaen on 2005-09-29
[QUOTE=KageKeeper]Ok. New one I think.
Building evfs, get this error:
```
/usr/bin/ld: cannot find -lfam
``` 
Which I think means it needs libfam-dev.
But, for libfam-dev, I am told it depends on libfam0c102 and if I try to install that, it wants to remove a TON of things.
Any suggestions?
Should I just not build evfs?[/QUOTE]

the same goes for me; i dont know if there are any real dependencies to install the most of those packages; and the most of them are already installed if you run ubuntu with gnome, its really strange, anyone know how to just install the required packages? instead of getting a whole bunch of useless-packages installed on a system?

writing from enlightenment, but it seems that i have several things to build left, but the core seems to work

---

### Post by sinaen on 2005-09-29
Here's a complete list of dependencies; that i got by reading through all the pages again

im not sure i can have missed something somewhere, but with my eyes i dont think thats to possible

gcc-3.4
g++-3.4
libx11-dev
libpng12-dev
libtiff4-dev
libfreetype6-dev
libssl-dev
zlib1g-dev
xlibmesa-dev
xlibmesa-gl-dev
libxine-dev
libtag1-dev
libxml2-dev
automake1.7
autogen
libsqlite3-dev
libtagc0-dev

Also install your graphicsdrivers dev

build
essentials
libtool
libsqlite3-dev
libltdl3-dev
libgtk2.0-dev
libfam-dev
libfam0c102 (removes a whole bunch of stuff; is it worth it? check last piece)
libjpeg62-dev
flex
giblib1
giblib-dgettext
cvs
libpng3-dev
libungif4-dev
lbbz2-dev
pkg-config
bison
byacc
bmesa-gl-dev
libxine-dev
libtag1-dev
libxml2-dev
automake1.7
autogen
libsqlite3-dev
libtagc0-dev

That's all hehe! hope you can make something usefull of this
This is what does get removed if you install libfam

sinaen@Yoshi:~$ sudo apt-get install libfam-dev libfam0c102
Password:
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  fam
The following packages will be REMOVED:
  azureus bug-buddy capplets contact-lookup-applet eog evolution
  evolution-data-server evolution-exchange evolution-webcal file-roller gamin
  gcalctool gconf-editor gdm gedit gedit-common gnome-about gnome-applets
  gnome-applets-data gnome-control-center gnome-cups-manager gnome-games
  gnome-gv gnome-media gnome-menus gnome-netstatus-applet gnome-nettool
  gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-utils gnome-volume-manager gnomemeeting goobox gstreamer0.8-gnomevfs
  gthumb gtkhtml3.6 gucharmap hal-device-manager hwdb-client ifp-gnome
  libbonoboui2-0 libcamel1.2-3 libebook1.2-3 libecal1.2-2 libedata-book1.2-2
  libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-4 libeel2-2
  libegroupwise1.2-5 libgal2.4-0 libgal2.4-common libgamin0 libgnome-desktop-2
  libgnome-menu0 libgnome2-0 libgnome2-perl libgnome2-vfs-perl
  libgnomecupsui1.0-1 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common
  libgtkhtml3.6-18 libgucharmap4 libnautilus-extension1 libpanel-applet2-0
  libswt-gtk-3.1-java libswt-gtk-3.1-jni libwvstreams3-base mozilla-firefox
  mozilla-firefox-gnome-support mozilla-mplayer nautilus nautilus-cd-burner
  nautilus-sendto netspeed nvu python-gnome2 python2.4-gnome2 rhythmbox screem
  sound-juicer totem-xine update-manager update-notifier vino yelp
The following NEW packages will be installed:
  libfam-dev libfam0c102

SO libfam-dev libfam0c102 seems to remove the whole gnome completely, and firefox, anyway the core system, so that it doesn't run again 

thats not fun anyone know how to reverse this later? so that you not need to install gnome over again?

---

### Post by wbiggers on 2005-09-29
[QUOTE=sinaen]
writing from enlightenment, but it seems that i have several things to build left, but the core seems to work[/QUOTE]

Yes - you will get several items more when you use the script than by manual compile/install.

Also, before using the script, go to synaptic/aptitude and remove automake1.4.  Make sure that automake1.7 is installed.  The automake packages can all co-exist on your system.  When I installed manually, I had no problem even though both 1.4 and 1.7 were installed.  When I used the script, automake1.4 was the only one called and it crashed the process.  This will hopefully also solve your AM_ error mentioned above.

As for the dependencies, I used the most up-to-date versions and didn't have gnome uninstalled.

---

### Post by juantxorena on 2005-10-01
Greetings.
I have decided to uninstall E17, which I installed with this script. There is some fast way to uninstall everithing or I uninstall lib by lib and component by component doing make uninstall && make clean?

---

### Post by sinaen on 2005-10-03
[QUOTE=wbiggers]Yes - you will get several items more when you use the script than by manual compile/install.
Also, before using the script, go to synaptic/aptitude and remove automake1.4.  Make sure that automake1.7 is installed.  The automake packages can all co-exist on your system.  When I installed manually, I had no problem even though both 1.4 and 1.7 were installed.  When I used the script, automake1.4 was the only one called and it crashed the process.  This will hopefully also solve your AM_ error mentioned above.
As for the dependencies, I used the most up-to-date versions and didn't have gnome uninstalled.[/QUOTE]

Well i never did any manual install i figured to try once again, after i got the libfam packages, and guess what it worked, althoug it didn't make a nice scene afterwards no gdm no firefox no nothing, when i wrote last time from enlightenment, i chose to install libfam and libfam dev packages, althoug it removed a whole lot of usefull stuff, i still had firefox in the memory, but not this time since i reboot to se how it worked, awful thats how it worked no graphical display login, but that doesnt botherd me, i started up entranced, and tried to log in.
It did not work the screen blinked a few times then it resolved back to the login-screen.

now this time i just ran startx, started som terminals, and installed firefox gdm and azureus for now, i thought of to try other browsers, but every browser i selected was the same results, that libfam* would be removed.
Fine i thougt i have enlightenment up atm and i need to go browse the web.

I have chatted about libfam packages with a friend, and he thougt he had them on his system, but found out he had'nt, then when he tried to install it too, it wanted to remove several packages, on his system to, but not as many as in my case.

that i think is the main update. Does anyone here have some strange apt-messages to? i think its a bug somewhere or glitch.

Oh Yeah i forgot, i do have only automake1.7.9 on my system

Another edit:
I dont really know if any of the dependencies in my list, is really neccessary or which isn't

---

### Post by volvoguy on 2005-10-06
[QUOTE=sinaen]Well it seems like i also had run into these problems, so i already had them installed. but its a good thing to have a list somewhere that you can watch what preparations you should make when trying to build e17 from cvs. the first page howto is one sure thing to place it, update the message there. if youre the one who wrote it for example.[/QUOTE]

I agree, but I'm obviously not the one who wrote it. In fact I'm starting to wonder if the original author has abandoned the project since all the dependency issues, typos and various other fixes mentioned in the thread don't seem to be making it back into the origional post. 

Since I'm absolutely blown away by elive, I may try giving that method of installing e17 on ubuntu a try if I can figure out how to uninstall everything from this attempt.

---

### Post by sinaen on 2005-10-13
[QUOTE=volvoguy]I agree, but I'm obviously not the one who wrote it. In fact I'm starting to wonder if the original author has abandoned the project since all the dependency issues, typos and various other fixes mentioned in the thread don't seem to be making it back into the origional post. 

Since I'm absolutely blown away by elive, I may try giving that method of installing e17 on ubuntu a try if I can figure out how to uninstall everything from this attempt.[/QUOTE]

Hehe i get your point. i finally got back my gnome again. well not all of it, since the backports arent functioning at all now, so azureus is not into the repositories at all

i figure out how to change to the stabile enlightenment instead. and to get all my programs i want to use in there instead.

Or ill just install windows. and dont give a shi** about linux in a while. cause im anyway going to cut down on my computer-hours and everything i need i can have in windows too

hmm i wonder if someone did a how to get e17 out of your system :D

---

### Post by stevea1210 on 2005-10-18
I have this up and running and breezy.  It does give you a new appreciation for apt-get.  I did run into a lot of missing dependencies.  Unfortunately, I only had the brilliant idea of writing them down half way through.  So when I build on my laptop, I will have to go through it all over again.  I will try to remember to write them down, and post here, to make it a little easier on others.   

One issue I’m having is that minimize, maximize, and close window buttons only work in the default theme.  On all other themes, they aren’t working.  Has anyone else had this with a recent build?

I also got E17 running as my default session in VNC.  
```
exec enlightenment
``` 
is what you need to add at the bottom of your xstartup.  Speed is fine across my LAN, even over wireless.

---

### Post by aftertaf on 2005-10-20
I got e17 working on my breezy laptop, instaled via cvs and sources compiled.

a couple of things maybe mentioned but worthwhile:

1. compile in the order given in the [www.get-e.org](www.get-e.org) user guides, starting with the EFL packages, the libraries.
after each compile, run sudo ldconfig

2. if you use the --prefix=[path] option with autogen or automake, make sure you use it in all the package compilations.
Also, add the path to your /etc/profile  & /etc/ld.so.conf

3. make sure you have installed automake 1.7, and removed automake 1.4, i also removed the older version of autoconf - i kept version 2.53

4. install the xlibs-dev package, and the -dev package corresponding to your gfx card.    I ended up installing a LOT of -dev packages to get past the XF86 error thrown by one of the libs (evas, ecore?)

5. i'll put more as and when i remember/discover.



E17 is still a work i progress, but it is looking fantastic and runs a dream on my 500 mhz PIII laptop.

For the moment, don't use any repositories to install it, the .debs are all out of date, to my knowledge.... See if in the deb packages, you have cvs & date in the name, if the deb isnt more tham a month old, you can get round this.

---

### Post by johnnymo87 on 2006-01-13
[quote=aftertaf]4. install the xlibs-dev package, **and the -dev package corresponding to your gfx card**. I ended up installing a LOT of -dev packages to get past the XF86 error thrown by one of the libs (evas, ecore?)[/quote]

how do I find which -dev package corresponds with my graphics card? I have a voodoo 3dfx.

---

### Post by N8K99 on 2006-01-18
I have an ancient machine with terrible memory issues- I have written about this many times before - hence my desire to run enlightenment instead of metacity. Performance has dramatically increased since removing metacity, I ran DR16 for about three weeks until CVS worked out some more bugs and apparently in the meantime, this script has been updated so that it puts enlighenment directly into path directories. Things do work much, much better now. I ran it twice to get things to work but now I am very, very happy with my  fresh install of e17!
Here's a little screenshot
[IMG]http://eckenrodehouse.net/kjgart/Screenshot.png[/IMG]

---

