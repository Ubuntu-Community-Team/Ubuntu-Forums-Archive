---
title: "HOWTO: Aut. Script for installing PyMusique (For itunes.com)"
date: 2005-05-17
forum: Outdated Tutorials &amp; Tips
---

### Post by madzzoni on 2005-05-17
[SIZE=3]**This script is for Ubuntu Hoary i386 users!**[/SIZE]
Purpose: To make an easy installation of PyMusique, the program that make's it possible to browse and buy music from [www.itunes.com](www.itunes.com)

**PyMusique Features:**
    * Preview songs
    * Signup for an account
    * Buy songs
    * Redownload songs that were bought with PyMusique

Homepage: [http://fuware.nanocrew.net/pymusique/](http://fuware.nanocrew.net/pymusique/)

This script download- and install PyMusique and it's dependencies with deb-packages made for hoary.
- It will add universe, multiverse, backports and misc repositories in /etc/apt/sources.list and then do a apt-get update.
(Note: If you get an error with libfaad2, please uninstall your version and run the script again)
  
To run the script, just open a terminal and type:
```
$ wget http://madzzoni.1go.dk/ubuntu/pymusiquesetup.sh
$ sudo sh pymusiquesetup.sh
```
You should be done!
Restart Gnome and hit "Applications- > Internet-> PyMusique"

This is my very first script, so please don,t shout at me, if something went wrong.
I have testet this script on 3 ubuntu Hoary PC's with success, but renember, you use this script on your own risk.

Have fun  :wink:

---

### Post by cwestpha on 2005-05-18
[QUOTE=madzzoni][SIZE=3]**This script is for Ubuntu Hoary i386 users!**[/SIZE]
Purpose: To make an easy installation of PyMusique, the program that make's it possible to browse and buy music from [www.itunes.com](www.itunes.com)

**PyMusique Features:**
    * Preview songs
    * Signup for an account
    * Buy songs
    * Redownload songs that were bought with PyMusique

Homepage: [http://fuware.nanocrew.net/pymusique/](http://fuware.nanocrew.net/pymusique/)

This script download- and install PyMusique and it's dependencies with deb-packages made for hoary.
- It will add universe, multiverse, backports and misc repositories in /etc/apt/sources.list and then do a apt-get update.
(Note: If you get an error with libfaad2, please uninstall your version and run the script again)
  
To run the script, just open a terminal and type:
```
$ wget http://madzzoni.1go.dk/ubuntu/pymusiquesetup.sh
$ sudo sh pymusiquesetup.sh
```
You should be done!
Restart Gnome and hit "Applications- > Internet-> PyMusique"

This is my very first script, so please don,t shout at me, if something went wrong.
I have testet this script on 3 ubuntu Hoary PC's with success, but renember, you use this script on your own risk.

Have fun  :wink:[/QUOTE]
 Got this error at the end:

Selecting previously deselected package libfaad2.
(Reading database ... 76853 files and directories currently installed.)
Unpacking libfaad2 (from libfaad2_2.0-1_i386.deb) ...
dpkg: error processing libfaad2_2.0-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libfaad.so.0.0.0', which is also in package libfaad2-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 libfaad2_2.0-1_i386.deb
ERROR # 1 : There was an error in libfaad2_2.0-1_i386 installation.

---

### Post by henriquemaia on 2005-05-18
[QUOTE=cwestpha]Got this error at the end:

Selecting previously deselected package libfaad2.
(Reading database ... 76853 files and directories currently installed.)
Unpacking libfaad2 (from libfaad2_2.0-1_i386.deb) ...
dpkg: error processing libfaad2_2.0-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libfaad.so.0.0.0', which is also in package libfaad2-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 libfaad2_2.0-1_i386.deb
ERROR # 1 : There was an error in libfaad2_2.0-1_i386 installation.[/QUOTE]

Had the same error here.

---

### Post by madzzoni on 2005-05-18
Re: ERRORS's

It seems like the libfaad2 from the repo's got an error/problem!
Uninstall it:
Open Synaptic an find your libfaad2, then uninstall it.

Run the script again and then the script will install libfaad2 from [http://fuware.nanocrew.net/pymusique/](http://fuware.nanocrew.net/pymusique/)

(I got the same problem myself, that's why the script dosn't use the one from the repo's!)

Hope this works for  :razz:

---

### Post by Bo Rosén on 2005-05-18
Does this version include the new shops for Denmark, Sweden etc?

---

### Post by madzzoni on 2005-05-18
[QUOTE=Bo Rosén]Does this version include the new shops for Denmark, Sweden etc?[/QUOTE]

Not yet, but i made another post about that in this forum.
Need to update the Country-codes/numbers

---

### Post by Bo Rosén on 2005-05-19
Ok. Let's hope Jon & co get a new version out soon then.

Mange tak

---

### Post by bhound89 on 2005-06-14
this script worked great on my old install, but now the links are all dead.

---

### Post by joakim2 on 2005-06-14
Fetched 40.0kB in 16s (2393B/s)
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz  MD5Sum mismatch
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz  MD5Sum mismatch
Reading package lists... Done
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
ERROR # 100 : There was an error in apt-get update.

---

### Post by madzzoni on 2005-06-14
[QUOTE=bhound89]this script worked great on my old install, but now the links are all dead.[/QUOTE]

It seems like the server is down. :?

---

