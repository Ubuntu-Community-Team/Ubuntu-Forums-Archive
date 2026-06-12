---
title: "Need help with package that just copies files"
date: 2009-12-14
forum: Packaging and Compiling Programs
---

### Post by MattJones on 2009-12-14
Howdy all,

I've been playing with ubuntu and fedora packaging for a bit, and have
basic packaging of c and python apps down. The problem is when I need a
package that just copies some files, I can't get it to work.

What I want to do is just copy the source tree to /usr/share/blah and
symlink a script to /usr/bin/blah. Like this:

cp -R . /usr/share/blah/
ln -s /usr/share/blah/bin/blah /usr/bin/blah

I have tried putting that in the rules file under build and install, a
separate make file, and a post script. But they all fail, run at package
time,or the source tree is not found.

Any help would be appreciated, as I have been head-butting this for a
few days.

---

### Post by SevenMachines on 2009-12-15
especially if your making simple packages but just in general, if you can use debhelper then it will make your life easier. as a simple example, say you had a binary in your source directory named 'kaboom' and you were making a package called test-kaboom

only two lines in our rules file needed for this!
debian/rules:
```
#!/usr/bin/make -f
include /usr/share/cdbs/1/rules/debhelper.mk
```then create a .install file to install the binary
debian/test-kaboom.install:
```
kaboom    usr/bin/
```and a .links file create any links you want
debian/test-kaboom.links:
```
usr/bin/kaboom    usr/bin/alinktokaboom
```note you will want cdbs and debhelper in your build-depends.

for a less simple example you might include cdbs makefile.mk and so on to do some actual compiilation

---

### Post by MattJones on 2009-12-15
Thanks. That worked.

I got a link to a tutorial a few hours ago that showed the same thing, except the links part. The links file is much better than postinst and prerm scripts: [https://wiki.ubuntu.com/MOTU/School/PackagingWithoutCompiling](https://wiki.ubuntu.com/MOTU/School/PackagingWithoutCompiling)

---

