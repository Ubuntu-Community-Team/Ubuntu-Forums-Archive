---
title: "How to add a file as a patch."
date: 2011-10-31
forum: Packaging and Compiling Programs
---

### Post by MG&amp;TL on 2011-10-31
I've been working on a fairly simple, bite-size patch for me to get stuck into, however I have run into a problem. I need to add some files, as well as modify them, to apply my patch. (the issue is the icons for the .desktop files are missing, and the .desktop files don't reference an icon.)

I've been reading the various wikis on how to patch bugs in launchpad, but I can't work out how to add a file, rather than just modify it.


And a second issue (probably due to a lack of comprehension, but hey), the bzr bd command issued here:  [wiki.ubuntu.com/Bugs/HowToFix]("wiki.ubuntu.com/Bugs/Howtofix") works fine, but throws errors, saying that the files I've added don't correspond with the orig.tar.gz....that I don't have. How does it find this tarball, and what can I do about it?

---

### Post by MG&amp;TL on 2011-10-31
Bug ref: [https://bugs.launchpad.net/ubuntu/+source/ace-of-penguins/+bug/651366]("https://bugs.launchpad.net/ubuntu/+source/ace-of-penguins/+bug/651366")

---

### Post by MadCow108 on 2011-10-31
this particular package is a 3.0 (quilt) package so patches are best handled via quilt.
adding a new text file would go like this:
```

export QUILT_PATCHES="debian/patches"
quilt new my-patch-name
quilt add new-file
<create-and-edit-file>
quilt refresh
```

this will create a patch that will create a file when applied. patching existing files works the same way including the bug
you can apply and remove patch with *quilt push* and *pop* and get a list of applied patches with *quilt applied*

with the 3.0 format you can also just edit the source and execute *debuild*
that will create a patch from your changes for you and place it in debian/patches.
Make sure to rename it to something meaningful and fill out the header information in it.
Take care not to accidentally add these automatic patches.

adding binary files like icons is not possible with a normal patch (at least without encoding it which is discouraged).
you have to add the name of binaries to debian/source/include-binaries for them to be included.
You must make sure you forward this binary to the upstream developers so that it will be in the original tarball next release.
see man dpkg-source for more information


If you use bzr-buildpackage it will create the orig.tar.gz from the bzr repository for you.
I never use bzr builddeb.

---

### Post by SevenMachines on 2011-10-31
One additional thing to remember about quilt is that patches are applied in series, so apply all current patches first, make your own changes as madcow108 shows, then unapply all patches afterwards before debuilding
$ quilt push -a
# do all the stuff to make your own patch here
$ quilt pop -a

---

### Post by MG&amp;TL on 2011-11-01
Cool. Thanks, guys. The confusion arose from trying to do this instead:

1. <create and edit files>

2. quilt new

3. quilt add

4. quilt refresh

...which obviously doesn't work. Thanks. :)


I already talked to the upstream people, they do not want to add icons, as apparently it's debian-specific. IDK, but I thought the free desktop specification thing was meant to be universal. But hey. I'll stick it in debian/include-binaries, and see what happens. Is this advisable?

---

### Post by MG&amp;TL on 2011-11-01
I think I've found a workaround/solution. If I put the files in debian/, they can't cause a problem, right? They don't need to be anywhere else.

---

### Post by MadCow108 on 2011-11-01
debian/ is a good place for files not associated with upstream, thought you have to make sure they are installed correctly yourself (e.g. by editing debian/install or debian/package-name.install, see man dh_install)

---

### Post by MG&amp;TL on 2011-11-01
Okay...so the steps would be?

My guess:

bzr branch
make orig.tar.gz w/out debian directory
copy files over
edit .install file
debuild
test
edit debian/changelog
bzr push lp:~/michaelrawson/ubuntu/oneiric/fixforace-of-penguins#1234 or something?

Only learned packaging about a month ago, so still newbish. Thanks for support :)

---

### Post by MadCow108 on 2011-11-01
with bzr its something around the lines of this:
```

bzr branch
edit and add stuff (use bzr add for new files)
edit changelog (with dch)
debcommit (will automatically link fixed bugs from the changelog) or bzr commit
bzr-buildpackage
test
repeat or push when done
```

---

