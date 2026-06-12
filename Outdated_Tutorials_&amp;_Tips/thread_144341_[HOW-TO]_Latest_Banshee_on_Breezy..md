---
title: "[HOW-TO] Latest Banshee on Breezy."
date: 2006-03-14
forum: Outdated Tutorials &amp; Tips
---

### Post by TomaszD on 2006-03-14
I know you want it. :) The latest version at the time of writing was 0.10.8.
 
(if you don't have the breezy banshee version already installed, please do so, this will give you a Banshee menu entry in GNOME, so it definitely won't hurt. Issue sudo apt-get install banshee .) 

First, we need some recent mono packages. These can be found in the filefind repository.
 
```
sudo gedit /etc/apt/sources.list
```

add this line:

```
deb http://apt.filefind.net/ breezy main contrib non-free
```

Save and close gedit.
```

sudo apt-get update && sudo apt-get upgrade
```
 
Alright, we have mono. Now onto other dependencies...

```
sudo apt-get build-dep banshee
```

Cool, but some are outdated. 

```
wget http://banshee-project.org/files/libipoddevice/libipoddevice-0.4.1.tar.gz
tar zxvf libipoddevice-0.4.1.tar.gz
cd libipoddevice-0.4.1
./configure --prefix=/usr
make
sudo make install

wget http://banshee-project.org/files/ipod-sharp/ipod-sharp-0.5.15.tar.gz
tar zxvf ipod-sharp-0.5.15.tar.gz
cd ipod-sharp-0.5.15
./configure --prefix=/usr
make
sudo make install

wget http://banshee-project.org/files/njb-sharp/njb-sharp-0.2.2.tar.gz
tar zxvf njb-sharp-0.2.2.tar.gz
cd njb-sharp-0.2.2
./configure --prefix=/usr
make
sudo make install

```
Right on. Now onto Banshee itself.

```
wget http://banshee-project.org/files/banshee/banshee-0.10.8.tar.gz
tar zxvf banshee-0.10.8.tar.gz
cd banshee-0.10.8
./configure --prefix=/usr --disable-helix
make
sudo make install
```

That's it. Cheers!

---

### Post by BeachBum on 2006-03-17
Thanks for the how-to!

Upon running the config script for libipoddevice, I get this error:

checking for LID... Package libgtop-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgtop-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgtop-2.0' found
configure: error: Package requirements (gobject-2.0     glib-2.0        dbus-1 dbus-glib-1      hal >= 0.5.2    libgtop-2.0 >= 2.12.0) were not met:



Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LID_CFLAGS
and LID_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Any clues?  Thanks!

---

### Post by zi99y on 2006-03-18
```
sudo apt-get install libgtop2-dev
```
should sort you out

---

### Post by zi99y on 2006-03-18
Ok I had some more dependency problems, as follows:

```
configure: error: You need to install mdassembler
```

fixed by doing a:

./configure --prefix=/usr --disable-docs

```
configure: error: You need to install gacutil
```

fixed by:

sudo apt-get install mono-gac

```
checking for NJB... configure: error: Package requirements (libnjb >= 2.2.4) were not met.
```

fixed by doing...

sudo apt-get install libnjb-dev

```
configure: error: You need to install monodoc
```

fix:

sudo apt-get install monodoc

But now, when attempting to configure the banshee source, I get this error:

```
checking for GTKSHARP... configure: error: Package requirements (gtk-sharp-2.0 >= 2.7   gnome-sharp-2.0 >= 2.7  gnome-vfs-sharp-2.0 >= 2.7      glade-sharp-2.0 >= 2.7  gconf-sharp-2.0 >= 2.7) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GTKSHARP_CFLAGS and GTKSHARP_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```

Any ideas? is it worth flogging it like this??!

---

### Post by zachtib on 2006-03-18
I love you...

This is the first time I've EVER gotten banshee to recognize my 4G iPod.  No idea what you did different, but IT WORKED

I'm off to add music to my iPod for the first time in forever...

---

### Post by spanella47 on 2006-03-18
getting the following errors when making banshee, any ideas?

```
./daap-sharp/Server.cs(525,54): error CS0246: The type or namespace name `ClientStateArgs' could not be found. Are you missing a using directive or an assembly reference?
./daap-sharp/Server.cs(568,58): error CS0246: The type or namespace name `EntryGroupStateArgs' could not be found. Are you missing a using directive or an assembly reference?
./daap-sharp/ServiceLocator.cs(205,48): error CS0246: The type or namespace name `ServiceInfoArgs' could not be found. Are you missing a using directive or an assembly reference?
./daap-sharp/ServiceLocator.cs(215,51): error CS0246: The type or namespace name `ServiceInfoArgs' could not be found. Are you missing a using directive or an assembly reference?
./daap-sharp/ServiceLocator.cs(261,50): error CS0246: The type or namespace name `ServiceInfoArgs' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 5 error(s), 0 warnings
make[4]: *** [Daap.dll] Error 1
make[4]: Leaving directory `/home/spanella47/banshee-0.10.8/src/Banshee.Plugins/Daap'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/spanella47/banshee-0.10.8/src/Banshee.Plugins'make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/spanella47/banshee-0.10.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/spanella47/banshee-0.10.8'
make: *** [all] Error 2
```

