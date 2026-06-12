---
title: "HOWTO: Install Kiba Dock + Akamaru on JAUNTY"
date: 2009-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by raafaell on 2009-06-30
[CENTER][SIZE="4"][[[ [color="red"]how to install **kiba-dock with akamaru** on ubuntu jaunty jacklope 9.04[/color] ]]][/SIZE][/CENTER]


---


Okay guys, this is my very first how to, so please don't be angry if I do something wrong.. but you can trust me.. ;)

As we all know, kiba-dock is NOT a very stable software on _jaunty_, but it will work as far as you follow the steps below..

[COLOR="Red"][SIZE="4"]WARNING[/SIZE][/COLOR]: Do it at your own RISK! 	\\:D/

[SIZE="3"]So let's get started![/SIZE]

[COLOR="Red"][CENTER]__________________________________________________[/CENTER]
[/COLOR]

IN YOUR TERMINAL, DO:

[COLOR="Red"][SIZE="5"]STEP 1:[/SIZE][/COLOR] [SIZE="3"]Delete/Uninstall[/SIZE] your current kiba-dock, [SIZE="3"]_in case you have it installed_, otherwise [COLOR="Red"]SKIP IT[/COLOR][/SIZE].. Do the following... 

```
cd kiba-dock/kiba-dbus-plugins
sudo make uninstall
cd ..
```

then

```
cd kiba-plugins
sudo make uninstall
cd ..
```

then

```
cd kiba-dock
sudo make uninstall
cd ..
```

then

```
cd akamaru
sudo make uninstall
cd ..
```

and then

```
cd ..
```

_[SIZE="4"]Make sure the Kiba-dock's Folder is [COLOR="Red"]GONE[/COLOR]![/SIZE]_
):P

[COLOR="Red"][SIZE="5"]STEP 2:[/SIZE][/COLOR] Now let's [COLOR="Red"]make sure we have all the [SIZE="3"]_dependencies_[/SIZE][/COLOR]! Do the following... [COLOR="Red"][SIZE="3"](Start from here if you _don't have_ kiba-dock already installed.)[/SIZE][/COLOR]


```
sudo aptitude remove automake1.4
```

then

```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
```

Now that we have the dependencies, lets make the directories... do:

```
mkdir kiba-dock
cd kiba-dock
```

then

```
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/ akamaru
```

then

```
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/ kiba-dock
```

then

```
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/ kiba-plugins
```

and then

```
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/ kiba-dbus-plugins
```

[COLOR="Red"][SIZE="5"]STEP 3:[/SIZE][/COLOR] Now [COLOR="Red"]we have to [SIZE="3"]DOWNgrade[/SIZE][/COLOR] the kiba-dock files, so we will be able to make it to work.. so do the following... 

```
svn update -r 602 *
```

[COLOR="Red"][SIZE="5"]STEP 4:[/SIZE][/COLOR] Now that we have the revision 602, we [COLOR="Red"]will need[/COLOR] to edit/change a few things, so please do exactly as I tell you.. So do the following...

```
gedit akamaru/configure.in
```

Once it's opened, locate the following > AC_SUBST("$AKAMARU_REQUIRES") and change it to > AC_SUBST(AKAMARU_REQUIRES) then save and exit!

then

```
gedit kiba-dock/configure.ac
```

Once it's opened, locate the following > AC_SUBST("$PKG_CONFIG_PATH") and change it to > AC_SUBST(PKG_CONFIG_PATH) then locate > AC_SUBST("$KIBA_DOCK_REQUIRES") and change it to > AC_SUBST(KIBA_DOCK_REQUIRES) then save and exit.

then

```
gedit kiba-plugins/configure.in
```

 Once it's opened, locate the following > AC_SUBST("$KIBA_PLUGINS_REQUIRES") and change it to > AC_SUBST(KIBA_PLUGINS_REQUIRES) then save and exit.

[COLOR="Red"][SIZE="5"]STEP 5:[/SIZE][/COLOR] Installing Kiba-Dock with Akamaru, (damm, when is this gonna end..) doing [COLOR="Red"]_one line_[/COLOR] at a time.. do the following...

```
cd akamaru
./autogen.sh --prefix=/usr --exec-prefix=/usr
make && sudo make install
cd ..
```

then

```
cd kiba-dock
./autogen.sh
make && sudo make install 
cd ..
```

then

```
cd kiba-plugins
./autogen.sh
make && sudo make install
cd ..
```

and then

```
cd kiba-dbus-plugins
./autogen.sh
make && sudo make install
cd ..
```

[SIZE="4"]AND NOW YOU ARE _DONE_![/SIZE]

[COLOR="Red"][SIZE="3"]NOTICE:[/SIZE][/COLOR] [SIZE="3"]You _might_ need to change the kiba-dock settings, to add launchers, trash, clock etc... you can find Kiba Settings by right clicking on the dock and then choosing Kiba Settings, or simply going to: Applications/Accessories/Kiba-Settings.. and don't worry if you see just a little blue dock before changing settings.. it's normal in this case..[/SIZE]