### Post by MG&amp;TL on 2011-11-01
Thanks, madcow, I will try this in the morn.

---

### Post by MG&amp;TL on 2011-11-02
Works fine up until building the package:

```
michael@michael-desktop:~/Documents/ace-of-penguins$ bzr-buildpackage
Building using working tree
Building package in normal mode
Looking for a way to retrieve the upstream tarball
Using apt to look for the upstream tarball.
apt could not find the needed tarball.
Trying to use get-orig-source to retrieve needed tarball.
dh get-orig-source
dh: Unknown sequence get-orig-source (choose from: binary binary-arch binary-indep build build-arch build-indep clean install install-arch install-indep)
make: *** [get-orig-source] Error 255
Trying to run get-orig-source rule failed
Using uscan to look for the upstream tarball.
uscan warning: In /tmp/tmpsGnU7N no matching hrefs for version 1.3-3 in watch line
  http://www.delorie.com/store/ace/ace-([\d\.]*)\.tar\.gz
uscan could not find the needed tarball.
bzr: ERROR: Unable to find the needed upstream tarball for package ace-of-penguins, version 1.3-3.

```

What am I doing wrong?

---

### Post by SevenMachines on 2011-11-02
bzr-buildpackage tries a sequence of different ways to get an orig tarball, some of those below you might want to check you have enabled

* Make sure you've got a deb-src entry in apt sources.list, eg

/etc/apt/sources.list
```
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric restricted main multiverse universe
```* install pristine-tar
```
$ sudo apt-get install bzr-builddeb pristine-tar
```See if either of those are missing

---

### Post by MG&amp;TL on 2011-11-02
Nope, they're both installed. :confused:

---

### Post by MG&amp;TL on 2011-11-02
I'm using Lubuntu-is this an issue?

---

### Post by MG&amp;TL on 2011-11-02
File tree (sorry, big file):

