---
title: "Howto compile ubuntu-packages on your own?"
date: 2008-11-12
forum: Packaging and Compiling Programs
---

### Post by qos on 2008-11-12
Hello,

I want to compile the ubuntu version of libgtk2.0-0 on my own. Somewhere on bugzilla there was a patch to fix a scrollwheel issue and of course i want to apply it before ;)
So, my target is to build the same libgtk2.0-0 as the ubuntu-maintainer did but mine has the patch.

I even was successfull but my version has a problem with displaying images in GnomeDo. I guess this comes from various patches in the source directory which were ignored by me ;)

So, i did the following:
```
wget http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk+2.0_2.14.4.orig.tar.gz
wget http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk+2.0_2.14.4-0ubuntu1.diff.gz

unp gtk+2.0/gtk+2.0_2.14.4.orig.tar.gz
unp gtk+2.0/gtk+2.0_2.14.4-0ubuntu1.diff.gz
cd gtk+-2.14.4/
patch <../gtk+2.0_2.14.4-0ubuntu1.diff
patch <../scroll.patch

./configure --prefix=/usr
make
```

For testing i backuped my /usr/lib/libgtk-x11-2.0.so.0.1400.4 and replaced it with the generated one. Then i logged out and in and i was impressed that it worked ;)

But as mentioned mine has problems with images and some other problems.
And i think this has todo with these patches which comes with the source:
```
000_gtk+-2.0.6-exportsymbols.patch
001_static-linking-dont-query-immodules.patch
002_static-linking-dont-build-perf.patch
003_gdk.pc_privates.patch
004_gtk+-ximian-gtk2-filesel-navbutton-5.patch
005_xpmico.patch
006_proper-directfb-modules.patch
007_implicit_pointer_conversion_gdkdrawable_directfb.patch
008_implicit_pointer_conversion_gdkgc_directfb.patch
009_gtk-export-filechooser.patch
010_gdkpixbuf_-lm.patch
015_default-fallback-icon-theme.patch
020_immodules-files-d.patch
021_loader-files-d.patch
022_disable-viqr-im-for-vi-locale.patch
022_module-files-append-compat-module-files-d.patch
030_gtkentry_password-char-circle.patch
033_treeview_resizing.patch
041_ia32-libs.patch
042_treeview_single-focus.patch
060_ignore-random-icons.patch
061_use_pdf_as_default_printing_standard.patch
070_mandatory-relibtoolize.patch
071_correct_directfb_declarations.patch
072_workaround_directfb_build.patch
091_workaround_no_gtk_init_incorrect_display.patch
```

So, how get these patches applied or am i doing wrong the whole stuff?

---

### Post by Pro-reason on 2008-11-12
You could start by making your own [PPA]("https://help.launchpad.net/Packaging/PPA").

---

### Post by qos on 2008-11-12
It would be enought to know what went wrong or to know how to apply these packages correcly ;)

---

### Post by InfinityCircuit on 2008-11-12
```
sudo aptitude install devscripts ubuntu-keyring
sudo apt-get build-dep libgtk2.0-0
dget -x http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk+2.0_2.14.4-0ubuntu1.dsc
cd gtk+2.0-2.14.4
cp ../scroll.patch debian/patches
echo "scroll.patch" >> debian/patches/series
dch --local +scroll  # arbitrary changelog bump here
debuild -us -uc
sudo debi
```

---

### Post by qos on 2008-11-13
Thank you very much...

After a while and with the approach from InfinityCircuit i figured out how this will work.
I hope this will help someone else to apply patches.

In my example i am adding the patch for using the scrollwheel with compact view in nautilus. The patch is original from [Gnome bug 558659]("http://bugzilla.gnome.org/show_bug.cgi?id=558659"):

I modified the patch a bit and attached it to this post. Download it, place it on your Desktop and run the script below.

```

#requirements and tools for packaging and compiling
#there are eventually missing some more packages ;)
sudo aptitude install devscripts ubuntu-keyring
sudo apt-get build-dep libgtk2.0-0

```

```

#!/bin/sh

#create workdir
  mkdir ~/Desktop/tmp
  cd ~/Desktop/tmp

#get the sources and patch for libgtk2.0 in once
  dget -x http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk+2.0_2.14.4-0ubuntu1.dsc

#unpack the patch & and use it
  unp gtk+2.0_2.14.4-0ubuntu1.diff.gz
  patch -p0 <gtk+2.0_2.14.4-0ubuntu1.diff

#unpack the sources and move them into the patch directory
  unp gtk+2.0_2.14.4.orig.tar.gz gtk+2.0-2.14.4/
  mv gtk+-2.14.4/* gtk+2.0-2.14.4/
  rmdir gtk+-2.14.4/
  cd gtk+2.0-2.14.4/

#add your patch
  cp ../../000_scroll.patch debian/patches/
  echo "000_scroll.patch" >> debian/patches/series

#put your additions to the changelog (optional)
  dch --local +scroll  # arbitrary changelog bump here

#compile (this will take some time)
  debuild -us -uc
```

```

#i guess this will install the generated packages
#but i didn't try it and used another methode
sudo debi
```

greetz

---

### Post by cariboo on 2008-11-13
You also use checkinstall to create a .deb file. Use it in place of make.

Jim

---

### Post by qos on 2008-11-14
Isn't it so that you first have to use *make* and *checkinstall* just builts the .deb?

---

