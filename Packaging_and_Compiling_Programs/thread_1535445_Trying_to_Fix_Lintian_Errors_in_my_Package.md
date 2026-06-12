---
title: "Trying to Fix Lintian Errors in my Package"
date: 2010-07-20
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-07-20
Here I have the output of the lintian command for one of my packages.  I'm trying to understand what the errors mean.  I have already fixed about three or four.  The errors that I am focusing on at the moment are the "md5sums-lists-nonexisting-file" and "file-missing-in-md5sums" errors.  My guess is that my md5sums file is not formatted correctly.  All of the files exist, and the packages appears to install fine.  Does someone know how to fix this?

debreate_lintian.log:
```
E: debreate: debian-changelog-file-missing-or-wrong-name
W: debreate: syntax-error-in-debian-changelog line 1 "badly formatted heading line"
W: debreate: syntax-error-in-debian-changelog line 2 "found blank line where expected first heading"
W: debreate: syntax-error-in-debian-changelog line 3 "found change data where expected first heading"
W: debreate: syntax-error-in-debian-changelog line 8 "badly formatted heading line"
W: debreate: syntax-error-in-debian-changelog line 10 "found change data where expected next heading or eof"
Use of uninitialized value in hash element at /usr/share/lintian/checks/changelog-file line 291.
Use of uninitialized value $first_upstream in substitution (s///) at /usr/share/lintian/checks/changelog-file line 315.
Use of uninitialized value $first_upstream in string eq at /usr/share/lintian/checks/changelog-file line 318.
E: debreate: no-copyright-file
W: debreate: extended-description-line-too-long
W: debreate: possible-unindented-list-in-extended-description
W: debreate: essential-no-not-needed
W: debreate: unknown-section Development
W: debreate: non-standard-file-perm usr/share/debreate/_md5.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/bitmaps/add32.png 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/bitmaps/del32.png 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/bitmaps/icon.png 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/bitmaps/icon16.png 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/building.wav 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/db.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/db/dbabout.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/debreate.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/debrpm.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/docs/changelog 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/docs/release_notes 0666 != 0644
W: debreate: non-standard-executable-perm usr/share/debreate/launch.py 0777 != 0755
W: debreate: non-standard-file-perm usr/share/debreate/panbuild.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/pancontrol.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/pandepends.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/pandocs.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/panfiles.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/paninfo.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/panmenu.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/panscripts.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/rules.py 0666 != 0644
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/pancontrol.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/applications/Debreate.desktop
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbcharctrl.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/icon32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/pandocs.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/preview64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/building.wav
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbwizard.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/pipe32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/import32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/build64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbpathctrl.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/icon24.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/add32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/debianize.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbbuttons.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/save32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/icon16.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/debreate.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/doc/debreate/changelog.gz
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/next32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/exit16.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panbuild.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/globe16.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/rpm16.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/debrpm.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/save64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/prev32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/paninfo.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/browse64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/pandepends.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panfiles.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/docs/changelog
E: debreate: md5sums-lists-nonexisting-file /usr/share/mime/packages/dbp.xm
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panscripts.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/docs/gpl-3.0.txt
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panmenu.py
E: debreate: md5sums-lists-nonexisting-file */usr/share/debreate/launch.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/icon.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/browse32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/question64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/_md5.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/docs/release_notes
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/rules.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/build32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/cancel32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/confirm32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/preview32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panlog.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/debreate64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbabout.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/del32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/exit32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/clear32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/pandepends.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/question64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/preview32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/exit32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbbuttons.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/next32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/icon32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/del32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/panbuild.py
W: debreate: file-missing-in-md5sums usr/share/doc/debreate/changelog.gz
W: debreate: file-missing-in-md5sums usr/share/debreate/panlog.py
W: debreate: file-missing-in-md5sums usr/share/debreate/pandocs.py
W: debreate: file-missing-in-md5sums usr/share/applications/Debreate.desktop
W: debreate: file-missing-in-md5sums usr/share/debreate/paninfo.py
W: debreate: file-missing-in-md5sums usr/share/debreate/docs/release_notes
W: debreate: file-missing-in-md5sums usr/share/debreate/panscripts.py
W: debreate: file-missing-in-md5sums usr/share/debreate/_md5.py
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbcharctrl.py
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbpathctrl.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/rpm16.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/globe16.png
W: debreate: file-missing-in-md5sums usr/share/debreate/debreate.py
W: debreate: file-missing-in-md5sums usr/share/debreate/building.wav
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/confirm32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/docs/changelog
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/exit16.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/save32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/prev32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/pipe32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/build32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/add32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/cancel32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/rules.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/icon16.png
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbwizard.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/build64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbabout.py
W: debreate: file-missing-in-md5sums usr/share/debreate/db.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/icon24.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/import32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/debianize.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/debreate64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/docs/gpl-3.0.txt
W: debreate: file-missing-in-md5sums usr/share/debreate/debrpm.py
W: debreate: file-missing-in-md5sums usr/share/mime/packages/dbp.xml
W: debreate: file-missing-in-md5sums usr/share/debreate/panmenu.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/browse64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/panfiles.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/icon.png
W: debreate: file-missing-in-md5sums usr/share/debreate/pancontrol.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/clear32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/preview64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/launch.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/save64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/browse32.png
W: debreate: desktop-command-not-in-package /usr/share/applications/Debreate.desktop debreate
E: debreate: python-script-but-no-python-dep ./usr/share/debreate/launch.py
W: debreate: maintainer-script-ignores-errors postrm
W: debreate: maintainer-script-ignores-errors postinst
W: debreate: maintainer-script-ignores-errors prerm
```

