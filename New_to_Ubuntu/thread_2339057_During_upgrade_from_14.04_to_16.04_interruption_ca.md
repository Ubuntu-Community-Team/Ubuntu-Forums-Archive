---
title: "During upgrade from 14.04 to 16.04 interruption caused loss of Unity GUI"
date: 2016-10-04
forum: New to Ubuntu
---

### Post by nungwe on 2016-10-04
During download to upgrade my Dell 64bit Inspiron 15 3000 series laptop to 16.04 an interruption to the download caused the loss of the Unity GUI and the following errors were displayed on the command line.
First, on login the following error was displayed:-

```

/etc/update-motd.d/91-release-upgrade: 4: /etc/update-motd.d/91-release-upgrade: lsb_release: not found

```

Secondly, when I typed in 'sudo apt-get update' the following error was displayed:-

```

Err:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
     Temporary failure resolving 'archive.canonical.com'
Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
     Temporary failure resolving 'archive.ubuntu.com'
Err:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
     Temporary failure resolving 'security.ubuntu.com'
Err:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease
     Temporary failure resolving 'archive.ubuntu.com'
Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-proposed InRelease
     Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease) 
     Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)
     Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)
     Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/InRelease](http://archive.canonical.com/ubuntu/dists/xenial/InRelease)
     Temporary failure resolving 'archive.canonical.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease)
     Temporary failure resolving 'archive.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Finally, when I typed 'sudo apt-get -u upgrade' the following error was displayed:-

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
     myspell-en-au
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
22 not fully installed or removed.
After this operation, 637 kB disk space will be freed.
Do you want to continue? [Y/n] y
Unescaped left brace in regex is depreciated, passed through in regex; marked by <-- HERE in m/^(.*?)([\\)?\$]("file://\\)?\$"){<-- HERE ([^{}]+)}(.*)$/ at /usr/share/per15/Debconf/Question.pm line 72.
Unescaped left brace in regex is depreciated, passed through in regex; marked by <-- HERE in m/\${ <-- HERE  ([^}]+)}/ at /usr/share/per15/Debconf/Config.pm line 30.
(Reading database ... 355626 files and directories currently installed.)
Removing myspell-en-au (2.1-5.4) ...
Error: update-dictcommon-hunspell not present or executable. Missing dependency on dictionaries-common?
dpkg: error processing package myspell-en-au (--remove):
     subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
     myspell-en-au
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any solutions to this problem would be much appreciated.

---

### Post by colmax on 2016-10-04
Hi Nungwe
I can only suggest re-installing from scratch as trying to put things together piece by piece will probably leave you with a compromised system
May take a little time but it will save a lot of grief in the long run
Cheers

---

### Post by nungwe on 2016-10-09
Hi Colmax,
Thank you very much for your suggestion.
My Dell Inspiron laptop came with Ubuntu 14.04 preinstalled.  As I now have no Unity desktop, how do I uninstall 16.04 from the command line and any other files which might interfere with the successful reinstallation of 16.04 ?
Cheers

---

### Post by howefield on 2016-10-09
> **nungwe said:**
> My Dell Inspiron laptop came with Ubuntu 14.04 preinstalled.

If Ubuntu came pre-installed, you most likely have a recovery partition from which you can do a factory restore ?

If you want to do a clean install with 16.04.1, download it from ubuntu.com and create a Live USB stick or DVD. Installing with such a media allows for keeping the original /home folder intact, possibly useful of you didn't backup your important data before attempting the upgrade process ?

---

### Post by nungwe on 2016-10-23
Thank you for your response.  Have done a reboot to factory settings which seems to have solved the problem.

---

