---
title: "required packages are named differently"
date: 2009-03-23
forum: Packaging and Compiling Programs
---

### Post by speedkreature on 2009-03-23
Trying to compile an app from source in hopes of packaging it and getting the current version updated in the repos.  The problem is the packages it's looking for are using a slightly different naming convention than they do in Ubuntu.

The program in question is Almanah and the creator has made some significant fixes and feature adds in the 0.5.0 and 0.6.0 releases.
I'd like to update this package to a more recent version (0.6.0), but when attempting to run ./configure, I get:

...
checking for STANDARD... configure: error: Package requirements (glib-2.0 gtk+-2.0 >= 2.14 gmodule-2.0 gio-2.0 sqlite3 cairo gconf-2.0 atk libecal-1.2 libedataserver-1.2 libedataserverui-1.2) were not met:

No package 'sqlite3' found
No package 'libecal-1.2' found
No package 'libedataserver-1.2' found
No package 'libedataserverui-1.2' found


Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.


Alternatively, you may set the environment variables STANDARD_CFLAGS
and STANDARD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
...

This, I would presume, is not explicitly a bug in the source...it seems to be a problem with naming conventions--though sqlite3 is a valid package and is installed on this system.  The other 3 packages are named slightly differently (I'm ignoring the mess just above the "No package" lines), removing the dash between the package name and the version in Ubuntu.

I guess the real question is: who/what is the right channel to resolve this or what can I do so it will compile so I can create a package for Ubuntu.

Can anyone point me in the right direction?  I know I'm not the only one to run accross this error but I couldn't find anything useful when I searched.

---

### Post by lloyd_b on 2009-03-23
Library packages are typically split into two pieces - the main package, and a dev package (same name, just with "-dev" on the end).  The dev package contains stuff that's not needed to actually use the library, but which *are* required to compile code against the library.

Try installing the corresponding "-dev" packages for all of those errors (including the ones on that "Package requirements (glib-2.0 gtk+-2.0 ..." line), and then try it again.

Lloyd B.

---

