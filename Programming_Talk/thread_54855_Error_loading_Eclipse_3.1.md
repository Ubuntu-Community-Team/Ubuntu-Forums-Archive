---
title: "Error loading Eclipse 3.1"
date: 2005-08-06
forum: Programming Talk
---

### Post by npaladin2000 on 2005-08-06
I figured on dinking around with Eclipse 3.1, since theres both python and jython plugins available for it (well, not for v3.1 yet on jython) as well as some RAD interface designers.  

Now, when I shoehorned the 1.4 JRE onto this thing, it worked.  Problem is, Synaptic and APT wouldn't let me do anything else until I removed the "broken" package (it depended on a version of libc6 that's one VERY minor version higher than Hoary's. Ran fine anyway.)  

So I went and got the 1.5 JRE from backports which installed without any nasty little dependency probs, but now Eclipse won't start.  I get this:

> !SESSION 2005-08-06 10:54:37.106 -----------------------------------------------
eclipse.buildId=I20050627-1435
java.fullversion=GNU libgcj 4.0.0 20050301 (prerelease) (Debian 4.0-0pre6ubuntu7)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.runtime 2005-08-06 10:54:37.648
!MESSAGE Product org.eclipse.sdk.ide could not be found.


I get the DISTINCT sense that the Hoary GCJ isn't handling it properly.  java -version spits out this:

> root@ubuntu42:/usr/src/linux # java -version
java version "1.4.2"
gcj-4.0 (GCC) 4.0.0 20050301 (prerelease) (Debian 4.0-0pre6ubuntu7)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Shouldn't it be spitting out the SUN Java?  And where the heck do I change that in here?

*EDIT:* Never mind, I fixed both.  The first problem was solved by just deleting the configuration file under $HOME/.eclipsever

The second one, I figured out which symlink to replace.  And yeah, Hoary's GCJ can't handle Eclipse.  Dunno about breezy's

---

### Post by charlieg on 2005-08-07
Well, looks like you don't need any help! ;)

---

### Post by npaladin2000 on 2005-08-07
[QUOTE=charlieg]Well, looks like you don't need any help! ;)[/QUOTE]

Nope, but I did want to leave it up here in case enyone else has the same problem :)

---

### Post by jwenting on 2005-08-09
gcj is a disaster, the first thing you should do when installing Java is to get rid of it :)

My Linux machine isn't powerful enough to run Eclipse (Celeron 400 with 196MB RAM and an 800x600 LCD screen) but I do work in Java on it (mainly testing my stuff).

The Sun JDK installer works fine, and you get the latest version. Does take some more configuration of course but well worth it.

---

