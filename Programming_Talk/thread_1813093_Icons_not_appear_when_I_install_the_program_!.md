---
title: "Icons not appear when I install the program !?"
date: 2011-07-27
forum: Programming Talk
---

### Post by yahyai-0 on 2011-07-27
Hi there

I have finished writing my first gtkmm program , I have used anjuata.
the program use icons from folder icons....

When I run the program from (anjuata) the icon appear perfectly.
but after making the Tarball to package (Deb) and install(./configure , make , make install) it 
It run without the icons!!! (the icon folder exist on tarball)

plz help me

---

### Post by JupiterV2 on 2011-07-27
Need more information. Assuming the project uses GNU autotools, have you run the 'distcheck' rule? Does the project otherwise compile/run as expected with ./configure && make && make install? My guess is that you've configured your Makefile(s) incorrectly and are either not installing the icons at all or they're being installed to the wrong directory. It's also possible you've hard-coded your directories/file names and gtkmm can't locate them because they've been installed into a different directory. Can you perhaps show us a copy of the Makefile you use to install your icons?

You won't, as I think you've already guessed, be able to properly build a .deb file until your standard build script works properly.

---

### Post by yahyai-0 on 2011-07-27
thanks for you replay

this is the tarball [ATTACH]198606[/ATTACH]

the program not yet done ;)

---

### Post by Zugzwang on 2011-07-27
You icons paths are relative. This means that if you run your program from a different path than the one that contains the folder "icons", then they won't be found. There is a common solutions in connection with the autotools. Hopefully, someone else can describe it, as I have no clue about the autotools.

---

### Post by JupiterV2 on 2011-07-27
Zugzwang is correct, you are using relative paths; meaning, path's relative to the installed binary. So, it will work when testing it but won't work when the program has been installed. According to the [XDG Icon Theme Specification]("http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html") (Application Icons are discussed near the bottom) icons are normally installed to ${prefix}/share/icons/hicolor/16x16/apps where prefix is set by configure. You will need a method of knowing/discovering where your icons have been installed to and then supply the absolute path to them.

I've never developed with Anjuta so I don't know how to adjust how the automatic autotools scripts are written or adjusted.

---

