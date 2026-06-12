---
title: "Make source package for single script"
date: 2012-04-19
forum: Packaging and Compiling Programs
---

### Post by maximus57 on 2012-04-19
I have created a single bash script that I would like to be able to turn into a Debian source package so that it can be uploaded to a PPA. I have searched and read, over and over and over again, and I am lost! Most everything I find talks about how to use source code to create a deb file, but very little on how to create source code, at least that is anywhere near easy to understand.

What I can do right now is use dh_make, edit the control, copyright, and changelog files and use dpkg to build a deb package. So I can make a deb file that only has a few warnings with a lintian check. But what the heck do I upload for source code? HELP!

---

### Post by raja.genupula on 2012-04-19
[https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading)

---

### Post by bregma on 2012-04-19
> **maximus57 said:**
> 
What I can do right now is use dh_make, edit the control, copyright, and changelog files and use dpkg to build a deb package. So I can make a deb file that only has a few warnings with a lintian check. But what the heck do I upload for source code? HELP!

If you can build a binary deb file from your packaging branch you can build a source deb.

If you normally use [FONT="Courier New"]dpkg-buildpackage[/FONT] as your package builder, you can just use [FONT="Courier New"]dpkg-buildpackage -S[/FONT] to build the source package.  The source package will have a *.changes* file, among other files (probably at least a *.tar.gz* file and a *.dsc* file) that lists the rest of the files in the source package, and it's what you use to *dput* the source package to your PPA.

---

### Post by maximus57 on 2012-04-20
> **raja.genupula said:**
> [https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading)
Been there already, followed the how to links and it does a wonderful job of telling me how to download the HELLO source and repackage it. Not much help at how to do my own from scratch as a beginner.


> **bregma said:**
> If you can build a binary deb file from your packaging branch you can build a source deb.

If you normally use [FONT=Courier New]dpkg-buildpackage[/FONT] as your package builder, you can just use [FONT=Courier New]dpkg-buildpackage -S[/FONT] to build the source package.  The source package will have a *.changes* file, among other files (probably at least a *.tar.gz* file and a *.dsc* file) that lists the rest of the files in the source package, and it's what you use to *dput* the source package to your PPA.
That might help me. I figured as much, but just didn't know how. I have managed to put together enough information from a few odd places to even be able to get to the point I am at. I really don't know what I am doing when it comes to this part of it, but I am learning. Will try that soon, lost power earlier tonight so didn't have the chance.

---

### Post by maximus57 on 2012-04-22
Every step forward seems to bring more questions. 

First, you mean that the .changes file and the other files that are listed in the .changes file (currently .dsc, .orig.tar.gz, and .debian.tar.gz files) are what I would upload?

Second, you mention a packaging branch. I am a little lost on the whole branch thing. That and bazzar does not seem to work right for me for what I tried. Do I have to use bazzar and make a branch? I just want to upload my package, and maybe in the future upload new versions. Nothing fancy.

Third, I get some warnings with lintian that I would like to work on:
Now running lintian...
Use of uninitialized value $prefix in string ne at /usr/share/lintian/collection/index line 150.
W: ddrutility source: format-3.0-but-debian-changes-patch
W: ddrutility: new-package-should-close-itp-bug
W: ddrutility: extended-description-line-too-long
W: ddrutility: binary-without-manpage usr/bin/ddrutility

From the bottom up:
The manpage I understand, I may add one before uploading.
The description I understand, but if I break it up like I am supposed to, it runs some words together (when looked at though ubuntu software center).
New package should close bug... It is brand new, I am not fixing any bugs. Kind of annoying.
The format/patch one I am totally lost on.
Also don't know why lintian seems to be giving an error of its own.

---

### Post by bregma on 2012-04-22
> **maximus57 said:**
> 
First, you mean that the .changes file and the other files that are listed in the .changes file (currently .dsc, .orig.tar.gz, and .debian.tar.gz files) are what I would upload?

Yes, exactly that.  When you upload to your PPA, you use a command like **dput ppa:maximus/ddrutility ddrutility_0.1-0ubuntu1~ppa1.changes** and the .dsc, .orig.tar.gz, and .debian.tar.gz files (which constitute the Debian source package) will be copied to the PPA.
> Second, you mention a packaging branch. I am a little lost on the whole branch thing. That and bazzar does not seem to work right for me for what I tried. Do I have to use bazzar and make a branch? I just want to upload my package, and maybe in the future upload new versions. Nothing fancy.
I meant 'packaging branch' in the generic sense (and out of habit).  You are not required to use bzr or any other version control system, although I would strongly recommend it.

The traditional workflow for software packages involves an *upstream* which releases a *source tarball* and a packager who takes the pristine upstream tarball and adds packaging, such as a [FONT="Courier New"]debian/[/FONT] directory or a [FONT="Courier New"].spec[/FONT] file, and ends up with the actual packages (.deb or .rpm files).  The packaging is independent of the actual upstream project.  This may not be appropriate for what you're trying to do, I'm just outlining the most frequent workflow.  As long as you can get the Debian source package, you can upload it to a PPA.
> Third, I get some warnings with lintian that I would like to work on:
Now running lintian...
Use of uninitialized value $prefix in string ne at /usr/share/lintian/collection/index line 150.
W: ddrutility source: format-3.0-but-debian-changes-patch
W: ddrutility: new-package-should-close-itp-bug
W: ddrutility: extended-description-line-too-long
W: ddrutility: binary-without-manpage usr/bin/ddrutility

From the bottom up:
The manpage I understand, I may add one before uploading.
The description I understand, but if I break it up like I am supposed to, it runs some words together (when looked at though ubuntu software center).
New package should close bug... It is brand new, I am not fixing any bugs. Kind of annoying.
The format/patch one I am totally lost on.
Also don't know why lintian seems to be giving an error of its own.
The packaging workflow in Debian normally requires an ITP (intent to package) bug be files against the WNPP pseudo-package, and that bug be closed with the first upload of the package to Debian.  You can safely ignore that message from lintian (unless you're planning to get your package into Debian).

You can try running wrap-and-sort from the devscripts package to see if it eliminates the the line length warning.  Most packages seem to be able to conform to the 80-character line length length limit without problems.

The debian-changes-patch warning is probably because you do not have an upstream tarball (the [FONT="Courier New"].orig.tar.gz[/FONT] file) and you're using source-format 3.0, which expects one.  You could try changing to format 1.0, or just ignore the warning for now.

The uninitialized $prefix message may be due to an empty .orig.tar.gz file.  Just a guess.

---

### Post by maximus57 on 2012-04-24
I would like to say thanks for all the good answers and info. I have managed to upload a package to a PPA. It was a learning experience for sure, if not a somewhat painful one. I am just now hoping that it was in time (am hoping to get it included on a live cd which will come out when 12.04 comes out in a couple days).

---

