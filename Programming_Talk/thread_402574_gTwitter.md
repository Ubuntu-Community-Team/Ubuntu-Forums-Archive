---
title: "gTwitter"
date: 2007-04-05
forum: Programming Talk
---

### Post by MakubeX on 2007-04-05
[http://code.google.com/p/gtwitter/](http://code.google.com/p/gtwitter/)

I was compiling gtwitter's 0.2.4 version (and 0.2.3 too), executed ./configure and "make" respectively, here are the results:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for mcs... /usr/bin/mcs
checking pkg-config is at least version 0.9.0... yes
checking for MONO_CAIRO... yes
checking for GTK_SHARP_20... yes
checking for GNOME_VFS_SHARP_20... yes
checking for GLIB_SHARP_20... yes
checking for GCONF_SHARP_20... yes
configure: creating ./config.status
config.status: creating ./Makefile
config.status: creating ./gtwitter/Makefile
config.status: creating ./gtwitter/gtwitter
config.status: creating ./gtwitter/gtwitter.gtwitter.pc 
```

```
Making all in gtwitter
make[1]: Entering directory `/home/noel/AppsHD/gtwitter-0.2.3/gtwitter'
mkdir -p ./bin/Release/
mcs -noconfig -codepage:utf8 -warn:4 -out:bin/Release/gtwitter.exe -target:exe . /./gtk-gui/generated.cs ././MainWindow.cs ././Main.cs ././AssemblyInfo.cs ././gt k-gui/gtwitter.MainWindow.cs ././PreferencesWindow.cs ././gtk-gui/gtwitter.Prefe rencesWindow.cs ././ReadInfo.cs ././ReadConfig.cs ././GetTwitterData.cs ././Post ToTwitter.cs ././CompositeInterface.cs ././AboutDialog.cs  -resource:././gtk-gui /gui.stetic,gui.stetic  -resource:./../data/gtwitter-48.png ,gtwitter-48.png  -re source:./../data/gtwitter-64.png,gtwitter-64.png -r:System -r:/usr/lib/pkgconfig /../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mo no/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2. 0/gdk- sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll  -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:System.X ml -r:Mono.Posix -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0 /gnome-vfs-sh arp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/1.0/Mono.Cairo.dll   -r:/usr/lib/ pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/pkgconfig/.. /../lib/mono/gtk-sharp-2.0/gconf-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/ gtk-sharp-2.0/gconf-sharp-peditors.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk- sharp-2.0/gnome-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pan go-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0 /atk-sharp.dll -r :/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgco nfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/ mono/gtk-sharp-2.0/art-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp- 2.0/gnome-vfs-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib- sharp.dll
././MainWindow.cs(24,3): error CS0246: The type or namespace name `StatusIcon' c ould not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 1 error(s), 0 warnings
make[1]: *** [bin/Release/gtwitter.exe] Error 1
make[1]: Leaving directory `/home/noel/AppsHD/gtwitter-0.2.3/gtwitter'
make: *** [all-recursive] Error 1
```

The last line on executing make: "././MainWindow.cs(24,3): error CS0246: The type or namespace name `StatusIcon' c ould not be found. Are you missing a using directive or an assembly reference?" is the problem where I got confused.

Anyone here who has a workaround for this? Thanks in advance!

---

### Post by MakubeX on 2007-04-06
For the update, I already have a [workaround]("http://noel.feria.name/blog/2007/04/06/gtwitter/")

---