[SIZE="5"]PEACE![/SIZE]

---

### Post by cariboo on 2009-07-02
Needs editing.

Edit: well done

---

### Post by steigerjb on 2009-07-02
> **cariboo907 said:**
> Needs editing.

why? whats wrong cariboo907?

---

### Post by raafaell on 2009-07-02
> **steigerjb said:**
> why? whats wrong cariboo907?

The team had to validate the howto as usual, so I had to correct a few points, but it's good to go now. :twisted:

---

### Post by steigerjb on 2009-07-03
then locate

Quote:
AC_SUBST("$KIBA_DOCK_REQUIRES")

and change it to

Quote:
AC_SUBST(KIBA_DOCK_REQUIRES)

then save and exit.

_________________________________

I can't find it

```
#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.
AC_PREREQ(2.57)

AC_INIT([kiba-dock],esyscmd(. ./VERSION;echo -n $VERSION), [danielb@kiba-dock.org])

AC_DEFINE_UNQUOTED(VERSION,"$VERSION",[Version])
AC_DEFINE_UNQUOTED(PACKAGE_STRING,"$PACKAGE $VERSION",[Package String])

# Macro to allow debugging, [0] for releases
AC_DEFINE([ENABLE_DEBUG_MODE], [1], [Enable Debugging])

AM_INIT_AUTOMAKE([1.9 dist-bzip2])

AM_CONFIG_HEADER([config.h])
AM_MAINTAINER_MODE

AC_ISC_POSIX
AC_PROG_CC
AC_HEADER_STDC
AC_CHECK_HEADERS([stdlib.h sys/time.h unistd.h])
AC_SUBST(PKG_CONFIG_PATH)

# Enables translation
AC_PROG_INTLTOOL([0.35.0], [yes-xml])
AC_SUBST(ALL_LINGUAS)
AM_GLIB_GNU_GETTEXT
GETTEXT_PACKAGE=kiba-dock
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE,"$GETTEXT_PACKAGE", [Gettext package.])
AC_SUBST(GETTEXT_PACKAGE)

AC_C_BIGENDIAN

# Gets configure arguments
AC_ARG_ENABLE(svg,
  [  --disable-svg         Disable svg support],
  [use_svg=$enableval], [use_svg=yes])
AC_ARG_ENABLE(glitz,
  [  --enable-glitz         Use glitz backend],
  [use_glitz=$enableval], [use_glitz=no])
AC_ARG_ENABLE(sdl,
  [  --enable-sdl         Use sdl backend],
  [use_sdl=$enableval], [use_sdl=no])
AC_ARG_ENABLE(akamaru,
  [  --enable-akamaru         Enable akamaru support],
  [use_akamaru=$enableval], [use_akamaru=yes])
AC_ARG_ENABLE(kde,
  [  --enable-kde         Configure kiba-dock for kde],
  [use_kde=$enableval], [use_kde=no])
AC_ARG_ENABLE(xfce,
  [  --enable-xfce         Configure kiba-dock for xfce],
  [use_xfce=$enableval], [use_xfce=no])
AC_ARG_ENABLE(libsn,
  [  --enable-libsn         Enable libsn support],
  [use_libsn=$enableval], [use_libsn=yes])

KIBA_DOCK_REQUIRES="[glib-2.0 >= 2.8.0 gobject-2.0] [gtk+-2.0 >= 2.8.0] [cairo >= 1.0.0] [pango >= 1.10.0 pangocairo >= 1.10.0] [libxml-2.0]"

if test "x$use_kde" = "xyes"; then
  AC_DEFINE([USE_KDE], [1], [Kde support])
elif test "x$use_xfce" = "xyes"; then
  AC_DEFINE([USE_XFCE], [1], [Xfce support])
fi

# Checks for libraries.
PKG_CHECK_MODULES([GLIB],  [glib-2.0 >= 2.6.0 gobject-2.0 >= 2.4.0])
PKG_CHECK_MODULES([PANGO], [pango >= 1.10.0 pangocairo >= 1.10.0])
PKG_CHECK_MODULES([GTK],   [gtk+-2.0 >= 2.8.0])
PKG_CHECK_MODULES([CAIRO], [cairo >= 1.0.0])
PKG_CHECK_MODULES([LIBXML], [libxml-2.0])

PKG_CHECK_MODULES([DBUS], [dbus-glib-1])

build_libsn=no
if test "x$use_libsn" = "xyes"; then
  PKG_CHECK_MODULES([LIBSN],   [libstartup-notification-1.0],
                  [AC_DEFINE([USE_LIBSN], [1], [Libsn support])
                   KIBA_DOCK_REQUIRES+=" [libstartup-notification-1.0]"
                   build_libsn=yes],
                  [echo -n])
fi
AM_CONDITIONAL(USE_LIBSN, test "x$build_libsn" = "xyes")

build_akamaru=no
if test "x$use_akamaru" = "xyes"; then
  PKG_CHECK_MODULES([AKAMARU],   [akamaru >= 0.1],
                    [AC_DEFINE([USE_AKAMARU], [1], [Akamaru support])
                     KIBA_DOCK_REQUIRES+=" [akamaru >= 0.1]"
                     build_akamaru=yes],
                    [echo -n])
fi
AM_CONDITIONAL(USE_AKAMARU, test "x$build_akamaru" = "xyes")

build_svg=no
if test "x$use_svg" = "xyes"; then
  librsvgdefine="// macro for optional svg feature\n"
  PKG_CHECK_MODULES([SVG],   [librsvg-2.0 >= 2.13.91],
                    [AC_DEFINE([HAVE_SVG], [1], [Svg support])
                     KIBA_DOCK_REQUIRES+=" [librsvg-2.0 >= 2.13.91]"
                     librsvgdefine+="#ifndef USE_SVG\n  #define USE_SVG\n#endif\n"
                     build_svg=yes],
                    [echo -n
                     librsvgdefine+="#ifdef USE_SVG\n  #undef USE_SVG\n#endif\n"])
  echo -e $librsvgdefine > include/kiba-svg-macro.h
fi
AM_CONDITIONAL(USE_SVG, test "x$build_svg" = "xyes")

build_glitz=no
if test "x$use_glitz" = "xyes"; then
  PKG_CHECK_MODULES([GLITZ], [glitz-glx >= 0.4],
                    [AC_DEFINE([USE_GLITZ], [1], [Glitz glx rendering])
                     build_glitz=yes
                     KIBA_DOCK_REQUIRES+=" [glitz-glx >= 0.4]"],
                    [echo -n])
fi
AM_CONDITIONAL(USE_GLITZ, test "x$build_glitz" = "xyes")

build_sdl=no
if test "x$use_glitz" = "xno"; then
  if test "x$use_sdl" = "xyes"; then
    PKG_CHECK_MODULES([SDL], [sdl],
                    [AC_DEFINE([USE_SDL], [1], [SDL rendering])
                     build_sdl=yes
                     KIBA_DOCK_REQUIRES+=" [sdl]"],
                    [echo -n])
  fi
fi
AM_CONDITIONAL(USE_SDL, test "x$build_sdl" = "xyes")

PKG_CHECK_MODULES(KIBA_DOCK, "$KIBA_DOCK_REQUIRES")
AC_SUBST("$KIBA_DOCK_REQUIRES")

DBUS_GLIB_BIN="`$PKG_CONFIG --variable=exec_prefix dbus-glib-1`/bin"
AC_SUBST(DBUS_GLIB_BIN)

AC_CONFIG_FILES([kiba-dock.pc
           Makefile
           src/Makefile
           include/Makefile
           kiba-settings/Makefile
           icons/Makefile
           files/populate-dock.sh
           files/Makefile
           po/Makefile.in])

AC_OUTPUT

echo
echo "Optional Features :"
echo "  Akamaru : "	$build_akamaru
echo "  SVG     : "	$build_svg
echo
echo "Rendering Platform :"
if test "x$build_glitz" = "xyes"; then
	echo "  Glitz"
elif test "x$build_sdl" = "xyes"; then
	echo "  SDL"
else
	echo "  Xlib + Offscreen Pixmap"
fi

echo
```