---

### Post by zi99y on 2006-03-19
I'm really not sure - I managed to configure and build banshee in the end with the --disable-ipod --disable-daap options.

Although the effor it took to get it setup seems a bit futile now, as I think I still prefer Amarok [-(

---

### Post by spanella47 on 2006-03-19
thanks the --disable-daap did it.

does banshee always start playing the first song in your library as soon as it comes up? Is there a way to turn this off?

---

### Post by zachtib on 2006-03-19
[QUOTE=spanella47]thanks the --disable-daap did it.

does banshee always start playing the first song in your library as soon as it comes up? Is there a way to turn this off?[/QUOTE]

this annoys me as well

---

### Post by minio on 2006-03-19
Just one tip - if you want banshee to play audio-CD automatically (instead of gnome-cd) then go to System -> Preferences -> Removable drives and media. Go to Multimedia tab and change command for audio CD to this:```
banshee --audio-cd %d --play
```
If you omit the "--play" banshee will open CD when it is inserted but won't start to play it :)

---

### Post by minio on 2006-03-19
[QUOTE=spanella47]thanks the --disable-daap did it.

does banshee always start playing the first song in your library as soon as it comes up? Is there a way to turn this off?[/QUOTE]
Open "Applications Menu Editor" find in it entry for banshee. Right click on entry and select "Properties" from context menu. Window will pop up. From field "Command" delete string "--play" and click on OK. Close menu editor and here you go :)

---

### Post by Morbett on 2006-03-21
Thank you to everyone who put so much effort into this thread and sorting through the dependency hell and the settings.

I upgraded from 0.9.7 to 0.10.4 following all the indications in the first few posts.  It's up and running, but I noticed that Banshee crashes more often than before!  The program will close randomly even more often. Did anyone find this?



I also noticed that audio cuts out here and there if I'm running other applications (only a mail client, nothing too draining).  I thought maybe it was the Gstreamer engine?  Do I need to update it or something?

:)

EDIT:  the audio also gets choppy in Totem when a couple applications are open.  So it's not distinct to Banshee..  hmm.


SECOND EDIT:

D'oh.  I completely missed the end of the first post about actually installing Banshee 0.10.8.  I had simply updated to 0.10.4 through synaptic.  When I try to configure Banshee before running the make file, I get this error:

> 
checking for MUSICBRAINZ... configure: error: Package requirements (libmusicbrainz >= 2.1.1) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the MUSICBRAINZ_CFLAGS and MUSICBRAINZ_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.


How do I fix this?

---

### Post by Morbett on 2006-03-23
So any ideas how to fix the musicbrainz error in order to compile banshee?

---

### Post by Wallakoala on 2006-03-23
[QUOTE=Morbett]So any ideas how to fix the musicbrainz error in order to compile banshee?[/QUOTE]
What I did was go into synaptic and search for "musicbrainz"
I'm not sure which package I installed, but one of them worked.

---

### Post by Wallakoala on 2006-03-23
I have to say, this guide has brought me happiness. Although there were problems, I am very happy now.

I am going to try and help with the most notable problems:
The musicbrainz thing,

```
sudo apt-get install libmusicbrainz4c2 libmusicbrainz4-dev
```

I don't know if you need both, but I installed both and it worked.

For me, I had some problems because it had some weird conflict with monodoc when trying to use checkinstall. It also had a daap issue. So in order to fix this, when you ./configure, use this instead:

```
./configure --prefix=/usr --disable-helix --disable-daap --disable-docs

```

Before, whenever I plugged my ipod in, banshee would crash and then I wouldn't be able to start it back up. Now, it works perfectly. This new version of banshee is quite an upgrade, and I hope what I said helps people so they can enjoy it too.

---

### Post by Morbett on 2006-03-24
Thanks so much!  I was able to properly run the make file, but when I did make install, it gave me this:


