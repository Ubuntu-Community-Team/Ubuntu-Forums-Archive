---
title: "HOWTO: E17 Installation/Customization on Hoary"
date: 2005-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by epaolox on 2005-04-29
Just uploaded (a new release, I haven't found anymore my yesterday post ... :-?

---

### Post by seven on 2005-04-29
great thanks man,  I always tried tto install E17 from the CVS.
the deb packages aren't always updated. now im going to try this out
great  :roll:

---

### Post by ykpaiha on 2005-04-29
Very good but a bit complcated (lol)
I mixed your how to with the one ( sorry in french) here:
[https://vogelweith.homeftp.net/Linux/e17.php](https://vogelweith.homeftp.net/Linux/e17.php)
I could, like this, apreciate the future e17 desk
Wonderfull it's just the word, may I add it's really in early stage but with a lot of promesses included:
The 5 tools alredy working are superbs!!!
Try it 
For the next E-ubuntu ??? \\:D/

---

### Post by seven on 2005-04-29
[QUOTE=ykpaiha]Very good but a bit complcated (lol)
I mixed your how to with the one ( sorry in french) here:
[https://vogelweith.homeftp.net/Linux/e17.php](https://vogelweith.homeftp.net/Linux/e17.php)
I could, like this, apreciate the future e17 desk
Wonderfull it's just the word, may I add it's really in early stage but with a lot of promesses included:
The 5 tools alredy working are superbs!!!
Try it 
For the next E-ubuntu ??? \\:D/[/QUOTE]

nice, but is there any english version or something? ;\
you can understand what to do basiclly , but still, english is the best :)

---

### Post by Debmat on 2005-04-29
I'm working on an english version.
coming soon ...  :wink:

---

### Post by epaolox on 2005-04-30
To Matthieu Vogelweith

Very, very good HOWTO (and very nice to see too). 

I don't know french language (sorry) but I founded your guide so clear
that IMHO it can be a perfect start to E-Ubuntu.  :) 

Best regards

PC

P.S. If there is someone interested of, I can prepare an italian translation  :wink:

---

### Post by ykpaiha on 2005-04-30
For those having problems with french (is it possible?)
I mention that a base how-to in english is available here:

[http://get-e.org//Documentation/User_Guide_pages/print.html](http://get-e.org//Documentation/User_Guide_pages/print.html)

A bit tuff, but usable, for sure the one in French is the easiest , thanks for those going to work a translation on it (just advice the owner pls)

For my part I am a bit too busy actually, but if any help let me know.

It realy worth to let a lot of people see what can be done out of a Linux box!!And here is a wonder.

---

### Post by jonny on 2005-04-30
If you try this stuff and don't like it, is it easy to get back to standard gnome / metacity setup?  Or have you borked your box?

---

### Post by Fab on 2005-04-30
[QUOTE=jonny]If you try this stuff and don't like it, is it easy to get back to standard gnome / metacity setup?  Or have you borked your box?[/QUOTE]
 as easy as selecting gnome when logging in :P

---

### Post by ykpaiha on 2005-04-30
As mentioned in the howto leave the configure at its own place : 
/usr/local
and dont mix pls with package in /usr
like this it is easy to remove with make uninstall
and no mix with your own desk.

---

### Post by epaolox on 2005-05-01
Originally Posted by jonny
If you try this stuff and don't like it, is it easy to get back to standard gnome / metacity setup? Or have you borked your box?

Like I wrote in the "original" HOWTO I made a session in /usr/share/xsessions
just for Enlightenment.

I'm not using Entrance (till now) but using GDM you can just tell Gnome that your 
preferred session is Gnome.
 
So, of course, if you don't like E17 you can always go back to metacity.

I made E17 my preferred one, but this is tipical Linux philosophy, you can choose .. :grin: 

Regards
PC

---

### Post by Debmat on 2005-05-01
Thank you epaolox.
The english version coming soon and i can add your italian translation if you want.

---

### Post by epaolox on 2005-05-02
To Debmat:

Thank you. Let me know when English version is ready so I can contribute.

---

### Post by Debmat on 2005-05-02
ok, thanks.

---

### Post by vrln on 2005-05-10
[QUOTE=ykpaiha]For those having problems with french (is it possible?)
I mention that a base how-to in english is available here:

[http://get-e.org//Documentation/User_Guide_pages/print.html](http://get-e.org//Documentation/User_Guide_pages/print.html)

A bit tuff, but usable, for sure the one in French is the easiest , thanks for those going to work a translation on it (just advice the owner pls)

For my part I am a bit too busy actually, but if any help let me know.

It realy worth to let a lot of people see what can be done out of a Linux box!!And here is a wonder.[/QUOTE]

Just noticed today that I had accidentally replied in the old warty thread and not this active one. I'm one of the staff from get-e.org. The installation part in the guide is not very thorough, that's pretty much on purpose because it has to be distribution-neutral so it's impossible to have all the dependencies etc listed for every available distribution.  It should be noted though that as E17 is not officially supported and still in a pre-alpha state and the CVS version is broken/buggy every now and then, it's not meant to be used mainstream yet (of course those who are interested enough are free to try it, and there seem to be alot of those people). The French site is great too, especially the installation part is more thorough if your using Ubuntu/Debian, but for configuration information it doesn't replace get-e.org.

We are much more than just a site about installation information. The install section on the user guide is less than ~20% of the whole guide. It's true that manual compiling notes are told first, but that's because that works for all distributions. There's also a distribution specific section, which points at various unofficial package repositories. Granted though, things like ld.so.conf settings are only briefly explained as the installation section isn't really the focus of the guide.

The real point of get-e.org however, is to be a users' portal - something like kde-look.org is to KDE. The user guide, after the initial brief installation section, explains (almost) everything there is to know about configuring E17 and using the most popular EFL (Enlightenment Foundation Libraries) based applications. The are several ways to create EAPP/EDJ files for example, and our point is to have them all, even if it means that the guide is a bit harder to read. It's written as a book, so I'd suggest reading it from the beginning using the printable monolithic version, which can be found at [http://get-e.org/User_Guide/English_pages/print.html](http://get-e.org/User_Guide/English_pages/print.html). We currently have the guide translated into 6 languages (and more coming soon). These are all maintained to be concurrent with the current development version in CVS.

Besides the user guide, we also have a FAQs section that has all the most common questions (and answers) - noticed some of those questions in this thread too (this FAQs section is meant to be read after the user guide of course). The real deal with the site however, is that we host themes for various E17/EFL related programs - this includes EAPP iconsets, E17 themes and both static and animated background EDJ files. In the future we're hoping to have some Evidence themes there too. The status page has the current development state "in a nutshell", so if your wondering why a certain feature doesn't exist yet, you might want to check that. Last but not least, we also have the obligatory screenshots section.

All in all, this site has just been launched around 1-2 weeks ago, so this is hopefully just the beginning. Feedback, comments, etc is welcome.

---

### Post by eMamo on 2005-05-20
hi,

im trying to compile e17 from the cvs, but when im running ./autogen.sh (for ecore)
at the end of the log i get this error:
```
checking whether ecore_evas module is to be built... yes
 is not in your $PATH. Please ensure it is.
Read the manual page for you shell as to how to extend your path.
configure: error: Cannot find
```

---

### Post by battletux on 2005-05-25
I think i'm gonna give this a go. I have a bad feeling that i'm gonna commpletely b0rk my box, but how else am i going to learn Linux? :)

*edit:* On second thoughts i'll give it a miss, i don't think i'm upto this :(

---

### Post by Kyral on 2005-05-26
It may be just because I woke up only an hour ago, or because I have like no experiance in CVS, but could you make an "E17 for complete idiots" guide? It looks great and I would love to use it. My main thing is that I don't know hwo to use CVS to get the things I need

---

### Post by smoon on 2005-06-08
Just in case anyone is interested: I created a shell script that pulls the efl/e17 sources from CVS, creates .deb packages out of that and installs them. More can be found here: [http://www.ubuntuforums.org/showpost.php?p=205028&postcount=81](http://www.ubuntuforums.org/showpost.php?p=205028&postcount=81)

---

### Post by Neo40 on 2005-06-10
Hi,

I have installed E17 but I can't use entrance. GDM is always starting. How can I use entrance? 

Thanks for your help.

---

### Post by vassalle on 2005-06-10
[QUOTE=smoon]Just in case anyone is interested: I created a shell script that pulls the efl/e17 sources from CVS, creates .deb packages out of that and installs them. More can be found here: [http://www.ubuntuforums.org/showpost.php?p=205028&postcount=81](http://www.ubuntuforums.org/showpost.php?p=205028&postcount=81)[/QUOTE]
 hi, great to know that someone created something that could make things simpler.. but how do i use it ? i tried this,

vassalle@vassalle:~/downloads$ sh e17install.sh
 Updating source from CVS-Repository
 This may take a while depending on your internet connection
 Honestly, we're grabbing something around 150 Megabytes now

** CVS: login failed
** An error occured. Exiting...

any ideas ? thanks in advance

---

### Post by smoon on 2005-06-10
[QUOTE=vassalle]hi, great to know that someone created something that could make things simpler.. but how do i use it ? i tried this,

vassalle@vassalle:~/downloads$ sh e17install.sh
 Updating source from CVS-Repository
 This may take a while depending on your internet connection
 Honestly, we're grabbing something around 150 Megabytes now

** CVS: login failed
** An error occured. Exiting...

any ideas ? thanks in advance[/QUOTE]

You need to have some packages installed: cvs, fakeroot, sudo, dpkg-buildpackage and of course a compiler. There are more dependencies, but the script will tell you if and what you're missing.

---

### Post by vassalle on 2005-06-10
[QUOTE=smoon]You need to have some packages installed: cvs, fakeroot, sudo, dpkg-buildpackage and of course a compiler. There are more dependencies, but the script will tell you if and what you're missing.[/QUOTE]
 thanks for the hint.. still apt-geting the dependencies, but its going somewhere allrite.. thanks agaiN!

---

### Post by vassalle on 2005-06-10
oh well, theres like loads of error in generating the .deb for engrave.. from here 

```
engrave.o
engrave.l:5:35: libengrave_la-engrave.h: No such file or directory
engrave.l: In function `yylex':
engrave.l:89: error: `ACCELERATE' undeclared (first use in this function)
engrave.l:89: error: (Each undeclared identifier is reported only once
engrave.l:89: error: for each function it appears in.)
engrave.l:90: error: `ACTION' undeclared (first use in this function)
.....
engrave.l:298: error: `SCRIPT' undeclared (first use in this function)
make[4]: *** [engrave.lo] Error 1
make[4]: Leaving directory `/home/vassalle/e17install/e17/libs/engrave/src/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/vassalle/e17install/e17/libs/engrave/src'
make[2]: *** [all-recursive-am] Error 2
make[2]: Leaving directory `/home/vassalle/e17install/e17/libs/engrave/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vassalle/e17install/e17/libs/engrave'
make: *** [build-stamp] Error 2
```

think im going to bed now.. anyhow, any ideas of whats going on here ? ](*,)

---

### Post by jens on 2005-06-11
Your script seems to need a "libepeg0-dev" package. Were can I find it? (or should I look for an other name?)

---

### Post by wondering_jew on 2005-06-11
using the script when it is building the deb for emotion I get an error, log says

"error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory"

libiconv.so.2 is located in /usr/local/lib

any ideas?

---

### Post by smoon on 2005-06-11
[QUOTE=vassalle]oh well, theres like loads of error in generating the .deb for engrave.. from here 

```
engrave.o
engrave.l:5:35: libengrave_la-engrave.h: No such file or directory
engrave.l: In function `yylex':
engrave.l:89: error: `ACCELERATE' undeclared (first use in this function)
engrave.l:89: error: (Each undeclared identifier is reported only once
engrave.l:89: error: for each function it appears in.)
engrave.l:90: error: `ACTION' undeclared (first use in this function)
.....
engrave.l:298: error: `SCRIPT' undeclared (first use in this function)
make[4]: *** [engrave.lo] Error 1
make[4]: Leaving directory `/home/vassalle/e17install/e17/libs/engrave/src/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/vassalle/e17install/e17/libs/engrave/src'
make[2]: *** [all-recursive-am] Error 2
make[2]: Leaving directory `/home/vassalle/e17install/e17/libs/engrave/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vassalle/e17install/e17/libs/engrave'
make: *** [build-stamp] Error 2
```

think im going to bed now.. anyhow, any ideas of whats going on here ? ](*,)[/QUOTE]

I'm unable to compile engrave either. It's some weird yacc/flex problem that I haven't figured out yet. As far is I can tell only e_utils depend on engrave, so it's not that bad that it doesn't compile. Try running e17install.sh with the -c switch to continue even though engrave fails to compile. This way you'll get elicit, engage, e, etc.

Maybe someone else here has an idea what's wrong with engrave?

---

### Post by smoon on 2005-06-11
[QUOTE=jens]Your script seems to need a "libepeg0-dev" package. Were can I find it? (or should I look for an other name?)[/QUOTE]

This package should be created by the script itself. Look if it is in $HOME/e17install/e17/libs/libepeg0-dev_0.9.0-0cvs20040808_i386.deb. If it is, install it by hand (`sudo dpkg -i ${HOME}/e17install/e17/libs/libepeg0-dev_0.9.0-0cvs20040808_i386.deb') or run the script again with the -i switch.

---

### Post by smoon on 2005-06-11
[QUOTE=wondering_jew]using the script when it is building the deb for emotion I get an error, log says

"error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory"

libiconv.so.2 is located in /usr/local/lib

any ideas?[/QUOTE]

I don't have that library on my system and emotion compiles fine. Why is yours in /usr/local/lib? Did you install it by hand? add /usr/local/lib to /etc/ld.so.conf and run ldconfig (both as root respectively with sudo). Then try building emotion again.

---

### Post by ggeneraux on 2005-06-11
I successfully installed e17, but I have a question that has to do more with the customization aspect.  I'm wondering if anyone knows how to get fonts and widgets in gtk-based programs within enlightenment to appear as they do using gnome.  In gnome they look normal for me (well integrated and nice fonts), but using an alternative window manager like e17 (prefered) or xfce4 the fonts look horrible and the widgets look very blocky.  Any idea on this are much appreciated.  Thanks!

---

### Post by lwl on 2005-06-11
I am experiencing problems while installing evas . From smoon's script i get the following :
```
** Unable to build a debian package of evas.
** Check /home/lwl/e17install/compile_logs/evas.log for details.
** An error occured. Exiting...
``` 

and then when i look into  /home/lwl/e17install/compile_logs/evas.log i see this:

```
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeQueryVersion'
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[5]: *** [evas_software_x11_test] Error 1
make[5]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src/bin'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src/bin'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/lwl/e17install/e17/libs/evas'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/lwl/e17install/e17/libs/evas'
make: *** [build-stamp] Error 2
``` 

what should i do to fix the problem ?

---

### Post by smoon on 2005-06-11
[QUOTE=ggeneraux]I successfully installed e17, but I have a question that has to do more with the customization aspect.  I'm wondering if anyone knows how to get fonts and widgets in gtk-based programs within enlightenment to appear as they do using gnome.  In gnome they look normal for me (well integrated and nice fonts), but using an alternative window manager like e17 (prefered) or xfce4 the fonts look horrible and the widgets look very blocky.  Any idea on this are much appreciated.  Thanks![/QUOTE]

Try running /usr/bin/gnome-settings-daemon in the background. I think this will do the trick.

---

### Post by smoon on 2005-06-11
[QUOTE=lwl]I am experiencing problems while installing evas . From smoon's script i get the following :
```
** Unable to build a debian package of evas.
** Check /home/lwl/e17install/compile_logs/evas.log for details.
** An error occured. Exiting...
``` 

and then when i look into  /home/lwl/e17install/compile_logs/evas.log i see this:

```
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeQueryVersion'
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[5]: *** [evas_software_x11_test] Error 1
make[5]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src/bin'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src/bin'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/lwl/e17install/e17/libs/evas'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/lwl/e17install/e17/libs/evas'
make: *** [build-stamp] Error 2
``` 

what should i do to fix the problem ?[/QUOTE]

I've created a patch that will fix this problem. The patch can be found at [http://nooms.de/misc/evas_xorg_configure.diff](http://nooms.de/misc/evas_xorg_configure.diff). You've to apply it manually: ```
cd ${HOME}/e17install/e17/libs/evas && patch -p0 < /path/to/evas_xorg_configure.diff
```

---

### Post by ggeneraux on 2005-06-11
[QUOTE=smoon]Try running /usr/bin/gnome-settings-daemon in the background. I think this will do the trick.[/QUOTE]

That did it, thanks!

---

### Post by lwl on 2005-06-11
thanks for the patch, i applied it manually but a new error appeared:
```
/usr/bin/ld: cannot find -lXxf86vm
collect2: ld returned 1 exit status
make[5]: *** [libevas.la] Error 1
make[5]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src/lib'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/lwl/e17install/e17/libs/evas'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/lwl/e17install/e17/libs/evas'
make: *** [build-stamp] Error 2
```

---

### Post by smoon on 2005-06-11
[QUOTE=lwl]thanks for the patch, i applied it manually but a new error appeared:
```
/usr/bin/ld: cannot find -lXxf86vm
collect2: ld returned 1 exit status
make[5]: *** [libevas.la] Error 1
make[5]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src/lib'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/lwl/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/lwl/e17install/e17/libs/evas'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/lwl/e17install/e17/libs/evas'
make: *** [build-stamp] Error 2
```[/QUOTE]

Oh, sorry. You need to have the packages libxxf86vm1 and libxxf86vm1-dev installed.

---

### Post by smoon on 2005-06-11
A little update: The installscript now tries to resolve all dependencies on its own. It even checks for essential packages like cvs, fakeroot, etc. and installs missing ones. The -d commandline switch is new and skips testing for essential packages.

Would be nice if someone could test this.

The script's still available at [http://nooms.de/misc/e17install.sh](http://nooms.de/misc/e17install.sh).

---

### Post by furrythugs on 2005-06-11
I'm right here too. Shouldn't evas install libevas ? I had E17 built on Gentoo a few years ago. I've never managed to build it since. This is pretty exciting as I always go down this road and get 1/2 way and bail out due to all the errors etc.

What does one do to get past this error below. 

Building .deb of ecore

** Missing dependencies, please install these packages: libevas0-dev
** An error occured. Exiting...

Thanks for making this happen folks.

---

### Post by lwl on 2005-06-11
[QUOTE=smoon]Oh, sorry. You need to have the packages libxxf86vm1 and libxxf86vm1-dev installed.[/QUOTE]

Thank you for your help mate. I installed the libraries but a new problem occurred.
```
main.o(.text+0x1e5): In function `main':
/home/lwl/e17install/e17/apps/iconbar/src/main.c:64: undefined reference to `ecore_x_window_prop_xy_set'
collect2: ld returned 1 exit status
make[3]: *** [iconbar] Error 1
make[3]: Leaving directory `/home/lwl/e17install/e17/apps/iconbar/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/lwl/e17install/e17/apps/iconbar/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lwl/e17install/e17/apps/iconbar'
make: *** [build-stamp] Error 2
``` 

i really don't know how to solve it.

---

### Post by smoon on 2005-06-11
[QUOTE=lwl]Thank you for your help mate. I installed the libraries but a new problem occurred.
```
main.o(.text+0x1e5): In function `main':
/home/lwl/e17install/e17/apps/iconbar/src/main.c:64: undefined reference to `ecore_x_window_prop_xy_set'
collect2: ld returned 1 exit status
make[3]: *** [iconbar] Error 1
make[3]: Leaving directory `/home/lwl/e17install/e17/apps/iconbar/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/lwl/e17install/e17/apps/iconbar/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lwl/e17install/e17/apps/iconbar'
make: *** [build-stamp] Error 2
``` 

i really don't know how to solve it.[/QUOTE]

This seems to be a common problem. I think iconbar's source is outdated and ecore's api has changed. I'll remove iconbar from the script ASAP since I don't think someone is working on it anymore.
To fix it at your site run e17install.sh with the -c switch to continue on errors or remove iconbar from line 30 in the script (EAPPS="iconbar ....") - you won't get iconbar this way but the script will continue and build the other applications.

---

### Post by lwl on 2005-06-12
okey, i skipped the iconbar package but something else appeared. 
```
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package
``` 
is this package needed by enlightenment to do well ?

also this ```
** Missing dependencies, please install these packages: libe-dev (>= 0.16.999.003)
** An error occured. -c switch found, proceeding...
``` 

i cannot find libe-dev in synaptic and in apt-get :
```
lwl@drumbi3nt:~$ sudo apt-get install libe-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libe-dev
```

---

### Post by lwl on 2005-06-12
i've install e17 without the apps for it ... anyone know how to start it, cause i don't see the executable?

---

### Post by smoon on 2005-06-12
Since almost everyone except me seems to have problems getting the script to work properly, I decided to create a repository for all this new e-stuff that you can use instead of the script. I'll update it every once in a while. To use it add ```
deb http://ubuntu.nooms.de/ hoary/
``` to your /etc/apt/sources.list, run ```
sudo apt-get update
``` and you'll be able to choose from the following applications to install:

enlightenment - The e17 windowmanager.
entice - An imageviewer.
engage - An OS X-like dock.
elicit - A screen zoomer/color picker.
eclair - Mediaplayer (Video and Audio).

To install the windowmanager itself you've to use the following command because it differs from e16 (in Hoary) in the version only: ```
sudo apt-get install enlightenment=0.16.999.003-0cvs20050325 enlightenment-data=0.16.999.003-0cvs20050325
```

I hope it works for you.

---

### Post by scrillamaan on 2005-06-12
[QUOTE=smoon]Since almost everyone except me seems to have problems getting the script to work properly, I decided to create a repository for all this new e-stuff that you can use instead of the script. I'll update it every once in a while. To use it add ```
deb http://ubuntu.nooms.de/ hoary/
``` to your /etc/apt/sources.list, run ```
sudo apt-get update
``` and you'll be able to choose from the following applications to install:

enlightenment - The e17 windowmanager.
entice - An imageviewer.
engage - An OS X-like dock.
elicit - A screen zoomer/color picker.
eclair - Mediaplayer (Video and Audio).

To install the windowmanager itself you've to use the following command because it differs from e16 (in Hoary) in the version only: ```
sudo apt-get install enlightenment=0.16.999.003-0cvs20050325 enlightenment-data=0.16.999.003-0cvs20050325
```

I hope it works for you.[/QUOTE]

I'm about to try this out. I'll be back with results...at some point.

---

### Post by ChinaCatJones on 2005-06-12
[QUOTE=scrillamaan]I'm about to try this out. I'll be back with results...at some point.[/QUOTE]
 scrillamaan-

Your repository works beautifully. Thanks a million.

Chris

---

### Post by luiska on 2005-06-13
Cheers!!!

Finally I get to see E17 too! Thanks for the repo, worked like a charm!

Luiska

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=smoon]

I hope it works for you.[/QUOTE]


This is awesome.

---

### Post by czynski on 2005-06-13
ok. e17 finally installed. i had been following the original guide from the warty section so i removed the /usr/share/xsessions/e17.desktop and everything else from that method. now i'm not sure what new e17.desktop file i should create to get it in my session list.

---

### Post by Juippisi on 2005-06-13
Epaolox and Smoon: Thank you soooo much!

e17 runs perfectly now, when I used smoons .debs. Before this crashed all the time. Now, I'll just read get-e's manuals and try to make this more beatiful ( [http://get-e.org/Main/Home.html](http://get-e.org/Main/Home.html) ).

---

### Post by scrillamaan on 2005-06-13
[QUOTE=ChinaCatJones]scrillamaan-

Your repository works beautifully. Thanks a million.

Chris[/QUOTE]

It's not my repository.

Please direct all thanks to smoon.

---

### Post by crane on 2005-06-13
Still no go here. I've reached dependacy hell
>  enlightenment: Depends: libe but it is not going to be installed
                 Depends: libevas0 but it is not going to be installed
                 Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed

---

### Post by lwl on 2005-06-14
e17 works just fine :) big thanks to smoon for his repository.

---

### Post by Nightwish on 2005-06-14
[QUOTE=crane]Still no go here. I've reached dependacy hell[/QUOTE]
you have to install the specific version 0.16.999... they he mentioned in the post, otherwise apt will try to install the e16 patch of hoary.

---

### Post by smoon on 2005-06-14
[QUOTE=Nightwish]you have to install the specific version 0.16.999... they he mentioned in the post, otherwise apt will try to install the e16 patch of hoary.[/QUOTE]

You can as well add the following lines to /etc/apt/preferences to make apt use version 0.16.999... instead of the one included in Hoary:
```
Package: enlightenment
Pin: version 0.16.999.*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999.*
Pin-Priority: 999
```

---

### Post by Tab on 2005-06-14
Awesome. We've been desperately in need of a working Ubuntu repository ever since the Debian ones started depending on the newer libc6.
Those debs are pretty outdated though (E is really in flux lately... ), any chance for an update sometime soon?

---

### Post by Labonte on 2005-06-14
How do i make GDM to find E17? i have tried everything now.. ;-)  but cant select E17 when i'm about to login only the ubuntu standard choices

---

### Post by smoon on 2005-06-14
[QUOTE=Tab]Awesome. We've been desperately in need of a working Ubuntu repository ever since the Debian ones started depending on the newer libc6.
Those debs are pretty outdated though (E is really in flux lately... ), any chance for an update sometime soon?[/QUOTE]

Outdated? I created them only two days ago :-? Of course I'll update them as often as possible. But I'm not able to follow the CVS changes, so you guys have to drop me a note if something changes in CVS and you want new packages.

---

### Post by cutOff on 2005-06-14
Pretty good job. Thanks a lot.

However I have a question, why should I use the repo you have mentioned instead of this other one?

```
http://www.soulmachine.net/debian/
```
Seems to have a newer version.

---

### Post by smoon on 2005-06-14
[QUOTE=cutOff]Pretty good job. Thanks a lot.

However I have a question, why should I use the repo have you mentioned instead of this other one?

```
http://www.soulmachine.net/debian/
```
Seems to have a newer version.[/QUOTE]

Newer? I don't think packages from May the 13th are newer than packages from a few mins (respectively two days) ago ;-)
Anyway, AFAIK the binaries in shadoi's Debian packages are compiled against libs from Debian Sid thus they don't install properly on Hoary (at least for me they do not).

---

### Post by jhk on 2005-06-14
[QUOTE=ggeneraux]I successfully installed e17, but I have a question that has to do more with the customization aspect.  I'm wondering if anyone knows how to get fonts and widgets in gtk-based programs within enlightenment to appear as they do using gnome.  In gnome they look normal for me (well integrated and nice fonts), but using an alternative window manager like e17 (prefered) or xfce4 the fonts look horrible and the widgets look very blocky.  Any idea on this are much appreciated.  Thanks![/QUOTE]
 Try running gnome-settings-daemon.  This should reload all your gtk2 theme settings.

---

### Post by Tab on 2005-06-14
[QUOTE=smoon]Outdated? I created them only two days ago :-?[/QUOTE]

But the deb is marked enlightenment_0.16.999.003-0cvs20050325 ... it seems to be from March. The current version is 0.16.999.008 if I'm not mistaken. |: ?

---

### Post by smoon on 2005-06-15
[QUOTE=Tab]But the deb is marked enlightenment_0.16.999.003-0cvs20050325 ... it seems to be from March. The current version is 0.16.999.008 if I'm not mistaken. |: ?[/QUOTE]

Don't get irritated by the version numbers, even though the tell you e is from March the 25th it's not true. I've just overseen that and it will be corrected the next time I update the packages (at least if it's not too much work ;)). The window manager's source I compiled the current packages from is from yesterday and the packages included the newest and coolest features e has to offer atm. All other packages are from three days ago even if the version numbers tell you anything other (didn't checked it though).

---

### Post by cutOff on 2005-06-15
Well, it works fine. 

Even so I had to create a file called [COLOR=Blue]enlightenment.desktop[/COLOR] in /usr/share/xsessions/ with this content.

```
[Desktop Entry]
Encoding=UTF-8
Name=E17
Exec=/usr/bin/enlightenment
Icon=
Type=Application
```

---

### Post by christooss on 2005-06-15
[QUOTE=Labonte]How do i make GDM to find E17? i have tried everything now.. ;-)  but cant select E17 when i'm about to login only the ubuntu standard choices[/QUOTE]
 How can this be done?

---

### Post by AndyAWS on 2005-06-15
My 'Configuration' menu (and most of the others) are empty...is this normal?

Also I just installed Enlightenment last night from smoon's repo...and this morning it wanted to be upgraded, to the same version I installed...???

Is this an effect of locking the version or was there actually an upgrade since last night?

Also installed entice, engage, elicit and eclair from smoon's repo...they don't show up in the menu...do I have to manually edit the menu?

Last question...should I install 'e_utils' and where do I find it?

I know, I know...I should just go to get-e.org and read..right?

---

### Post by dazzla on 2005-06-15
I've made the changes to /etc/apt/preferences and added the repository, but i still get the following dependancy errors:

```
The following packages have unmet dependencies:
  enlightenment: Depends: libe but it is not going to be installed
                 Depends: libevas0 but it is not going to be installed
                 Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
```

Any  ideas what is wrong, this is pretty much a new installation of Hoary.

Aditionally, when i run your e17install.sh script it gets to the build of edb and errors with: 
```
** Unable to build a debian package of edb.
** Check /home/dazzla/e17install/compile_logs/edb.log for details.
** An error occured. Exiting...
```

Checking in the speficied log i get this:

```
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such
 file or directory
dpkg-buildpackage: unable to determine source package
```
Any ideas at all?

---

### Post by smoon on 2005-06-15
[QUOTE=christooss]How can this be done?[/QUOTE]

Look at [cutOff's post](http://www.ubuntuforums.org/showpost.php?p=213881&postcount=62). This should work.

---

### Post by smoon on 2005-06-15
[QUOTE=AndyAWS]My 'Configuration' menu (and most of the others) are empty...is this normal?

Also I just installed Enlightenment last night from smoon's repo...and this morning it wanted to be upgraded, to the same version I installed...???

Is this an effect of locking the version or was there actually an upgrade since last night?

Also installed entice, engage, elicit and eclair from smoon's repo...they don't show up in the menu...do I have to manually edit the menu?

Last question...should I install 'e_utils' and where do I find it?

I know, I know...I should just go to get-e.org and read..right?[/QUOTE]

For the configuration-menu to fill up you've to install the package eutils from my repository since it contains the tools used to configure e17. It contains entangle (menu-editor), emblem (a gui-tool to set the background), exige (run-dialog), e17setroot (cli tool to set the background) and e_util_eapp_edit to edit .eapp files.

Actually there was an update last night. It's correct that the version number didn't change, that's my fault - It's my first repository and I've to figure some things out before it's perfect ;-)

The other apps you installed show not up in the menus by default. Go, read get-e.org to figure out how to add them :-P


*Edit*

Just fixed a typo...

---

### Post by smoon on 2005-06-15
[QUOTE=dazzla]I've made the changes to /etc/apt/preferences and added the repository, but i still get the following dependancy errors:

```
The following packages have unmet dependencies:
  enlightenment: Depends: libe but it is not going to be installed
                 Depends: libevas0 but it is not going to be installed
                 Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
```

Any  ideas what is wrong, this is pretty much a new installation of Hoary.

Aditionally, when i run your e17install.sh script it gets to the build of edb and errors with: 
```
** Unable to build a debian package of edb.
** Check /home/dazzla/e17install/compile_logs/edb.log for details.
** An error occured. Exiting...
```

Checking in the speficied log i get this:

```
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such
 file or directory
dpkg-buildpackage: unable to determine source package
```
Any ideas at all?[/QUOTE]

Don't use the script, the repository should work fine. Have you done an `sudo apt-get update' before running `sudo apt-get install enlightenment'? I've no idea what else could be wrong.

Somebody has an idea how to make apt more verbose?

---

### Post by headswim on 2005-06-15
I just installed Ubuntu 2 days ago, and was reading this forum to get e17 installed.  I have tried the newest version of the script, which says it is unable to build a debian package of edb, and gives me the following output in the edb.log file:

  dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or     directory
dpkg-buildpackage: unable to determine source package

When I try using the repository, after editing the sources.list and preferences files, I get the following:

  The following packages have unmet dependencies:
  enlightenment: Depends: libevas0 but it is not going to be installed
                 Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
E: Broken packages

I did run apt-get update before trying to do the install, and have tried both using sudo, and a root terminal.  If anyone has any advice or ideas, I would appreciate it.

-Jones

---

### Post by Tab on 2005-06-15
Ah, tried it and it works perfectly over here. You, Smoon, are a hero.

I follow E17 development pretty closely, so I'll let you know about major changes.

---

### Post by super on 2005-06-16
i am having problems getting the apps to work. e17 and e_data install perfectly from the repos but i get the following error when i try to install entice, eutils, libengrave0, etc . . . 

[FONT=Courier New]The following packages have unmet dependencies:
  entice: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages[/FONT]

any ideas?

---

### Post by Iuliux on 2005-06-16
how much space e17 takes? --with the aditional packager of course!

---

### Post by headswim on 2005-06-16
Finally got e17 working.  Not sure why I was getting those errors, but it's going now.  I had to reinstall Ubuntu this morning, as I screwed a few things up trying to play with the kernel.  No biggie since it's such a fast install.  First thing I did after the reinstall was to try and get e17 going.  Now it's working beautifully.  Thanks to Smoon for the repo.

---

### Post by clb137 on 2005-06-16
[QUOTE=christooss]How can this be done?[/QUOTE]


try this and you will have ne problems starting E17 (as long as you have installed all)

Create a file called e17.desktop in /usr/share/xsessions/
Add the following lines to this file:

Code:

[Desktop Entry]
Encoding=UTF-8
Name=e17
Comment= 
Exec=enlightenment 
Icon= 
Type=Application

good luck

clinton


PS Iam running it  now

---

### Post by Iuliux on 2005-06-16
how do i star it if i am using kubuntu (kdm)?

//later I made it
now  I want to remove it #sudo apt-get --purge enlightenment does not work....how do I delete it?

---

### Post by AndyAWS on 2005-06-17
smoon,

Just wanted to say thanks for setting up the repo, and thank you for all of the help and information.

Everything seems to be working fine here...at least within the bounds of the known bugs and development issues in e17... ;-)

---

### Post by super on 2005-06-18
i finally decided to give up on the cvs install and go with the debs in the smoon repos, but i am unable to compile the background files. i seem to be missing Esetroot and edje_cc. any ideas? btw i installed the eutils package and i do have emblem.

---

### Post by super on 2005-06-18
ok i got the wallpaper thing working by installing edjce-bin and eterm. my final problem is with engage in module mode. it doesn't seem to remember any of the settings. everytime e17 starts, engage is a miniscule dot at the bottom of the screen.  i have to open something and then turn on edit mode and resize it. otherwise it is too small to work with.

---

### Post by mrf on 2005-06-25
Has anyone successfully installed with Smoon's script on amd64?

I'm getting this error when compiling evas, which doesn't look promising :

```

 x86_64-linux-gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I. -I../../../../src/lib -I../../../../src/lib/include -I/usr/include/freetype2 -Wall -g -I/usr/include/freetype2 -include /usr/include/png.h -include /usr/include/freetype2/freetype/internal/ftobjs.h -O3 -mcpu=pentiumpro -MT evas_polygon_main.lo -MD -MP -MF .deps/evas_polygon_main.Tpo -c evas_polygon_main.c  -fPIC -DPIC -o .libs/evas_polygon_main.o
evas_polygon_main.c: In function `polygon_point_sorter':
evas_polygon_main.c:64: error: unrecognizable insn:
(insn:HI 58 57 29 0 0x2a95fb2c60 (set (reg:SI 58)
        (plus:SI (mult:SI (reg:SI 58)
                (const_int 2 [0x2]))
            (const_int -1 [0xffffffffffffffff]))) -1 (insn_list 57 (nil))
    (nil))
evas_polygon_main.c:64: internal compiler error: in extract_insn, at recog.c:2175
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.

```

---

### Post by lwl on 2005-06-26
after the latest upgrade, when i try to start e17 i get the followin output:

```
Xlib : extension "XpExtension" missing on display ":0.0".
Xlib : extension "XINERAMA" missing on display ":0.0".
E17 INIT: XINERAMA CHOSEN: [0], 1024x768+0+0
Xlib : extension "XpExtension" missing on display ":0.0".
Xlib : extension "XpExtension" missing on display ":0.0".
Xlib : extension "XpExtension" missing on display ":0.0". 
``` 

if someone knows tell me how to fix this :)

---

### Post by dolny on 2005-06-27
I'm going to try the repository but I wanted to ask why do I always get this error when compiling many apps:

```
engines/gl_x11/.libs/libevas_engine_gl_x11.a -Wl,--no-whole-archive  /usr/lib/libfreetype.so -lpng -lm -L/usr/lib /usr/lib/libeet.so /usr/lib/libjpeg.so /usr/lib/libedb.so -lz -L/usr/X11R6/lib -lX11 -lXext -lXxf86vm -lGL -lGLU -lpthread  -mcpu=pentiumpro -Wl,-soname -Wl,libevas.so.1 -o .libs/libevas.so.1.0.0
**/usr/bin/ld: cannot find -lXxf86vm**
collect2: ld returned 1 exit status
make[5]: *** [libevas.la] B&#322;&#261;d 1
make[5]: Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas/src/lib'
make[4]: *** [all-recursive] B&#322;&#261;d 1
make[4]: Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas/src/lib'
make[3]: *** [all-recursive] B&#322;&#261;d 1
make[3]: Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas'
make[1]: *** [all] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas'
make: *** [build-stamp] B&#322;&#261;d 2

```

This is from 
```

 + Building and installing libraries.
   .debs for edb already built.
   .debs for eet already built.
   .debs for imlib2 already built.
   .debs for imlib2_loaders already built.
   Building .deb of evas

** Unable to build a debian package of evas.
** Check /home/dolny/e17install/compile_logs/evas.log for details.
** An error occured. Exiting...
```

:( How do I delete the installation stuff now? Cause I want to use the debs.

I'm installing libxxf86vm-dev to see if it works :/

---

### Post by smoon on 2005-06-27
> **dolny]I'm going to try the repository but I wanted to ask why do I always get this error when compiling many apps:

```
engines/gl_x11/.libs/libevas_engine_gl_x11.a -Wl,--no-whole-archive  /usr/lib/libfreetype.so -lpng -lm -L/usr/lib /usr/lib/libeet.so /usr/lib/libjpeg.so /usr/lib/libedb.so -lz -L/usr/X11R6/lib -lX11 -lXext -lXxf86vm -lGL -lGLU -lpthread  -mcpu=pentiumpro -Wl,-soname -Wl,libevas.so.1 -o .libs/libevas.so.1.0.0
**/usr/bin/ld: cannot find -lXxf86vm**
collect2: ld returned 1 exit status
make[5]: *** [libevas.la] B&#322 said:**
> : Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas/src/lib'
make[4]: *** [all-recursive] B&#322;&#261;d 1
make[4]: Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas/src/lib'
make[3]: *** [all-recursive] B&#322;&#261;d 1
make[3]: Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas'
make[1]: *** [all] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/dolny/e17install/e17/libs/evas'
make: *** [build-stamp] B&#322;&#261;d 2

```

This is from 
```

 + Building and installing libraries.
   .debs for edb already built.
   .debs for eet already built.
   .debs for imlib2 already built.
   .debs for imlib2_loaders already built.
   Building .deb of evas

** Unable to build a debian package of evas.
** Check /home/dolny/e17install/compile_logs/evas.log for details.
** An error occured. Exiting...
```

:( How do I delete the installation stuff now? Cause I want to use the debs.

I'm installing libxxf86vm-dev to see if it works :/

This is an already known problem with evas and XOrg. To fix it apply the patch found at [http://nooms.de/misc/evas_xorg_configure.diff](http://nooms.de/misc/evas_xorg_configure.diff) (`cd ${HOME}/e17install/e17/libs/evas && patch -p0 < /path/to/evas_xorg_configure.diff').

To use the repository just delete the e17install directory in your $HOME dir.

---

### Post by dolny on 2005-06-27
Yeah I applied it, but I  had to install the dev package I mentioned. I get another error:
```

Installing .debs for e
   Building .deb of e_utils

** Unable to build a debian package of e_utils.
** Check /home/dolny/e17install/compile_logs/e_utils.log for details.
** An error occured. Exiting...

```

LOG:

```

found eof where expected first heading at /usr/lib/dpkg/parsechangelog/debian line 136.
dpkg-buildpackage: unable to determine source package

```
       
:( I'll use the repository if you don't know how to fix this error :/

---

### Post by dolny on 2005-06-27
OK I'm going to use the repository.

---

### Post by AndyAWS on 2005-06-27
After the big update from smoon's repo I've lost everything...

I don't mean just the things I added to the menu, I mean everything that was there by default before...all menus are empty, and the bottom launch bar that used to have the terminal, firefox, gimp..etc, is also empty...eutils also updated but the configuration menu is now empty...the e17 themes I had still show up but that's about it.

Is this just a normal result of the latest development versions of the e stuff, or is it just something with my configuration?

---

### Post by dolny on 2005-06-27
I downloaded the enlightement and enlightement-data + one additional theme packages but the new entry didn't show up in the GDM, even after rebooting. I added it manually but instead of Enlightement, GNOME launched. Not to mention that I use kubuntu, and I deleted the ubuntu-desktop package. I don't know why but E17 doesn't work for me (I installed it through Synaptic).

---

### Post by Tim Shark on 2005-06-28
I thought I would post a bug that may solve problems for those of you who use entrance to log into E17 - but keep entering gnome. If I choose E17 for the session BEFORE I type in user and password I will enter gnome. If I type username and password and THEN choose E17 from the menu in entrance and then press enter - I will get into E17. Anyone else?

---

### Post by smoon on 2005-06-28
[QUOTE=AndyAWS]After the big update from smoon's repo I've lost everything...

I don't mean just the things I added to the menu, I mean everything that was there by default before...all menus are empty, and the bottom launch bar that used to have the terminal, firefox, gimp..etc, is also empty...eutils also updated but the configuration menu is now empty...the e17 themes I had still show up but that's about it.

Is this just a normal result of the latest development versions of the e stuff, or is it just something with my configuration?[/QUOTE]

Since e17 is in an early stage of development many things may change over time (configuration, etc.) and thus it is totally normal and may happen more often. I just removed my ${HOME}/.e directory and everything, except the entries in the configuration menu, are back to normal.

Btw. does anyone of you use e17 as its default window manager? I for myself don't because I think it's not yet mature enough.

---

### Post by smoon on 2005-06-28
[QUOTE=dolny]I downloaded the enlightement and enlightement-data + one additional theme packages but the new entry didn't show up in the GDM, even after rebooting. I added it manually but instead of Enlightement, GNOME launched. Not to mention that I use kubuntu, and I deleted the ubuntu-desktop package. I don't know why but E17 doesn't work for me (I installed it through Synaptic).[/QUOTE]

Check out [this post from clb137](http://ubuntuforums.org/showpost.php?p=216038&postcount=74). He describes how to add e17 to GDM - I never tried it myself but it should work just fine.

---

### Post by smoon on 2005-06-28
[QUOTE=lwl]after the latest upgrade, when i try to start e17 i get the followin output:

```
Xlib : extension "XpExtension" missing on display ":0.0".
Xlib : extension "XINERAMA" missing on display ":0.0".
E17 INIT: XINERAMA CHOSEN: [0], 1024x768+0+0
Xlib : extension "XpExtension" missing on display ":0.0".
Xlib : extension "XpExtension" missing on display ":0.0".
Xlib : extension "XpExtension" missing on display ":0.0". 
``` 

if someone knows tell me how to fix this :)[/QUOTE]

I get the same messages, but I think there's no need to worry. Or stopped enlightenment working for you?

---

### Post by christooss on 2005-06-28
hm Im having trubles installing enlightenment

I used sudo apt-get install enlightenment=0.16.999.003-0cvs20050325 enlightenment-data=0.16.999.003-0cvs20050325
and I get an error

---

### Post by AndyAWS on 2005-06-28
[QUOTE=smoon]Since e17 is in an early stage of development many things may change over time (configuration, etc.) and thus it is totally normal and may happen more often. I just removed my ${HOME}/.e directory and everything, except the entries in the configuration menu, are back to normal.[/QUOTE]


Ok, thanks, I'll try that.

I'll also try reinstalling eutils after, that might get the configuration menu back, although it was only a couple items and think only one worked.

---

### Post by christooss on 2005-06-28
Ok now I handeled my problem but...

It sux I have to coment all repositories in sources.list. Why beacause apt-get downloads universe packages.

---

### Post by xalphas on 2005-06-28
Force the package you want from synaptic or use pinning.

---

### Post by lwl on 2005-06-28
[QUOTE=smoon]I get the same messages, but I think there's no need to worry. Or stopped enlightenment working for you?[/QUOTE]

enlightenment just did not start up, so i removed the packages via apt-get ... removed my ~/.e dir and /.ecore dir and installed the updated enlightenment packages and everything works just fine now ;)

---

### Post by smoon on 2005-06-29
On request I created a new package called emodules which contains the following additional modules for e17:

flame - Displays an animated flame on the bottom of you screen.
monitor - A system monitor for monitoring CPU- and Network-Load.
notes - Put sticky notes on your desktop.
snow - This one shows christmas trees and falling snow.

To use one of them do the usual `sudo apt-get update && sudo apt-get install emodules' followed by `enlightenment_remote -module-load <module name>'.

For those of you who are still unaware, the repository is ```
deb http://ubuntu.nooms.de/ hoary/
```

---

### Post by sipstar on 2005-07-02
the repo was great! im now running e17! thanks smoon!  :smile:

---

### Post by XDevHald on 2005-07-02
Interesting, I placed the mirror, but got this error..

> 
Summary:
 libimlib2(1 bug), libimlib2-dev(1 bug)
Are you sure you want to install/upgrade the above packages? [Y/n/?/...]
 

Not an issue to me because this can be fixed, but did anyone else get this error when trying to -f the upgrade?

---

### Post by jayps on 2005-07-03
Hi i'm new here... I tried installing E17 from smoon's repos and followed the instructions but after I downloaded the packages and installed them, I tried running them and it won't work. I'm getting a Segmentation Fault error message. What does that mean and how do I fix it? BTW I'm using hoary

---

### Post by Tamir on 2005-07-07
I have the same problem on **amd64** while compiling evas :

```
evas_polygon_main.c: In function `polygon_point_sorter':
evas_polygon_main.c:64: error: unrecognizable insn:
(insn:HI 58 57 29 0 0x2aaaab507c60 (set (reg:SI 58)
        (plus:SI (mult:SI (reg:SI 58)
                (const_int 2 [0x2]))
            (const_int -1 [0xffffffffffffffff]))) -1 (insn_list 57 (nil))
    (nil))
evas_polygon_main.c:64: internal compiler error: in extract_insn, at recog.c:2175
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[6]: *** [evas_polygon_main.lo] Error 1
make[6]: Leaving directory `/root/e17install/e17/libs/evas/src/lib/engines/common'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/root/e17install/e17/libs/evas/src/lib/engines'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/root/e17install/e17/libs/evas/src/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/e17install/e17/libs/evas'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/e17install/e17/libs/evas'
make: *** [build-stamp] Error 2
```

I made many e17 debs of amd64, and I want to continue and relese it  :razz:

---

### Post by smoon on 2005-07-07
[QUOTE=Tamir]I have the same problem on **amd64** while compiling evas :

```
evas_polygon_main.c: In function `polygon_point_sorter':
evas_polygon_main.c:64: error: unrecognizable insn:
(insn:HI 58 57 29 0 0x2aaaab507c60 (set (reg:SI 58)
        (plus:SI (mult:SI (reg:SI 58)
                (const_int 2 [0x2]))
            (const_int -1 [0xffffffffffffffff]))) -1 (insn_list 57 (nil))
    (nil))
evas_polygon_main.c:64: internal compiler error: in extract_insn, at recog.c:2175
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[6]: *** [evas_polygon_main.lo] Error 1
make[6]: Leaving directory `/root/e17install/e17/libs/evas/src/lib/engines/common'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/root/e17install/e17/libs/evas/src/lib/engines'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/root/e17install/e17/libs/evas/src/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/e17install/e17/libs/evas'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/e17install/e17/libs/evas'
make: *** [build-stamp] Error 2
```

I made many e17 debs of amd64, and I want to continue and relese it  :razz:[/QUOTE]

Try removing the "-mcpu=pentiumpro" string from the line "        CFLAGS += -O3 -mcpu=pentiumpro" in evas/debian/rules. If this does not fix your problem I'll need a bit more output. Best would be to post the whole compile log to [http://nopaste.biz/](http://nopaste.biz/) to not flood the forum.


*Edit*
On a sidenote: There's no need to do the package building stuff as root. When root privileges are required the scripts uses sudo. ;-)

---

### Post by Tamir on 2005-07-07
It helped  :-P !

Guess what? I have another problem  :-| :

```
/usr/bin/ld: /usr/lib/libGL.a(glapi.o): relocation R_X86_64_32 can not be used when making a shared object; recompile with -fPIC
/usr/lib/libGL.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[5]: *** [libevas.la] Error 1
make[5]: Leaving directory `/root/e17install/e17/libs/evas/src/lib'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/root/e17install/e17/libs/evas/src/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/e17install/e17/libs/evas'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/e17install/e17/libs/evas'
make: *** [build-stamp] Error 2
```

and the whole file almost:
[http://nopaste.biz/?2128](http://nopaste.biz/?2128)

I tried the -fPIC, didn't work.
Thank you very much.

---

### Post by smoon on 2005-07-07
> **Tamir]It helped  :-P !

Guess what? I have another problem  :-| :

```
/usr/bin/ld: /usr/lib/libGL.a(glapi.o): relocation R_X86_64_32 can not be used when making a shared object said:**
> : *** [libevas.la] Error 1
make[5]: Leaving directory `/root/e17install/e17/libs/evas/src/lib'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/root/e17install/e17/libs/evas/src/lib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/e17install/e17/libs/evas/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/e17install/e17/libs/evas'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/e17install/e17/libs/evas'
make: *** [build-stamp] Error 2
```

and the whole file almost:
[http://nopaste.biz/?2128](http://nopaste.biz/?2128)

I tried the -fPIC, didn't work.
Thank you very much.

Check if /usr/lib/libGL.so is a symbolic link to /usr/lib/libGL.so.1.2 If so, check if /usr/lib/libGL.so.1.2 exists. If it doesn't do the following: `sudo ( cd /usr/lib && ln -s libGL.so.1 libGL.so.1.2 )' and try again.

---

### Post by tommy04 on 2005-07-07
When I start E17, I just get a white screen. All I can do is CTRL+ALT+Backspace. Any ideas?

---

### Post by vrln on 2005-07-09
Sounds like things are seriously broken - try reinstalling everything related to E17, including the EFL libraries. Then delete your E17 config files (of course backup things if you have something imporant in those directories first) and try again.

At least things haven't been broken in CVS that badly for a very long time, so it's very likely just a broken installation.

---

### Post by Tamir on 2005-07-10
[QUOTE=smoon]Check if /usr/lib/libGL.so is a symbolic link to /usr/lib/libGL.so.1.2 If so, check if /usr/lib/libGL.so.1.2 exists. If it doesn't do the following: `sudo ( cd /usr/lib && ln -s libGL.so.1 libGL.so.1.2 )' and try again.[/QUOTE]

I don't have those files at all.
not in : /usr/lib. not in /usr/lib32 and not in /usr/lib64.

 :-|

[COLOR=DarkRed]Edit:[/COLOR]

I found this file with : whereis

and did what you said. It WORKED!.  \\:D/

---

### Post by buildid on 2005-07-10
impressed look good , fast , with video converting it goes 20 frames faster .

i wish i could use my Kmenu or intregrate it , then i would switch from kde to e 17

---

### Post by smoon on 2005-07-10
[QUOTE=Tamir]I don't have those files at all.
not in : /usr/lib. not in /usr/lib32 and not in /usr/lib64.

 :-|

[COLOR=DarkRed]Edit:[/COLOR]

I found this file with : whereis

and did what you said. It WORKED!.  \\:D/[/QUOTE]

Oh, nice. So we're going to get 64Bit packages soon? :-)

---

### Post by Tamir on 2005-07-10
[QUOTE=smoon]Oh, nice. So we're going to get 64Bit packages soon? :-)[/QUOTE]

Yes we are  :smile:, But there are some things that I can't solve  ](*,) .
I need your help for making these debs as fast as I can. this post will be destroyed if I will send all of my problems here.

Sorry for my English  :-| .
By the way, are you amd64 user too?

---

### Post by Tamir on 2005-07-11
OK, I made everything but : 

1. e_modules 
2. examine 
3. eclair 
4. entrance

I searched I think all over the internet, and I can't deb it right now - **e_modules**.
How did you make this package smoon? it gives me :

```
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package
``` 

But when I do :
```
./configure; make; make install
``` 
there is not problem...

---

### Post by smoon on 2005-07-11
[QUOTE=Tamir]OK, I made everything but : 

1. e_modules 
2. examine 
3. eclair 
4. entrance

I searched I think all over the internet, and I can't deb it right now - **e_modules**.
How did you make this package smoon? it gives me :

```
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package
``` 

But when I do :
```
./configure; make; make install
``` 
there is not problem...[/QUOTE]

I've problems with dpkg-parsechangelog too. It complains every now and then about the changelogs, but I haven't figured out what's wrong with it. e17install.sh should create a simple changelog if none exists, but that seems to fail as well sometimes... I'll give you the changelogs for these packages later today since I've no time to do it now and have to go now.

---

### Post by Tamir on 2005-07-11
No problem  :-P thanks very much, but how did you get these changlogs?

---

### Post by smoon on 2005-07-11
[QUOTE=Tamir]No problem  :-P thanks very much, but how did you get these changlogs?[/QUOTE]

I created them by hand. But now that I read your post again, I realized that the packages eclair and e_modules didn't have the debian/ directory at all, so I created them:
[http://nooms.de/misc/debian-eclair.tar.bz2](http://nooms.de/misc/debian-eclair.tar.bz2)
[http://nooms.de/misc/debian-emodules.tar.bz2](http://nooms.de/misc/debian-emodules.tar.bz2)

Extract them to the appropriate directories and try again:
```
cd /path/to/e17install/e17/apps/eclair && tar xvfj /path/to/debian-eclair.tar.bz2
cd /path/to/e17install/e17/apps/e_modules && tar xvfj /path/to/debian-emodules.tar.bz2
```

As for entrance and examine I've no idea what the problem could be. Let's just try to get eclair and emodules to compile.

---

### Post by Flane on 2005-07-12
Thanks for the help with eterm, but now i've got a different problem.

I've installed xterm and apt-get install xterm tells me xterm is already installed.
But when i log in to enlightenment and try starting xterm i get the errormessage that the command xterm is not found!

Any suggestions what I'm doing wrong?

Thanks a lot
Flane

---

### Post by Tamir on 2005-07-12
Try from console (another one - gnome-terminal, Eterm, Aterm...), and tell us what's happenning.
if it doesn't work, try:
```
apt-get --reinstall install xterm
```

 ;-)

---

### Post by Tamir on 2005-07-12
OK, I have the last problem (I belive and hope  :-| ), on the last package (examine).
However, when I do **make \ dpkg-buildpackage**, I get this:
```
make  all-recursive
make[1]: Entering directory `/root/e17install/e17/apps/examine'
Making all in src
make[2]: Entering directory `/root/e17install/e17/apps/examine/src'
/bin/sh ../libtool --mode=link x86_64-linux-gcc  -g -O2   -o examine  examine-examine_client.o examine-ecore_config_client.o examine-examine.o -L/usr/lib -lewl -L/usr/lib -ledje -L/usr/lib -lecore -lecore_job -lecore_x -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_fb -lecore_config -lecore_file -L/usr/lib -leet -lz -ljpeg -lm -L/usr/local/lib -ledb -lz -L/usr/lib -levas -lm 
x86_64-linux-gcc -g -O2 -o examine examine-examine_client.o examine-ecore_config_client.o examine-examine.o  -L/usr/lib /usr/lib/libewl.so /usr/lib/libedje.so /usr/lib/libecore.so /usr/lib/libecore_job.so /usr/lib/libecore_x.so /usr/lib/libecore_evas.so /usr/lib/libecore_con.so /usr/lib/libecore_ipc.so /usr/lib/libecore_txt.so /usr/lib/libecore_fb.so /usr/lib/libecore_config.so /usr/lib/libecore_file.so /usr/lib/libeet.so /usr/lib/libjpeg.so -L/usr/local/lib /usr/lib/libedb.so -lz /usr/lib/libevas.so -lm
examine-examine_client.o(.text+0xbf3): In function `examine_client_get_val_cb':
/root/e17install/e17/apps/examine/src/examine_client.c:523: undefined reference to `ewl_entry_text_set'
examine-examine_client.o(.text+0x96b): In function `examine_client_revert':
/root/e17install/e17/apps/examine/src/examine_client.c:381: undefined reference to `ewl_entry_text_set'
collect2: ld returned 1 exit status
make[2]: *** [examine] Error 1
make[2]: Leaving directory `/root/e17install/e17/apps/examine/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/e17install/e17/apps/examine'

make: *** [all] Error 2
```
I have all the depencies for this package, I didn't see something 
wrong in **debian/control** or **debian/rules**.

[COLOR=Red]Solved![/COLOR]  \\:D/ 
Now I made all of E17 debs for amd64!

---

### Post by smoon on 2005-07-12
[QUOTE=Tamir]OK, I have the last problem (I belive and hope  :-| ), on the last package (examine).
However, when I do **make \ dpkg-buildpackage**, I get this:
```
make  all-recursive
make[1]: Entering directory `/root/e17install/e17/apps/examine'
Making all in src
make[2]: Entering directory `/root/e17install/e17/apps/examine/src'
/bin/sh ../libtool --mode=link x86_64-linux-gcc  -g -O2   -o examine  examine-examine_client.o examine-ecore_config_client.o examine-examine.o -L/usr/lib -lewl -L/usr/lib -ledje -L/usr/lib -lecore -lecore_job -lecore_x -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_fb -lecore_config -lecore_file -L/usr/lib -leet -lz -ljpeg -lm -L/usr/local/lib -ledb -lz -L/usr/lib -levas -lm 
x86_64-linux-gcc -g -O2 -o examine examine-examine_client.o examine-ecore_config_client.o examine-examine.o  -L/usr/lib /usr/lib/libewl.so /usr/lib/libedje.so /usr/lib/libecore.so /usr/lib/libecore_job.so /usr/lib/libecore_x.so /usr/lib/libecore_evas.so /usr/lib/libecore_con.so /usr/lib/libecore_ipc.so /usr/lib/libecore_txt.so /usr/lib/libecore_fb.so /usr/lib/libecore_config.so /usr/lib/libecore_file.so /usr/lib/libeet.so /usr/lib/libjpeg.so -L/usr/local/lib /usr/lib/libedb.so -lz /usr/lib/libevas.so -lm
examine-examine_client.o(.text+0xbf3): In function `examine_client_get_val_cb':
/root/e17install/e17/apps/examine/src/examine_client.c:523: undefined reference to `ewl_entry_text_set'
examine-examine_client.o(.text+0x96b): In function `examine_client_revert':
/root/e17install/e17/apps/examine/src/examine_client.c:381: undefined reference to `ewl_entry_text_set'
collect2: ld returned 1 exit status
make[2]: *** [examine] Error 1
make[2]: Leaving directory `/root/e17install/e17/apps/examine/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/e17install/e17/apps/examine'

make: *** [all] Error 2
```
I have all the depencies for this package, I didn't see something 
wrong in **debian/control** or **debian/rules**.

[COLOR=Red]Solved![/COLOR]  \\:D/ 
Now I made all of E17 debs for amd64![/QUOTE]


Great! :-D I'll send you a PM with instructions for uploading the debs.

---

### Post by Tamir on 2005-07-12
That's wonderful  :grin: .
Do you care if I will host these packages + your packages (i386) on my ftp too?
I just always wanted to have an apt repository of my own, and now that I understood how to make the debian dir myselfly, 
I will make many another packages.

---

### Post by smoon on 2005-07-12
[QUOTE=Tamir]That's wonderful  :grin: .
Do you care if I will host these packages + your packages (i386) on my ftp too?
I just always wanted to have an apt repository of my own, and now that I understood how to make the debian dir myselfly, 
I will make many another packages.[/QUOTE]

Would be nice if you could host my packages as well :) I'll keep my repository up, but it would be nice if you could my host packages at your site as well. I'll message you whenever I do an update so that you can keep your ftp in sync. If you get problems with your bandwidth or anything just let me know...

---

### Post by Tamir on 2005-07-12
yeah, I wanted to host your packages too as a "mirror".
Look, actualy, I don't have a host, I am looking for one.

source forge denied me - don't know why.
and I am trying berliOS.

What are you doing an update for?
And where do you host youe packages? a free host or private one?

---

### Post by smoon on 2005-07-12
[QUOTE=Tamir]yeah, I wanted to host your packages too as a "mirror".
Look, actualy, I don't have a host, I am looking for one.

source forge denied me - don't know why.
and I am trying berliOS.

What are you doing an update for?
And where do you host youe packages? a free host or private one?[/QUOTE]

I've rent myself a server that I've to pay for. I don't think sourceforge is accepting registrations for anything that you don't do the programming for, that may be that cause that they don't accepted you. If you want you can get an account on my server so that you can update the repository whenever you want without my help - just tell me and I'll create you one (but let's do this via PN then ;))

---

### Post by darkmatter on 2005-07-12
Ok. I did some configuring of dr 17 and enabled loading of the gnome-settings daemon in the background, but was wondering if there is a way to have it load a theme by default. Every time I start E, I have to manually load a theme to skin the gtk+ apps.

Still being new to the whole GNOME thing, I could use some advice.

---

### Post by Tamir on 2005-07-13
[QUOTE=darkmatter]Ok. I did some configuring of dr 17 and enabled loading of the gnome-settings daemon in the background, but was wondering if there is a way to have it load a theme by default. Every time I start E, I have to manually load a theme to skin the gtk+ apps.

Still being new to the whole GNOME thing, I could use some advice.[/QUOTE]
Yes there is a way, Install:
```
apt-get install gtk-theme-switch
``` 
gtk-theme-switch2 is for GTK+

WIth this graphical user interface, you can change themes without gnome  ;-)

---

### Post by Flane on 2005-07-13
[QUOTE=Tamir]Try from console (another one - gnome-terminal, Eterm, Aterm...), and tell us what's happenning.
if it doesn't work, try:
```
apt-get --reinstall install xterm
```
[/QUOTE]

Hi Tamir and all the others,

I installed gnome-terminal and it worked. In gnome-terminal xterm doesn't work (command not found), but when i try sudo xterm everything works fine.

Also which xterm doesn't return anything, whereas sudo which xterm returns the correct path.

So what I'm doing wrong (sorry I'm quite new to linux)

But I've got also another problem:
when I'm trying to load engage via
```
enlightenment-remote -load-module engage
``` 
it returns an error in module.so with e_apps_windows_name_not_found (i didn't remember the correct error name), wheres snow or any other module works without any problems.

Is there anything do be done after installing enlightenment (apt-get install enlightenment enlightenment-data engage etc) before loading engage?

Thanks a lot 

Flane

---

### Post by lwl on 2005-07-13
[QUOTE=Flane]Hi Tamir and all the others,

I installed gnome-terminal and it worked. In gnome-terminal xterm doesn't work (command not found), but when i try sudo xterm everything works fine.

Also which xterm doesn't return anything, whereas sudo which xterm returns the correct path.

So what I'm doing wrong (sorry I'm quite new to linux)

But I've got also another problem:
when I'm trying to load engage via
```
enlightenment-remote -load-module engage
``` 
it returns an error in module.so with e_apps_windows_name_not_found (i didn't remember the correct error name), wheres snow or any other module works without any problems.

Is there anything do be done after installing enlightenment (apt-get install enlightenment enlightenment-data engage etc) before loading engage?

Thanks a lot 

Flane[/QUOTE]

i have exactly the same problem

---

### Post by darkmatter on 2005-07-13
[QUOTE=Tamir]Yes there is a way, Install:
```
apt-get install gtk-theme-switch
``` 
gtk-theme-switch2 is for GTK+

WIth this graphical user interface, you can change themes without gnome  ;-)[/QUOTE]

Thanks. That did the trick.

---

### Post by smoon on 2005-07-13
[QUOTE=Flane]Hi Tamir and all the others,

I installed gnome-terminal and it worked. In gnome-terminal xterm doesn't work (command not found), but when i try sudo xterm everything works fine.

Also which xterm doesn't return anything, whereas sudo which xterm returns the correct path.

So what I'm doing wrong (sorry I'm quite new to linux)

But I've got also another problem:
when I'm trying to load engage via
```
enlightenment-remote -load-module engage
``` 
it returns an error in module.so with e_apps_windows_name_not_found (i didn't remember the correct error name), wheres snow or any other module works without any problems.

Is there anything do be done after installing enlightenment (apt-get install enlightenment enlightenment-data engage etc) before loading engage?

Thanks a lot 

Flane[/QUOTE]

This was my fault, I forgot to update the engage package and didn't realized that the old build did not work with the new e build. I've update engage, it should work fine now.

---

### Post by lwl on 2005-07-14
it works :) thnx a lot smoon. btw do you know how to make engage transparent ?

---

### Post by Tamir on 2005-07-14
[QUOTE=lwl]it works :) thnx a lot smoon. btw do you know how to make engage transparent ?[/QUOTE]

