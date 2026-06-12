---
title: "Flash for Ubuntu (PPC?)"
date: 2005-02-26
forum: Repositories &amp; Backports
---

### Post by jkibbe on 2005-02-26
I'm trying to use apt-get to get a Flash Player for use on my blueberry ibook.  I followed the instructions at [http://ubuntuguide.org/#multimedia-mozillanonp4](http://ubuntuguide.org/#multimedia-mozillanonp4) and here's what I get:
```

user@iBook:~ $ sudo apt-get install flashplayer-mozilla
Reading Package Lists... Done
Building Dependency Tree... Done
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-bp.sourceforge.net warty-backports/main Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_warty-backports_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-bp.sourceforge.net warty-backports/universe Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_warty-backports_universe_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-bp.sourceforge.net warty-backports/main Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_warty-backports_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-bp.sourceforge.net warty-backports/universe Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_warty-backports_universe_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package flashplayer-mozilla

```

I ran sudo apt-get update, too... Any advice?

-Jason :)

---

### Post by DJ_Max on 2005-02-26
Macromedia doesn't make LinuxPPC binaries. Do a search and you'll find what you're looking for.
[http://ubuntuppc.info/index.php?node=17](http://ubuntuppc.info/index.php?node=17)

---

### Post by jkibbe on 2005-02-26
Thanks so much for your help!  I never have had too much luck with PPC Linux (YDL), but Flash works!  It's was actually quick and easy!

Thanks again!,

Jason :D

---

### Post by DJ_Max on 2005-02-26
[QUOTE=jkibbe]Thanks so much for your help!  I never have had too much luck with PPC Linux (YDL), but Flash works!  It's was actually quick and easy!

Thanks again!,

Jason :D[/QUOTE]
No problemo' :cool:

---

### Post by Rovenhot on 2006-03-18
[QUOTE=jkibbe]Thanks so much for your help!  I never have had too much luck with PPC Linux (YDL), but Flash works!  It's was actually quick and easy!

Thanks again!,

Jason :D[/QUOTE]
Err...how did you install Flash?  I haven't found anything for PPC.  Ubuntuppc.info doesn't exist anymore, so the link doesn't work, either.  The only stuff that shows up on Google is blog entries explaining that Flash doesn't exist for PPC Linux.

EDIT: The Wayback Machine has nothing from ubuntuppc.info.  Was it ever a real website?

---

### Post by DJ_Max on 2006-03-19
[QUOTE=Rovenhot]Err...how did you install Flash?  I haven't found anything for PPC.  Ubuntuppc.info doesn't exist anymore, so the link doesn't work, either.  The only stuff that shows up on Google is blog entries explaining that Flash doesn't exist for PPC Linux.

EDIT: The Wayback Machine has nothing from ubuntuppc.info.  Was it ever a real website?[/QUOTE]
Yeah, there was data loss without a current snapshot. I'm going to try get the site back up with what I have. I'll be sure to do weekly backups this time.

---

### Post by mph66 on 2006-10-19
Is this site ever coming back up?  It's October of '06 and I'm getting the same "file not found" message, essentially.  Other threads indicate that there is no such thing as Flash for PPC Linux.  Is that true, or is this site like the Holy Grail, lost for all time?

-Marc

---

### Post by mclean_tom on 2006-11-11
-Bump-

I need this aswell

thankYou. :KS

---

### Post by fuoco on 2006-11-13
Or maybe someone knows of a repository with gnash for ppc ?

---

### Post by stmiller on 2006-11-17
Correct. There is no flash for PPC. You can install gnash, which is very basic. You could also try to get the x86 Linux flash version going with qemu (see gentoo ppc forum).

apt-get install gnash 

works for me. Though FWIW, gnash will only display trivial basic flash banners, etc. No flash video or anything. So it's not really any kind of holy grail. 

Also try installing swfdec. Another basic flash player.

Here are the enabled lines in my sources.list:

```


deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse


deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe


deb http://easyubuntu.cafuego.net main easyubuntu
```

---

