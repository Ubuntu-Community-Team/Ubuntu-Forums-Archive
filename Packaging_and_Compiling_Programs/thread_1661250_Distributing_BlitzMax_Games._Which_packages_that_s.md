---
title: "Distributing BlitzMax Games. Which packages that should be bundled for convenience?"
date: 2011-01-06
forum: Packaging and Compiling Programs
---

### Post by Repgahroll on 2011-01-06
Hello there.

I'm wondering how I should ship BlitzMax applications. Does they only depends on libstdc++5?

Should I only bundle libstdc++5 and libgcc1?

Is there any good universal installer that runs on may distros? (no python / java)

Also, can I link the dependencies statically?

For Windows and Mac i'm gonna release single .exe and .dmg files, but for Linux I can't find a way to release something less massive than 5 distinct packages for the main application along with dozens of dependencies to allow offline installation.

Thank you very much.

---

### Post by MadCow108 on 2011-01-06
linux distros are not windows, you don't bundle stuff with your software and you don't statically link stuff in when not absolutely neccesary either.

The universal installer for debian based distros is dpkg, with takes .deb packages as input, read the stickies here for an introduction.

for offline installation see e.g.:
[http://manpages.ubuntu.com/manpages/maverick/man8/apt-offline.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/apt-offline.8.html)

libstdc++5 is very very old. Does the program not work with libstdc++6?
if not the first priority should be fixing it ...

but you are lucky it was readded to the repositories for debian squeeze (I wonder why ...) and is thus in maverick universe and in lucid-- backports.

libgcc1 is ok, and it is in the repositories so no problem there.

---

### Post by Repgahroll on 2011-01-07
Thank you guy.

Yep... you're right... in fact the latest version of BlitzMax work with libstdc++6. The 5 version actually was needed a long time ago when I bought it... I just forgot about the updates :).

However... on Windows Systems, the range of potential users will be in practice 100%, because it will support from Windows 2000 to Windows 7 (incl 64 bit) with a single installation executable. It's just amazing.

On Macs also, the range will be very large, because it will be an universal application, so will be installable even on Macs back from 2002. A single installation file also.

On Linux it's being a pain to decide though. If I did not link the libraries statically, I believe users will need a system newer than 2006-07 to run it, because it was when most distros adopted libstdc++6, also, I will need to bundle a number of dependencies in a diversity of packs and the application itself will need to be packed for various distros (at least the 4 main package managers and tar).

So the Windows and Mac versions will fit a CD and the Linux Version will need 2 DVDs... It doesn't make a bit of sense to me.

Isn't it possible to just link everything statically and require only kernel2.6+, Xserver, video and audio modules??

My gosh... i'm beginning to understand why almost no software company at all supports Linux...

---

### Post by MadCow108 on 2011-01-07
why do you want to support distributions which are older than 4 years?
The only systems which should be that old are server systems or enterprise installations, everything else does not have security support anymore.
People using something these will either be morons or experts. The former should be negilible in numbers and the latter will know how to handle package dependencies correctly themselves.

just distribute the package with the dependencies registered correctly and let the distributions package manager handle the rest.
For the people without internet (who would seldom use package based linux distributions as internet is so important to them) you can create bundles based on the default installation which probably has 99% of the required dependencies pre-installed.
As even the minimal install has the most important stuff pre-installed (kernel, libstdc++, xserver, audio, ...) so the bundle will be very small.

what exactly are your depencies which would make the installation 2DVD's large? (a fully working whole ubuntu system fits on a single CD!)
here you can check how widespread the dependencies are:
[http://dev.linuxfoundation.org/navigator/browse/app_distr.php](http://dev.linuxfoundation.org/navigator/browse/app_distr.php)

---