**Edit:** I say that I am focusing on certain errors, but if you have advice on any others I would much appreciate it.

---

### Post by SevenMachines on 2010-07-21
its a bit of a guess, i'd need to look at the packaging to know a bit better, but the errors/warnings come in pairs, ie

> E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/icon.png

W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/icon.pngin addition to lines like
>  E: debreate: md5sums-lists-nonexisting-file */usr/share/debreate/debrpm.pyi'm beginning to think that maybe theres some mistakes in your rules or .install file that are causing these problems. you also need to be looking closely at those changelog and copyright errors. theres a few problems needing fixed.

---

### Post by dodle on 2010-07-21
SevenMachines, I don't have a rules or .install file.  I've built this package from precompiled binaries and python scripts.  I'm still trying to learn how to be a real Debian/Ubuntu packager :).  I found the lintian tag explanations and fixed a few more of the errors, [http://lintian.debian.org/tags.html](http://lintian.debian.org/tags.html).  Here is the output now:

debreate_lintian.log:
```
W: debreate: essential-no-not-needed
W: debreate: unknown-section Development
W: debreate: non-standard-file-perm usr/share/debreate/_md5.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/bitmaps/add32.png 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/bitmaps/del32.png 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/bitmaps/icon.png 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/bitmaps/icon16.png 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/building.wav 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/db.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/db/dbabout.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/debreate.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/debrpm.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/docs/changelog 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/docs/release_notes 0666 != 0644
W: debreate: non-standard-executable-perm usr/share/debreate/launch.py 0777 != 0755
W: debreate: non-standard-file-perm usr/share/debreate/panbuild.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/pancontrol.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/pandepends.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/pandocs.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/panfiles.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/paninfo.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/panmenu.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/panscripts.py 0666 != 0644
W: debreate: non-standard-file-perm usr/share/debreate/rules.py 0666 != 0644
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/pancontrol.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/applications/Debreate.desktop
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbcharctrl.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/icon32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/pandocs.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/preview64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/building.wav
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbwizard.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/pipe32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/import32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/build64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbpathctrl.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/icon24.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/add32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/debianize.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbbuttons.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/save32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/icon16.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/debreate.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/doc/debreate/changelog.gz
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/next32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/exit16.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panbuild.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/globe16.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/rpm16.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/debrpm.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/save64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/prev32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/paninfo.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/browse64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/pandepends.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panfiles.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/docs/changelog
E: debreate: md5sums-lists-nonexisting-file /usr/share/mime/packages/dbp.xm
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panscripts.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/docs/gpl-3.0.txt
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panmenu.py
E: debreate: md5sums-lists-nonexisting-file */usr/share/debreate/launch.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/icon.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/browse32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/question64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/_md5.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/docs/release_notes
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/rules.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/build32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/cancel32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/confirm32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/preview32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/panlog.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/debreate64.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/db/dbabout.py
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/del32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/exit32.png
E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/bitmaps/clear32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/pandepends.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/question64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/preview32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/exit32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbbuttons.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/next32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/icon32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/del32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/panbuild.py
W: debreate: file-missing-in-md5sums usr/share/doc/debreate/changelog.gz
W: debreate: file-missing-in-md5sums usr/share/debreate/panlog.py
W: debreate: file-missing-in-md5sums usr/share/debreate/pandocs.py
W: debreate: file-missing-in-md5sums usr/share/debreate/paninfo.py
W: debreate: file-missing-in-md5sums usr/share/debreate/docs/release_notes
W: debreate: file-missing-in-md5sums usr/share/debreate/panscripts.py
W: debreate: file-missing-in-md5sums usr/share/debreate/_md5.py
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbcharctrl.py
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbpathctrl.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/rpm16.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/globe16.png
W: debreate: file-missing-in-md5sums usr/share/debreate/debreate.py
W: debreate: file-missing-in-md5sums usr/share/debreate/building.wav
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/confirm32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/docs/changelog
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/exit16.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/save32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/prev32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/pipe32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/build32.png
W: debreate: file-missing-in-md5sums usr/share/applications/debreate.desktop
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/add32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/cancel32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/rules.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/icon16.png
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbwizard.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/build64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/db/dbabout.py
W: debreate: file-missing-in-md5sums usr/share/doc/debreate/changelog.Debian.gz
W: debreate: file-missing-in-md5sums usr/share/debreate/db.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/icon24.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/import32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/debianize.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/debreate64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/docs/gpl-3.0.txt
W: debreate: file-missing-in-md5sums usr/share/debreate/debrpm.py
W: debreate: file-missing-in-md5sums usr/share/mime/packages/dbp.xml
W: debreate: file-missing-in-md5sums usr/share/debreate/panmenu.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/browse64.png
W: debreate: file-missing-in-md5sums usr/share/doc/debreate/copyright
W: debreate: file-missing-in-md5sums usr/share/debreate/panfiles.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/icon.png
W: debreate: file-missing-in-md5sums usr/share/debreate/pancontrol.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/clear32.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/preview64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/launch.py
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/save64.png
W: debreate: file-missing-in-md5sums usr/share/debreate/bitmaps/browse32.png
E: debreate: python-script-but-no-python-dep ./usr/share/debreate/launch.py
```

