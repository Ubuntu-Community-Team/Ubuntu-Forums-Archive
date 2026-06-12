---
title: "Can't install/upgrade any packages - memtest86+ error"
date: 2006-02-15
forum: Repositories &amp; Backports
---

### Post by OneWingedAngel on 2006-02-15
I'm having a serious problem at the moment. Any attempt to install a package results in the following error:

[I]Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/$PACKAGE.deb (--unpack):
 unable to open files list file for package `memtest86+': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/$PACKAGE.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

($PACKAGE is the package in question, not part of the error)

I can't remove memtest86+, as I get the same error when I try to do that.
Does anyone know how I can repair this?

Thanks.

---

### Post by OneWingedAngel on 2006-02-16
Never mind.

It turns out the power cut the other day corrupted a few files in /var/lib/dpkg/info. I loaded up the System Rescue CD, ran fsck.ext3 and all is well.

---

