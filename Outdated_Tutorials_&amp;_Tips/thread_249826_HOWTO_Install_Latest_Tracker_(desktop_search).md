---
title: "HOWTO: Install Latest Tracker (desktop search)"
date: 2006-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by sciyoshi on 2006-09-03
First of all, if you haven't heard of [Meta]Tracker, you should [check it out]("http://freedesktop.org/wiki/Software/Tracker"). It is a very light and fast replacement for Beagle, and will hopefully be included in Gnome 2.18. However, the version on that page is a little old, and although a new version will be out soon, this howto will help you stay up-to-date on the latest great features :-).

First of all, you will need some basic tools and packages to build Tracker:

```

sudo apt-get install build-essential zlib1g-dev libbz2-dev autotools-dev automake1.9 autoconf libextractor-dev libmysqlclient15-dev libssl-dev libpango1.0-dev libwrap0-dev cvs

```

Now that you have all the dependencies, go ahead and download the source into a new folder:

```

svn co http://svn.gnome.org/svn/tracker/trunk tracker
cd tracker

```

You can now read the README and other docs. Check out a tutorial on CVS to find out how to keep up to date with the latest updates.

Now we can actually build and install Tracker:

```

autoreconf -fvi
./configure
make
sudo make install

```

This will install all files into /usr/local. To uninstall it, run
```
sudo make uninstall
```.

