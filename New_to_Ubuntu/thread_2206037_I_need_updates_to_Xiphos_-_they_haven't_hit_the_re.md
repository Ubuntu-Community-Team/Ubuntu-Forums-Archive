---
title: "I need updates to Xiphos - they haven't hit the repos"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by newb85 on 2014-02-17
I'm running Ubuntu Saucy, and using Xiphos (installed from the repos).  I'm experiencing the module manager column crush bug, which is crippling because it prevents the installation of modules.  According to the Xiphos release notes page [http://xiphos.org/development/release-notes/](http://xiphos.org/development/release-notes/), the latest release (a month old) addresses this problem (which comes from the gtk-3 issues).  However, this release hasn't hit the repos, and I can't seem to find a source for it.

Any help would be appreciated...

---

### Post by howefield on 2014-02-17
You could ask the question of the package maintainers via launchpad, or download the source from the xiphos website and compile (with all the usual caveats of installing software outside of the main repositories).

---

### Post by westie457 on 2014-02-17
Have you looked at the downloads page of the xiphos site?

They have links to 'Sourceforge'. This one works.

[http://sourceforge.net/projects/gnomesword/files/Xiphos/](http://sourceforge.net/projects/gnomesword/files/Xiphos/)

---

### Post by newb85 on 2014-02-17
Of course, I should have thought of compiling from source.  I guess I'm just so used to searching for pre-compiled PPAs.

I'm curious, if I compile from source, will the package update automatically in the future when further updates become available through the repos?  (Realistically, this probably won't matter in this case, since I'm planning to do a fresh install when Trusty comes out, anyways.  I doubt another update will hit the repos before then.)

---

### Post by newb85 on 2014-02-17
Hmmm...  so I thought compiling would be simple.  I attempted following the instructions in the INSTALL file, and hit a snag.  I probably look like an idiot, but is there some other dependency I need to install?

```
$ sudo ./waf configure build installLinux detected 
Check for program g++ or c++             : /usr/bin/g++ 
Check for program cpp                    : /usr/bin/cpp 
Check for program ar                     : /usr/bin/ar 
Check for program ranlib                 : /usr/bin/ranlib 
Check for program gcc or cc              : /usr/bin/gcc 
Check for program msgfmt                 : /usr/bin/msgfmt 
Check for program intltool-merge         : /usr/bin/intltool-merge 
Checking for header locale.h             : ok 
Check for program glib-genmarshal        : not found 
Check for program glib-mkenums           : not found 
Check for program dbus-binding-tool      : not found 
Check for program docbook2man            : not found 
Check for program xml2po                 : not found 
Check for program xsltproc               : not found 
Auto detecting gtk 3                     : fail 
Auto detecting gtk 2                     : Package libgtkhtml-3.14 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgtkhtml-3.14.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgtkhtml-3.14' found 
/home/aaron/temp/xiphos-3.1.6/wscript:233: error: the configuration failed (see '/home/aaron/temp/xiphos-3.1.6/build/config.log')

```

for the record, libgtkhtml-3.14 isn't installed on my system, but libgtkhtml-4.0-0 is.

---

### Post by sandyd on 2014-02-17
> **newb85 said:**
> I'm running Ubuntu Saucy, and using Xiphos (installed from the repos).  I'm experiencing the module manager column crush bug, which is crippling because it prevents the installation of modules.  According to the Xiphos release notes page [http://xiphos.org/development/release-notes/](http://xiphos.org/development/release-notes/), the latest release (a month old) addresses this problem (which comes from the gtk-3 issues).  However, this release hasn't hit the repos, and I can't seem to find a source for it.

Any help would be appreciated...

whoever is building these packages
they havent updated it in a long time - the build dependencies dont even work anymore.

I can build one for lucid, but I have no idea whether it will work or not.

---

### Post by newb85 on 2014-02-17
> **sandyd said:**
> whoever is building these packages
they havent updated it in a long time - the build dependencies dont even work anymore.

I can build one for lucid, but I have no idea whether it will work or not.

I'm not sure what you mean.  The release I'm trying to compile was just issued 35 days ago.  Perhaps the dependency issues stem from the fact that they've reverted this release to gtk2 as a temporary fix to problems caused by switching to gtk3.  (As it turns out, those are the very problems driving my desire to upgrade.)  [http://xiphos.org/development/release-notes/](http://xiphos.org/development/release-notes/), just in case the link in my initial post wasn't tempting enough...

---

### Post by sandyd on 2014-02-18
> **newb85 said:**
> I'm not sure what you mean.  The release I'm trying to compile was just issued 35 days ago.  Perhaps the dependency issues stem from the fact that they've reverted this release to gtk2 as a temporary fix to problems caused by switching to gtk3.  (As it turns out, those are the very problems driving my desire to upgrade.)  [http://xiphos.org/development/release-notes/](http://xiphos.org/development/release-notes/), just in case the link in my initial post wasn't tempting enough...

no - the build dependencies in the original package (which would be used if you were doing a backport + update) are out of date
Was going to go rebuild the debian package to provide an updated version and discovered  that the dependencies in the original xiphos debian source package are outdated - some of those packages havent existed since lucid D:

As a result, it is unlikely that someone will update it in the repos - until someone decides to fix the dependencies in the debian source package

---

### Post by newb85 on 2014-02-18
I would love to contact the developers and request that they update their dependencies.   However, I don't even know how to determine what dependencies are out-of-date.

---

### Post by sandyd on 2014-02-18
> **newb85 said:**
> I would Live to contact the developers and request that they update their dependencies.   However, I don't even know how to determine what dependencies are out-of-date.

I can give you a list when I get back home

---

### Post by newb85 on 2014-02-18
That would be great.

It does make me wonder, though, how earlier versions made it into the repos for Saucy if these dependency issues existed...

---

### Post by sandyd on 2014-02-18
> **newb85 said:**
> That would be great.

It does make me wonder, though, how earlier versions made it into the repos for Saucy if these dependency issues existed...

you can copy packages :)

---

### Post by sandyd on 2014-02-18
Found the right dependencies somewhere...
and failing to build... [https://launchpadlibrarian.net/166704503/buildlog_ubuntu-trusty-amd64.xiphos_3.1.6-3~trusty1_FAILEDTOBUILD.txt.gz](https://launchpadlibrarian.net/166704503/buildlog_ubuntu-trusty-amd64.xiphos_3.1.6-3~trusty1_FAILEDTOBUILD.txt.gz)

---

