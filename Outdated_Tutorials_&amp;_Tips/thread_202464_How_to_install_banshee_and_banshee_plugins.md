---
title: "How to install banshee and banshee plugins"
date: 2006-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by rekahsoft on 2006-06-23
OK...i will get right to it...If you want to keep the stable version of banshee (0.10.0) you can not install the podcast plugin or the smart playlist plugin. To install Banshee 0.10.0 and its plugins (Method 1) do this:
```
sudo apt-get install banshee
sudo apt-get build-dep banshee
sudo apt-get install automake1.9
sudo update-alternatives --set automake /usr/bin/automake-1.9
sudo ldconfig
sudo apt-get install subversion
svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins
cd banshee-official-plugins
./autogen.sh --prefix=/usr --disable-smart-playlists --disable-podcast
make
sudo make install
``` Thank cskeide for banshee build dependancies :)

Now if you can't live without the podcast and smart playlist plugins you have to build banshee from source...do this (Method 2):
```
sudo apt-get install banshee
sudo apt-get install cvs
sudo apt-get install subversion
sudo apt-get build-dep banshee
sudo apt-get install automake1.9
sudo update-alternatives --set automake /usr/bin/automake-1.9
sudo ldconfig
cvs -z3 -d:pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co -P banshee
cd banshee
./autogen.sh --prefix=/usr
make
sudo make install
cd ..
svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins
cd banshee-official-plugins
./autogen.sh --prefix=/usr
make
sudo make install
```

For both Methods:
Now open banshee (Applications>Music $ Video>Banshee) and in the banshee menu go to edit>plugins and select the plugins you want.

Uninstalling banshee (source installation [Method 2]). If you deleted you banshee directory from cvs do this:
```
sudo apt-get remove banshee
cvs -z3 -d:pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co -P banshee
cd banshee
./autogen.sh --prefix=/usr
sudo make uninstall
rm -rf ~/.gconf/apps/Banshee/
rm ~/.gnome2/banshee/banshee.db
rm -rf ~/.gnome2/banshee/
```

Unistalling Banshee (Method 1):
```
sudo apt-get remove banshee
rm -rf ~/.gconf/apps/Banshee/
rm ~/.gnome2/banshee/banshee.db
rm -rf ~/.gnome2/banshee/
```

---

### Post by billputer on 2006-06-26
```
$ sudo apt-get build-dep banshee
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for banshee could not be satisfied.

```

Any idea why this doesn't work?

---

### Post by moebis on 2006-07-01
Same problem here:
```
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for banshee could not be satisfied.

```