You may need to add the new library location to the system. To do this, open (or create) the file '/etc/ld.so.conf' and (if it's not there already) add a line with the text '/usr/local/lib'. This will allow Ubuntu to find the new libraries. Then run ```
sudo ldconfig
``` to reload them.

To start Tracker, type ALT+F2 and type 'trackerd'. You can view its progress by issuing 'tail -f ~/.Tracker/tracker.log'. Congrats, Tracker is now indexing your home directory!

You can configure Tracker by editing the file '~/.Tracker/tracker.cfg'. Add folders you want to watch to 'WatchDirectoryRoots', and folders you want to ignore to 'NoWatchDirectory'.

To search for files from the command line, type 'tracker-search *search terms*'.

If you want Tracker to start each time you log in, do the following:
[LIST]
[*]Click "System" -> "Preferences" -> "Sessions"
[*]Click the startup programs tab
[*]Click the add button and type "trackerd" as the name of the program.
[/LIST]

Adding Nautilus support will come to a HowTo near you later :-).

Please post all questions and comments here!

---

### Post by choffee on 2006-09-10
The current cvs has a debian package directory so rather than doing a local install you can just do

```
dpkg-buildpackage -r fakeroot
```

and then install the resulting package.

---

### Post by saracen on 2006-09-11
Will someone just post a .deb for those of us who don't want to install all the development packages?

---

### Post by ammarr on 2006-09-11
What features does this offer over the previous/older versions of tracker?

---

### Post by ammarr on 2006-09-11
sorry, double post.

---

### Post by sciyoshi on 2006-09-11
The new version of Tracker provides a bunch of improvements and bug fixes, see the changelog:

[http://cvs.gnome.org/viewcvs/*checkout*/tracker/ChangeLog](http://cvs.gnome.org/viewcvs/*checkout*/tracker/ChangeLog)

Last release was in May, so everything since then is new. A new version will be out soon though, so those of you who want debs should probably wait until then (I think the deb build as of now is broken)

---

### Post by mirak63 on 2006-10-02
will it be included in edgy ?

---

### Post by sciyoshi on 2006-10-02
it probably won't be included, since we're already in UVF (upstream version freeze.) However, we're working hard, and the next version should be released next weekend, which means there'll be working debs and/or repositories.

---

### Post by apelete on 2006-11-18
Can someone post Tracker 0.5.1 package for Ubuntu Dapper ?
It will be really good to have this as a Beagle replacement.

---

### Post by gammyhand on 2006-11-18
I am trying to run the configuration and get this error. What do I need to install to fix this?

Also, I had to install libtools in synaptic. Might be an idea if this is mentioned in the FAQ?

configure.in:97: error: possibly undefined macro: AC_PROG_INTLTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1

---

### Post by markmark on 2006-11-19
0.5.1 Edgy debs are available here: [http://www.gnome.org/~jamiemcc/tracker/DEB/Edgy/](http://www.gnome.org/~jamiemcc/tracker/DEB/Edgy/)

---

### Post by MellonCollie on 2006-11-20
markmark - what exactly do I have to install? Every .deb from the link you posted?

---

### Post by markmark on 2006-11-20
That's what I did (they aren't my debs, I just found them). I'm guessing you don't need the libtrackerclient0-dev one unless you are going to do some coding, and the nautilus one replaces nautilus with one that uses tracker for search, so don't install that if you don't want to do that.

[edit] The link above has been updated with 0.5.2 debs

---

### Post by stoffe on 2006-11-21
Blog post about the release of Tracker 0.5.2, with instructions and more: [http://jamiemcc.livejournal.com/5630.html?view=56830](http://jamiemcc.livejournal.com/5630.html?view=56830)

Starting to look real sharp and hopefully able to be the default not only desktop search but also metadata index and more for both Gnome and Ubuntu soon.

---

### Post by kwisatz on 2006-11-21
I have a problem trying to compile latest cvs sources on my dapper:

root@velino:/usr/local/src/tracker# autoreconf -fvi
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is unchanged
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy --force
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy
automake: src/libstemmer/Makefile.am: not supported: source file `libstemmer/libstemmer.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `runtime/api.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `runtime/utilities.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_danish.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_dutch.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_english.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_finnish.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_french.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_german.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_italian.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_norwegian.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_porter.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_portuguese.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_russian.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_spanish.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_swedish.c' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `include/libstemmer.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `libstemmer/modules.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `runtime/api.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `runtime/header.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_danish.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_dutch.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_english.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_finnish.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_french.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_german.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_italian.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_norwegian.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_porter.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_portuguese.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_russian.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_spanish.h' is in subdirectory
automake: src/libstemmer/Makefile.am: not supported: source file `src_c/stem_UTF_8_swedish.h' is in subdirectory
src/trackerd/Makefile.am:140: variable `MYSQL_LIBS' not defined
src/trackerd/Makefile.am:140: variable `MYSQL_LIBS' not defined
src/trackerd/Makefile.am: trackerd_OBJECTS should not be defined
src/trackerd/Makefile.am:140: variable `MYSQL_LIBS' not defined
src/trackerd/Makefile.am:140: variable `MYSQL_LIBS' not defined
autoreconf: automake failed with exit status: 1

---

### Post by cloakable on 2006-11-22
Is there anything like this for KDE? Or will [Meta] Tracker work well there?

---

### Post by imagine on 2006-11-23
> **cloakable said:**
> Is there anything like this for KDE? Or will [Meta] Tracker work well there?

The Tracker daemon itself is desktop agnostic, ie it doesn't care which desktop environments you use. The only thing you need to look for is a KDE GUI for Tracker (written in QT). Maybe a KDE user knows one.
Of course you could also use the Gnome GUI, but I guess it doesn't look very nice in KDE and it will also drag in a bunch of Gnome/Gtk libs as dependencies, if you don't have Gnome installed.

---

### Post by cloakable on 2006-11-27
I've make a KDE frontend in Kommander, available [here.]("http://http://www.kde-apps.org/content/show.php?content=49208")

:)

---

### Post by igb on 2006-11-28
I have made some amd64 packages. If anyone wants them I can make them available for download.

Ian.

---

### Post by Corbelius on 2006-11-28
> **igb said:**
> I have made some amd64 packages. If anyone wants them I can make them available for download.

Ian.

I can see the packages?

---

### Post by igb on 2006-11-29
> **Corbelius said:**
> I can see the packages?

You can download them from my wiki at [http://www.ian-barton.com/wiki/Linux/Tracker]("http://www.ian-barton.com/wiki/Linux/Tracker")

---

### Post by accensi on 2006-11-29
> **igb said:**
> You can download them from my wiki at [http://www.ian-barton.com/wiki/Linux/Tracker]("http://www.ian-barton.com/wiki/Linux/Tracker")

libtrackerclient0 is missing in the tarball. Pls add it.

---

### Post by igb on 2006-11-29
> **accensi said:**
> libtrackerclient0 is missing in the tarball. Pls add it.

Apologies. It's there now.

Ian.

---

### Post by accensi on 2006-11-29
> **igb said:**
> Apologies. It's there now.

Ian.

Thanks!

---

### Post by bodhi.zazen on 2006-11-30
Nice How-to 



This thread has been added to the UDSF wiki.



[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Corbelius on 2006-11-30
> **igb said:**
> You can download them from my wiki at [http://www.ian-barton.com/wiki/Linux/Tracker]("http://www.ian-barton.com/wiki/Linux/Tracker")

Good apps, i have compiled it and add to my repository :)

---

### Post by shane2peru on 2006-12-13
I have Tracker all installed, but I need some documentation.  I can't seem to do a search on an expression like 'apples with grapes' or some expression with more than one word.  Any ideas?  I tried with " I tried with + and it still only looks for the first phrase?  Thanks.

Shane

---

### Post by shizeon on 2007-05-07
> **sciyoshi said:**
> 
Adding Nautilus support will come to a HowTo near you later :-).


Have you created a How-to for Nautilus support yet? 

Thanks!

---

### Post by jackn on 2007-08-07
Here's what I get when I try to configur the lates subversion:

```
checking for GMIME... configure: error: Package requirements ( gmime-2.0 >= 2.1.0 ) were not met:

No package 'gmime-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GMIME_CFLAGS
and GMIME_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I've looked for gmime on my install and found (snipped):
```

/usr/lib/libgmime-2.0.so.2.2.3

```

While the path /usr/lib/ seems quite ordinary, I've gone ahead and added it to PKG_CONFIG_PATH, and rerun ./config, but to no avail...


I've also studied the relevant paragraph in the pkg-config manpages, and do not understand it enough to act on it.
Here it is:
```
PKG_CHECK_MODULES(VARIABLE-PREFIX,MODULES[,ACTION-IF-FOUND,[ACTION-IF-
       NOT-FOUND]])

              The macro PKG_CHECK_MODULES can be used in configure.ac to check
              whether modules exist. A typical usage would be:
               PKG_CHECK_MODULES([MYSTUFF], [gtk+-2.0 >= 1.3.5 libxml = 1.8.4])

              This  would  result in MYSTUFF_LIBS and MYSTUFF_CFLAGS substitu&#8208;
              tion variables, set to the libs and cflags for the given  module
              list.   If  a  module  is  missing  or has the wrong version, by
              default configure will abort with  a  message.  To  replace  the
              default  action,  specify an ACTION-IF-NOT-FOUND. PKG_CHECK_MOD&#8208;
              ULES will not print any error messages if you specify  your  own
              ACTION-IF-NOT-FOUND.    However,   it   will  set  the  variable
              MYSTUFF_PKG_ERRORS, which you  can  use  to  display  what  went
              wrong.

              Note   that  if  there  is  a  possibility  the  first  call  to
              PKG_CHECK_MODULES might  not  happen,  you  should  be  sure  to
              include  an explicit call to PKG_PROG_PKG_CONFIG in your config&#8208;
              ure.ac
```


Help?

jackn

---

### Post by stoffe on 2007-08-07
You usually need the -dev versions for compiling, try to find a package looking like libgmime-dev and install that.

---

### Post by jackn on 2007-08-07
OK, so went ahead and installed libgmime-2.0-2-dev.

Upon ./config, I got a new error message, which suggests that the gmime issue was solved. In response to the new error message, I installed -dev packages pertaining to dbus.

At this point, ./config gives:
```
./configure: line 22621: syntax error near unexpected token `0.35.0'
./configure: line 22621: `IT_PROG_INTLTOOL(0.35.0)'
```

This I have no idea what to do about. I'm stumped. At this point, I therefore still have the aptitude version, and not the latest svn. 
I would still like to install the latest, but don't know how to.

Thank you, stoffe, for this advice which let me advance some, and will surely come in handy more generally in the future...

---

### Post by bgturk on 2007-09-28
I installed the dependencies, however I am lacking the newest version of SQLite:

=========================================

Requested 'sqlite3 >= 3.4' but version of SQLite is 3.3

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

=========================================

Where can I get that from?

---

