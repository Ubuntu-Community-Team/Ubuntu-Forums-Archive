---
title: "dpkg/apt dead after lilypond-data install"
date: 2006-01-23
forum: Repositories &amp; Backports
---

### Post by o_fortuna on 2006-01-23
Okay, so I accidently tried to install something I didn't want. This particular package, lilypond, however, was unable to fully install. The package lilypond-data seems to be corrupted. Every time I run synaptic or dpkg, it tries to finish installing lilypond-data, but returns with the following error:
```
Preconfiguring packages ...
Selecting previously deselected package lilypond-data.
(Reading database ... 107345 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Does anyone have any idea how to fix this problem? I tried uninstalling it, but to no avail:
```
dpkg: error processing lilypond-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
```
Help?

---

### Post by dragonfyre13 on 2006-02-06
[http://ubuntuforums.org/showthread.php?p=680286#post680286](http://ubuntuforums.org/showthread.php?p=680286#post680286)

I fixed it. you should be able to follow it pretty well.

---