> Making install in data
make[1]: Entering directory `/home/aidan/banshee-0.10.8/data'
Making install in images
make[2]: Entering directory `/home/aidan/banshee-0.10.8/data/images'
make[3]: Entering directory `/home/aidan/banshee-0.10.8/data/images'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/share/icons/hicolor/scalable/apps
/usr/bin/install -c -m 644 ./music-player-banshee.svg /usr/share/icons/hicolor/scalable/apps/music-player-banshee.svg
/usr/bin/install: cannot remove `/usr/share/icons/hicolor/scalable/apps/music-player-banshee.svg': Permission denied
make[3]: *** [install-data-local] Error 1
make[3]: Leaving directory `/home/aidan/banshee-0.10.8/data/images'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/aidan/banshee-0.10.8/data/images'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/aidan/banshee-0.10.8/data'
make: *** [install-recursive] Error 1

---

### Post by Morbett on 2006-03-24
I just tried updating Banshee to 0.10.8 on my laptop following your directions and the info in the first two posts, and it worked without a hitch.  I wonder why the make install doesn't work on my destop.

EDIT:  Just reinstalled everything on desktop and it works fine now.  THANK YOU everyone for your help.  This board has the best community out there...

---

### Post by f0vela on 2006-03-24
I found this:
```
checking for GTKSHARP... configure: error: Package requirements (gtk-sharp-2.0 >= 2.7   gnome-sharp-2.0 >= 2.7  gnome-vfs-sharp-2.0 >= 2.7      glade-sharp-2.0 >= 2.7  gconf-sharp-2.0 >= 2.7) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GTKSHARP_CFLAGS and GTKSHARP_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```

Fix: Install mono 
sudo apt-get install mono
-----------------------------------------------------------
For the Avahi-Sharp problem you can install libavahi-cil from synaptic or apt-get.
sudo apt-get install libavahi-cil


I hope this helps.
this worked for me.

---

### Post by Wallakoala on 2006-03-24
[QUOTE=Morbett]Thanks so much!  I was able to properly run the make file, but when I did make install, it gave me this:[/QUOTE]

Try doing 
```
sudo make install
```

---

### Post by Wallakoala on 2006-03-24
Now I have one problem,
Whenever I try and import a cd, banshee crashes if I try and listen to any music while doing it.

---

### Post by arnieboy on 2006-03-24
I am getting the following errors when trying to "make" banshee
> ./daap-sharp/Server.cs(525,54): error CS0246: The type or namespace name `ClientStateArgs' could not be found. Are you missing a using directive or an assembly reference?
./daap-sharp/Server.cs(568,58): error CS0246: The type or namespace name `EntryGroupStateArgs' could not be found. Are you missing a using directive or an assembly reference?
./daap-sharp/ServiceLocator.cs(205,48): error CS0246: The type or namespace name `ServiceInfoArgs' could not be found. Are you missing a using directive or an assembly reference?
./daap-sharp/ServiceLocator.cs(215,51): error CS0246: The type or namespace name `ServiceInfoArgs' could not be found. Are you missing a using directive or an assembly reference?
./daap-sharp/ServiceLocator.cs(261,50): error CS0246: The type or namespace name `ServiceInfoArgs' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 5 error(s), 0 warnings
any insights? I have all the avahi packages installed.

EDIT: Solved (Look at following post)

---

### Post by arnieboy on 2006-03-24
ok I solved the above problem myself. seems like the problem is two-fold:

a) Changes in the latest mono break the avahi-sharp that was shipped in
the last Avahi release

b) daap-sharp does not work very well, even on a slightly older mono,
with the last released avahi-sharp

It is possible to install just avahi-sharp from CVS without replacing
the Avahi core packages from the Breezy repositories:

```
sudo apt-get install subversion
svn checkout svn://svn.0pointer.de/avahi/trunk avahi
cd avahi
./autogen.sh --prefix=/usr
make
cd avahi-sharp
sudo make install
cd ..
sudo cp avahi-sharp.pc /usr/lib/pkgconfig

```

now the banshee installation should go ahead smoothly.

---

### Post by Valavien on 2006-03-26
trying to use that to install avahi-sharp I get this error:

+ '[' x--prefix=/usr = xam ']'
+ rm -rf autom4te.cache
+ rm -f config.cache
+ test x = x
+ LIBTOOLIZE=libtoolize
+ libtoolize -c --force
./autogen.sh: line 54: libtoolize: command not found

I find this very frustrating because there is always something missing whenever I try and install from source.  In a lot of cases I have no idea on how to fix it myself without just looking up a forum and then not really learning anything.