> W: debreate: essential-no-not-needed
W: debreate: unknown-section Development
I think I can ignore these two lines.  Yes? No?

> non-standard-file-perm
I don't understand why permissions ar getting messed up.  I am using the command "**fakeroot dpkg -b**" to build my package.  File permissions are set to 0666 when they should be 0644.  

> non-standard-executable-perm
Executable file permissions are set to 0777 when they should be 0755

> file-missing-in-md5sums
This says that the files listed in md5sums do not exists.  I'll put the md5sums below and upload a tar with the .deb if anybody wants to take a look:  [ATTACH]164128[/ATTACH]

> md5sums-lists-nonexisting-file
Didn't find an explanation for this one, but I assume it will be fixed with "**file-missing-in-md5sums**".

> python-script-but-no-python-dep
This one has really got me confused, because python is listed as a dependency.  Here is the dependencies line from my control file:
> Depends: bash (>=4.1), dpkg (>=1.15), gzip (>=1.3), python (>>2.6) | python2.6, python-wxgtk2.8, python-wxversion, fakeroot

Here is the md5sums file:
> fed73d53fd90ab070ca42381e1f5205b  /usr/share/debreate/rules.py
76a20b0622d61400a0e42ec3822e54b5  /usr/share/debreate/_md5.py
88cc6df7e196fcdd340a594c655eeaf0  /usr/share/debreate/pandocs.py
a02a5fb948000e3ee6c4d907cc768b1d  /usr/share/debreate/panlog.py
f14990de6cca7e13c18816703416fe35  /usr/share/debreate/pandepends.py
77c74620d5720d6b8d92c7a3163df609  /usr/share/debreate/panscripts.py
965ec5362a644fb7c680767d80153343  /usr/share/debreate/pancontrol.py
58505102b20cea9de71a5accf9db9ea5  /usr/share/debreate/debreate.py
a4cc0e0d60055ce023f19b0f93939495  /usr/share/debreate/debianize.py
f1148bf72fa06efb7467ff95eba23b1f  /usr/share/debreate/panmenu.py
26666ef3aa50a83bbe26122a5ce34a05  /usr/share/debreate/panfiles.py
60ba9e7a093f7bcc176b38f84e1cf086  /usr/share/debreate/building.wav
fbda543284ce6d08a4c661bc49fd4d2a  /usr/share/debreate/paninfo.py
962537c889f140a2435d11b72bb90a65  /usr/share/debreate/db.py
d631650e38874f235eaa6ab142d29f09 */usr/share/debreate/launch.py
9fc2cbce0375e869b505f03fbbf4da99  /usr/share/debreate/debrpm.py
0313a6636bcc0c79a4db6332e3174ccd  /usr/share/debreate/panbuild.py
dbd3fd1b9d2998c32c1729e496ee97e5  /usr/share/debreate/bitmaps/next32.png
36bebefee96cc8d3ba2e6718c0e8556e  /usr/share/debreate/bitmaps/debreate64.png
2e8c4960d5307603e6d105c1c6b5661d  /usr/share/debreate/bitmaps/rpm16.png
03fec4022fd645d40d27f0fc3c62e191  /usr/share/debreate/bitmaps/clear32.png
9ab66c25afedd0c4ff29a64e3162c20a  /usr/share/debreate/bitmaps/add32.png
3566664ca0dc976f0ec80fefb23cd001  /usr/share/debreate/bitmaps/save32.png
6dba85b35e735a8b5b1e614f7880ae21  /usr/share/debreate/bitmaps/browse64.png
216d0ebe8e8ff6a5fcff56852f54ed9d  /usr/share/debreate/bitmaps/icon.png
901a44ad9f2978ce5e622a037449da7b  /usr/share/debreate/bitmaps/exit32.png
64d661649c30fc61ed01ebbaf45d7d65  /usr/share/debreate/bitmaps/icon24.png
49a169242de118afb01fc70d1db2b8ec  /usr/share/debreate/bitmaps/build64.png
52f135ae05f17b1eaf7114f7f508e0c1  /usr/share/debreate/bitmaps/browse32.png
42bce7bb64d70cdfa9a6e588fdf7d49e  /usr/share/debreate/bitmaps/prev32.png
d7124130661d8e937a3d28bc8b3772ef  /usr/share/debreate/bitmaps/cancel32.png
1713ec751b760c6b77c4afa6216d8889  /usr/share/debreate/bitmaps/question64.png
c7dda90c202b279df317163463d1f0f4  /usr/share/debreate/bitmaps/icon16.png
3ee55862848c72b0fd141e47e6aead17  /usr/share/debreate/bitmaps/del32.png
e8370c80be047eff91c257097bea90ed  /usr/share/debreate/bitmaps/preview64.png
402ab175f60c76933a5eb0b3e28221e1  /usr/share/debreate/bitmaps/preview32.png
24e547ebb2fa66c19eb08561e2c3f552  /usr/share/debreate/bitmaps/icon32.png
b02a5ade38316ffda86977352a43ea3a  /usr/share/debreate/bitmaps/save64.png
98d5beffe32e480906c29d512d1588dd  /usr/share/debreate/bitmaps/globe16.png
4b88f8cf0c16afdfd87908223d61e35f  /usr/share/debreate/bitmaps/exit16.png
5217cd69c792138fff27674063409a89  /usr/share/debreate/bitmaps/build32.png
9dbbdaa24c701f6462ec303c3979c0a6  /usr/share/debreate/bitmaps/import32.png
ab60be9389e9afa1b1525119c75221ed  /usr/share/debreate/bitmaps/confirm32.png
530967876d82d79e3ad772c706e541b4  /usr/share/debreate/bitmaps/pipe32.png
736313ac4cdb8879434999470618fcf2  /usr/share/debreate/docs/release_notes
d12d3fe4ef63c9496b168f5fefe70c55  /usr/share/debreate/docs/changelog
d4333f07cbfa8fe036e90820f556b2ad  /usr/share/debreate/docs/gpl-3.0.txt
93504709bc5f4c247b57df23f8a75b45  /usr/share/debreate/db/dbabout.py
c71561e4407822d429245967aa0696d9  /usr/share/debreate/db/dbcharctrl.py
410c7b672ad358d4459e53746b3cf846  /usr/share/debreate/db/dbpathctrl.py
737a8213ee9aaba580dc7c768b29850c  /usr/share/debreate/db/dbbuttons.py
f3bbaba8b1ce764e5e0ea307ef052d76  /usr/share/debreate/db/dbwizard.py
6aab1cd6de14bec0e83de7aa62b6d825  /usr/share/applications/Debreate.desktop
220fe0738565cfe087af8d2c5d215dec  /usr/share/doc/debreate/changelog.gz
1679dfc33e2b35bc5e645c38b4b3f1ad  /usr/share/mime/packages/dbp.xml