Plus if I try to build it (and I've tried to manually install all deps):
```
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.59
checking for automake >= 1.9...
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.22
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build banshee.  Download the appropriate package for
  from your distribution or get the source tarball at
    ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz

checking for intltool >= 0.30...
  testing intltoolize... found 0.35.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.20
Checking for required M4 macros...
  glib-gettext.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build banshee
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```

To bad there isn't a good build guide or a compiled .deb of the newest Banshee with Podcasting support. Bah!

---

### Post by mlind on 2006-07-01
[QUOTE=moebis]

Plus if I try to build it (and I've tried to manually install all deps):
```
/usr/bin/gnome-autogen.sh
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.

```
[/QUOTE]

tried installing libglib2.0-dev ?

[QUOTE=moebis]
To bad there isn't a good build guide or a compiled .deb of the newest Banshee with Podcasting support. Bah![/QUOTE]

Why don't you compile it yourself and write a guide about it?

---

### Post by moebis on 2006-07-01
[QUOTE=mlind]
tried installing libglib2.0-dev ?

Why don't you compile it yourself and write a guide about it?[/QUOTE]

Yes I got past libglib2.0-dev, but know I'm in dep hell. Something is wrong with the libcairo2 version in the repos. libcairo2-dev requires libcairo2 (1.0.4) but libcairo2 (1.1.10) is the only one available. This is why it is failing with the sudo apt-get build-dep banshee.

I have all dapper repos enabled, main, restricted, universe, multiverse. And it's a no go. It's odd that me and someone else here is having the same issue isn't it?

Hey mlind? Have you tried building the new Banshee according to this guide? And if not, why are you not contributing to a solution? I have an odd feeling if you tried you would fail too.

---

### Post by mlind on 2006-07-01
[QUOTE=moebis]Yes I got past libglib2.0-dev, but know I'm in dep hell. Something is wrong with the libcairo2 version in the repos. libcairo2-dev requires libcairo2 (1.0.4) but libcairo2 (1.1.10) is the only one available. This is why it is failing with the sudo apt-get build-dep banshee.
[/QUOTE]

```

$apt-cache policy libcairo2-dev
libcairo2-dev:
  Installed: (none)
  Candidate: 1.0.4-0ubuntu1
  Version table:
     1.0.4-0ubuntu1 0
        500 http://fi.archive.ubuntu.com dapper/main Packages

```

Do you edgy repos or something enabled ? I got only 1.0.4

[QUOTE=moebis]
Hey mlind? Have you tried building the new Banshee according to this guide? And if not, why are you not contributing to a solution? I have an odd feeling if you tried you would fail too.[/QUOTE]

I'll check this out later

---

### Post by moebis on 2006-07-01
I had compiz and beerorkid repos enabled, but I removed them, and did an apt-get update. Still shows the 1.1-10-0ubuntu1 version for libcairo2 (causes a bunch of other stuff to fail too, like libpango gtk2 etc. Can't remove it, because it will remove half of the system.

EDIT: Just tested this on another machine, same problem.

```

$ apt-cache policy libcairo2-dev libcairo2-dev:
  Installed: (none)
  Candidate: 1.0.4-0ubuntu1
  Version table:
     1.0.4-0ubuntu1 0
        500 http://us.archive.ubuntu.com dapper/main Packages
$ apt-cache policy libcairo2
libcairo2:
  Installed: 1.1.10-0ubuntu1
  Candidate: 1.1.10-0ubuntu1
  Version table:
 *** 1.1.10-0ubuntu1 0
        100 /var/lib/dpkg/status
     1.0.4-0ubuntu1 0
        500 http://us.archive.ubuntu.com dapper/main Packages

```

My other machine for libcairo2-dev shows something different: Version Table: 1.2.0-0ubuntu1 0 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Package.

How can I roll it back?

---

### Post by mlind on 2006-07-01
[QUOTE=moebis]I had compiz and beerorkid repos enabled, but I removed them, and did an apt-get update. Still shows the 1.1-10-0ubuntu1 version for libcairo2 (causes a bunch of other stuff to fail too, like libpango gtk2 etc. Can't remove it, because it will remove half of the system.[/QUOTE]

Try removing it with aptitude and see if it offers you a downgrade as a resolution.
Reinstalling from official repositories may help too.

---

### Post by moebis on 2006-07-01
IT Worked! Awesome!
$ sudo aptitude remove libcairo2

```

The following actions will resolve these dependencies:

Downgrade the following packages:
libcairo2 [1.1.10-0ubuntu1 (now) -> 1.0.4-0ubuntu1 (dapper)]

Score is -39

Accept this solution? [Y/n/q/?] Y
The following packages will be DOWNGRADED:
  libcairo2
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 305kB of archives. After unpacking 176kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com dapper/main libcairo2 1.0.4-0ubuntu1 [305kB]
Fetched 305kB in 1s (194kB/s)
dpkg - warning: downgrading libcairo2 from 1.1.10-0ubuntu1 to 1.0.4-0ubuntu1.
(Reading database ... 108873 files and directories currently installed.)
Preparing to replace libcairo2 1.1.10-0ubuntu1 (using .../libcairo2_1.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libcairo2 ...
Setting up libcairo2 (1.0.4-0ubuntu1) ...

```

Thank you so much! ubuntuforums.org rocks.

---

### Post by ericesque on 2006-07-04
I think this is currently uninstalling about half my system. haha.

---

### Post by ericesque on 2006-07-04
this... is... going.... to .....suck! 8-[

---

### Post by Hairy_Palms on 2006-07-05
i have a .deb of the itunes music store plugin available [http://www.ubuntuforums.org/attachment.php?attachmentid=12213&d=1152023396](http://www.ubuntuforums.org/attachment.php?attachmentid=12213&d=1152023396)
*note you must have already signed up for an account.

oh and btw does anyone why is it that mono applications run slower than java apps?

---

### Post by anodizer on 2006-07-05
Has anyone compiled the unofficial plugins (wikipedia, beagle etc.)?

---

### Post by ericesque on 2006-07-05
yup.  the banshee CVS ate my install.

---

### Post by elomire678 on 2006-07-06
> oh and btw does anyone why is it that mono applications run slower than java apps?
Uh... no they don't, or your java apps must run really freaking fast.

> Has anyone compiled the unofficial plugins (wikipedia, beagle etc.)?

I've compilied the Wikipeida one, but it doesn't work.. it complains about GTKEmedMozilla or something like that.

I do have the latest CVS packaged and the official plugins all packaged though for those of you running into problems. Try not to rape the bandwidth though, pretty unlikely though.

Banshee CVS
[http://home.pacbell.net/elomire/banshee_0.11-cvs-1_i386.deb](http://home.pacbell.net/elomire/banshee_0.11-cvs-1_i386.deb)
Banshee CVS Plugins
[http://home.pacbell.net/elomire/banshee-official-plugins_0.11-cvs-1_i386.deb](http://home.pacbell.net/elomire/banshee-official-plugins_0.11-cvs-1_i386.deb)

---

### Post by anodizer on 2006-07-06
I've installed your debs but unfortunately banshee doesn't start now, it hust gives a "fatal error" box. Maybe you have a guide to compile it manually from cvs? I need just the dependencies.

---

### Post by Shannon on 2006-07-06
hmm. can this work with Kubuntu? I tried it and even installed a couple extra things it said it needed and it seemed to be going well, but when I tried to run the program I got this;

```
An unhandled exception was thrown: Directory '/home/shannon/.gnome2/banshee/plugins' not found.

in <0x003ae> System.IO.Directory:GetFileSystemEntries (System.String path, System.String pattern, FileAttributes mask, FileAttributes attrs)
in <0x00011> System.IO.Directory:GetFiles (System.String path, System.String pattern)
in <0x0003d> System.IO.DirectoryInfo:GetFiles (System.String pattern)
in (wrapper remoting-invoke-with-check) System.IO.DirectoryInfo:GetFiles (string)
in <0x00025> Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin]:LoadPluginsFromDirectory (System.IO.DirectoryInfo )
in <0x00052> Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin]:LoadPlugins ()
in <0x00047> Banshee.Plugins.PluginCore:Initialize ()
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
in <0x000b3> Banshee.Base.ComponentInitializer:Run ()
in <0x0036f> Banshee.Base.Globals:Initialize ()
in <0x00548> Banshee.BansheeEntry:Startup (System.String[] args)
in <0x0001b> Banshee.BansheeEntry:Main (System.String[] args)
.NET Version: 2.0.50727.42

Assembly Version Information:

burn-sharp (0.0.0.0)
gnome-vfs-sharp (2.8.0.0)
Banshee.Dap.MassStorage (0.0.0.0)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.0.0.0)
hal-sharp (0.0.0.0)
gst-player (0.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.8.0.0)
dbus-sharp (0.60.0.0)
Mono.Posix (2.0.0.0)
Banshee.Widgets (0.0.0.0)
glade-sharp (2.8.0.0)
gnome-sharp (2.8.0.0)
gconf-sharp (2.8.0.0)
Banshee.Base (0.0.0.0)
gdk-sharp (2.8.0.0)
System (2.0.0.0)
atk-sharp (2.8.0.0)
glib-sharp (2.8.0.0)
gtk-sharp (2.8.0.0)
banshee (0.11.0.23926)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.15-25-386 i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"


```

any ideas?

---

### Post by amunimanghi on 2006-07-07
Hi,

I'm using the first method. Everything worked fine untill I ran ```
./autogen.sh --prefix=/usr --disable-smart-playlists --disable-podcast
``` Here is what happened: ```
**ameen@manghi:~$** cd banshee-official-plugins
**ameen@manghi:~/banshee-official-plugins$** ./autogen.sh --prefix=/usr --disable-smart-playlists --disable-podcast
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.59
checking for automake >= 1.9...
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.22
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.10.3
checking for intltool >= 0.30...
  testing intltoolize... found 0.35.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.20
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
Running autoconf...
Running automake-1.9...
Processing ./banshee/configure.ac
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `..'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite
**ameen@manghi:~/banshee-official-plugins$**
```
Do you think you can help?

---

### Post by elomire678 on 2006-07-07
> **anodizer said:**
> I've installed your debs but unfortunately banshee doesn't start now, it hust gives a "fatal error" box. Maybe you have a guide to compile it manually from cvs? I need just the dependencies.

What's the fatal error? You might have to add a plugins folder to .gnome2/banshee. 

I'm not an expert at packaging yet.. so there could easily be something with the .debs..
 
Tutorial-wise.. 

Well I basically followed the one in the 1st post up to a the autogen part and modded it a bit.. 

Banshee CVS
```

sudo apt-get install cvs
sudo apt-get install subversion
sudo apt-get build-dep banshee
sudo apt-get install checkinstall
sudo apt-get install automake1.9
cvs -z3 -d:pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co -P banshee
cd banshee
./autogen.sh --prefix=/usr --disable-helix --disable-docs
make
sudo checkinstall

```

Banshee Plugins for Banshee CVS
```

svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins
cd banshee-official-plugins
./autogen.sh --prefix=/usr
make
sudo checkinstall
```

This should get it built for most people. There may be other dependencies for some though. If you're missing something that's needed to build following the tutorial, just post it and I'll try to track it down.

---

### Post by Hairy_Palms on 2006-07-07
i alreay have cvs banshee,to use the wikipedia plugin youve gotta compile gecko-sharp from source and then once you install it and the plugin it crashes banshee.
> oh and btw does anyone why is it that mono applications run slower than java apps?

my java apps dont run really fast they run damn slow, its just that mono apps run really slow and suck up just as much ram as java apps.

---

### Post by mlind on 2006-07-07
I made a .deb of the plugins. It's configure using **--disable-smart-playlists** **--disable-podcast** switches, because you'll need 0.10.11 CVS build to get those working.

I'll upload the source package later, if someone wants to enable those features too.

---

### Post by anodizer on 2006-07-07
> **elomire678 said:**
> 
This should get it built for most people. There may be other dependencies for some though. If you're missing something that's needed to build following the tutorial, just post it and I'll try to track it down.

```
$ sudo apt-get build-dep banshee
E: Build-dependencies for banshee could not be satisfied.
```

And if I try to build it using .autogen:
```
Running autoconf...
configure.ac:313: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
```

---

### Post by elomire678 on 2006-07-07
> **anodizer said:**
> ```
$ sudo apt-get build-dep banshee
E: Build-dependencies for banshee could not be satisfied.
```

And if I try to build it using .autogen:
```
Running autoconf...
configure.ac:313: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
```

Hmmm.. The first problem is extremely weird. Something's up with the packages on whatever Ubuntu source you're using or you haven't done "apt-get update" lately, or you don't have universe and multiverse enabled. 

The second's because you're missing a dev package needed to compile banshee, it looks like it's libgconf-dev from that error.

---

### Post by anodizer on 2006-07-07
> **elomire678 said:**
> Hmmm.. The first problem is extremely weird. Something's up with the packages on whatever Ubuntu source you're using or you haven't done "apt-get update" lately, or you don't have universe and multiverse enabled.

I'm updating every day and of course I have universe/multiverse enabled. The installed Banshee package is 0.10.10-0ubuntu10.

Still getting the same error after installing libgconf-dev.

---

### Post by itsdaveperdue on 2006-07-07
I'm having the same problem.  Everytime I run #./autogen.sh intltoolize is telling me my Makefile.in.in is out of date.  I've tried deleting the file, but when it gets made again it still says out of date...

By the way I'm running SuSE 10.1. heh, I've been googling this problem trying to figure it out and this is the first forum I've come across that's got this problem.  So it may not be just Ubuntu.

> **amunimanghi said:**
> Hi,

I'm using the first method. Everything worked fine untill I ran ```
./autogen.sh --prefix=/usr --disable-smart-playlists --disable-podcast
``` Here is what happened: ```
**ameen@manghi:~$** cd banshee-official-plugins
**ameen@manghi:~/banshee-official-plugins$** ./autogen.sh --prefix=/usr --disable-smart-playlists --disable-podcast
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.59
checking for automake >= 1.9...
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.22
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.10.3
checking for intltool >= 0.30...
  testing intltoolize... found 0.35.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.20
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
Running autoconf...
Running automake-1.9...
Processing ./banshee/configure.ac
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `..'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite
**ameen@manghi:~/banshee-official-plugins$**
```
Do you think you can help?

---

### Post by itsdaveperdue on 2006-07-07
Okay, so I've edited /usr/bin/intltoolize and commented out the part at the bottom that checks for the Makefile.in.in  Seems like it worked out just fine.  There was one problem I ran into while running make, but I took care of that fine.  

If you're going to do what I did just make sure to backup your intltoolize before editing.

---

### Post by mlind on 2006-07-07
> **itsdaveperdue said:**
> Okay, so I've edited /usr/bin/intltoolize and commented out the part at the bottom that checks for the Makefile.in.in  Seems like it worked out just fine.  There was one problem I ran into while running make, but I took care of that fine.  

If you're going to do what I did just make sure to backup your intltoolize before editing.

I've packaged this plugin without any Makefile.in.in trouble on Dapper. I suggest to build it on clean-room environment, so that none other installed
tools don't interfiere. Having different autotools and autonconfs installed can make things messy.


These packages were required for the build process
```

autotools-dev, automake1.9, gnome-common, libglib2.0-dev,
libmono-dev (>= 1.1.13), mono-mcs (>=1.1.13), mono-gmcs (>= 1.1.13),
gtk-sharp2, banshee (>= 0.10.10)

```

---

### Post by anodizer on 2006-07-07
mlind maybe you could build a CVS banshee package too?

---

### Post by mlind on 2006-07-08
> **anodizer said:**
> mlind maybe you could build a CVS banshee package too?

Okay, I'll see what I can do. It would be great if there was someplace to host these .debs.

---

### Post by anodizer on 2006-07-08
I think I can host them on my ISP's ftp.

---

### Post by Technoviking on 2006-07-08
> **mlind said:**
> Okay, I'll see what I can do. It would be great if there was someplace to host these .debs.

I could host them, but now way to make a debian repo to get it via apt-get (no command line access).

---

### Post by mlind on 2006-07-08
> **Mike said:**
> I could host them, but now way to make a debian repo to get it via apt-get (no command line access).

Sounds good to me. I got these packages working, where should I sent these binaries
(and source packages too) ?

---

### Post by mlind on 2006-07-08
If someone wants to try these packages, here's how to install. CVS snapshot requires newer ipod library. MTP support is not enabled, and plugins are built to support new 0.10.11 features.

```

sudo aptitude install binfmt-support libdbus-1-cil libgconf2.0-cil libglade2.0-cil libglib2.0-cil libgnome2.0-cil libgtk2.0-cil libmono0 mono-classlib-1.0 mono-classlib-2.0 mono-common mono-jit

(extract archive or install contents using gdebi)
sudo dpkg -i libipoddevice0_0.4.6-cvs20060707-0ubuntu1_i386.deb
sudo dpkg -i banshee_0.10.11-cvs20060708-0ubuntu1_i386.deb
sudo dpkg -i banshee-official-plugins_20060708-0ubuntu1_i386.deb

```
**archive**: [http://www.freefilehoster.com/uploads/1152406895banshee_0.10.11-cvs20060708-dapper.tar.gz](http://www.freefilehoster.com/uploads/1152406895banshee_0.10.11-cvs20060708-dapper.tar.gz)

---

### Post by joakim2 on 2006-07-08
> **mlind said:**
> If someone wants to try these packages, here's how to install. CVS snapshot requires newer ipod library. MTP support is not enabled, and plugins are built to support new 0.10.11 features.

```

sudo aptitude install binfmt-support libdbus-1-cil libgconf2.0-cil libglade2.0-cil libglib2.0-cil libgnome2.0-cil libgtk2.0-cil libmono0 mono-classlib-1.0 mono-classlib-2.0 mono-common mono-jit

(extract archive or install contents using gdebi)
sudo dpkg -i libipoddevice0_0.4.6-cvs20060707-0ubuntu1_i386.deb
sudo dpkg -i banshee_0.10.11-cvs20060708-0ubuntu1_i386.deb
sudo dpkg -i banshee-official-plugins_20060708-0ubuntu1_i386.deb

```
[http://www.freefilehoster.com/uploads/1152405671banshee_0.10.11-cvs20060708-dapper.tar.gz](http://www.freefilehoster.com/uploads/1152405671banshee_0.10.11-cvs20060708-dapper.tar.gz)


Cool, if you enable DAAP in this build you will win one more user. ;)

---

### Post by mlind on 2006-07-08
> **joakim2 said:**
> Cool, if you enable DAAP in this build you will win one more user. ;)

oops, daap was supposed to be in that archive. I re-uploaded it.

---

### Post by amunimanghi on 2006-07-08
> ```
sudo aptitude install binfmt-support libdbus-1-cil libgconf2.0-cil libglade2.0-cil libglib2.0-cil libgnome2.0-cil libgtk2.0-cil libmono0 mono-classlib-1.0 mono-classlib-2.0 mono-common mono-jit

(extract archive or install contents using gdebi)
sudo dpkg -i libipoddevice0_0.4.6-cvs20060707-0ubuntu1_i386.deb
sudo dpkg -i banshee_0.10.11-cvs20060708-0ubuntu1_i386.deb
sudo dpkg -i banshee-official-plugins_20060708-0ubuntu1_i386.deb
```

I have all the necessary files that you mentioned using sudo aptitude....
I just have one question, where do i get the debs?

---

### Post by mlind on 2006-07-08
> **amunimanghi said:**
> 
I have all the necessary files that you mentioned using sudo aptitude....
I just have one question, where do i get the debs?

There's a link on below the instructions

---

### Post by amunimanghi on 2006-07-08
Okay, I installed the plugins but when I go to run Banshee, nothing happens. I went to the terminal and I got this: ```
ameen@manghi:~$ banshee
&#65279;Debug: [7/8/2006 7:01:36 PM] (Default player engine) - GStreamer 0.10
Debug: [7/8/2006 7:01:36 PM] (Audio CD Core Initialized) -

** (/usr/lib/banshee/banshee.exe:14807): WARNING **: nautilus_burn_drive_copy is deprecated please use nautilus_burn_drive_ref() instead

** (/usr/lib/banshee/banshee.exe:14807): WARNING **: nautilus_burn_drive_copy is deprecated please use nautilus_burn_drive_ref() instead
Segmentation fault
ameen@manghi:~$
```

Can I disable the ability to burn? I don't mind it at all.

---

### Post by joakim2 on 2006-07-08
I can't seem to get the it to run more than once :( The first time it starts up (after having cleaned everything banshee from ~/.gnome2*) it starts and runs OK, subsequent runs yield:

$ banshee --debug
** Running Banshee in Debug Mode **
&#65279;Warning: [7/8/2006 8:48:56 PM] (Cannot connect to NetworkManager) - An available, working network connection will be assumed
Debug: [7/8/2006 8:48:57 PM] (Default player engine) - GStreamer 0.10
Debug: [7/8/2006 8:48:58 PM] (Audio CD Core Initialised) -

** (/usr/lib/banshee/banshee.exe:25746): WARNING **: nautilus_burn_drive_copy is deprecated please use nautilus_burn_drive_ref() instead
Segmentation fault

---

### Post by mlind on 2006-07-09
yeah it crashes for me too now. I'll try to fix it.

---

### Post by anodizer on 2006-07-09
I compiled it yesterday and got a seg fault too. I fixed it after removing banshee 0.10.10 (the version installed from the official repos) only to get another seg fault when I compiled the official plugins, so probably one of the plugins is causing this error.

---

### Post by mlind on 2006-07-09
> **anodizer said:**
> I compiled it yesterday and got a seg fault too. I fixed it after removing banshee 0.10.10 (the version installed from the official repos) only to get another seg fault when I compiled the official plugins, so probably one of the plugins is causing this error.

If your getting the error that plugins directory doesn't exist, apply 06_userdir_missing patch. Dapper also needs 07_libdbus-glib patch. I recall patch 06 needed --fuzz=1 to apply cleanily. I'll attach the patches here.


I can send you my source .deb package, which you can easily upgrade just by doing *cvs up* and then repackage it using pbuilder.

---

### Post by anodizer on 2006-07-09
Ok, I'll try it later. Btw did you get an error about libXrender.la during the compilinng process? There is a bug report about this which is marked as fixed, so I'm wondering if this appeared again or it's just because of the patched beerorkid's libcairo packages.

edit: this libdbus patch is great. I had to downgrade dbus for banshee to compile.

---

### Post by PingunZ on 2006-07-09
Works perfectly, only a little typo
should be ```
sudo apt-get source banshee
sudo apt-get build-dep banshee
```
instead of sudo apt-get install banshee ;)

Grtz PingunZ

---

### Post by amunimanghi on 2006-07-09
What about this: > ** (/usr/lib/banshee/banshee.exe:14807): WARNING **: nautilus_burn_drive_copy is deprecated please use nautilus_burn_drive_ref() instead

** (/usr/lib/banshee/banshee.exe:14807): WARNING **: nautilus_burn_drive_copy is deprecated please use nautilus_burn_drive_ref() instead
Segmentation fault Does anyone know how to fix this?

---

### Post by mlind on 2006-07-09
> **anodizer said:**
> Ok, I'll try it later. Btw did you get an error about libXrender.la during the compilinng process? There is a bug report about this which is marked as fixed, so I'm wondering if this appeared again or it's just because of the patched beerorkid's libcairo packages.

edit: this libdbus patch is great. I had to downgrade dbus for banshee to compile.

nope, no erros from libXrender.la. I'm not using any foreign libraries, execpt what banshee requires.

---

### Post by mlind on 2006-07-09
> **amunimanghi said:**
> What about this:  Does anyone know how to fix this?

I'm currently waiting response from banshee devs about a crash. I don't think that segmentation fault is caused by the warning message. It's only warning, not error.

---

### Post by amunimanghi on 2006-07-09
I actually fixed it. I was in the configuration editor trying to get my trash can on the destkop. I was curious and looked at the Banshee section. There it had all the plugins that I wanted installed. I just looked over each one and unchecked each one that I didn't want. I ran banshee by clicking on the icon in the applications menu and it worked.

To get there go to: 
Application => System Tools => Configuration Editor
.............................................................|
.............................................................|=Apps =>Banshee

---

### Post by anodizer on 2006-07-10
Yep, actually Internet Radio plugin is causing the trouble, if you disable this banshee should work.
"Write cd" option isn't working either, therefore there are the warnings.

edit: Hmm, weird. I enabled Internet radio again, via Banshee plugins preferences this time, and it works ok now with all plugins enabled. Maybe there is a bug with iradio plugin initialising itself for first time.

---

### Post by mlind on 2006-07-10
> **anodizer said:**
> Yep, actually Internet Radio plugin is causing the trouble, if you disable this banshee should work.
"Write cd" option isn't working either, therefore there are the warnings.

edit: Hmm, weird. I enabled Internet radio again, via Banshee plugins preferences this time, and it works ok now with all plugins enabled. Maybe there is a bug with iradio plugin initialising itself for first time.

I'll try rebuilding the plugins too and put this stuff on external repository.

---

### Post by joakim2 on 2006-07-10
> **anodizer said:**
> Yep, actually Internet Radio plugin is causing the trouble, if you disable this banshee should work.
"Write cd" option isn't working either, therefore there are the warnings.

edit: Hmm, weird. I enabled Internet radio again, via Banshee plugins preferences this time, and it works ok now with all plugins enabled. Maybe there is a bug with iradio plugin initialising itself for first time.

I dunno man... it seems to be doing some weird wacky shtuff over here:

$ rm -rf ~/.gconf/apps/Banshee/
$ rm -rf ~/.gnome2/banshee/banshee.db
$ rm -rf ~/.gnome2/banshee/
$ banshee
&#65279;Creating track table
Creating playlists table
Creating playlistentries table
Debug: [7/10/2006 1:44:00 PM] (Default player engine) - GStreamer 0.10
Debug: [7/10/2006 1:44:00 PM] (Audio CD Core Initialised) -

** (/usr/lib/banshee/banshee.exe:12470): WARNING **: nautilus_burn_drive_copy is deprecated please use nautilus_burn_drive_ref() instead
Segmentation fault

---

### Post by mlind on 2006-07-11
I put banshee packages and banshee-official plugins to
```

deb-src http://www.elisanet.fi/mlind/ubuntu dapper experimental

```

---

### Post by lazyd2 on 2006-07-11
Yeap, I've got the same behaviour with the iRadio plugin enabled....

---

### Post by bsalt on 2006-07-13
Could anyone make a .deb package of banshee with mtp support enabled? I have no clue how to enable this, and I would really like to be fully away from MS Windows... stupid PlaysForSure devices...

---

### Post by RAOF on 2006-07-19
> **bsalt said:**
> Could anyone make a .deb package of banshee with mtp support enabled? I have no clue how to enable this, and I would really like to be fully away from MS Windows... stupid PlaysForSure devices...
You need a couple of libraries from SVN to get mtp working.  I'll see how easy it is to add those to my repository.

For those interested, I've got an AMD64 repository with Banshee-0.11.0-cvs and all the banshee-official-plugins.  It seems to need a newer version of mono than is shipped with Dapper*, so there are **also** mono packages backported from Edgy.  If you're not on AMD64 you can still get the deb-src and **apt-get source -b banshee**.

Check out [raof.dyndns.org/falcon](raof.dyndns.org/falcon).  Be sure to use the mirrors - they've got **much** better bandwith and uptime.  The mirrors are at [ubuntu.moshen.de](ubuntu.moshen.de) and the new one, [ubuntu.systemadministrator.org](ubuntu.systemadministrator.org).

*At least, it would always segfault when I tried to import a file.  With the new mono it no longer does that, and it runs pretty much rock solid.

---

### Post by gurgle on 2006-07-19
raof, can your repo be used with 32bit? 

i downgraded my shiznit because of the multiarch drama. i just wanted 32bit apps to work.

---

### Post by RAOF on 2006-07-19
> **gurgle said:**
> raof, can your repo be used with 32bit? 

i downgraded my shiznit because of the multiarch drama. i just wanted 32bit apps to work.
Currently it only builds AMD64 binaries, but you can certainly use the deb-src lines.  Add them, then you can **apt-get source -b *foo***.  It's not as nice, but it works :).  I've been thinking of branching out into i386, now that there's not only packages you couldn't get for AMD64 in there.  I'll do it, just as soon as I can get pbuild to build i386 binaries :).

@bsalt - I've built a Banshee .deb with MTP support (and the requisite libgphoto2-2-cil packages).  Of course, they're for AMD64 :).  I haven't yet pushed them to the mirrors, so they're currently unavailable, but I should be able to put them up this evening.

---

### Post by plutoprime on 2006-07-20
Failed to fetch [http://ubuntu.moshen.de/dists/dapper/Release](http://ubuntu.moshen.de/dists/dapper/Release)  Unable to find expected entry  mono/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

What gives?

---

### Post by RAOF on 2006-07-20
I haven't built anything for i386 (I'm working on it).  That's an AMD64 repository :)

You can still use the deb-src line, and **apt-get source -b *packagename***, though.

---

### Post by Bruno Amaral on 2006-07-20
i tried following method two, but got the message:
You need to install gnome-common from the GNOME CVS

while running : ./autogen.sh --prefix=/usr
I'm using kubuntu, could this have something to do with it?

--edit

Ok, after i ran sudo apt-get install gnome-common, I proceded and got this error message while running Make:
make[3]: *** [banshee.exe] Error 1
make[3]: Leaving directory `/home/bruno/banshee/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bruno/banshee/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bruno/banshee'
make: *** [all] Error 2

---

### Post by gurgle on 2006-07-24
how can i turn off the temporary internet option? i cant get in to banshee, it crashes out on me

---

### Post by joakim2 on 2006-07-24
> **gurgle said:**
> how can i turn off the temporary internet option? i cant get in to banshee, it crashes out on me

gconf-editor -> apps -> Banshee -> iradio

---

### Post by bailey_ca on 2006-07-28
Hi rekahsoft,
Thanks for the walkthrough! I was running into some problems after I followed it, specifically with iPod support (it wouldn't sync.)

I spent the better part of the day chatting with people on the #banshee IRC channel, and they recommended a few steps that cleared it up all the problems.

[LIST=1]
[*]After you apt-get build-dep and download the cvs source, be sure to ```
apt-get remove banshee banshee-daap
```The consensus was building 0.11 on top of 0.10 was a bad idea. One of the errors I was getting with iPod syncing in 0.11 was related to a function that exists in 0.10 but not 0.11. (BTW, the exact quote was "omg... post and tell them they need to remove banshee before installing from CVS!" :))
[*]You probably *should* update libipoddevice and ipod-sharp to the latest versions. I'll see if I can come up with instructions for that.
[*]YMMV, but the iRadio plugin works fine for me, it's the Podcast one that causes Banshee to segfault. I just ran ./autogen with ```
--disable-podcast
``` as an option.
[*]If autogen complains about monodocs, add the ```
--disable-docs
``` switch. As a bonus, it speeds up the process immensely.
[/LIST]

---

### Post by bailey_ca on 2006-07-29
Here we go! Just did it on my home machine:

---Quasi-HOWTO starts here----

YMMV, this is what worked on my system. I may have missed some steps if you
have a vanilla Dapper box, eg, I can't remember if I already installed Mono
before I wrote all this down.

Judging by my Synaptic history, I think you need to install mono-jit,
mono-common, mono-classlib-1.0 and libmono0.

If any of the steps below fail, post the error notice and this document will be updated!

**To install the latest, greatest Banshee:**


[list=1]
[*]sudo apt-get install banshee banshee-daap subversion cvs automake1.9
[*]sudo apt-get build-dep banshee
[*]sudo apt-get remove banshee banshee-daap
[*]sudo rm -rf /usr/lib/banshee
[*]sudo rm -f /usr/bin/banshee
[*]sudo update-alternatives --set automake /usr/bin/automake-1.9
[*]sudo ldconfig
[*]cd /tmp
[*]cvs -z3 -d:pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co -P libipoddevice
[*]svn co svn://svn.myrealbox.com/source/trunk/ipod-sharp
[*]cvs -z3 -d:pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co -P banshee
[*]svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins
[*]sudo apt-get remove libipoddevice0 libipod-cil
[*]sudo apt-get install libgtop2-7 libgtop2-dev
[*]cd /tmp/libipoddevice
[*]./autogen.sh --prefix=/usr
[*]make && sudo make install
[*]sudo apt-get install mono-gac
[*]cd /tmp/ipod-sharp
[*]./autogen.sh --prefix=/usr --disable-docs
[*]make && sudo make install
[*]cd /tmp/banshee
[*]./autogen.sh --prefix=/usr --enable-ipod --disable-docs
[*]cd /tmp/banshee-official-plugins
[*]./autogen.sh --prefix=/usr --disable-podcast --disable-docs
[*]make && sudo make install
[/list]
**To test:**
banshee --debug

If all goes well, you should only see warning messages, no fatal errors,
segmentation faults (segfaults), etc.

**iPod warning:**
If you're doing something weird like I am, like trying to sync a Windows-formatted iPod on a Mac and use it with Banshee, it's pretty much guaranteed to not work. If I sync my iPod with my iBook, Banshee can understand the iTunes library on the iPod, though it doesn't show playlists.

If I sync my iPod using Banshee, iTunes sees the correct number of songs, but the library is empty.

For the time being, if you're using your iPod anywhere but on your own Linux box, I recommend just syncing it with iTunes and using it as a read-only device with Banshee.

---

### Post by denisesballs on 2006-07-31
Oops. Double post. See below

---

### Post by denisesballs on 2006-07-31
bailey_ca great tutorial. I have a few edits:

#14 should be:

```
sudo apt-get **[color=red]install[/color]** libgtop2-7 libgtop2-dev
```

and when I do #20, I get this error:

```
Selecting previously deselected package ipod-sharp.
(Reading database ... 144450 files and directories currently installed.)
Unpacking ipod-sharp (from .../ipod-sharp_svn1-1_i386.deb) ...
dpkg: error processing /home/jesse/systems/ipod-sharp/ipod-sharp_svn1-1_i386.deb (--install):
 trying to overwrite `/usr/share/automake-1.9/INSTALL', which is also in package automake1.9
Errors were encountered while processing:
/home/jesse/systems/ipod-sharp/ipod-sharp_svn1-1_i386.deb
```

So I had to do:

```
sudo mv /usr/share/automake-1.9/INSTALL{,.bak}
```

then I could do

```
./autogen.sh --prefix=/usr **[color=red]--disable-docs**[/color]
```

You should add the --disable-docs to #20 as well otherwise you get complaints about mdassembler not being installed.

Then move it back:

```
sudo mv /usr/share/automake-1.9/INSTALL.bak /usr/share/automake-1.9/INSTALL
```

**[color=red]EDIT![/color]**

I figured out why it was crashing. Music applet - [http://web.ics.purdue.edu/~kuliniew/music-applet/](http://web.ics.purdue.edu/~kuliniew/music-applet/) - isn't compatible with the newest Banshee yet. Woo hoo for working latest Banshee and plugins!.

Great job bailey_ca, and thanks for the howto!

**[color=red]EDIT AGAIN![/color]**

One more edit, there's a typo in step 1. "bashee" should be "banshee"

---

### Post by mlind on 2006-07-31
> **denisesballs said:**
> 
I figured out why it was crashing. Music applet - [http://web.ics.purdue.edu/~kuliniew/music-applet/](http://web.ics.purdue.edu/~kuliniew/music-applet/) - isn't compatible with the newest Banshee yet. Woo hoo for working latest Banshee and plugins!.

Yeah, I had that very same issue myself. Looks like music-applet sends illegal request using DBUS and Banshee doesn't like it :(
I use that applet with Rhythmbox, so I just *killall music-applet* while using Banshee (and leave that "reload dialog" on background).

---

### Post by denisesballs on 2006-07-31
Anyone get the podcast plugin compiled?

---

### Post by mlind on 2006-07-31
> **denisesballs said:**
> Anyone get the podcast plugin compiled?

You can grab cvs version of banshee-official-plugins from
```

deb http://www.elisanet.fi/mlind/ubuntu dapper experimental

```

That official-plugins trunk was broken few days ago when I last time tried it.

---

### Post by denisesballs on 2006-07-31
> **mlind said:**
> You can grab cvs version of banshee-official-plugins from
```

deb http://www.elisanet.fi/mlind/ubuntu dapper experimental

```

That official-plugins trunk was broken few days ago when I last time tried it.

Where's the key?

---

### Post by mlind on 2006-07-31
> **denisesballs said:**
> Where's the key?

You can get if from public key server (It's not mandatory though).
```

gpg --keyserver pgp.mit.edu --recv-key D0AFFF5E937215FF
gpg -a --export D0AFFF5E937215FF | sudo apt-key add -

```

---

### Post by denisesballs on 2006-07-31
Are you sure that's the right repo?

```
jesse@homedapper:~/systems$ sudo apt-get install banshee-official-plugins
Reading package lists... Done
Building dependency tree... Done
Package banshee-official-plugins is not available, but is referred to by another package.
```

---

### Post by mlind on 2006-07-31
> **denisesballs said:**
> Are you sure that's the right repo?

```
jesse@homedapper:~/systems$ sudo apt-get install banshee-official-plugins
Reading package lists... Done
Building dependency tree... Done
Package banshee-official-plugins is not available, but is referred to by another package.
```

oops, package never went to upload queue. Should be okay now.

---

### Post by denisesballs on 2006-07-31
Ok mlind, now they install fine:

```
jesse@homedapper:~/systems/banshee-official-plugins$ sudo apt-get install banshee-official-plugins
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  banshee-official-plugins
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B/220kB of archives.
After unpacking 659kB of additional disk space will be used.
Selecting previously deselected package banshee-official-plugins.
(Reading database ... 144448 files and directories currently installed.)
Unpacking banshee-official-plugins (from .../banshee-official-plugins_0.10.11+svn20060720-0ubuntu1_i386.deb) ...
Setting up banshee-official-plugins (0.10.11+svn20060720-0ubuntu1) ...
```

However Banshee crashes now with pretty much the same error a lot of us were getting when trying to compile the podcast plugin:

```
An unhandled exception was thrown: Method not found: 'Banshee.Sources.PlaylistSource.get_Playlists'.

in (unmanaged) 0xb7e9b152
in <0x0003c> (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_SourceAddedArgs (Banshee.Sources.SourceAddedArgs)
in <0x00026> (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_SourceAddedArgs (Banshee.Sources.SourceAddedArgs)
in <0x0004e> <>AnonHelp<16>:<#AnonymousMethod>5 (object,System.EventArgs)
in <0x00041> (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
in <0x00047> Banshee.Base.ThreadAssist:ProxyToMain (System.EventHandler)
in <0x0026d> Banshee.Sources.SourceManager:AddSource (Banshee.Sources.Source,bool)
in <0x0003c> Banshee.PlayerUI:OnLibraryReloaded (object,System.EventArgs)
in <0x00041> (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
in <0x00035> <>AnonHelp<40>:<#AnonymousMethod>57 (object,System.EventArgs)
in <0x00041> (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
in <0x0001a> InvokeCB:Invoke ()
in <0x00037> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> TimeoutProxy:Handler ()
in <0x00036> (wrapper native-to-managed) TimeoutProxy:Handler ()
in (unmanaged) 0xb7d654a7
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x005da> Banshee.BansheeEntry:Startup (string[])
in <0x0001b> Banshee.BansheeEntry:Main (string[])

.NET Version: 2.0.50727.42

Assembly Version Information:

Mono.CompilerServices.SymbolWriter (2.0.0.0)
DBusProxy (0.0.0.0)
Mono.Security (2.0.0.0)
SmartPlaylists (0.11.0.0)
Recommendation (0.11.0.0)
Radio (0.11.0.0)
System.Xml (2.0.0.0)
Podcast (0.11.0.0)
NotificationAreaIcon (0.0.0.0)
MiniMode (0.11.0.0)
MusicBrainz (0.0.0.0)
MetadataSearch (0.0.0.0)
MMKeys (0.0.0.0)
avahi-sharp (1.0.0.0)
Daap (1.0.0.0)
Audioscrobbler (0.0.0.0)
burn-sharp (0.0.0.0)
ipod-sharp-ui (0.0.1.0)
gnome-vfs-sharp (2.8.0.0)
Banshee.Dap.MassStorage (0.0.0.0)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.0.0.0)
hal-sharp (0.0.0.0)
gst-player (0.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.8.0.0)
dbus-sharp (0.60.0.0)
Mono.Posix (2.0.0.0)
Banshee.Widgets (0.0.0.0)
glade-sharp (2.8.0.0)
gnome-sharp (2.8.0.0)
gconf-sharp (2.8.0.0)
Banshee.Base (0.0.0.0)
gdk-sharp (2.8.0.0)
System (2.0.0.0)
atk-sharp (2.8.0.0)
glib-sharp (2.8.0.0)
gtk-sharp (2.8.0.0)
banshee (0.11.0.871)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.15-25-k7 i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"
```

How did you get the podcast plugin compiled?

---

### Post by mlind on 2006-07-31
> **denisesballs said:**
> 
However Banshee crashes now with pretty much the same error a lot of us were getting when trying to compile the podcast plugin:

[code]An unhandled exception was thrown: Method not found: 'Banshee.Sources.PlaylistSource.get_Playlists'.

How did you get the podcast plugin compiled?

I created .deb package from banshee-official-plugins module, which contains podcast plugin. You can get the source package from same repository and try to rebuild it yourself.

Try installing banshee package from same repository and see if basnhee still crashes. I checked /src/Banshee.Base/Sources/PlaylistSource.cs and it contains getter for "playlists" enumeration.

If it fixes the issue for you, then there's something wrong how you've compiled banshee from cvs.

---

### Post by denisesballs on 2006-07-31
> **mlind said:**
> I created .deb package from banshee-official-plugins module, which contains podcast plugin. You can get the source package from same repository and try to rebuild it yourself.

Try installing banshee package from same repository and see if basnhee still crashes. I checked /src/Banshee.Base/Sources/PlaylistSource.cs and it contains getter for "playlists" enumeration.

If it fixes the issue for you, then there's something wrong how you've compiled banshee from cvs.

I compiled Banshee and banshee-plugins-official both from the latest cvs. I cannot compile the podcast plugin at all, I have to throw --disable-podcast, just like was in the tutorial above. When I install the plugins from your deb, I get the same error as when I try to compile the the plugins with the podcast. I haven't seen anyone able to compile that one yet.

---

### Post by mlind on 2006-07-31
> **denisesballs said:**
> I compiled Banshee and banshee-plugins-official both from the latest cvs. I cannot compile the podcast plugin at all, I have to throw --disable-podcast, just like was in the tutorial above. When I install the plugins from your deb, I get the same error as when I try to compile the the plugins with the podcast. I haven't seen anyone able to compile that one yet.

That podcasting plugin requires banshee >= 0.10.11, but since we're all compiling it from cvs that's no problem.

Add same experimental repository as **deb-src**, then
```

mkdir /tmp/test
cd /tmp/test
apt-get source banshee-official-plugins

```

use *dpkg-buildpackage -rfakeroot -us -uc* to test how it builds. You'll need banshee package from the repository for plugins to compile.

---

### Post by bailey_ca on 2006-07-31
> **denisesballs said:**
> bailey_ca great tutorial. I have a few edits:

#14 should be:

```
sudo apt-get **[color=red]install[/color]** libgtop2-7 libgtop2-dev
```

Whoops! I even misspelt it a couple of times when trying to do the install. Lousy muscle memory related to typing "bash". Hehe. (Hopefully all other typos corrected as well.)

> **denisesballs said:**
> and when I do #20, I get this error:

```
Selecting previously deselected package ipod-sharp.
(Reading database ... 144450 files and directories currently installed.)
Unpacking ipod-sharp (from .../ipod-sharp_svn1-1_i386.deb) ...
dpkg: error processing /home/jesse/systems/ipod-sharp/ipod-sharp_svn1-1_i386.deb (--install):
 trying to overwrite `/usr/share/automake-1.9/INSTALL', which is also in package automake1.9
Errors were encountered while processing:
/home/jesse/systems/ipod-sharp/ipod-sharp_svn1-1_i386.deb
```


Really? That's #20? That's odd, isn't it? You shouldn't be interacting with .debs at all. (I'm relatively new to Debian-based systems, so is this just something I haven't run up against yet?)

> **denisesballs said:**
> **[color=red]EDIT![/color]**

I figured out why it was crashing. Music applet - [http://web.ics.purdue.edu/~kuliniew/music-applet/](http://web.ics.purdue.edu/~kuliniew/music-applet/) - isn't compatible with the newest Banshee yet.
Bah! I used Rhythmbox Applet for ages-- I didn't even know Music Applet existed! Now that I know it does, I want it to work! :lol: 

> **denisesballs said:**
> Woo hoo for working latest Banshee and plugins!.
Amen. I dunno about you, but Banshee CVS is a **huge** improvement for me, resource-wise.

0.10 would stutter when I was doing simple stuff like using Nautilus. 0.11 is rock-solid. (I'm on a freebie P3 1 GHz rescued from the recycle pile at work. O:))

Also, Mini mode is just beautiful. Kinda makes mini iTunes look a bit dated and pointless-- oh wait! (And this is coming from an Apple guy...) ;)

> **denisesballs said:**
> Great job bailey_ca, and thanks for the howto!

Thanks; I'm actually just happy to finally be able to contribute something back to the community!

---

### Post by elomire678 on 2006-08-01
> **denisesballs said:**
> I compiled Banshee and banshee-plugins-official both from the latest cvs. I cannot compile the podcast plugin at all, I have to throw --disable-podcast, just like was in the tutorial above. When I install the plugins from your deb, I get the same error as when I try to compile the the plugins with the podcast. I haven't seen anyone able to compile that one yet.

Aaron Brockover just redid much of Banshee's internals in the last few days, and it's a known bug that the podcast plugin doesn't work with the latest cvs. The podcast plugin's maintainer just a few hours ago committed an update to his plugin, so hopefully it'll compile with the newer banshees right now. But sadly the latest updated in Banshee's cvs doesn't want to compile so I can't say for sure right now.

#Update

Well I must've caught an update in progress, because after updating the cvs again Banshee compiles. The Podcast plugin works again.

---

### Post by denisesballs on 2006-08-01
> **bailey_ca said:**
> Really? That's #20? That's odd, isn't it? You shouldn't be interacting with .debs at all. (I'm relatively new to Debian-based systems, so is this just something I haven't run up against yet?)

Yeah it is kinda odd. I'm not sure why I had to do that.

> Bah! I used Rhythmbox Applet for ages-- I didn't even know Music Applet existed! Now that I know it does, I want it to work! :lol: 

Well I've been in contact with the developer for quite some time working with him and abock on the crashes so hopefully we'll have it fixed again. It does work with the stable verion of Banshee (.10), but not the CVS yet. He's very helpful and responsive though, here's an excerpt from his latest e-mail so you can see what's going on:

> Looks like another variation on the same problem as before.  One of
Banshee's string-returning DBus methods returns null, which is a no-no
for DBus.  But since the crash happens after Banshee's code has finished
executing, the stack trace gives no information on just *where* the
errant method is.

Can you provide a specific list of instructions on how to reproduce
this, starting with launching Banshee and Music Applet?  Pay particular
attention to the time between the stream is first "opened" and when
Music Applet crashes Banshee, and whether Banshee is displaying the
stream's metadata in its own window at the time of the crash.

My hunch here is that Banshee isn't pulling metadata from .ogg streams,
whereas it can with .mp3 streams.  Could you try some other streams too
and see if the problem only and/or always happens with .ogg streams?

If it sounds like I'm being picky about what information I need, well,
it's because I am.  There's a good risk of timing issues complicating
things, what with two separate apps *and* a network stream all
interacting with each other, so I'm trying to figure out exactly what
set of conditions triggers the crash.

Thanks.

I think he may have missed my point that it crashes Banshee immediately on startup, instead of crashing when loading an internet stream, which was the problem before.

---

### Post by mlind on 2006-08-01
> **denisesballs said:**
> 
I think he may have missed my point that it crashes Banshee immediately on startup, instead of crashing when loading an internet stream, which was the problem before.

Do you mean developer of bashee or music-applet? You can direct him/her to this bug for details of that crash [http://bugzilla.gnome.org/show_bug.cgi?id=347028](http://bugzilla.gnome.org/show_bug.cgi?id=347028)

---

### Post by denisesballs on 2006-08-01
> **mlind said:**
> Do you mean developer of bashee or music-applet? You can direct him/her to this bug for details of that crash [http://bugzilla.gnome.org/show_bug.cgi?id=347028](http://bugzilla.gnome.org/show_bug.cgi?id=347028)

Music Applet.

---

### Post by newen on 2006-08-03
I´m trying to build the banshee plugins from [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org)  using

```
apt-get source -b banshee-official-plugins
```

but I get this error

```
dh_clideps

** (process:20599): WARNING **: The following assembly referenced from /home/newen/banshee-official-plugins-svn-r184/debian/banshee-official-plugins/usr/lib/banshee/Banshee.Plugins/MiniMode.dll could not be loaded:
     Assembly:   Banshee.Base    (assemblyref_index=0)
     Version:    0.0.0.0
     Public Key: (none)
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/newen/banshee-official-plugins-svn-r184/debian/banshee-official-plugins/usr/lib/banshee/Banshee.Plugins/).


** (process:20599): WARNING **: Could not load file or assembly 'Banshee.Base, Version=0.0.0.0, Culture=neutral' or one of its dependencies.

** (process:20599): WARNING **: Missing method .ctor in assembly /home/newen/banshee-official-plugins-svn-r184/debian/banshee-official-plugins/usr/lib/banshee/Banshee.Plugins/MiniMode.dll, type Mono.Gettext.AssemblyCatalogAttribute

** ERROR **: Can't find custom attr constructor image: /home/newen/banshee-official-plugins-svn-r184/debian/banshee-official-plugins/usr/lib/banshee/Banshee.Plugins/MiniMode.dll mtoken: 0x0a000094
aborting...
sh: line 1: 20599 Aborted                 LANG=C /usr/bin/monodis --assemblyref MiniMode.dll 2>&1 >/tmp/dh_clideps.AfRD
dh_clideps: cli_parser call failed: 'LANG=C /usr/bin/monodis --assemblyref MiniMode.dll 2>&1 > /tmp/dh_clideps.AfRD' rc: 34304 output:
```

I have already compiled and installed without any problems banshee, so I don´t understand why I get this error.

---

### Post by one_stinky_bum on 2006-08-04
When I do #16, I get the following error:
```
bum@pc:/tmp/libipoddevice$ ./autogen.sh --prefix=/usr
/usr/local/bin/gnome-autogen.sh
grep: ./configure.in: No such file or directory
grep: ./configure.in: No such file or directory
grep: ./configure.in: No such file or directory
grep: ./configure.in: No such file or directory
Running ./configure --enable-maintainer-mode --enable-compile-warnings --prefix=/usr ...
/usr/local/share/aclocal/gnome2-macros/autogen.sh: line 158: ./configure: No such file or directory

```

Any help?

> **bailey_ca said:**
> 
[list=1]
[*]sudo apt-get install banshee banshee-daap subversion cvs automake1.9
[*]sudo apt-get build-dep banshee
[*]sudo apt-get remove banshee banshee-daap
[*]sudo rm -rf /usr/lib/banshee
[*]sudo rm -f /usr/bin/banshee
[*]sudo update-alternatives --set automake /usr/bin/automake-1.9
[*]sudo ldconfig
[*]cd /tmp
[*]cvs -z3 -d:pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co -P libipoddevice
[*]svn co svn://svn.myrealbox.com/source/trunk/ipod-sharp
[*]cvs -z3 -d:pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co -P banshee
[*]svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins
[*]sudo apt-get remove libipoddevice0 libipod-cil
[*]sudo apt-get install libgtop2-7 libgtop2-dev
[*]cd /tmp/libipoddevice
[*]./autogen.sh --prefix=/usr
[*]make && sudo make install
[*]sudo apt-get install mono-gac
[*]cd /tmp/ipod-sharp
[*]./autogen.sh --prefix=/usr --disable-docs
[*]make && sudo make install
[*]cd /tmp/banshee
[*]./autogen.sh --prefix=/usr --enable-ipod --disable-docs
[*]cd /tmp/banshee-official-plugins
[*]./autogen.sh --prefix=/usr --disable-podcast --disable-docs
[*]make && sudo make install
[/list]

---

### Post by Craig Caldwell on 2006-08-21
I have banshee 0.11.0-cvs running with all of the plugins installed and working but my problem is that my freshly flashed ipod won't sync.
I've tried turning off the plugins and it still won't sync. I've googled (verb he he) and searched the forums with out any luck. I've had syncing problems in the past but a flash fixed things. Any help or at least someone letting me know that I'm not the only one with this problem would be appreciated.[HTML]&#65279;Warning: [21/08/2006 8:33:55 AM] (Cannot connect to NetworkManager) - An available working network connection will be assumed
Debug: [21/08/2006 8:33:55 AM] (Default player engine) - GStreamer 0.10
Debug: [21/08/2006 8:33:56 AM] (Audio CD Core Initialized) -
glibtop: This machine has 2 CPUs, 2 are being monitored.

** (/usr/lib/banshee/banshee.exe:12701): WARNING **: nautilus_burn_drive_copy is deprecated please use nautilus_burn_drive_ref() instead
Warning: [21/08/2006 8:33:56 AM] (Power Management Call Failed) - Unsupported version of GNOME Power Manager: Method "GetOnAc" with signature "" on interface "org.gnome.PowerManager" doesn't exist


(Banshee:12701): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.


[/HTML]

---

### Post by moebis on 2006-08-21
Is there any reason that after 9 pages of threads going on and on about deps and repos and sources, etc, no one has thought to build .deb's of these packages with the latest plugings. The 64 bits guys are ahead of us on this one at: [http://ubuntu.moshen.de/dists/dapper/multimedia/](http://ubuntu.moshen.de/dists/dapper/multimedia/)

..weird...

---

### Post by mlind on 2006-08-21
> **moebis said:**
> Is there any reason that after 9 pages of threads going on and on about deps and repos and sources, etc, no one has thought to build .deb's of these packages with the latest plugings. The 64 bits guys are ahead of us on this one at: [http://ubuntu.moshen.de/dists/dapper/multimedia/](http://ubuntu.moshen.de/dists/dapper/multimedia/)

..weird...

Depends what plugins you mean, but I guess RAOF's repository contains 'official-plugins' and mine does too for i386 arch.

---

### Post by Craig Caldwell on 2006-08-22
I now have banshee working. I think what helped was deleting /usr/lib/banshee and /usr/lib/ipod-sharp directories as well as the banshee directories in .gconf and .gnome2 in my home directory before inst. just a guess though because there was also an update this morning.



```
craig@ubuntu:~$ banshee
&#65279;Warning: [22/08/2006 8:30:32 AM] (Cannot connect to NetworkManager) - An available working network connection will be assumed
Debug: [22/08/2006 8:30:33 AM] (Default player engine) - GStreamer 0.10
Debug: [22/08/2006 8:30:33 AM] (Audio CD Core Initialized) -
Building initial DAAP database from local library...
Starting DAAP Server
Scanning library for tracks to update
Done scanning library
Processing track queue for pending queries
Setting MusicBrainz proxy to www.musicbrainz.org:80
Done processing track queue


```

---

### Post by Tiede on 2006-08-22
My banshee install failed. Here is the original error > configure: error: The Recommendation plugin requires Banshee 0.11.0-cvs or better. Please pass --disable-recommendation to configure..
If I *do* pass --disable-recommendation to the commandline it does seem to work, but then the make step fails and consecutively make install.
Is there something  I am missing

---

### Post by hanzomon4 on 2006-08-24
I got everything installed but the music library doesn't have a breakdown of my music. This screenshot should explain 

[[IMG]http://img244.imageshack.us/img244/280/screenshot32ax6.th.png[/IMG]](http://img244.imageshack.us/my.php?image=screenshot32ax6.png)

---

### Post by Tiede on 2006-08-24
Ditto here. I remember being able to break it down "iTunes style" when I was uing the synaptic-installed version... Has that feature been deprecated?

Oh, and for some reason, banshee keeps freezing upon shut down for 5 seconds before finally closing since I updated to the bleeding-edge package...

---

### Post by hanzomon4 on 2006-08-24
I got that shutdown thing to.

---

### Post by lazyd2 on 2006-08-24
> **hanzomon4 said:**
> I got that shutdown thing to.
+1

---

### Post by Tiede on 2006-08-25
> **denisesballs said:**
> 
I think he may have missed my point that it crashes Banshee immediately on startup, instead of crashing when loading an internet stream, which was the problem before.

Hmm.... I am still having the internet stream problem.
It does begin to play the stream just fine, than out of the blue, it shuts off with a segmentation fault. Nothing else in the terminal output seems to indicate the problem, but this seg-fault error upon shuting off.

---

### Post by edcox86 on 2006-08-29
Hey I think it's fair to say i'm a linux noobie, The compiling of all the official plugins went fairly well.  I tried to do the same with the unofficial plugins for MP3Tunes and ITms following the instructions on their website and i get the following error when i  type make:

[INDENT]
error CS1715: `Banshee.Plugins.Locker.LockerSource.Tracks': type must be `System.Collections.Generic.IEnumerable<Banshee.Base.TrackInfo>' to match overridden member `Banshee.Sources.Source.Tracks'
/usr/lib/banshee/Banshee.Base.dll: `Banshee.Sources.Source.Tracks', name of symbol related to previous error
Compilation failed: 1 error(s), 0 warnings
make[1]: *** [Locker.dll] Error 1
make[1]: Leaving directory `/tmp/banshee-unofficail/banshee-locker-plugin/src'
make: *** [install-recursive] Error 1
[/INDENT]
](*,) 

I've had a look around and haven't found a solution as yet?  Sorry if this has been asked a thousand times over!
Any help greatly appreciated!

---

### Post by mlind on 2006-08-29
@edcox86
Looks like the code is broken on the svn/cvs.. I guess you'll have to wait until its fixed upsteam.

---

### Post by edcox86 on 2006-08-29
> **mlind said:**
> @edcox86
Looks like the code is broken on the svn/cvs.. I guess you'll have to wait until its fixed upsteam.

Cheers thankyou you've prevented hours of frustraition on my part!! :mrgreen:

---

### Post by rko618 on 2006-09-09
> **mlind said:**
> @edcox86
Looks like the code is broken on the svn/cvs.. I guess you'll have to wait until its fixed upsteam.

I believe it's fixed now.  I was able to successfully compile and install banshee and the plugins from cvs.

---

### Post by Valavien on 2006-09-15
I have .10-10 installed and I want to goto 10-12 but I can't compile from source, I get this message: 
checking for MONO... configure: error: Package requirements (mono >= 1.1.10) were not met:

No package 'mono' found


I tried to update in synaptic as it said there were updates available as I get this:
banshee-daap:
 Depends: libmono-corlib2.0-cil (>=1.1.16.1) but it is not installable
 Depends: libmono-sharpzip2.84-cil (>=1.0) but it is not installable
 Depends: libmono-system2.0-cil (>=1.1.16.1) but it is not installable
 Depends: libmono2.0-cil (>=1.1.16.1) but it is not installable
  Depends: banshee (=0.11.0-cvs-0raof13) but 0.10.10-0ubuntu10 is to be installed

anyone got any locations for this stuff?

---

### Post by RAOF on 2006-09-17
> **Valavien said:**
> I have .10-10 installed and I want to goto 10-12 but I can't compile from source, I get this message: 
checking for MONO... configure: error: Package requirements (mono >= 1.1.10) were not met:

No package 'mono' found


I tried to update in synaptic as it said there were updates available as I get this:
banshee-daap:
 Depends: libmono-corlib2.0-cil (>=1.1.16.1) but it is not installable
 Depends: libmono-sharpzip2.84-cil (>=1.0) but it is not installable
 Depends: libmono-system2.0-cil (>=1.1.16.1) but it is not installable
 Depends: libmono2.0-cil (>=1.1.16.1) but it is not installable
  Depends: banshee (=0.11.0-cvs-0raof13) but 0.10.10-0ubuntu10 is to be installed

anyone got any locations for this stuff?

You've got one of my repositories enabled, and you're not on AMD64.  That's where you're getting the banshee-daap from (which is arch-independent), but it depends on a bunch of the packages in my repository which only have an AMD64 version.

Remove my repository from your sources.list, run "sudo aptitude update" and try again.

Also, "sudo apt-get build-dep banshee" will probably fix your build-from-source problems.

---

### Post by saracen on 2006-09-18
Can someone make a .deb of banshee-plugins?  Or make a request for it to get packaged and put into universe?  Banshee is in universe and so is banshee-daap (music sharing plugin).  But no banshee-plugins...

---

### Post by RAOF on 2006-09-18
> **saracen said:**
> Can someone make a .deb of banshee-plugins?  Or make a request for it to get packaged and put into universe?  Banshee is in universe and so is banshee-daap (music sharing plugin).  But no banshee-plugins...

I might try.  Learn how to use REVU :).  It'd only be for Edgy Universe, though.

---

### Post by saracen on 2006-09-19
Sure, that's fine.  It doesn't have to be in main.

---

### Post by denisesballs on 2006-09-23
mlind, any chance on updating your repo with .11?

---

### Post by spartan777 on 2007-02-10
I'm trying to install banshee 11.6 and this is what I get. I don't think I have any of the 3rd party repo's that raof could be referring to. perhaps there is a .deb somewhere?

```
checking for GStreamer 0.10 gnomevfssrc plugin... yes
checking for GStreamer 0.10 audioconvert plugin... yes
checking for GStreamer 0.10 gconfaudiosink plugin... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for MONO_MODULE... configure: error: Package requirements (mono >= 1.1.10) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_MODULE_CFLAGS
and MONO_MODULE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

calvin@calvin-desktop:~/Desktop/to_install/banshee-0.11.6$ 

```

---

### Post by DWRZ on 2007-02-27
I'm getting the same error as spartan777... any ideas?

---

### Post by revertex on 2007-05-15
> **DWRZ said:**
> I'm getting the same error as spartan777... any ideas?

```
sudo apt-get install libmono-dev
```

---

### Post by AlienLinux on 2008-05-26
Hi I recently just installed the itms plugin for banshee on version 0.11.1.
It goes to the store, i can search for music, but how do I do everything else.
I need to know how to buy.

I added two photos:
The one running through linspire is me,
and the one being used through (I believe) Suse, is a pic I got off google.
You'll see the second shows a download.

---

### Post by LinuxNoob07 on 2008-11-21
When i try to install Banshee i get this error message.

The following packages have unmet dependencies:
  banshee: Depends: libmtp6 but it is not installable
E: Broken packages

How do i fix this?

---

