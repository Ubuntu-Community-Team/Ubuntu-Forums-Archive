---
title: "Teng package"
date: 2008-10-28
forum: Packaging and Compiling Programs
---

### Post by JaspSoft on 2008-10-28
Don't know if this is the right place to post but I've made a debian source package for Teng ([http://teng.sourceforge.net/](http://teng.sourceforge.net/))

[http://we8jgfj39ghksm.googlepages.com/tengforubuntu](http://we8jgfj39ghksm.googlepages.com/tengforubuntu)

Theres some binary packages from i386 and amd64 on that page also.

---

### Post by nhandler on 2008-10-28
Thank you for taking the time to package teng. I would suggest that you read [this]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages") and [this]("https://wiki.ubuntu.com/MOTU/Packages/REVU"). They should help explain the process that you need to follow in order to get your package uploaded to the repositories. Basically, the next thing you will want to do is upload it to [REVU]("http://revu.ubuntuwire.com/"). That will allow it to be reviewed by other MOTUs.

I quickly looked over the source package. Here are some suggestions that I have:

debian/changelog:
  1) The version should be 1.0.4-0ubuntu1. The Debian revision number is 0 because the package is not present in the Debian repositories.
  2) Instead of 'unstable', it should say 'jaunty'. Intrepid is about to be released, so jaunty is about to become the development version of Ubuntu.
  3) The changelog entry should only say "Initial release" or "Initial Ubuntu release". It should also say "(LP: #NNNNNN)" where NNNNNN is the number of a needs-packaging bug report on Launchpad for teng.

debian/control:
  4) Are you sure the Priority should be ’extra’? Extra is for packages that may conflict with packages in one of the other categories. It is also used for specialized packages that would only be useful to people who already know the purpose of the package.
  5) The Maintainer should be 'Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>'
  6) You should set yourself as the 'XSBC-Original-Maintainer'. You can read more about this [here]("https://wiki.ubuntu.com/DebianMaintainerField").
  7) You should bump the Standards-Version to 3.8.0
  8) The Descriptions could contain a little more information about the application

debian/copyright:
  9) It looks like you did not modify the template copyright file. Your package can not be uploaded to the repositories without a complete and accurate debian/copyright file.

debian/rules:
  10) You should remove all of the comments that were added by dh-make.

The package is also not lintian clean. Here are some of the warnings that lintian produced (I am not including warnings that will be fixed by following the above suggestions):

W: teng source: maintainer-script-lacks-debhelper-token debian/libteng.postinst
N:
N:   This package is built using debhelper commands that may modify
N:   maintainer scripts, but the maintainer scripts do not contain the
N:   "#DEBHELPER#" token debhelper uses to modify them.
N:   
N:   Adding the token to the scripts is recommended.

W: libteng1-dev: zero-byte-file-in-doc-directory usr/share/doc/libteng1-dev/chan
gelog.gz
N:
N:   Package contains a file which is empty.

W: libteng1: zero-byte-file-in-doc-directory usr/share/doc/libteng1/changelog.gz
E: libteng1: no-shlibs-control-file usr/lib/libteng.so.1.0.0
N:
N:   Although the package includes a shared library, the package does not
N:   have a shlibs control file. If this is intentional, please override
N:   this error.
N:   
N:   Refer to Policy Manual, section 8.6 for details.