Try this:
[http://get-e.org/User_Guide/English/_pages/4.2.html](http://get-e.org/User_Guide/English/_pages/4.2.html)

I am not sure.

---

### Post by lwl on 2005-07-14
[QUOTE=Tamir]Try this:
[http://get-e.org/User_Guide/English/_pages/4.2.html](http://get-e.org/User_Guide/English/_pages/4.2.html)

I am not sure.[/QUOTE]

In the User guide in get-e.org it is written:


If you don't like how the default Engage module theme looks like, you can make it completely transparent (as long as Engage is on the bottom of the screen) by editing data/themes/module.edc **before compiling it**. You'll need to add "color: 255 255 255 0;" at line 34 - without the quotes of course.


I've installed e17 from smoon's repos... i haven't compiled it so if someone knows how to make the engage module (not the  standalone app) transparent please write here ;)

---

### Post by Tamir on 2005-07-14
[QUOTE=lwl]In the User guide in get-e.org it is written:


If you don't like how the default Engage module theme looks like, you can make it completely transparent (as long as Engage is on the bottom of the screen) by editing data/themes/module.edc **before compiling it**. You'll need to add "color: 255 255 255 0;" at line 34 - without the quotes of course.


I've installed e17 from smoon's repos... i haven't compiled it so if someone knows how to make the engage module (not the  standalone app) transparent please write here ;)[/QUOTE]
 I can do it, but are you sure you want color: 255 255 255 0; which means completly transpatent?
and are amd64 user, or i386?

---

### Post by smoon on 2005-07-14
[QUOTE=lwl]In the User guide in get-e.org it is written:


If you don't like how the default Engage module theme looks like, you can make it completely transparent (as long as Engage is on the bottom of the screen) by editing data/themes/module.edc **before compiling it**. You'll need to add "color: 255 255 255 0;" at line 34 - without the quotes of course.


I've installed e17 from smoon's repos... i haven't compiled it so if someone knows how to make the engage module (not the  standalone app) transparent please write here ;)[/QUOTE]

You just need to make an edje for the theme:
```
cd
mkdir engage-theme && cd engage-theme
cvs -d:pserver:anonymous:@cvs.sourceforge.net:/cvsroot/enlightenment login
cvs -z3 -d:pserver:anonymous:@cvs.sourceforge.net:/cvsroot/enlightenment co misc/engage/data/themes
cp -R misc/engage/data/themes/module* .
rm -rf misc
```

Now open **module.edc** with your favourite texteditor:
```
gedit module.edc
``` and modify it to you needs.

After that compile the edje:
```
edje_cc -v -id module/images -fd module/fonts module.edc
```

You'll get a file called **module.edj** that you can copy to **/usr/share/engage/themes**:
```
sudo cp module.edj /usr/share/engage/themes/module.edj
```

Restart enlightenment and you should see the changes.

I've created a transparent theme: [http://nooms.de/misc/engage_module_transparent.edj](http://nooms.de/misc/engage_module_transparent.edj)

---

### Post by vrln on 2005-07-15
I was just about to answer that that question, you were faster :) There are two more Engage (module) themes out there by the way - they are included with the Japan2005 and ICE theme at Get-E.org. The theme included with Japan2005 isn't entirely transparent, but it is more transparent than the default Engage - and it uses a different font as well. Personally I think that by default Engage isn't transparent enough. The ICE Engage module theme is fully transparent.

And as smoom said, all you need to do is to overwrite the module.edj and restart E17.

---

### Post by Neo40 on 2005-07-20
[QUOTE=smoon]Try running /usr/bin/gnome-settings-daemon in the background. I think this will do the trick.[/QUOTE]


Ok, and how to start this command each time I boot E17?

Thanks!

---

### Post by smoon on 2005-07-20
[QUOTE=Neo40]Ok, and how to start this command each time I boot E17?

Thanks![/QUOTE]

Try the following:

```
cd ${HOME}/.e/e/applications/all
cp gnome-terminal.eap gnome-settings-daemon.eap
enlightenment_eapp -set-name "gnome-settings-daemon" -set-exe "gnome-settings-daemon" gnome-settings-daemon.eap
gedit ../startup/.order
```

and add this line:

```
gnome-settings-daemon.eap
```

gnome-settings-daemon should be started every time you run e now.

---

### Post by Flane on 2005-07-20
Thanks for the help with xterm and engage.
Now everything works fine, but :-) there are some other questions.
Perhaps you can help...