```
&#9500;&#9472;&#9472; ace-of-penguins #This is the modded one
&#9474;   &#9500;&#9472;&#9472; aclocal.m4
&#9474;   &#9500;&#9472;&#9472; AUTHORS
&#9474;   &#9500;&#9472;&#9472; ChangeLog
&#9474;   &#9500;&#9472;&#9472; config.guess
&#9474;   &#9500;&#9472;&#9472; config.h.in
&#9474;   &#9500;&#9472;&#9472; config.sub
&#9474;   &#9500;&#9472;&#9472; configure
&#9474;   &#9500;&#9472;&#9472; configure.in
&#9474;   &#9500;&#9472;&#9472; COPYING
&#9474;   &#9500;&#9472;&#9472; debian
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.6.pod
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.debhelper.log
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.doc-base
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.install
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.lintian-overrides
&#9474;   &#9474;   &#9500;&#9472;&#9472; changelog
&#9474;   &#9474;   &#9500;&#9472;&#9472; clean
&#9474;   &#9474;   &#9500;&#9472;&#9472; compat
&#9474;   &#9474;   &#9500;&#9472;&#9472; control
&#9474;   &#9474;   &#9500;&#9472;&#9472; copyright
&#9474;   &#9474;   &#9500;&#9472;&#9472; debian-compile.mk
&#9474;   &#9474;   &#9500;&#9472;&#9472; debian-vars.mk
&#9474;   &#9474;   &#9500;&#9472;&#9472; dirs
&#9474;   &#9474;   &#9500;&#9472;&#9472; icons
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 128x128
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 16x16
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 22x22
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 24x24
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 32x32
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 36x36
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 48x48
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 64x64
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 72x72
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; 96x96
&#9474;   &#9474;   &#9474;       &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; manpages
&#9474;   &#9474;   &#9500;&#9472;&#9472; menu
&#9474;   &#9474;   &#9500;&#9472;&#9472; NEWS.Debian
&#9474;   &#9474;   &#9500;&#9472;&#9472; patches
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 10-autoreconf-fi--2.65.patch
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 20-lib--make-imglib.c-closedir.patch
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 30-spider.c-implicit-pointer-conversion.patch
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 40-include.patch
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; series
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-canfield.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-freecell.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-golf.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-mastermind.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-merlin.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-minesweeper.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-pegged.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-solitaire.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-spider.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-taipei.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-taipei-editor.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-thornq.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; pod2man.mk
&#9474;   &#9474;   &#9500;&#9472;&#9472; README.source
&#9474;   &#9474;   &#9500;&#9472;&#9472; rules
&#9474;   &#9474;   &#9500;&#9472;&#9472; source
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; format
&#9474;   &#9474;   &#9500;&#9472;&#9472; source.lintian-overrides
&#9474;   &#9474;   &#9492;&#9472;&#9472; watch
&#9474;   &#9500;&#9472;&#9472; depcomp
&#9474;   &#9500;&#9472;&#9472; docs
&#9474;   &#9474;   &#9500;&#9472;&#9472; as.gif
&#9474;   &#9474;   &#9500;&#9472;&#9472; COPYING
&#9474;   &#9474;   &#9500;&#9472;&#9472; intro.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin.gif
&#9474;   &#9474;   &#9500;&#9472;&#9472; title.gif
&#9474;   &#9474;   &#9492;&#9472;&#9472; toolkit.html
&#9474;   &#9500;&#9472;&#9472; games
&#9474;   &#9474;   &#9500;&#9472;&#9472; canfield.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; canfield.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; freecell.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; freecell.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; freecell.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf-arrow.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf-noarrow.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; Makefile.am
&#9474;   &#9474;   &#9500;&#9472;&#9472; Makefile.in
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-b.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-c.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-eb.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-e.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-g.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-k.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-o.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-p.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-r.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-w.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-y.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin-b.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin-c.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-c12.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-c24.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-c36.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-c48.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-t.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-x.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged-h.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged-p.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; solitaire.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; solitaire.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; solitaire.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; spider.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; spider.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; spider.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit-bs.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit-bt.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit-bu.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-bridge.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-castle.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-cube.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-glyph.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-jason.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipeilib.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipeilib.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-pyramid.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-rebecca.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-simple.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-smiley.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-spiral.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-standard.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-tiles.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; thornq-arrow.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; thornq.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; thornq.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; thornq-noarrow.png
&#9474;   &#9474;   &#9492;&#9472;&#9472; thornq.png
&#9474;   &#9500;&#9472;&#9472; INSTALL
&#9474;   &#9500;&#9472;&#9472; install-sh
&#9474;   &#9500;&#9472;&#9472; lib
&#9474;   &#9474;   &#9500;&#9472;&#9472; cards.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; funcs.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; funcs.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; help.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; imagelib.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; imagelib.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; images.in
&#9474;   &#9474;   &#9500;&#9472;&#9472; Makefile.am
&#9474;   &#9474;   &#9500;&#9472;&#9472; Makefile.in
&#9474;   &#9474;   &#9500;&#9472;&#9472; make-imglib.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguins.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; a-k.2.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; a-k.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; back.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; back-tile.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; big-penguin.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; jack.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; king.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; no-drop.25.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; no-drop.50.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; penguin.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; queen.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; splash.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; suits.13.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; suits.26.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; suits.39.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; suits.9.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; xemboss.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; youlose.png
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; youwin.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; stack.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; table.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; table.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; table_rn.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; text2c.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; xwin.c
&#9474;   &#9474;   &#9492;&#9472;&#9472; xwin.h
&#9474;   &#9500;&#9472;&#9472; ltconfig
&#9474;   &#9500;&#9472;&#9472; ltmain.sh
&#9474;   &#9500;&#9472;&#9472; Makefile.am
&#9474;   &#9500;&#9472;&#9472; Makefile.in
&#9474;   &#9500;&#9472;&#9472; missing
&#9474;   &#9500;&#9472;&#9472; mkdist
&#9474;   &#9500;&#9472;&#9472; mkinstalldirs
&#9474;   &#9500;&#9472;&#9472; NEWS
&#9474;   &#9500;&#9472;&#9472; README
&#9474;   &#9492;&#9472;&#9472; tests
&#9474;       &#9500;&#9472;&#9472; Makefile.am
&#9474;       &#9500;&#9472;&#9472; Makefile.in
&#9474;       &#9500;&#9472;&#9472; penguins.c
&#9474;       &#9500;&#9472;&#9472; test1.c
&#9474;       &#9500;&#9472;&#9472; test3.c
&#9474;       &#9500;&#9472;&#9472; test4.c
&#9474;       &#9500;&#9472;&#9472; test5.c
&#9474;       &#9500;&#9472;&#9472; test6.c
&#9474;       &#9492;&#9472;&#9472; test6.png
&#9500;&#9472;&#9472; ace-of-penguins.diff #this is where I keep changes for safe-keeping
&#9474;   &#9500;&#9472;&#9472; aclocal.m4
&#9474;   &#9500;&#9472;&#9472; AUTHORS
&#9474;   &#9500;&#9472;&#9472; ChangeLog
&#9474;   &#9500;&#9472;&#9472; config.guess
&#9474;   &#9500;&#9472;&#9472; config.h.in
&#9474;   &#9500;&#9472;&#9472; config.sub
&#9474;   &#9500;&#9472;&#9472; configure
&#9474;   &#9500;&#9472;&#9472; configure.in
&#9474;   &#9500;&#9472;&#9472; COPYING
&#9474;   &#9500;&#9472;&#9472; debian
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.6.pod
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.debhelper.log
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.doc-base
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.install
&#9474;   &#9474;   &#9500;&#9472;&#9472; ace-of-penguins.lintian-overrides
&#9474;   &#9474;   &#9500;&#9472;&#9472; changelog
&#9474;   &#9474;   &#9500;&#9472;&#9472; clean
&#9474;   &#9474;   &#9500;&#9472;&#9472; compat
&#9474;   &#9474;   &#9500;&#9472;&#9472; control
&#9474;   &#9474;   &#9500;&#9472;&#9472; copyright
&#9474;   &#9474;   &#9500;&#9472;&#9472; debian-compile.mk
&#9474;   &#9474;   &#9500;&#9472;&#9472; debian-vars.mk
&#9474;   &#9474;   &#9500;&#9472;&#9472; dirs
&#9474;   &#9474;   &#9500;&#9472;&#9472; icons
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 128x128
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 16x16
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 22x22
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 24x24
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 32x32
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 36x36
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 48x48
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 64x64
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 72x72
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; 96x96
&#9474;   &#9474;   &#9474;       &#9492;&#9472;&#9472; ace-of-penguins.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; manpages
&#9474;   &#9474;   &#9500;&#9472;&#9472; menu
&#9474;   &#9474;   &#9500;&#9472;&#9472; NEWS.Debian
&#9474;   &#9474;   &#9500;&#9472;&#9472; patches
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 10-autoreconf-fi--2.65.patch
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 20-lib--make-imglib.c-closedir.patch
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 30-spider.c-implicit-pointer-conversion.patch
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; 40-include.patch
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; series
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-canfield.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-freecell.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-golf.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-mastermind.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-merlin.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-minesweeper.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-pegged.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-solitaire.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-spider.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-taipei.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-taipei-editor.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin-thornq.desktop
&#9474;   &#9474;   &#9500;&#9472;&#9472; pod2man.mk
&#9474;   &#9474;   &#9500;&#9472;&#9472; README.source
&#9474;   &#9474;   &#9500;&#9472;&#9472; rules
&#9474;   &#9474;   &#9500;&#9472;&#9472; source
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; format
&#9474;   &#9474;   &#9500;&#9472;&#9472; source.lintian-overrides
&#9474;   &#9474;   &#9492;&#9472;&#9472; watch
&#9474;   &#9500;&#9472;&#9472; depcomp
&#9474;   &#9500;&#9472;&#9472; docs
&#9474;   &#9474;   &#9500;&#9472;&#9472; as.gif
&#9474;   &#9474;   &#9500;&#9472;&#9472; COPYING
&#9474;   &#9474;   &#9500;&#9472;&#9472; intro.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguin.gif
&#9474;   &#9474;   &#9500;&#9472;&#9472; title.gif
&#9474;   &#9474;   &#9492;&#9472;&#9472; toolkit.html
&#9474;   &#9500;&#9472;&#9472; games
&#9474;   &#9474;   &#9500;&#9472;&#9472; canfield.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; canfield.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; freecell.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; freecell.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; freecell.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf-arrow.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf-noarrow.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; golf.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; Makefile.am
&#9474;   &#9474;   &#9500;&#9472;&#9472; Makefile.in
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-b.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-c.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-eb.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-e.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-g.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-k.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-o.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-p.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-r.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-w.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; mastermind-y.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin-b.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin-c.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; merlin.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-c12.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-c24.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-c36.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-c48.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-t.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; minesweeper-x.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged-h.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; pegged-p.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; solitaire.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; solitaire.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; solitaire.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; spider.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; spider.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; spider.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit-bs.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit-bt.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit-bu.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipedit.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-bridge.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-castle.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-cube.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-glyph.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-jason.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipeilib.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipeilib.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-pyramid.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-rebecca.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-simple.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-smiley.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-spiral.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-standard.tp
&#9474;   &#9474;   &#9500;&#9472;&#9472; taipei-tiles.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; thornq-arrow.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; thornq.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; thornq.html
&#9474;   &#9474;   &#9500;&#9472;&#9472; thornq-noarrow.png
&#9474;   &#9474;   &#9492;&#9472;&#9472; thornq.png
&#9474;   &#9500;&#9472;&#9472; INSTALL
&#9474;   &#9500;&#9472;&#9472; install-sh
&#9474;   &#9500;&#9472;&#9472; lib
&#9474;   &#9474;   &#9500;&#9472;&#9472; cards.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; funcs.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; funcs.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; help.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; imagelib.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; imagelib.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; images.in
&#9474;   &#9474;   &#9500;&#9472;&#9472; Makefile.am
&#9474;   &#9474;   &#9500;&#9472;&#9472; Makefile.in
&#9474;   &#9474;   &#9500;&#9472;&#9472; make-imglib.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; penguins.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; a-k.2.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; a-k.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; back.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; back-tile.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; big-penguin.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; jack.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; king.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; no-drop.25.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; no-drop.50.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; penguin.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; queen.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; splash.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; suits.13.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; suits.26.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; suits.39.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; suits.9.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; xemboss.png
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; youlose.png
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; youwin.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; stack.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; table.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; table.h
&#9474;   &#9474;   &#9500;&#9472;&#9472; table_rn.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; text2c.c
&#9474;   &#9474;   &#9500;&#9472;&#9472; xwin.c
&#9474;   &#9474;   &#9492;&#9472;&#9472; xwin.h
&#9474;   &#9500;&#9472;&#9472; ltconfig
&#9474;   &#9500;&#9472;&#9472; ltmain.sh
&#9474;   &#9500;&#9472;&#9472; Makefile.am
&#9474;   &#9500;&#9472;&#9472; Makefile.in
&#9474;   &#9500;&#9472;&#9472; missing
&#9474;   &#9500;&#9472;&#9472; mkdist
&#9474;   &#9500;&#9472;&#9472; mkinstalldirs
&#9474;   &#9500;&#9472;&#9472; NEWS
&#9474;   &#9500;&#9472;&#9472; README
&#9474;   &#9492;&#9472;&#9472; tests
&#9474;       &#9500;&#9472;&#9472; Makefile.am
&#9474;       &#9500;&#9472;&#9472; Makefile.in
&#9474;       &#9500;&#9472;&#9472; penguins.c
&#9474;       &#9500;&#9472;&#9472; test1.c
&#9474;       &#9500;&#9472;&#9472; test3.c
&#9474;       &#9500;&#9472;&#9472; test4.c
&#9474;       &#9500;&#9472;&#9472; test5.c
&#9474;       &#9500;&#9472;&#9472; test6.c
&#9474;       &#9492;&#9472;&#9472; test6.png
&#9500;&#9472;&#9472; build-area

```

---

### Post by MadCow108 on 2011-11-02
you branched this?
```
bzr branch lp:ubuntu/ace-of-penguins
```

you can also just download the tarball from debian or launchpad.
or apt-get source package-name
or pull-debian-source package-name
or pull-lp-source package-name
or dget url-to-dsc-file
etc etc

---

### Post by MG&amp;TL on 2011-11-03
OKay, but ho do I tell bzr where the tarball is? If I point it to the dir with ---orig-dir= it still searches apt, etc.

And no, I got lp:~ubuntu/oneiric/ace-of-penguins

---

### Post by MG&amp;TL on 2011-11-03
Okay, I have a ~/Documents/debian directory containing all my changes.

How would you suggest that I went about applying the patch? (I thought I'd simplify things a bit)

---