---

### Post by raafaell on 2009-07-03
> **steigerjb said:**
> then locate

Quote:
AC_SUBST("$KIBA_DOCK_REQUIRES")

and change it to

Quote:
AC_SUBST(KIBA_DOCK_REQUIRES)

then save and exit.

_________________________________

I can't find it

```
#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.
AC_PREREQ(2.57)

AC_INIT([kiba-dock],esyscmd(. ./VERSION;echo -n $VERSION), [danielb@kiba-dock.org])

AC_DEFINE_UNQUOTED(VERSION,"$VERSION",[Version])
AC_DEFINE_UNQUOTED(PACKAGE_STRING,"$PACKAGE $VERSION",[Package String])

# Macro to allow debugging, [0] for releases
AC_DEFINE([ENABLE_DEBUG_MODE], [1], [Enable Debugging])

AM_INIT_AUTOMAKE([1.9 dist-bzip2])

AM_CONFIG_HEADER([config.h])
AM_MAINTAINER_MODE

AC_ISC_POSIX
AC_PROG_CC
AC_HEADER_STDC
AC_CHECK_HEADERS([stdlib.h sys/time.h unistd.h])
AC_SUBST(PKG_CONFIG_PATH)

# Enables translation
AC_PROG_INTLTOOL([0.35.0], [yes-xml])
AC_SUBST(ALL_LINGUAS)
AM_GLIB_GNU_GETTEXT
GETTEXT_PACKAGE=kiba-dock
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE,"$GETTEXT_PACKAGE", [Gettext package.])
AC_SUBST(GETTEXT_PACKAGE)

AC_C_BIGENDIAN

# Gets configure arguments
AC_ARG_ENABLE(svg,
  [  --disable-svg         Disable svg support],
  [use_svg=$enableval], [use_svg=yes])
AC_ARG_ENABLE(glitz,
  [  --enable-glitz         Use glitz backend],
  [use_glitz=$enableval], [use_glitz=no])
AC_ARG_ENABLE(sdl,
  [  --enable-sdl         Use sdl backend],
  [use_sdl=$enableval], [use_sdl=no])
AC_ARG_ENABLE(akamaru,
  [  --enable-akamaru         Enable akamaru support],
  [use_akamaru=$enableval], [use_akamaru=yes])
AC_ARG_ENABLE(kde,
  [  --enable-kde         Configure kiba-dock for kde],
  [use_kde=$enableval], [use_kde=no])
AC_ARG_ENABLE(xfce,
  [  --enable-xfce         Configure kiba-dock for xfce],
  [use_xfce=$enableval], [use_xfce=no])
AC_ARG_ENABLE(libsn,
  [  --enable-libsn         Enable libsn support],
  [use_libsn=$enableval], [use_libsn=yes])

KIBA_DOCK_REQUIRES="[glib-2.0 >= 2.8.0 gobject-2.0] [gtk+-2.0 >= 2.8.0] [cairo >= 1.0.0] [pango >= 1.10.0 pangocairo >= 1.10.0] [libxml-2.0]"

if test "x$use_kde" = "xyes"; then
  AC_DEFINE([USE_KDE], [1], [Kde support])
elif test "x$use_xfce" = "xyes"; then
  AC_DEFINE([USE_XFCE], [1], [Xfce support])
fi

# Checks for libraries.
PKG_CHECK_MODULES([GLIB],  [glib-2.0 >= 2.6.0 gobject-2.0 >= 2.4.0])
PKG_CHECK_MODULES([PANGO], [pango >= 1.10.0 pangocairo >= 1.10.0])
PKG_CHECK_MODULES([GTK],   [gtk+-2.0 >= 2.8.0])
PKG_CHECK_MODULES([CAIRO], [cairo >= 1.0.0])
PKG_CHECK_MODULES([LIBXML], [libxml-2.0])

PKG_CHECK_MODULES([DBUS], [dbus-glib-1])

build_libsn=no
if test "x$use_libsn" = "xyes"; then
  PKG_CHECK_MODULES([LIBSN],   [libstartup-notification-1.0],
                  [AC_DEFINE([USE_LIBSN], [1], [Libsn support])
                   KIBA_DOCK_REQUIRES+=" [libstartup-notification-1.0]"
                   build_libsn=yes],
                  [echo -n])
fi
AM_CONDITIONAL(USE_LIBSN, test "x$build_libsn" = "xyes")

build_akamaru=no
if test "x$use_akamaru" = "xyes"; then
  PKG_CHECK_MODULES([AKAMARU],   [akamaru >= 0.1],
                    [AC_DEFINE([USE_AKAMARU], [1], [Akamaru support])
                     KIBA_DOCK_REQUIRES+=" [akamaru >= 0.1]"
                     build_akamaru=yes],
                    [echo -n])
fi
AM_CONDITIONAL(USE_AKAMARU, test "x$build_akamaru" = "xyes")

build_svg=no
if test "x$use_svg" = "xyes"; then
  librsvgdefine="// macro for optional svg feature\n"
  PKG_CHECK_MODULES([SVG],   [librsvg-2.0 >= 2.13.91],
                    [AC_DEFINE([HAVE_SVG], [1], [Svg support])
                     KIBA_DOCK_REQUIRES+=" [librsvg-2.0 >= 2.13.91]"
                     librsvgdefine+="#ifndef USE_SVG\n  #define USE_SVG\n#endif\n"
                     build_svg=yes],
                    [echo -n
                     librsvgdefine+="#ifdef USE_SVG\n  #undef USE_SVG\n#endif\n"])
  echo -e $librsvgdefine > include/kiba-svg-macro.h
fi
AM_CONDITIONAL(USE_SVG, test "x$build_svg" = "xyes")

build_glitz=no
if test "x$use_glitz" = "xyes"; then
  PKG_CHECK_MODULES([GLITZ], [glitz-glx >= 0.4],
                    [AC_DEFINE([USE_GLITZ], [1], [Glitz glx rendering])
                     build_glitz=yes
                     KIBA_DOCK_REQUIRES+=" [glitz-glx >= 0.4]"],
                    [echo -n])
fi
AM_CONDITIONAL(USE_GLITZ, test "x$build_glitz" = "xyes")

build_sdl=no
if test "x$use_glitz" = "xno"; then
  if test "x$use_sdl" = "xyes"; then
    PKG_CHECK_MODULES([SDL], [sdl],
                    [AC_DEFINE([USE_SDL], [1], [SDL rendering])
                     build_sdl=yes
                     KIBA_DOCK_REQUIRES+=" [sdl]"],
                    [echo -n])
  fi
fi
AM_CONDITIONAL(USE_SDL, test "x$build_sdl" = "xyes")

PKG_CHECK_MODULES(KIBA_DOCK, "$KIBA_DOCK_REQUIRES")
AC_SUBST("$KIBA_DOCK_REQUIRES")

DBUS_GLIB_BIN="`$PKG_CONFIG --variable=exec_prefix dbus-glib-1`/bin"
AC_SUBST(DBUS_GLIB_BIN)

AC_CONFIG_FILES([kiba-dock.pc
           Makefile
           src/Makefile
           include/Makefile
           kiba-settings/Makefile
           icons/Makefile
           files/populate-dock.sh
           files/Makefile
           po/Makefile.in])

AC_OUTPUT

echo
echo "Optional Features :"
echo "  Akamaru : "	$build_akamaru
echo "  SVG     : "	$build_svg
echo
echo "Rendering Platform :"
if test "x$build_glitz" = "xyes"; then
	echo "  Glitz"
elif test "x$build_sdl" = "xyes"; then
	echo "  SDL"
else
	echo "  Xlib + Offscreen Pixmap"
fi

echo
```
take a look on the text that you just quoted, and you WILL find it.. ;)
you can search by doing: Ctrl + F, and then write > AC_SUBST("$KIBA_DOCK_REQUIRES")

