---
title: "Ubuntu package doesn't appear in dash"
date: 2015-08-06
forum: Packaging and Compiling Programs
---

### Post by jonathon-love on 2015-08-06
Hi,

I have created some packages, and placed them in my PPA

[https://launchpad.net/~jonathon-love/+archive/ubuntu/jasp](https://launchpad.net/~jonathon-love/+archive/ubuntu/jasp)

They install correctly, however, I'm having difficulty getting the program to appear in the dash.

My menu file (placed inside the debian directory)

```
?package(jasp): needs="X11" section="Applications/Science/Data Analysis" title="JASP" icon="/usr/share/pixmaps/jasp.xpm" command="/usr/lib/JASP/JASP"

```

and if i scroll to the bottom of the build log, i see that it is placed into the .deb file correctly:

[https://launchpadlibrarian.net/213713152/buildlog_ubuntu-vivid-amd64.jasp_0.7.1.11-9_BUILDING.txt.gz](https://launchpadlibrarian.net/213713152/buildlog_ubuntu-vivid-amd64.jasp_0.7.1.11-9_BUILDING.txt.gz)

However, when I install this package, and type 'JASP' into the dash, i don't get the option to execute this package.

Any ideas what I might be doing wrong?

I wondered if I needed to add a call to the debian 'update-menus' script, but it doesn't seem to be installed in ubuntu.

with thanks

---

### Post by jonathon-love on 2015-08-08
ah, ok, i needed to add a desktop entry file:

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

jonathon

---

