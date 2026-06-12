---
title: "one more thing..."
date: 2006-07-16
forum: Repositories &amp; Backports
---

### Post by yourearthlymaster on 2006-07-16
the only other error I keep getting is this:  

E: lilypond-data: subprocess post-removal script returned error exit status 1



Again thanx

---

### Post by aysiu on 2006-07-16
> **yourearthlymaster said:**
> the only other error I keep getting is this:  

E: lilypond-data: subprocess post-removal script returned error exit status 1



Again thanx
[This](http://www.ubuntuforums.org/showthread.php?t=103013)  may help.

---

### Post by yourearthlymaster on 2006-07-16
i tried what they suggested, but got different results.  
this is what I got with apt-get remove:  

keith@ubuntu:~$ sudo apt-get remove lilypond-data
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  lilypond-data
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 73524 files and directories currently installed.)
Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by yourearthlymaster on 2006-07-16
one note, unless i use sudo i get the package is locked, see


keith@ubuntu:~$ apt-get install lilypond-data
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
keith@ubuntu:~$ sudo apt-get install lilypond-data
Reading package lists... Done
Building dependency tree... Done
lilypond-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4736kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package lilypond-data.
(Reading database ... 73525 files and directories currently installed.)
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

---