---

### Post by steigerjb on 2009-07-03
> **raafaell said:**
> take a look on the text that you just quoted, and you WILL find it.. ;)
you can search by doing: Ctrl + F, and then write

yeah, i found it after I posted it :lolflag: i did the ctrl f thing.

****************************************************************************

ok, it installed and everything, w/physics i believe. 

Now how do I do:

-rope
-spring from all
-stack
-ping pong

?

---

### Post by raafaell on 2009-07-03
> **steigerjb said:**
> yeah, i found it after I posted it :lolflag: i did the ctrl f thing.

****************************************************************************

ok, it installed and everything, w/physics i believe. 

Now how do I do:

-rope
-spring from all
-stack
-ping pong

?

go to Kiba-Settings, select akamaru.. and then choose the settings that you want..

---

### Post by steigerjb on 2009-07-03
gotcha

---

### Post by serious7 on 2009-07-20
add a note to say that synaptic package manager must be closed. I  had it open and I couldnt complete sudo aptitude commands. I'm a noob lol.

---

### Post by serious7 on 2009-07-20
ok I went thru many tutorials and I'm asking you the guy who made this please give codes for 64-bit installation. I used these codes to get my installation to (semi-finish). 

cd akamaru/ 
./autogen.sh --prefix=/usr --exec-prefix=/usr --libdir=/usr/lib64 
sudo make install 
cd ..


