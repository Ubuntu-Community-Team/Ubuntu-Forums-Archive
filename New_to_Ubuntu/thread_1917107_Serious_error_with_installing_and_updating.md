---
title: "Serious error with installing and updating"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by James Francis Kenny on 2012-01-29
Hello all,

Another novice question which I do not seem to be able to fix. I get the same error message when trying to install a new program or check for updates.

I have copied it here for reference and would be greatly appreciative for any advice and guidance as to how to correct it.


This is the text when trying to install Acidrip using Ubuntu Software centre and to my eyes it seems when I try and use update manager I get an identical error message.

InstallArchives() failed: Selecting previously deselected package lsdvd.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'ri-li-data': Input/output error
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
Setting up python-cssutils (0.9.8~a1-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 290, in <module>
    main()
  File "/usr/bin/pycompile", line 263, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 161, in compile
    os.readlink(fn))
OSError: [Errno 5] Input/output error: '/usr/lib/python2.7/dist-packages/cssutils/css/cssnamespacerule.py'
dpkg: error processing python-cssutils (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-qt4 (4.8.5-0ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 290, in <module>
    main()
  File "/usr/bin/pycompile", line 263, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 161, in compile
    os.readlink(fn))
OSError: [Errno 5] Input/output error: '/usr/lib/python2.7/dist-packages/PyQt4/uic/Compiler/compiler.py'
dpkg: error processing python-qt4 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-avogadro:
 python-avogadro depends on python2.7-qt4; however:
  Package python2.7-qt4 is not installed.
  Package python-qt4 which provides python2.7-qt4 is not configured yet.
dpkg: error processing python-avogadro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of calibre:
 calibre depends on python-cssutils (>= 0.9.7~); however:
  Package python-cssutils is not configured yet.
 calibre depends on python-qt4 (>= 4.8.3-2); however:
  Package python-qt4 is not configured yet.
dpkg: error processing calibre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde4:
 python-kde4 depends on python-qt4 (>= 4.8.3-3~); however:
  Package python-qt4 is not configured yet.
dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured

---

### Post by 2F4U on 2012-01-29
How do you install that software, is this software from Ubuntu repositories? It looks as if there are unfulfilled dependencies and that makes me thinking that the software doesn't come from Ubuntus repositories.

---

### Post by James Francis Kenny on 2012-01-29
I honestly don't know what you are asking me.

This is the error log from installing via the Ubuntu Software Centre.

I am using the latest Ubuntu release on a 32bit machine

---

### Post by James Francis Kenny on 2012-01-31
Does anybody have any more thoughts on this one?

It won't let me install anything at all.

I am reluctant to reinstall the operating system again.

---

### Post by James Francis Kenny on 2012-02-01
Will reinstall tonight and hope this never happens again as it is clearly unsolve-able!

---

### Post by CJ_Hudson on 2012-03-31
Re: oneiric won't boot- reinstall and retrieve data from Deja Dup?
I don't think "Nuke 'em from orbit" is the only choice just yet.

If you can get to the recovery mode right now (I realize you were getting all sorts of frustrating behavior based on your previous thread), choose the option to check the disk. If you get no satisfaction, get back to the recovery mode and start the boot in verbose mode to see where it hangs.
__________________
Character is not demonstrated by what you do when you think somebody may be watching, but by what you do when you are absolutely sure nobody is watching.
Sarcoidosis: The booby prize for "Good news! It's not cancer!"

[http://ubuntuforums.org/showthread.php?t=1948019](http://ubuntuforums.org/showthread.php?t=1948019)

I don't know if you reinstalled but suggest try above first.:KS

---