On some screenshots [http://www.enlightenment.org/Applications/Engage/](http://www.enlightenment.org/Applications/Engage/) Engage has some seperater areas (launcher, running apps, systray) and also a very cool theme.

Does anybody know what this theme is called and you to seperate these areas?

Thanks so far!

Flane

---

### Post by Aasitus on 2005-08-11
So, finally managed to install e17. A couple of questions, though. I'm sorry if these have been answered in the thread, but I read some pages and the e17 documentation already and imho couldn't find it.

First of all, e17 seems awfully clumsy in some ways. Can I, for example, add another panel that has all the windows? Also, I hate that I have to click the title to select a window, can it be configured so that I simply need to click somewhere at the window?

Also, the documentation suggests not to use fake transparency (but that it can be set by e17setroot) and it says somewhere that e17 supports real transparency. I'd like to make that usual transparent terminal effect - how do I do that? Either real or fake transparency is ok :)

Third, non e17 programs (basically any program at all) look horrible inside e17. Can I make nautilus or firefox, for example, to somehow fit more nicely?

e17 apps also seem to crash a lot. Even now I have Emblem running that I can't close - I've killed the process, but it still shows in the window list and the borders can occassionally be seen for a few seconds when changing desktops.

I'm beginning to wonder if I should try that e16 + gnome combination instead :> I love the eye candy in e17 but, well, it's alpha. Hard to configure and doesn't seem to work too well after all :/

---

### Post by Tab on 2005-08-11
[quote=Aasitus]Can I, for example, add another panel that has all the windows?[/quote]

If I'm understanding correctly, yes. Use enlightenment_remote -module-load ibox and then enable it from the modules menu.

[quote=Aasitus]Also, I hate that I have to click the title to select a window, can it be configured so that I simply need to click somewhere at the window?[/quote]

E17 has I think three click modes at this point: mouse, sloppy, and click. Mouse is the default. Sloppy is the same as mouse, except the desktop doesn't take focus when mousing-out of a window. Click is what you want. However, mouse can be quite convenient for interacting with windows that are underneath the focused window.
Anyway, set that with enlightenment_remote -click-policy-set click
I believe that's the correct command. I'm actually in GNOME right now, but I'll double-check as soon as I post.

[quote=Aasitus]Also, the documentation suggests not to use fake transparency (but that it can be set by e17setroot) and it says somewhere that e17 supports real transparency. I'd like to make that usual transparent terminal effect - how do I do that? Either real or fake transparency is ok [/quote]

E17 is in a weird place regarding transparency. It doesn't support hacks that allow for fake trans (except with e17setroot), but it can't force X to do real trans either. The only real transparency it can do is within Evas canvasses. That is, you can have real trans between desktop modules and the background, and this is very nice, but it can't force X to make whatever window you're using transparent.

[quote=Aasitus]Third, non e17 programs (basically any program at all) look horrible inside e17. Can I make nautilus or firefox, for example, to somehow fit more nicely?[/quote]

Maybe you don't have themes running? Try running gnome-theme-manager from a terminal, you can select a theme from there. To have themes start with E, create an eap to run gnome-settings-daemon, and put it under startup with entangle.

---

### Post by i3dmaster on 2005-08-11
Nice howto, thanks!

---

### Post by christooss on 2005-08-23
smoon: Are you thinking about putting enligtenment in Breezy.

You could do it like you did for breezy <-- hint hint

---

### Post by smoon on 2005-08-23
[QUOTE=christooss]smoon: Are you thinking about putting enligtenment in Breezy.

You could do it like you did for breezy <-- hint hint[/QUOTE]

Sorry, but I won't even provide any further updates for Hoary. Like I mentioned in [http://www.ubuntuforums.org/showthread.php?p=314018#post314018](http://www.ubuntuforums.org/showthread.php?p=314018#post314018):
[QUOTE=smoon]I just wanted to let you all know that I switched to [Arch Linux](http://www.archlinux.org/) today for various reasons and **will not provide any further updates** on e17, its libs and apps. The repository will stay up for a while though.

Who knows, maybe I'll come back to Ubuntu...[/QUOTE]
Sorry, guys.

---

### Post by AndyAWS on 2005-08-23
Bummer, now I'll have to learn how to get and install e17 from cvs.

Thanks for all you did, and all your help, smoon.

---

### Post by bored2k on 2005-08-23
[QUOTE=smoon]Sorry, guys.[/QUOTE]
You don't need to exclude yerself man ! You did it for the heck of it and you can certaintly stop doing it for the heck of it too :D. It's not like your Princess_Leia-Jabba_the_Hutt chained to Ubuntu or something.

Keep it rockin' with Pacman !

---

### Post by smoon on 2005-08-23
[QUOTE=bored2k]You don't need to exclude yerself man ! You did it for the heck of it and you can certaintly stop doing it for the heck of it too :D. It's not like your Princess_Leia-Jabba_the_Hutt chained to Ubuntu or something.

Keep it rockin' with Pacman ![/QUOTE]

Haha, that's true.

Btw: Everyone who wants to create enlightenment packages on his own can use the script I wrote for myself to update the repository: [http://nooms.de/misc/e17install.sh](http://nooms.de/misc/e17install.sh)

---

### Post by GreyDuck on 2005-08-25
Just one question: How the hell does one make e17setroot behave in a Xinerama environment? All I get out of my dualscreen wallpaper files is a scrunched-to-one-window-sized image, and my other display stuck with the grey default.

Argh. ](*,)

---

### Post by nickless on 2005-08-26
I am so frustrated with enlightenment :(
Just can't get it right... it's ugly as hell :D

---