cd kiba-dock/ 
./autogen.sh --prefix=/usr --libdir=/usr/lib64
sudo make install 
cd ..

cd kiba-plugins/ 
CC="gcc -fPIC" ./autogen.sh --prefix=/usr --libdir=/usr/lib64 
sudo make install 
cd ..

cd kiba-dbus-plugins/ 
./autogen.sh --prefix=/usr --libdir=/usr/lib64 
sudo make install 
cd ..

just cause im using 64 bit. Otherwise everything else i followed in your tutorial however when i go to terminal to launch kiba-dock i get this error:

nicky@nicky-desktop:~$ sudo kiba-dock
[sudo] password for nicky: 
Segmentation fault


What did I do wrong?

---

### Post by serious7 on 2009-07-20
edit disregard this post

---

### Post by soad6 on 2009-08-27
ok strange, but it works!! yay!! but heres my problem everytime i log off or restart or shutdown the computer and reload kiba-dock starts up but doesnt have my launchers or anything. It just starts up as a little blue triangle and then i have to click and unclick things in kiba-dock settings to fix it. I have kiba-dock as the command for start up applications, but im beginning to think there's more to this... please help if possible cuz its really annoying to have to reload my launchers every time. Thanx](*,)

---

### Post by soad6 on 2009-08-27
ok so nvm my earlier post i figured it out!! and guess what so simple to fix. if u have this issue or a similar issue where u cant save your configuration to kiba-dock. go to home and find a folder called ./kiba-dock
itll be hidden just delete it completely and restart. That should take care of everything. The problem is that in ./kiba-dock theres a folder called config and the terminal thinks this is the config file and tries to load it but then it gets error this is a directory no config file to save to. And if you remove it then it realizes that there's a config file in the other folder and it saves to that file!! \\:D/  and major thanx to everyone who helped figure out how to get this awesome dock to work in the new ubuntu. I just hope i dont have to change anything for 9.10 when it comes out...

---

