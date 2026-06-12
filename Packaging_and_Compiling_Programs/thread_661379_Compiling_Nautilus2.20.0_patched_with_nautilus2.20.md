---
title: "Compiling Nautilus2.20.0 patched with nautilus2.20.0ubuntu7.diff"
date: 2008-01-07
forum: Packaging and Compiling Programs
---

### Post by imoatama on 2008-01-07
I downloaded, patched and installed nautilus 2.20.0 with a patch to enable compiz to draw different wallpapers on each side of my cube. This compiled and worked fine, but it meant that I lost all the nice modifications ubuntu gutsy made to Nautilus.

So in order to have the best of both worlds, I downloaded [nautilus source]("http://packages.ubuntu.com/gutsy/gnome/nautilus") from the [ubuntu packages page]("http://packages.ubuntu.com/gutsy/gnome/nautilus").

This consisted of the original source, and a diff file with the changes made in the ubuntu version. ```
patch -p1 file
``` succesfully applied this patch, but unfortunately all this did was create a debian subdirectory with a bunch of files (including a rules file) and a patch subdirectory containing a dozen or so patches.

After a fair amount of searching I finally discovered that this is a fairly standard way to do patches in Debian, and that I likely needed to use quilt to apply them. I managed to get the patches imported into quilt using the (admittedly hacky) ```
quilt import -p1 $(ls debian/patch/*.patch)
``` and then apply them using ```
quilt push -a
```. This is where I began experiencing problems.

First of all, not all the patches seem to apply. I get errors saying that the files they should apply to cant be found, and on one patch an error saying it doesn´t seem to apply to the file. In the end I just applied all the patches that I could, and then applied the patch that has nautilus draw a transparent background when compiz wallpapers are enabled.

However compilation fails. When I try to make, I get 
```
Processing file nautilus-metafile-server.idl
Error: `Bonobo' undeclared identifier

** (orbit-idl-2:6824): WARNING **: nautilus-metafile-server.idl compilation failed
make[2]: *** [nautilus_metafile_server_idl_stamp] Error 1
make[2]: Leaving directory `/home/potato/src/nautilus-2.20.0/libnautilus-private'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/potato/src/nautilus-2.20.0'
make: *** [all] Error 2

```

Any tips? What is the correct way to apply the patches that came out of the ubuntu diff file? I´m fairly sure my hackery with quilt was not the right way. Any guesses on how I can get it to compile?

---

### Post by imoatama on 2008-01-19
Well I ended up solving this myself, but I thought I'd post how just in case anyone ever runs into similar problems.

I worked out how to patch the original source with the diff using quilt by reading this [excellent quilt howto]("http://pkg-perl.alioth.debian.org/howto/quilt.html"). Essentially all I needed to do was set the environment variable QUILT_PATCHES=debian/patches, and then i could simply run 'quilt push -a' from the nautilus source directory to apply all the patches in the series file.

I still got the same compile error though, until I realised I needed to run 'sudo apt-get build-dep nautilus' to get the build dependencies (and re-run ./configure), and then it made with no problems.

---

### Post by Foxmike on 2008-01-20
One way you can do it all, is by putting your .diff file into the ```
${source-directory}/debian/patches
``` using a terminology as ```
${number}-${patch-very-short-description}.diff
``` and then list that file into the ```
${source-directory}/debian/patches/source
``` Afterwards, you can go back to the ${source-directory} and type in ```
dpkg-buildpackage -rfakeroot.
```Make sure before that you have all your build depends on, by tying ```
sudo apt-get build-dep nautilus
```.

Have fun!

---

### Post by Foxmike on 2008-01-20
And make sure that you are working with the ubuntu packages, not the debian ones!  You can go to packages.ubuntu.com, make a search for the package you want to work with, the locate the .dsc download in the bottom of the page, copy the address of the link and in a terminal, put in:
```
dget <copied_link>
```, il will download all necessary files, and extract them into a <package_name>-<version>/ directory. If it doesn't extract, running ```
dpkg-source -x *.dsc
``` will do the job.

Cheers!

---

### Post by HDave on 2008-05-15
Does this patch mean you can keep your desktop icons and still get different wallpapers in each workspace?

If you, could you please post a simpler "how-to" -- I've been dying for this capability, but can't navigate how to apply the patches to the sources...

Thanks!

---

### Post by carlinuxlearner on 2008-08-05
Yes, PLEASE post a How-To!

C@RL

---

### Post by imoatama on 2008-08-05
This only applied to Gutsy, and was about patching nautilus and libeel to allow diffeent wallpapers on each side of the cube AND also keeping all the patches applied to nautilus 2.20 by the ubuntu distribution.

There are already howtos written on how to get multiple wallpapers with compiz, the first one is [here]("http://forum.compiz-fusion.org/showthread.php?t=6199"). However I don't recommend using them, as they only work for nautilus/ell 2.20. Hardy uses 2.22 so the patches wont work.

The nautilus team are working on a fix for this problem to allow transparent desktop, it is planned for release 2.24. There is a ticket for the bug/issue [here]("http://bugzilla.gnome.org/show_bug.cgi?id=444320").

The best thing to do if you want different wallpapers on the cube in Hardy with Gnome is to wait. The other option is to switch to KDE, which now supports it natively with KDE4.

---

