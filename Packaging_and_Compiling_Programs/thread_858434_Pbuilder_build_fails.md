---
title: "Pbuilder build fails"
date: 2008-07-13
forum: Packaging and Compiling Programs
---

### Post by Balachmar on 2008-07-13
Hi, I want to create a package for openFTD.
[http://openftd.signalrunner.com/openftd-1.1.1.tar.bz2](http://openftd.signalrunner.com/openftd-1.1.1.tar.bz2)
And I am following the video guide.
but doing sudo pbuilder build opftd.dsc fails

Here is the total output:
[http://pastebin.com/m2ea5c57](http://pastebin.com/m2ea5c57)

Help is greatly appreciated.

These are the dependancies:
libz (>= 1.1.4), glib (>= 2.6.0), gtk (>= 2.4.0), libxml2 (>= 2.2.5), libxslt (>= 1.0.5), pcre (>= 5.0), gtkhtml (>= 3.4.0), LibCURL (>= 7.10.6), DBUS (>= 0.60), libnotify (>= 0.4.1), libgnome (>= 2.0), xulrunner-1.9

---

### Post by bobbocanfly on 2008-07-19
That is a problem in pbuilder, it doesnt download virtual packages (dont know why) so your Build-Depends cant be satisfied.

You should try building this in your Launchpad PPA as it is a 'proper' buildd so grabs all the dependencies you tell it to.

---