### Post by ichundu on 2009-08-27
akamaru physics work but when i enable akamaru i cannot use effects (reflection, pulse, rotate etc). if i disable akamaru they do work... weird :(

my question is: does anyone else have the same behavior or is it just me? 

this also happened on intrepid and hardy, i could get akamaru to work but i couldn't use it simultaneously with the 'effects' plugin.

---

### Post by soad6 on 2009-08-31
ICHUNDU the fix i posted above is the way to fix ur problem with the effects and the physics engine in akamaru. You need to go to your home folder and go to view hidden files then in hidden files find a folder that says ./kiba-dock and delete it. Thats all you have to do then follow the steps over again for the installation of kiba dock for version 602!! Its pretty simple really, if you dont understand that, then try using a different docking bar like cairo dock or something as it has decent effects. But im almost 100% certain that if you remove that folder and then follow the steps again and add the file to ur directory it will work. Then all u have to do is go to kiba settings and play with the settings and that should fix your problems. ](*,)

---

### Post by Sephoroth on 2009-09-13
Just thought I'd mention Kiba-Dock doesn't seem to be working on Karmic Koala through traditional installation methods.  Has anyone found a way to get it working (with or without Akamaru)?

---

### Post by jw_90 on 2009-09-18
When I try to make the kiba-plugins it brings up some errors that I'm not sure how to fix. 

> john@john-desktop:~/kiba-dock/kiba-plugins$ make
make  all-recursive
make[1]: Entering directory `/home/john/kiba-dock/kiba-plugins'
Making all in src
make[2]: Entering directory `/home/john/kiba-dock/kiba-plugins/src'
make  all-am
make[3]: Entering directory `/home/john/kiba-dock/kiba-plugins/src'
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o liblauncher.la -rpath /usr/local/lib/kiba-dock -module -avoid-version -no-undefined launcher-plugin.lo -lxml2 -lstartup-notification-1 -lakamaru -lrsvg-2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lfreetype -lfontconfig -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lglib-2.0     liblauncher-type.la 
libtool: link: gcc -shared  .libs/launcher-plugin.o  -Wl,--whole-archive ./.libs/liblauncher-type.a -Wl,--no-whole-archive  /usr/lib/libxml2.so -lstartup-notification-1 /usr/lib/libakamaru.so -L/usr/lib -lrsvg-2 /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libpangoft2-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libgio-2.0.so /usr/lib/libfreetype.so -lz -lfontconfig /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libglib-2.0.so    -Wl,-soname -Wl,liblauncher.so -o .libs/liblauncher.so
/usr/bin/ld: ./.libs/liblauncher-type.a(launcher.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/liblauncher-type.a(launcher.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [liblauncher.la] Error 1
make[3]: Leaving directory `/home/john/kiba-dock/kiba-plugins/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/john/kiba-dock/kiba-plugins/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/john/kiba-dock/kiba-plugins'
make: *** [all] Error 2

Also kiba dock shows up under my applications but won't start when I try to open it, when I run it in a terminal it says: 

> john@john-desktop:~$ kiba-dock

** (kiba-dock:13681): WARNING **: Error (main.c @ line 252):
	Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.

anyone who knows how to help it would be very appreciated

---

### Post by slayerlambert on 2009-09-24
I installed it (strange, it works!), but i look that when I start akamaru, the icons are under the dock, and, even with akamaru, the open icons looks like white squares! How can I fix it??

---

### Post by coalescentdivide on 2009-10-07
ok...followed everything exactly, but the physics engine seems to have a problem...when i turn on the physics, it 'works' but the dock duplicates itself, so there is two, and the second one moves around with the physics while the other stays static..i cant figure it out

---

### Post by steigerjb on 2009-11-06
> **raafaell said:**
> [CENTER][SIZE="4"][[[ [color="red"]how to install **kiba-dock with akamaru** on ubuntu jaunty jacklope 9.04[/color] ]]][/SIZE][/CENTER]

It installs in Karmic Koala too all

---

### Post by tommytomato on 2009-11-20
Thank you it worked well on Ubuntu 9.10 Karmic Koala

cheers TT

---

### Post by PsychoDevon on 2009-11-27
Um...sorry, I am a complete noob to complicated things like this, but: i did everything correctly to my knowledge...but I can't figure out how to open it. xD! It isn't in my applications menu, or anywhere else. So, where does the dock show up, and how do I open it? Is there a terminal code to start it?

---

### Post by tommytomato on 2009-11-27
if you have installed OK, it will be under Applications,Accessories

if not type kiba-dock in the terminal to run it

TT

---

### Post by PsychoDevon on 2009-11-27
> **tommytomato said:**
> if you have installed OK, it will be under Applications,Accessories

if not type kiba-dock in the terminal to run it

TT

Well, I guess that means I did not install correctly.

All I'm supposed to do is enter each command in the terminal, and after it's finished, type in the next one, and when needed, change those things in gedit? So, everything is only done in temrinal and gedit, right?

