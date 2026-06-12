---
title: "get a source package, tweak options?"
date: 2006-02-22
forum: Repositories &amp; Backports
---

### Post by zojas on 2006-02-22
how do I download a source code package?

My goal is to download a source package, tweak a configure (compile-time) option, then somehow use apt/dpkg to build and install the tweaked version of the package.

I don't even know how to find out what source code packages are available.

thanks.

---

### Post by andrewsawyer on 2006-02-24
You should be able to get the source directly from the software website.  It will probably be in a tar archive, so look for the .tar.gz or tar.bz2 file.  There are also loads of programs at sourceforge.net that you might like to look at.

As far as compiliing it and making a deb, you can use a program called checkinstall.  Just type ```
sudo checkinstall
``` rather than ```
sudo make install
``` when compiling the program and it will make a deb that you can then keep and reinstall whenever you want.  It also has the advantage of appearing in Synaptic for easy removal.

---

### Post by zojas on 2006-02-24
ok. I have 2 target packages in mind: xpdf-reader and vim-gtk. the xpdf-reader which ships with breezy won't show the table of contents
 (I've kind of given up on this for now, there doesn't seem to be a compile-time option for that, so it's just a bug; I started using evince for now)

and vim-gtk2 has some outstanding issues where it crashes a lot. so my plan was to create myself a vim-athena (there is a compile time option to select the athena widget set instead of gtk)

I did find that 

```

apt-get source vim-gtk

```

will fetch me a ready-to-be-built, .deb-ified source tree. then I tweaked the changelog, control, and rules files to add a new athena variant. then I ran

```

dpkg-buildpackage -rfakeroot

```

which built .debs for all the vim variants, including my new vim-athena. the only problem is that when I tried to install the .deb, I got an odd error message, and it failed to install:

```

9:42pm0imrryr>sudo dpkg -i vim-athena_6.3-078+1ubuntu3_i386.deb                                                                                                ~/packages/vim
dpkg: considering removing vim-gtk in favour of vim-athena ...
dpkg: yes, will remove vim-gtk in favour of vim-athena.
(Reading database ... 96574 files and directories currently installed.)
Unpacking vim-athena (from vim-athena_6.3-078+1ubuntu3_i386.deb) ...
dpkg-divert: `diversion of /usr/bin/vim to /usr/bin/vim.org by vim-athena' clashes with `diversion of /usr/bin/vim to /usr/bin/vim.org by vim-gtk'
dpkg: error processing vim-athena_6.3-078+1ubuntu3_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 vim-athena_6.3-078+1ubuntu3_i386.deb

```

I solved that by 'apt-get remove vim-gtk' then installing the .deb. but I don't have the compile flags set correctly in the control file yet, so I'm still tweaking it.

---

### Post by az on 2006-02-25
[QUOTE=zojas]
I solved that by 'apt-get remove vim-gtk' then installing the .deb. but I don't have the compile flags set correctly in the control file yet, so I'm still tweaking it.[/QUOTE]

I think the package maintainer did not count on someone duplicating the package and so the package conflict with itself.  Both packages are trying to create the same dpkg-divert at the same time.  Probably a postrm script should be changed into a prerm script or something.  There are policies (a bookfull) for this.


It is nothing you did wrong.

---

### Post by zojas on 2006-02-25
ok, got it. you were right about the divert. I removed the vim-gtk package and it removed the divert. I couldn't figure out how to get the new vim-athena packages to remove the divert from vim-gtk; I tried adding a call to remove the divert in the vim-variant.preinst but that didn't help. there wasn't a .prerm, and I didn't want to try to add one.

the thread [http://ubuntuforums.org/showthread.php?t=51003&highlight=create+deb]("http://ubuntuforums.org/showthread.php?t=51003&highlight=create+deb") was an invaluable reference; that thread documents the packages you have to install to be able to build deb files.

here's what I did, from the beginning, to create a vim-athena deb. 

```

mkdir ~/package
cd ~/package
apt-get source vim-gtk
cd vim
apply patch posted below, but in the changelog use an email address for which you have a private gpg key
cd vim-6.3
dpkg-buildpackage -rfakeroot

```

that last line takes a while (it has to build all the vim variants), and it will prompt you for the passphrase for your gpg key; it signs the new .deb files.

you must remove the old vim-gtk package before installing the new .debs because of the divert 

you have to install all the .deb files which match the version number of the changelog entry you added. (i.e., the ones for vim, vim-common, vim-doc, and vim-athena) because their versions must match (you can't just install the new vim-athena along with the old vim and vim-common).

patch:
```

diff --git a/vim-6.3/debian/changelog b/vim-6.3/debian/changelog
index 883d117..053e204 100644
--- a/vim-6.3/debian/changelog
+++ b/vim-6.3/debian/changelog
@@ -1,3 +1,9 @@
+vim (1:6.3-078+1ubuntu4) breezy; urgency=low
+
+  * add athena
+
+ -- Kevin Geiss <kevin@desertsol.com>  Thu, 23 Feb 2006 22:08:18 -0700
+
 vim (1:6.3-078+1ubuntu3) breezy; urgency=low
 
   * Rebuild for the cairo1 -> cairo2 transition.
diff --git a/vim-6.3/debian/control b/vim-6.3/debian/control
index bec4870..4856509 100644
--- a/vim-6.3/debian/control
+++ b/vim-6.3/debian/control
@@ -4,7 +4,7 @@ Priority: optional
 Maintainer: Debian VIM Maintainers <pkg-vim-maintainers@lists.alioth.debian.org>
 Uploaders: Norbert Tretkowski <nobse@debian.org>, Pierre Habouzit <pierre.habouzit@m4x.org>, Torsten Landschoff <torsten@debian.org>, Matthijs Mohlmann <matthijs@cacholong.nl>, Stefano Zacchiroli <zack@debian.org>, Alexis Sukrieh <sukria@sukria.net>, Pepijn de Langen <pepijn@ce.et.tudelft.nl>, James Vega <jamessan@jamessan.com>
 Standards-Version: 3.6.1.1
-Build-Depends: debhelper (>> 4), dpkg (>> 1.7.0), bzip2, perl (>= 5.6), libgpmg1-dev [!hurd-i386] | not+linux-gnu, libperl-dev (>= 5.6), tcl8.4-dev [!hurd-i386] | tcl8.3-dev [!hurd-i386], python-dev, libncurses5-dev, libxt-dev, libgtk2.0-dev (>= 2.2) | libgtk1.2-dev, libgnomeui-dev [!hurd-i386]
+Build-Depends: debhelper (>> 4), dpkg (>> 1.7.0), bzip2, perl (>= 5.6), libgpmg1-dev [!hurd-i386] | not+linux-gnu, libperl-dev (>= 5.6), tcl8.4-dev [!hurd-i386] | tcl8.3-dev [!hurd-i386], python-dev, libncurses5-dev, libxt-dev, libgtk2.0-dev (>= 2.2) | libgtk1.2-dev, libgnomeui-dev [!hurd-i386] | libxaw7-dev
 Build-Conflicts: libperl-dev (= 5.8.4-1)
 
 Package: vim
@@ -14,8 +14,8 @@ Pre-Depends: dpkg (>= 1.6.8)
 Depends: ${shlibs:Depends}, vim-common (= ${Source-Version})
 Suggests: ctags, vim-doc
 Provides: editor, vim-rt
-Conflicts: vim-rt, vim-tiny, vim-perl (<< 6.0), vim-python (<< 6.0), vim-tcl (<< 6.0), vim-tty (<< 6.0), vim-gtk (<< 6.0), vim-lesstif (<< 6.0)
-Replaces: vim-rt, vim-tiny (<< 6.0), vim-perl (<< 6.0), vim-python (<< 6.0), vim-tcl (<< 6.0), vim-tty (<< 6.0), vim-gtk (<< 6.0), vim-lesstif (<< 6.0), kvim (<< 1:6.2.135+1)
+Conflicts: vim-rt, vim-tiny, vim-perl (<< 6.0), vim-python (<< 6.0), vim-tcl (<< 6.0), vim-tty (<< 6.0), vim-gtk (<< 6.0), vim-athena (<< 6.0), vim-lesstif (<< 6.0)
+Replaces: vim-rt, vim-tiny (<< 6.0), vim-perl (<< 6.0), vim-python (<< 6.0), vim-tcl (<< 6.0), vim-tty (<< 6.0), vim-gtk (<< 6.0), vim-athena (<< 6.0), vim-lesstif (<< 6.0), kvim (<< 1:6.2.135+1)
 Description: Vi IMproved - enhanced vi editor
  Vim is an almost compatible version of the UNIX editor Vi.  Many new
  features have been added: multi level undo, syntax highlighting,
@@ -45,8 +45,8 @@ Architecture: any
 Depends: vim (= ${Source-Version}), ${shlibs:Depends}
 Suggests: cscope, vim-doc, ttf-bitstream-vera
 Provides: gvim
-Conflicts: vim-tiny, vim-python, vim-gtk, vim-lesstif, vim-ruby, vim-tcl, vim-tty, vim-gnome, kvim, kvim-perl, kvim-python, kvim-ruby, kvim-tcl, vim (= 1:6.2-532+4ubuntu2)
-Replaces: vim-tiny, vim-python, vim-gtk, vim-lesstif, vim-ruby, vim-tcl, vim-tty, vim-gnome, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-python, kvim-ruby, kvim-tcl
+Conflicts: vim-tiny, vim-python, vim-gtk, vim-athena, vim-lesstif, vim-ruby, vim-tcl, vim-tty, vim-gnome, kvim, kvim-perl, kvim-python, kvim-ruby, kvim-tcl, vim (= 1:6.2-532+4ubuntu2)
+Replaces: vim-tiny, vim-python, vim-gtk, vim-athena, vim-lesstif, vim-ruby, vim-tcl, vim-tty, vim-gnome, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-python, kvim-ruby, kvim-tcl
 Description: Vi IMproved, with perl scripting support
  Vim is an almost compatible version of the UNIX editor Vi.  Many new
  features have been added: multi level undo, syntax highlighting,
@@ -62,8 +62,8 @@ Architecture: any
 Depends: vim (= ${Source-Version}), ${shlibs:Depends}
 Suggests: cscope, vim-doc, ttf-bitstream-vera
 Provides: gvim
-Conflicts: vim-tiny, vim-perl, vim-gtk, vim-lesstif, vim-ruby, vim-tcl, vim-tty, vim-gnome, kvim, kvim-python, kvim-perl, kvim-tcl, kvim-ruby, vim (= 1:6.2-532+4ubuntu2)
-Replaces: vim-tiny, vim-perl, vim-gtk, vim-lesstif, vim-ruby, vim-tcl, vim-tty, vim-gnome, kvim, vim (<= 1:6.3-068+1), kvim-python, kvim-perl, kvim-tcl, kvim-ruby
+Conflicts: vim-tiny, vim-perl, vim-gtk, vim-athena, vim-lesstif, vim-ruby, vim-tcl, vim-tty, vim-gnome, kvim, kvim-python, kvim-perl, kvim-tcl, kvim-ruby, vim (= 1:6.2-532+4ubuntu2)
+Replaces: vim-tiny, vim-perl, vim-gtk, vim-athena, vim-lesstif, vim-ruby, vim-tcl, vim-tty, vim-gnome, kvim, vim (<= 1:6.3-068+1), kvim-python, kvim-perl, kvim-tcl, kvim-ruby
 Description: Vi IMproved, with python scripting support
  Vim is an almost compatible version of the UNIX editor Vi.  Many new
  features have been added: multi level undo, syntax highlighting,
@@ -79,8 +79,8 @@ Architecture: any
 Depends: vim (= ${Source-Version}), ${shlibs:Depends}
 Suggests: cscope, vim-doc, ttf-bitstream-vera
 Provides: gvim
-Conflicts: vim-tiny, vim-perl, vim-gtk, vim-lesstif, vim-python, vim-tcl, vim-tty, kvim, kvim-perl, kvim-python, kvim-tcl
-Replaces: vim-tiny, vim-perl, vim-gtk, vim-lesstif, vim-python, vim-tcl, vim-tty, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-python, kvim-tcl
+Conflicts: vim-tiny, vim-perl, vim-gtk, vim-athena, vim-lesstif, vim-python, vim-tcl, vim-tty, kvim, kvim-perl, kvim-python, kvim-tcl
+Replaces: vim-tiny, vim-perl, vim-gtk, vim-athena, vim-lesstif, vim-python, vim-tcl, vim-tty, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-python, kvim-tcl
 Description: Vi IMproved, with ruby scripting support
  Vim is an almost compatible version of the UNIX editor Vi.  Many new
  features have been added: multi level undo, syntax highlighting,
@@ -96,8 +96,8 @@ Architecture: any
 Depends: vim (= ${Source-Version}), ${shlibs:Depends}
 Suggests: cscope, vim-doc, ttf-bitstream-vera
 Provides: gvim
-Conflicts: vim-tiny, vim-perl, vim-gtk, vim-lesstif, vim-python, vim-ruby, vim-tty, vim-gnome, kvim, kvim-perl, kvim-ruby, kvim-tcl, kvim-python
-Replaces: vim-tiny, vim-perl, vim-gtk, vim-lesstif, vim-python, vim-ruby, vim-tty, vim-gnome, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-ruby, kvim-tcl, kvim-python, vim (= 1:6.2-532+4ubuntu2)
+Conflicts: vim-tiny, vim-perl, vim-gtk, vim-athena, vim-lesstif, vim-python, vim-ruby, vim-tty, vim-gnome, kvim, kvim-perl, kvim-ruby, kvim-tcl, kvim-python
+Replaces: vim-tiny, vim-perl, vim-gtk, vim-athena, vim-lesstif, vim-python, vim-ruby, vim-tty, vim-gnome, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-ruby, kvim-tcl, kvim-python, vim (= 1:6.2-532+4ubuntu2)
 Description: Vi IMproved, with tcl scripting support
  Vim is an almost compatible version of the UNIX editor Vi.  Many new
  features have been added: multi level undo, syntax highlighting,
@@ -113,8 +113,8 @@ Architecture: any
 Depends: vim (= ${Source-Version}), ${shlibs:Depends}
 Suggests: cscope, vim-doc, ttf-bitstream-vera
 Provides: gvim
-Conflicts: vim-tiny, vim-perl, vim-python, vim-ruby, vim-tcl, vim-lesstif, vim-tty, vim-gnome, kvim, kvim-perl, kvim-ruby, kvim-tcl, kvim-python
-Replaces: vim-tiny, vim-perl, vim-python, vim-ruby, vim-tcl, vim-lesstif, vim-tty, vim-gnome, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-ruby, kvim-tcl, kvim-python, vim (= 1:6.2-532+4ubuntu2)
+Conflicts: vim-tiny, vim-perl, vim-athena, vim-python, vim-ruby, vim-tcl, vim-lesstif, vim-tty, vim-gnome, kvim, kvim-perl, kvim-ruby, kvim-tcl, kvim-python
+Replaces: vim-tiny, vim-perl, vim-athena, vim-python, vim-ruby, vim-tcl, vim-lesstif, vim-tty, vim-gnome, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-ruby, kvim-tcl, kvim-python, vim (= 1:6.2-532+4ubuntu2)
 Description: Vi IMproved - GTK2 Version
  Vim is an almost compatible version of the UNIX editor Vi.  Many new features
  have been added: multi level undo, syntax highlighting, command line history,
@@ -123,14 +123,30 @@ Description: Vi IMproved - GTK2 Version
  .
  This package contains a version of vim compiled with support for GTK2 gui.
 
+Package: vim-athena
+Priority: extra
+Architecture: any
+Depends: vim (= ${Source-Version}), ${shlibs:Depends}
+Suggests: cscope, vim-doc
+Provides: gvim
+Conflicts: vim-tiny, vim-perl, vim-gtk, vim-python, vim-ruby, vim-tcl, vim-lesstif, vim-tty, vim-gnome, kvim, kvim-perl, kvim-ruby, kvim-tcl, kvim-python
+Replaces: vim-tiny, vim-perl, vim-gtk, vim-python, vim-ruby, vim-tcl, vim-lesstif, vim-tty, vim-gnome, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-ruby, kvim-tcl, kvim-python, vim (= 1:6.2-532+4ubuntu2)
+Description: Vi IMproved - Athena Version
+ Vim is an almost compatible version of the UNIX editor Vi.  Many new features
+ have been added: multi level undo, syntax highlighting, command line history,
+ on-line help, filename completion, block operations, folding, Unicode support,
+ etc.
+ .
+ This package contains a version of vim compiled with support for Athena gui.
+
 Package: vim-gnome
 Priority: extra
 Architecture: any
 Depends: vim (= ${Source-Version}), ${shlibs:Depends}
 Suggests: cscope, vim-doc, ttf-bitstream-vera
 Provides: gvim
-Conflicts: vim-tiny, vim-perl, vim-python, vim-ruby, vim-tcl, vim-tty, vim-gtk, vim-lesstif, kvim, kvim-perl, kvim-ruby, kvim-tcl, kvim-python
-Replaces: vim-tiny, vim-perl, vim-python, vim-ruby, vim-tcl, vim-tty, vim-gtk, vim-lesstif, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-ruby, kvim-tcl, kvim-python, vim (= 1:6.2-532+4ubuntu2)
+Conflicts: vim-tiny, vim-perl, vim-python, vim-ruby, vim-tcl, vim-tty, vim-gtk, vim-athena, vim-lesstif, kvim, kvim-perl, kvim-ruby, kvim-tcl, kvim-python
+Replaces: vim-tiny, vim-perl, vim-python, vim-ruby, vim-tcl, vim-tty, vim-gtk, vim-athena, vim-lesstif, kvim, vim (<= 1:6.3-068+1), kvim-perl, kvim-ruby, kvim-tcl, kvim-python, vim (= 1:6.2-532+4ubuntu2)
 Description: Vi IMproved - GNOME2 Version
  Vim is an almost compatible version of the UNIX editor Vi.  Many new features
  have been added: multi level undo, syntax highlighting, command line history,
diff --git a/vim-6.3/debian/rules b/vim-6.3/debian/rules
index 3c97953..5ca9108 100755
--- a/vim-6.3/debian/rules
+++ b/vim-6.3/debian/rules
@@ -34,6 +34,9 @@ GUIFLAGS+=--enable-fontset
 GTK2FLAGS+=--enable-gui=gtk2
 GTK2FLAGS+=--with-features=big
 
+ATHENAFLAGS+=--enable-gui=athena
+ATHENAFLAGS+=--with-features=big
+
 GNOMEFLAGS+=--enable-gui=gnome2
 
 KDEFLAGS+=--enable-gui=kde
@@ -78,6 +81,7 @@ ifneq ($(DEB_HOST_GNU_SYSTEM),gnu)
   VARIANTS_SKIP+=vim-ruby
   VARIANTS+=vim-tcl
   VARIANTS+=vim-gtk
+  VARIANTS+=vim-athena
   VARIANTS+=vim-perl
   VARIANTS+=vim-python
   VARIANTS+=vim-gnome
@@ -86,6 +90,7 @@ else
   VARIANTS+=vim-basic
   VARIANTS+=vim-ruby
   VARIANTS+=vim-gtk
+  VARIANTS+=vim-athena
   VARIANTS+=vim-python
   VARIANTS_SKIP+=vim-tiny
   VARIANTS_SKIP+=vim-perl
@@ -117,6 +122,9 @@ CFGFLAGS_vim-tcl=$(CFGFLAGS) $(OPTFLAGS)
 CFLAGS_vim-gtk=$(CFLAGS)
 CFGFLAGS_vim-gtk=$(CFGFLAGS) $(OPTFLAGS) $(GUIFLAGS) $(BASICFLAGS) $(GTK2FLAGS)
 
+CFLAGS_vim-athena=$(CFLAGS)
+CFGFLAGS_vim-athena=$(CFGFLAGS) $(OPTFLAGS) $(GUIFLAGS) $(BASICFLAGS) $(ATHENAFLAGS)
+
 CFLAGS_vim-gnome=$(CFLAGS)
 CFGFLAGS_vim-gnome=$(CFGFLAGS) $(OPTFLAGS) $(GUIFLAGS) $(BASICFLAGS) $(GNOMEFLAGS)
 
diff --git a/vim_6.3-078+1ubuntu3.diff.gz b/vim_6.3-078+1ubuntu3.diff.gz
index 9fb762c..5a2ed58 100644
Binary files a/vim_6.3-078+1ubuntu3.diff.gz and b/vim_6.3-078+1ubuntu3.diff.gz differ
diff --git a/vim_6.3-078+1ubuntu3.dsc b/vim_6.3-078+1ubuntu3.dsc
index 0ee12d0..a719ada 100644
--- a/vim_6.3-078+1ubuntu3.dsc
+++ b/vim_6.3-078+1ubuntu3.dsc
@@ -1,10 +1,7 @@
------BEGIN PGP SIGNED MESSAGE-----
-Hash: SHA1
-
 Format: 1.0
 Source: vim
 Version: 1:6.3-078+1ubuntu3
-Binary: vim-gtk, vim, vim-python, vim-gnome, vim-common, vim-tiny, vim-tcl, vim-perl, vim-ruby, vim-doc
+Binary: vim-gtk, vim, vim-python, vim-athena, vim-doc, vim-tiny, vim-tcl, vim-perl, vim-ruby, vim-common, vim-gnome
 Maintainer: Debian VIM Maintainers <pkg-vim-maintainers@lists.alioth.debian.org>
 Architecture: any
 Standards-Version: 3.6.1.1
@@ -13,12 +10,4 @@ Build-Conflicts: libperl-dev (= 5.8.4-1)
 Uploaders: Norbert Tretkowski <nobse@debian.org>, Pierre Habouzit <pierre.habouzit@m4x.org>, Torsten Landschoff <torsten@debian.org>, Matthijs Mohlmann <matthijs@cacholong.nl>, Stefano Zacchiroli <zack@debian.org>, Alexis Sukrieh <sukria@sukria.net>, Pepijn de Langen <pepijn@ce.et.tudelft.nl>, James Vega <jamessan@jamessan.com>
 Files: 
  de1c964ceedbc13538da87d2d73fd117 5624622 vim_6.3.orig.tar.gz
- 8f0876ca7b820c0e3370c9f01a70dcff 333385 vim_6.3-078+1ubuntu3.diff.gz
-
------BEGIN PGP SIGNATURE-----
-Version: GnuPG v1.4.1 (GNU/Linux)
-
-iD8DBQFDCfYQvjztR8bOoMkRAvv1AJ9xTILSv98zsOBwK1doeUZboLNQQQCeMrzs
-de6I+vtEraMIICH79CdjR88=
-=Dhe9
------END PGP SIGNATURE-----
+ edf33f6bc9efad792f29caef38f12341 338533 vim_6.3-078+1ubuntu3.diff.gz

```

---