---

### Post by SevenMachines on 2010-07-21
> W: debreate: essential-no-not-neededyou have an essential: field in a binary section of your debian/control file that says no, so the field isnt actually needed at all

> 
W: debreate: unknown-section DevelopmentDevelopment isnt a valid section, see the list
[http://www.debian.org/doc/debian-policy/ch-archive.html#s-subsections](http://www.debian.org/doc/debian-policy/ch-archive.html#s-subsections)
you probably want devel

>  W: debreate: non-standard-file-perm usr/share/debreate/_md5.py 0666 != 0644standard file permissions in /usr/share are 0644, if they arent then there will be complaints. with 0666 then essentially you're allowing people that shouldnt to write to the system directories! 

>  E: debreate: python-script-but-no-python-dep ./usr/share/debreate/launch.pysee,
[http://lintian.debian.org/tags/python-script-but-no-python-dep.html](http://lintian.debian.org/tags/python-script-but-no-python-dep.html)
you have a control file with a versioned python dependency and a launch.py that uses any python version, both need to match to avoid this warning


> E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/pancontrol.py

W: debreate: file-missing-in-md5sums usr/share/debreate/pandepends.pyi would just be making too many bad guesses without seeing packaging. dh_md5sums should create the sums when you build from the files installed into the package so something isnt very well

---

### Post by SevenMachines on 2010-07-21
> dh_md5sums should create the sums when you build from the files installed into the package so something isnt very well
sorry, ignore this bit, that was about packaging and i just remembered what dpkg -b was :)  i still think its probably easier to package it instead but hopefully some the previous post  helped get rid of some of those errors/warnings

---

### Post by dodle on 2010-07-21
> **SevenMachines said:**
> you have an essential: field in a binary section of your debian/control file that says no, so the field isnt actually needed at allFixed, thank you.

> **SevenMachines said:**
> Development isnt a valid section...
...you probably want develFixed, thank you.

I didn't realize that the file permissions were messed up to begin with.  I thought that the command I was using, "**fakeroot dpkg -b**", was changing them.  I had transferred these files to/from a Windows machine, I guess that is what messed up the permissions.


> **SevenMachines said:**
> you have a control file with a versioned python dependency and a launch.py that uses any python version, both need to match to avoid this warningFixed, thank you.

Now all that is left is to fix the md5sums errors.

---

### Post by SevenMachines on 2010-07-21
> E: debreate: md5sums-lists-nonexisting-file /usr/share/debreate/pancontrol.py

W: debreate: file-missing-in-md5sums usr/share/debreate/pandepends.py                      currently md5sums contain system installed paths, ie
fed73d53fd90ab070ca42381e1f5205b  /usr/share/debreate/rules.py

but they're there to verify the package, ie, should have package relative paths (drop the first '/'), 
fed73d53fd90ab070ca42381e1f5205b  usr/share/debreate/rules.py

---

### Post by dodle on 2010-07-21
> **SevenMachines said:**
> currently md5sums contain system installed paths, ie
fed73d53fd90ab070ca42381e1f5205b  /usr/share/debreate/rules.py

but they're there to verify the package, ie, should have package relative paths (drop the first '/'), 
fed73d53fd90ab070ca42381e1f5205b  usr/share/debreate/rules.py

Thank you!  All of my errors are fixed.

---

### Post by SevenMachines on 2010-07-21
good stuff! 
your life will be easier though if you you move on to
[https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python)
it will make it easier, i swear :)

---

### Post by dodle on 2010-07-21
Nice, thank you.

---

### Post by TheeMahn2003 on 2011-05-22
I know this is old news, however what I am writing is not.  [http://forumubuntusoftware.info/viewtopic.php?f=23&t=5692](http://forumubuntusoftware.info/viewtopic.php?f=23&t=5692)

---

