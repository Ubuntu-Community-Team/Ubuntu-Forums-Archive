---
title: "Need help understanding debuild error"
date: 2013-05-11
forum: Packaging and Compiling Programs
---

### Post by DaneM on 2013-05-11
Hello.  I'm trying to package the latest version of Muse (midi sequencing software) via Launchpad.  I started with the version in the repository, downloaded the source, edited the debian directory's stuff, copied it to the directory of the new version, and then did the following:

```

dane@orchestrator ~/tmp/muse/muse-2.1.2 $ debuild -S -sa
parsechangelog/debian: warning:     debian/changelog(l5): badly formatted trailer line
LINE:  --Dane Mutters <dmutters@gmail.com>  Sat, 11 May 2013 2:12:00 -0800
parsechangelog/debian: warning:     debian/changelog(l7): found start of entry where expected more change data or trailer
LINE: muse (2.0~rc2-1) unstable; urgency=low
parsechangelog/debian: warning:     debian/changelog(l7): found eof where expected more change data or trailer
This package has a Debian revision number but there does not seem to be
an appropriate original tar file or .orig directory in the parent directory;
(expected one of muse_2.1.2.orig.tar.gz, muse_2.1.2.orig.tar.bz2,
muse_2.1.2.orig.tar.lzma,  muse_2.1.2.orig.tar.xz or muse-2.1.2.orig)
continue anyway? (y/n) y
 dpkg-buildpackage -rfakeroot -d -us -uc -S -sa
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
parsechangelog/debian: warning:     debian/changelog(l5): badly formatted trailer line
LINE:  --Dane Mutters <dmutters@gmail.com>  Sat, 11 May 2013 2:12:00 -0800
parsechangelog/debian: warning:     debian/changelog(l7): found start of entry where expected more change data or trailer
LINE: muse (2.0~rc2-1) unstable; urgency=low
parsechangelog/debian: warning:     debian/changelog(l7): found eof where expected more change data or trailer
dpkg-buildpackage: error: unable to determine source changed by
dpkg-buildpackage: source package muse
dpkg-buildpackage: source version 2.1.2-1
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -d -us -uc -S -sa failed

```

Debuild doesn't ask me for my gpg password, and (as you can see) won't create the .changes file I need to upload to Launchpad.  What do I do?  What does this error mean?

I can post any file in the debian directory, as needed, but since they're lengthy, I'll refrain unless asked.

I'll appreciate any help you can provide!

---

### Post by hakermania on 2013-05-11
the debian/changelog file seems to be corrupt, according to the error messages.

---

### Post by DaneM on 2013-05-11
Thanks for the (fast!) reply, hakermania.

I found the problem!  I had to change this:

```

 --Dane Mutters <dmutters@gmail.com>  Sat, 11 May 2013 2:12:00 -0800

```

to this:

```

 -- Dane Mutters <dmutters@gmail.com>  Sat, 11 May 2013 2:12:00 -0800

```

(Add a space after the "--")

Holy cow, that's sensitive!

Thanks for the tip, hakermania!  Definitely the fastest solution I've yet had on a forum!

---

### Post by hakermania on 2013-05-11
Glad to help, but, in order to avoid losing so much time on stuff like this learn to read the error messages, it didn't take me more than 5 seconds :)

---

### Post by DaneM on 2013-05-11
Where can I learn how to read the errors?  I searched the web for an hour (quite unfruitfully) before posting here.

---

### Post by hakermania on 2013-05-11
Just read the output of the command that you posted there, and try to find the important bits:
```

dane@orchestrator ~/tmp/muse/muse-2.1.2 $ debuild -S -sa
parsechangelog/debian: warning:     debian/changelog(l5): badly formatted trailer line
LINE:  --Dane Mutters <dmutters@gmail.com>  Sat, 11 May 2013 2:12:00 -0800
parsechangelog/debian: warning:     debian/changelog(l7): found start of entry where expected more change data or trailer
LINE: muse (2.0~rc2-1) unstable; urgency=low
parsechangelog/debian: warning:     debian/changelog(l7): found eof where expected more change data or trailer
This package has a Debian revision number but there does not seem to be
an appropriate original tar file or .orig directory in the parent directory;
(expected one of muse_2.1.2.orig.tar.gz, muse_2.1.2.orig.tar.bz2,
muse_2.1.2.orig.tar.lzma,  muse_2.1.2.orig.tar.xz or muse-2.1.2.orig)
continue anyway? (y/n) y
 dpkg-buildpackage -rfakeroot -d -us -uc -S -sa
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
**parsechangelog/debian: warning:     debian/changelog(l5): badly formatted trailer line**
**LINE:  --Dane Mutters <dmutters@gmail.com>  Sat, 11 May 2013 2:12:00 -0800**
**parsechangelog/debian: warning:     debian/changelog(l7): found start of entry where expected more change data or trailer**
**LINE: muse (2.0~rc2-1) unstable; urgency=low**
**parsechangelog/debian: warning:     debian/changelog(l7): found eof where expected more change data or trailer**
dpkg-buildpackage: error: unable to determine source changed by
dpkg-buildpackage: source package muse
dpkg-buildpackage: source version 2.1.2-1
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -d -us -uc -S -sa failed

```

---

### Post by DaneM on 2013-05-11
Thanks for trying to explain things.

I'd actually found the warning and error lines and searched for each one in turn.  Since I'm pretty new to debuild, expressions like, "found eof where expected more change data" are still pretty foreign to me.  I realized my mistake whilst in the process of pasting the changelog output to this forum (because it was different from the other entries)--but I still don't know how a lack of whitespace after two dashes equates to the above errors.

Is there a list of these errors and what they mean, anywhere?  That would be immensely helpful!

---

### Post by schragge on 2013-05-11
To save yourself from such mistakes, use [dch](http://manpages.ubuntu.com/manpages/raring/en/man1/dch.1.html) when adding to *debian/changelog*.

---

### Post by DaneM on 2013-05-14
Ooh, good tip!  I'll give that a shot!  Thanks, schragge.

---