E: libteng1: postinst-must-call-ldconfig usr/lib/libteng.so.1.0.0
N:
N:   The package installs shared libraries in a directory controlled by the
N:   dynamic library loader. Therefore, the package must call `ldconfig' in
N:   its postinst script.
N:   
N:   Refer to Policy Manual, section 8.1.1 for details.

---

### Post by JaspSoft on 2008-10-29
Thanks for the very informative response.

I'm totally new to packaging, but if you think it is worth me tidying it up and submitting then I'll have a go when I have some time.

Cheers.

---

### Post by JaspSoft on 2008-10-29
I think I've fixed most of the issues you highlight, but I cannot fix some, it seems, because the original tar ball contains a debian/ directory with files that are throwing errors up in lintian...

I understand (from here: [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-mistakes.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-mistakes.html)) that changes to the original tarball should only be done by the original authors.

So I've fired off an email to ask if they can drop the debian/

---

### Post by nhandler on 2008-10-29
> **JaspSoft said:**
> I think I've fixed most of the issues you highlight, but I cannot fix some, it seems, because the original tar ball contains a debian/ directory with files that are throwing errors up in lintian...

I understand (from here: [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-mistakes.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-mistakes.html)) that changes to the original tarball should only be done by the original authors.

So I've fired off an email to ask if they can drop the debian/

You did the correct thing. Here is an excerpt from the [URL="http://people.debian.org/~mpalmer/debian-mentors_FAQ.html"]debian-mentors FAQ
[/URL]
> What's wrong with upstream shipping a debian/ directory?

There are cases where upstream ships a tarball which already contains a debian directory. This is undesirable, even if you're upstream yourself or can commit there. Keep the released tarballs (used as .orig.tar.gz) and the debian directory separated.

The problem is that at some point, upstream's debian directory will deviate from the one in the Debian package -- because the maintainer changes, the directory was already outdated, or someone does an NMU or a security upload. Because it was The .diff.gz will now be a diff between the two debian dirs, which is very confusing.

The Debian package format is designed to keep upstream and Debian-specific neatly separated into orig.tar.gz and .diff.gz. Putting the debian dir in the .orig.tar.gz confuses this.

If upstream has a debian directory in their releases, you should contact them and ask if they can remove the debian/ directory from their tarball releases. There's no need to remove the debian directory from their revision control system (although if it's out of date they may decide to do so anyway), but at the very least the directory shouldn't appear in releases. If you are upstream yourself, well, you can ask yourself to do it.

Also, you are allowed to modify the contents of the package outside of the debian directory. However, when you do this, you are meant to use a [patch system]("https://wiki.ubuntu.com/PackagingGuide/PatchSystems").

---

### Post by JaspSoft on 2008-10-30
> **nhandler said:**
> 
Also, you are allowed to modify the contents of the package outside of the debian directory. However, when you do this, you are meant to use a [patch system]("https://wiki.ubuntu.com/PackagingGuide/PatchSystems").

Thanks.

I've put my changes into dpatch files. 

I believe I have fixed all the problems you mention and all the files appear lintian clean.

Submitted needs-packaging bug: [https://bugs.launchpad.net/ubuntu/+bug/290930](https://bugs.launchpad.net/ubuntu/+bug/290930) and added # to changelog

Latest files:
[http://www.jasp.com/teng/](http://www.jasp.com/teng/)

teng-1.0.4.tar.gz is the tarball downloaded from authors site
teng_1.0.4.orig.tar.gz is the above with debian/ removed

I've received an email from the original author, regarding debian/ removal, and he has passed the details on to the new maintainer.

---

### Post by InfinityCircuit on 2008-10-30
A few more things:

First, remove debian/dirs: it is a relic of dh_make

Second, you should add the upstream email to the copyright file.

Third, debian/docs currently isn't installing the docs because it isn't labeled as referring to a specific package.  You should make a debian/packagename.docs to keep consistency.

Fourth, you can clean up the rules file a bit:
-clean target depends on clean-patched, but clean-patched doesn't depend on patch, so it won't work as you intend.
-just include /usr/share/dpatch/dpatch.make and then call the patch-stamp and unpatch targets from there--no need to specify that in your rules file.
-no need to call dh_installman or dh_installexamples if you have no examples or manpages.
-config.status calls the configure target but you have no configure target.
-your .PHONY target is missing some stuff (it should include everything that doesn't make a file with its name.)

You might want to still clean up these information points from Lintian:

```
dmr@kronos:~/Work/mentor$ lintian -iI *.deb *.dsc
I: teng source: debian-watch-file-is-missing
N:
N:   This source package is not Debian-native but it does not have a
N:   debian/watch file. This file is used for automatic detection of new
N:   upstream versions by the Debian External Health Status project and
N:   other project infrastructure. If this package is maintained upstream,
N:   please consider adding a debian/watch file to detect new releases.
N:   
N:   If the package is not maintained upstream or if upstream uses a
N:   distribution mechanism that cannot be meaningfully monitored by uscan
N:   and the Debian External Health Status project, please consider adding
N:   a debian/watch file containing only comments documenting the
N:   situation.
N:   
N:   Refer to Debian Policy Manual section 4.11 (Optional upstream source
N:   location: debian/watch) and the uscan(1) manual page for details.
N:   
N:   Severity: wishlist; Certainty: certain
N:
I: libteng1: no-symbols-control-file usr/lib/libteng.so.1.0.0
N:
N:   Although the package includes a shared library, the package does not
N:   have a symbols control file.
N:   
N:   dpkg can use symbols files in order to generate more accurate library
N:   dependencies for applications, based on the symbols from the library
N:   that are actually used by the application.
N:   
N:   Refer to the dpkg-gensymbols(1) manual page for details.
N:   
N:   Severity: wishlist; Certainty: certain
N:

```

---

### Post by nhandler on 2008-10-30
This discussion should really be moved to [REVU]("http://revu.ubuntuwire.com/"). You will need to upload it to REVU at some point (if you want to have it added to the repositories), so you might as well do it now. It will also make it much easier for people to review the package and provide feedback.

---

### Post by JaspSoft on 2008-10-31
> **nhandler said:**
> This discussion should really be moved to [REVU]("http://revu.ubuntuwire.com/").

[http://revu.ubuntuwire.com/details.py?package=teng](http://revu.ubuntuwire.com/details.py?package=teng)

I've yet to upload the changes InfinityCircuit suggests.

---