Well I installed libtool and I got a bit further, now it's:
aclocal: configure.ac: 513: macro `AM_PATH_PYTHON' not found in library
aclocal: macro `AM_PATH_PYTHON' required but not defined
aclocal: macro `AM_PATH_PYTHON' required but not defined

---

### Post by arnieboy on 2006-03-26
[QUOTE=Valavien]trying to use that to install avahi-sharp I get this error:

+ '[' x--prefix=/usr = xam ']'
+ rm -rf autom4te.cache
+ rm -f config.cache
+ test x = x
+ LIBTOOLIZE=libtoolize
+ libtoolize -c --force
./autogen.sh: line 54: libtoolize: command not found

I find this very frustrating because there is always something missing whenever I try and install from source.  In a lot of cases I have no idea on how to fix it myself without just looking up a forum and then not really learning anything.

Well I installed libtool and I got a bit further, now it's:
aclocal: configure.ac: 513: macro `AM_PATH_PYTHON' not found in library
aclocal: macro `AM_PATH_PYTHON' required but not defined
aclocal: macro `AM_PATH_PYTHON' required but not defined[/QUOTE]

banshee has a million dependencies. u are bound to run into these errors.
for the time being do the following:
```
sudo apt-get install libtool
```

and then re-install avahi-sharp.

---

### Post by Mediocreman on 2006-03-26
```
checking for GTKSHARP... configure: error: Package requirements (gtk-sharp-2.0 >= 2.7   gnome-sharp-2.0 >= 2.7  gnome-vfs-sharp-2.0 >= 2.7      glade-sharp-2.0 >= 2.7  gconf-sharp-2.0 >= 2.7) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GTKSHARP_CFLAGS and GTKSHARP_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

This the error message I get. I've tried what others have suggested, diable daap, disable ipod, installing mono; nothing worked. Any help would be appreciated.](*,)

---

### Post by arnieboy on 2006-03-26
u dont need to disable anything other than helix if all dependencies are in place.
do the following:
```
sudo apt-get install gtk-sharp
```
and try running configure again.

---

### Post by Nordoelum on 2006-04-04
[quote=arnieboy]u dont need to disable anything other than helix if all dependencies are in place.
do the following:
```
sudo apt-get install gtk-sharp
``` and try running configure again.[/quote]

```
nordoelum@nordoelum:~/avahi$ sudo apt-get install gtk-sharp
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gtk-sharp: Depends: gtk-sharp-examples but it is not going to be installed
             Depends: libgtk-cil but it is not going to be installed
             Depends: libglade-cil but it is not going to be installed
             Depends: libgnome-cil but it is not going to be installed
             Depends: libvte-cil but it is not going to be installed
E: Broken packages
nordoelum@nordoelum:~/avahi$
```

:cry:

---

### Post by Nordoelum on 2006-04-11
```
checking for GTKSHARP... configure: error: Package requirements (gtk-sharp-2.0 >= 2.7   gnome-sharp-2.0 >= 2.7  gnome-vfs-sharp-2.0 >= 2.7      glade-sharp-2.0 >= 2.7      gconf-sharp-2.0 >= 2.7) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GTKSHARP_CFLAGS and GTKSHARP_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```

:(

---

### Post by xshady87 on 2006-04-22
When I get to this part:

wget [http://banshee-project.org/files/libipoddevice/libipoddevice-0.4.1.tar.gz](http://banshee-project.org/files/libipoddevice/libipoddevice-0.4.1.tar.gz)
tar zxvf libipoddevice-0.4.1.tar.gz
cd libipoddevice-0.4.1
./configure --prefix=/usr
make
sudo make install



I am told that there is no make file to be found. What am I doing wrong?

---

### Post by adamkane on 2006-04-22
Adding filefind to your sources.list fill will lead you into needless dependency frustration. 

If you try to install any packages that depend on mono, you'll get messages saying the required dependencies are unavailable, because apt doesn't know what to do with the filefind packages.

If you end up in dependency hell, then use synaptic to search for any packages that have filefind in the version number, and remove all those packages. Then remove filefind from sources.list:

> 
deb [http://apt.filefind.net/]("http://apt.filefind.net/") breezy main contrib non-free
 

Then update:

```

sudo apt-get update

```

The filefind repository is not maintained to play nicely with all your other repositories, and the filefind team needs to fix this.

---

### Post by xshady87 on 2006-04-23
Let's say I already installed filefind. Is there anything I could do to fix that. I'm still trying to install Banshee, but it's been increasingly difficult. As a matter of fact, I am not able to install any programs at all.

---

### Post by adamkane on 2006-04-23
xshady: see revised post 30.

If you don't use filefind, you can still install banshee 0.9.7 via the universe repository in breezy, but you won't have ipod support.

I really don't know how breezy users can make use of the filefind repo and the latest version of banshee without messing up their systems.

This howto is only useful if you have a machine or partition dedicated to your ipod, and don't have need to install much other than banshee.

This post is a caution to the users out there who are looking forward to using their ipod in breezy, and thought filefind might be the way.

For now you are better off using gtkpod or amaroK with your ipod.

---

