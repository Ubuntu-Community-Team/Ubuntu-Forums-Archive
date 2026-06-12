---
title: "how to install &quot;new&quot; gnutella version?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Amanda HazLaPaz on 2008-07-06
I received a reminder from the current version of GTK-gnutella-0.96.4, saying there's a [new version]("http://gtk-gnutella.sourceforge.net/en/?page=news"). I already sudo apt-get installed with no luck, there's nothing in synaptic, all extra repositories are enabled, I don't know where else to look.  

I've done a search for "how to install" and read a number of threads [(like this)]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually"), but I am stuck and frustrated. I successfully got as far as enabling build-essential in synaptic, but then got stuck before the command ./compile. Frankly, the instructions were confusing for this stone cold newbie. 

I followed the [sourceforge]("http://sourceforge.net/project/downloading.php?groupname=gtk-gnutella&filename=gtk-gnutella-0.96.5.tar.bz2&use_mirror=voxel") link and I have a cardboard box looking thing on my desktop. I believe I unzipped it because there's a corresponding file folder.

I'm not afraid of using the terminal, but I do need some hand holding as far as very specific instructions.

With all that preamble, the question is **How do I  install the new version of Gnutella? **

Thank you so much for your consideration.

---

### Post by billgoldberg on 2008-07-06
After you downloaded the .tar.gz file from sourceforge to your Desktop, do these commands.

```
sudo apt-get install build-essential
```

Then you can follow the installation notes in the README file after you extracted the .tar.bz.

If you have any questions, feel free to ask.

---

### Post by Amanda HazLaPaz on 2008-07-06
In the process of following instructions now:

[I]Supplementary Compile Instructions for Debian-based Systems
        ===========================================================

Unfortunately, many people have trouble compiling gtk-gnutella on Linux
distributions albeit it should be very simple. The following applies to
Debian-based system that is also Ubuntu.


1. Dependencies:
================

You'll have to install the following packages:

  apt-get install fakeroot        # required for compiling using the .deb
  apt-get install debhelper       # required for compiling using the .deb
  apt-get install gcc             # GCC; any version is fine
  apt-get install make            # the make tool; any version is fine
  apt-get install zlib1g-dev      # zlib
  apt-get install libxml2-dev     # libxml 2.x
  apt-get install libgnutls-dev   # GNU TLS

For the Gtk+ 2.x front-end you'll need these:

  apt-get install libglib2.0-dev  # GLib 2.x
  apt-get install libgtk2.0-dev   # Gtk+ 2.x

If you want to use the Gtk+ 1.2 front-end instead:

  apt-get install libglib1.2-dev  # GLib 1.2
  apt-get install libgtk1.2-dev   # Gtk+ 1.2

The following package is optional:

  apt-get install libdbus-1-dev   # D-Bus


2. Build:
=========

Run from the top of the source tree:

  fakeroot debian/rules binary

and it will build the .deb package for you in the parent directory.


3. Finish:
==========

You can then run gtk-gnutella without installing:

  src/gtk-gnutella

To install gtk-gnutella just run (version and architecture will vary):

  cd ..
  su
  dpkg --install gtk-gnutella*.deb

For further compile options and instructions, see the README file and
edit the debian/rules file to change the line calling "./build.sh" to suit
your taste. Run "./build.sh --help" to list available options.

$Id: README.Debian 14152 2007-07-22 13:36:14Z cbiere $[/I]

---

### Post by Amanda HazLaPaz on 2008-07-06
Okay, Bill, here's a question: what do the following mean to me? 

[I]For the Gtk+ 2.x front-end you'll need these:
If you want to use the Gtk+ 1.2 front-end instead:[/I]

I know "bigger =|= better". Will there be any difference in function or form?

Thanks for your help. Love the userpic, too. I am also a big fan!

---

### Post by Amanda HazLaPaz on 2008-07-06
I'm also stuck as far as the instructions starting at #2:

*Run from the top of the source tree:*

Do what now?

---

### Post by cariboo on 2008-07-06
Run from the top of the source tree = the directory the the gtk-gnutella source files are in eg:

```
~/Destop/gtk-gnutella
```

or where ever you extracted the files to.

Jim

---