If so, I think I did it right. But, what does it mean during the part to put each line in at the time? I just copied the command, and when i pasted it in there, it immediately entered  it in without me doing anything.

Grrr...can someone do me a favor and record them doing it, with step-by-step instructions? That would make this so much easier. There's one already on youtube, but it is VERY unclear.

---

### Post by tommytomato on 2009-11-27
> If so, I think I did it right. But, what does it mean during the part to put each line in at the time? I just copied the command, and when i pasted it in there, it immediately entered it in without me doing anything.

It means type each line at a time

Sample

# cd kiba-dock/kiba-dbus-plugins ( first line )

# sudo make uninstall ( 2nd line )

# cd .. ( 3rd line )

and so on

> STEP 1: Delete/Uninstall your current kiba-dock, in case you have it installed, otherwise SKIP IT.. Do the following...

to remove kiba-dock type in 

```
apt-get remove kiba-dock
```

> All I'm supposed to do is enter each command in the terminal, and after it's finished, type in the next one, and when needed, change those things in gedit? So, everything is only done in temrinal and gedit, right

yes

hope it helps

TT

---

### Post by PsychoDevon on 2009-11-27
OOOOH!
thank you SOOOOOOOOO much. The lines at a time is where I messed up...
I will update this when I redo this.

---

### Post by tommytomato on 2009-11-27
No Probs mate

Its all a bit scary at first using linux, but after time it will get better and better

kiba-dock is pretty cool stuff, looks abit like this

