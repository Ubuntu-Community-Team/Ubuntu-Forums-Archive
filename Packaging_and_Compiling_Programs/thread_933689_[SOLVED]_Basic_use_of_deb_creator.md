---
title: "[SOLVED] Basic use of deb creator"
date: 2008-09-29
forum: Packaging and Compiling Programs
---

### Post by Nonno Bassotto on 2008-09-29
Hello, I'm trying to create a simple, very very simple Debian package which just installs some bash scripts in /local/bin, a .desktop file and few more things. No compiling is involved, just copy the files to the appropriate locations.

I was trying to use [Deb Creator]("http://debcreator.cmsoft.net/") since I wanted
1) to do things as simple as possible
2) to create a decent package, that is with dependecies, metadata and so on.

Still I have no luck. What is the directory structure for the archive I have to give to Deb Creator? It always complains about
```

Unable to detect the top source directory in the archive. This should be something like <name>-<version>

```
even if of course the top directory is called goodsleep-0.1

---

### Post by Hairy_Palms on 2008-09-30
well i havent tried deb creator, but my suggestion is to just use dpkg-deb, you only need to create the file structure then run 
```
sudo dpkg-deb -b example
```
ill attach an example at the end, if you have any more questions feel free to ask :)

---

### Post by Nonno Bassotto on 2008-09-30
Does dpkg-deb allow you to set dependencies for your package? From what I understand one can use Deb Creator to build a proper Ubuntu package.

---

### Post by Hairy_Palms on 2008-09-30
yes, if you look at the control file, it has a depends section, heres the control file from the gimp2.5 package for example
> Package: gimp2.5
Priority: extra
Section: graphics
Installed-Size: 56468
Maintainer: [email]Hairy_palms@ubuntuforums.org[/email]
Architecture: i386
Version: 2.5.4-1
Depends: gegl, babl, libaa1 (>= 1.4p5), libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.71), libexif12, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.13.6), libgtkhtml2-0 (>= 2.11.1), libhal1 (>= 0.5.8.1), libjpeg62, liblcms1 (>= 1.15-1), libmng1 (>= 1.0.3-1), libpango1.0-0 (>= 1.21.3), libpng12-0 (>= 1.2.13-4), libpoppler-glib3, librsvg2-2 (>= 2.18.1), libtiff4, libwmf0.2-7 (>= 0.2.8.4), libx11-6, libxext6, libxmu6, libxpm4, zlib1g (>= 1:1.1.4)
Provides: gimp
Description: The GNU Image Manipulation Program
 GIMP lets you draw, paint, edit images, and much more! GIMP
 includes the functionality and plug-ins of other famous image
 editing and processing programs.
 This is the Development Release 2.5.4

---

### Post by Paul Weaver on 2008-09-30
At it's most basic view, a binary deb is simply a tarball, and some control information I guess "debcreator" creates the control files in a gui-way, and wraps up the other required steps. We have a similar program.

Our packages are stored in subversion in /trunk/usr, /trunk/etc, and /trunk/DEBIAN

We have an internally developed script 
 myorg-debmaker - a quick way to bash out an internal .deb
 
       myorg-debmaker is a quick way to create and check a simple  .deb  file
       for  use in the myorg Ubuntu repository. You should provide a subver&#8208;
       sion url to pull the version from, and myorg-debmaker checks the  code
       out, ensures permissions are correct, and builds the .deb

       Run:

       myorg-debmaker   [http://svn.server/svn/myorg](http://svn.server/svn/myorg)  myorg-myproject

       And  all  being  well   myorg-myproject.deb   will   be   created   in
       /usr/share/myorg-debmaker/debs

       We  don&#8217;t  do a lot of checking at the momemnt, and trust you to create
       the appropiate changelog, control files, and  maintain  versioning.  We
       don&#8217;t create a tag either, but all this is due in future versions



Basically the flow is
1) Lay out project in a directory structure
2) Create DEBIAN directory containing control, postinst, preinst, etc (we tend to have these hardlinked to keep installation functions together)
3) run myorg-debmaker as above

The problem then
1) relaunches as fakeroot
2) SVN export
3) Checks version number has incremented since last generated .deb
4) Checks file permissions
5) Creates md5sums
6) Creates the .deb with "dpkg -b"
7) moves deb into repository
8) uses dpkg-scanpackages and apt-ftparchive to update repo
9) gpg signs Release
10) Runs lintian

---

### Post by Nonno Bassotto on 2008-09-30
@Hairy-Palms: Thank you! It worked perfectly

@Paul: I don't understand. I don't have a subversion project, just some files to put here and there...

---

### Post by Elep.Repu on 2009-08-26
I don't get it.
How do you use debcreator?

I don't have a respository, or a svn. I just have all the dependencies, and the program installed. 
What next?

---

### Post by cowboysaif on 2010-08-26
> **Elep.Repu said:**
> I don't get it.
How do you use debcreator?

I don't have a respository, or a svn. I just have all the dependencies, and the program installed. 
What next?

i dont know if the answer is any help to you after exactly a year later, but i had the similar prob and i tried this - 

1. Open terminal
2. type "debcreator"

nd viola it starts............. :D

---