[http://www.youtube.com/smeggingtommy](http://www.youtube.com/smeggingtommy)

videos created by me

TT

---

### Post by PsychoDevon on 2009-11-27
Ok, NOW i need help.

When I'm putting in each line at a time (now, correctly,) the first time it works. But, with the others, it keeps telling me "no such file or directory exists".

Is there ANY other way to install kiba-dock? I mean, I don't know a lot about it, but it seems like it could be as easy as putting a source in the sources list and then installing it in Synaptic Package Manager.

---

### Post by tommytomato on 2009-11-27
Try this, see if it works

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy 

Then type copy paste the following in a terminal: wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

 Then run in the terminal the following 4 commands:
 
 ```
sudo apt-get update
```

```
sudo apt-get install kiba-dock
```
 
```
sudo apt-get install kiba-dock-dev
``` 

```
sudo apt-get install kiba-plugins
``` 

Thats it. Now you can start Kiba-Dock by typing "kiba-dock" in a terminal window. There is also a Kiba-Dock icon in your Applications_Accessories menu. Or you can open System-Preferences-Sessions and add a kiba-dock startup command.

[http://www.bgevolution.com/blog/kiba-dock-apt-deb-repository/](http://www.bgevolution.com/blog/kiba-dock-apt-deb-repository/)

TT

---

### Post by tommytomato on 2009-11-27
Same thing

[http://ubuntuforums.org/showpost.php?p=3447695&postcount=4](http://ubuntuforums.org/showpost.php?p=3447695&postcount=4)

TT

---

### Post by PsychoDevon on 2009-11-27
When i paste in wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -, it says 100% but it doesn't allow me to put in something new, so I can't put in the last 4 codes. Here's what I'm talking about:

devon@ubuntu:~$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
[sudo] password for devon: --2009-11-27 20:57:51--  [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4180 (4.1K) [application/octet-stream]
Saving to: `STDOUT'

100%[======================================>] 4,180       --.-K/s   in 0.1s    

2009-11-27 20:57:52 (34.1 KB/s) - `-' saved [4180/4180]






It doesn't come up with another devon@ubuntu:~$, so I can't put anything else in. Is it still processing, or is it supposed to do this? Also, when I put in the first code to my software sources, It comes up with an error.

---

### Post by tommytomato on 2009-11-27
Put sudo in front of it

> sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

TT

---

### Post by PsychoDevon on 2009-11-27
That code works now. But. because the software source still failed, the last three codes in the terminal do not work.

---

### Post by tommytomato on 2009-11-27
Go back to the start of the post and start again then use sudo

I have to go  out now,so I'll be back in a few hours,do you have ssh ?

TT

---

### Post by PsychoDevon on 2009-11-27
O_O
um...I have no idea what that means. xD

I have windows live + email

just either email me at [email]psychodevon@hotmail.com[/email], or add that same address to your im if it has MSN support.

---

### Post by PsychoDevon on 2009-11-28
I HAVE GOOD NEWS!

I have FINALLY (although probably noone cares) installed it correctly. It now shows up in my applications menu, and also it's settings.

However, (oh lord this noob still needs help), when I try to run it, the dock does not show up on my screen. What is wrong? The kiba-dock command in terminal works fine, and loads it, but it just doesnt show up. What's wrong?

---

### Post by tommytomato on 2009-12-11
show us your bash_history to see what you did wrong

it's been awhile since I have done it, so here's my .bash_history

```
sudo apt-get install kiba-dock 
sudo apt-get install gtk-doc-tools 
cd kiba-dock/kiba-dbus-plugins
ls
cd kiba-dock/kiba-dbus-plugins
cd kiba-dock/
ls
cd
ls
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
mkdir kiba-dock
cd kiba-dock
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/ akamaru
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/ kiba-dock
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/ kiba-plugins
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/ kiba-dbus-plugins
svn update -r 602 *
gedit akamaru/configure.in
gedit kiba-dock/configure.ac
gedit akamaru/configure.in
gedit kiba-dock/configure.a
gedit kiba-dock/configure.ac
gedit kiba-plugins/configure.in
cd akamaru
./autogen.sh --prefix=/usr --exec-prefix=/usr
make && sudo make install
cd ..
cd kiba-dock
./autogen.sh
make && sudo make install
cd ..
cd kiba-plugins
./autogen.sh
make && sudo make install
cd ..
cd kiba-dbus-plugins
./autogen.sh
make && sudo make install
```

TT

---

### Post by atkhan007 on 2010-05-08
I am trying to install Kiba-dock on lucid64 and i m getting this error. when make install kiba-dock

/kiba-dock# make install
Making install in include
make[1]: Entering directory `/home/at/kiba-dock/kiba-dock/include’
make[2]: Entering directory `/home/at/kiba-dock/kiba-dock/include’
make[2]: Nothing to be done for `install-exec-am’.
test -z “/usr/include/kiba-dock” || /bin/mkdir -p “/usr/include/kiba-dock”
/usr/bin/install -c -m 644 kiba-win.h kiba-dock.h kiba-plugin.h kiba-plugin-loader.h kiba-object.h kiba-icon.h kiba-fixed-object.h kiba-separator.h kiba-title.h kiba-progress.h kiba-triangle.h kiba-bubble.h kiba-dnd-arrow.h kiba-screen.h kiba-window.h kiba-cairo-utils.h kiba-x11.h kiba-prefs.h kiba-prefs-xml.h kiba-key-file.h kiba-debug.h kiba-utils.h kiba-inline-pixbufs.h kiba-dialog.h kiba-info-win.h kiba-desktop-icon.h kiba-icon-view.h kiba-image.h kiba-menu.h kiba-menu-items.h kiba-types.h kiba-macros.h kiba-rc.h kiba-globals.h kiba-app-chooser.h kiba-desktop-editor.h kiba-desktop-icon.h kiba-icon-view-win.h kiba-svg-macro.h kiba-akamaru.h ‘/usr/include/kiba-dock’
/usr/bin/install: will not overwrite just-created `/usr/include/kiba-dock/kiba-desktop-icon.h’ with `kiba-desktop-icon.h’
make[2]: *** [install-kiba_includeHEADERS] Error 1
make[2]: Leaving directory `/home/at/kiba-dock/kiba-dock/include’
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/at/kiba-dock/kiba-dock/include’
make: *** [install-recursive] Error 1

i did not get that error in jaunty and once in karmic but i keep getting this error in karmic and lucid, and i followed your tutorial step by step. what am i doing wrong ?

---

### Post by soad6 on 2010-11-10
Does anyone know if this works in Maverick?? 10.10?? also this is a 64 bit edition. I use cairo-dock as of right now, but I would love to get kiba-dock with its physics engine running again. I used to have a deb file for it with all dependencies, I'll try looking for it to link it to the site... or see what I can find out if anyone wants to use this dock.

---

### Post by soad6 on 2010-11-10
Ok so just tested the ppa repo and no luck. It installed fine, but it will not start. If anyone has any light to shed on this issue I'd love to know. As for now Cairo-dock works ok for me, just wish I could use this awesome program.

---

### Post by soad6 on 2010-11-10
I get this error when trying to run Kiba-dock. using ubuntu 10.10 64bit. thanks for any help!

needlez@needlez-Satellite-A505:~$ kiba-dock
Error (plugin.c @ line 207):
	'/usr/lib/kiba-dock/libdbus.so' is not loadable


(kiba-dock:8044): GLib-GObject-WARNING **: cannot register existing type `GFileMonitor'

(kiba-dock:8044): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(kiba-dock:8044): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed

(kiba-dock:8044): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

---

### Post by TurtleKing on 2011-02-10
I need some help, I followed your guide to the point, but when I reach the plugin part:
```
cd kiba-plugins
./autogen.sh
make && sudo make install
cd ..
```

I get the error:

```
checking for KIBA_DOCK... no
configure: error: Package requirements (kiba-dock = 9999) were not met:

No package 'kiba-dock' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KIBA_DOCK_CFLAGS
and KIBA_DOCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
I spent the last 6 hours trying to get this cool looking dock. Any help please?

---

### Post by TurtleKing on 2011-02-10
bump

---

### Post by TurtleKing on 2011-02-10
This is like my day 3 on getting this dock. I know there are more stable ones out there, but this dock is just awesome. And I would like to try that awesome.

So any help please?

---

