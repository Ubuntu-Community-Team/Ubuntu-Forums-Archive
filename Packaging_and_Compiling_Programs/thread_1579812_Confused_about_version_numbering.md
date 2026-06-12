---
title: "Confused about version numbering"
date: 2010-09-22
forum: Packaging and Compiling Programs
---

### Post by supremedalek on 2010-09-22
I am still trying to figure out ubuntu/debian package naming. So, let's say I want to create a version of a package that will only be used internally (openssh with lpk support would be a good example). Based on what I understood by reading [http://www.ducea.com/2006/06/17/ubuntu-package-version-naming-explanation/](http://www.ducea.com/2006/06/17/ubuntu-package-version-naming-explanation/) and [http://manpages.ubuntu.com/manpages/intrepid/man5/deb-version.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/deb-version.5.html) if I want to have my openssh-server package be able to replace openssh-server_5.3p1-3ubuntu4_amd64.deb while keeping the same version otherwise (I just apt-get the source, applied patch, and created the .deb), I would want to name it something like openssh-server_5.3p1+lpk-3ubuntu4_amd64.deb. That would indicate the file has the same debian and ubuntu version but be newer than that specific package. Am I correct or just confused?

---

### Post by Bachstelze on 2010-09-22
Nope. Here, you are changing the upstream version number, it's probably a bad idea. Do something like openssh-server_5.3p1-3ubuntu4+lpk.

---

### Post by supremedalek on 2010-09-22
Thanks! That sure makes sense. One more dumb question: where is the name of the .deb file created? I cannot believe it is in debian/changelog, so where else?

---

### Post by Bachstelze on 2010-09-22
> **supremedalek said:**
> Thanks! That sure makes sense. One more dumb question: where is the name of the .deb file created? I cannot believe it is in debian/changelog, so where else?

Of course it is. The version number is in debian/changelog. The filename of the final DEB package is constructed based on the package name and version number.

---

### Post by supremedalek on 2010-09-23
About the upstream version number, we have in universe the package sudo-ldap_1.7.2p1-1ubuntu5_amd64.deb which is a replacement for the package sudo_1.7.2p1-1ubuntu5_amd64.deb. How would that work out then? From what you said, it is changing the upstream version number. :confused:

Yeah, I do have a lot of silly questions. :D

---

### Post by Bachstelze on 2010-09-23
> **supremedalek said:**
> About the upstream version number, we have in universe the package sudo-ldap_1.7.2p1-1ubuntu5_amd64.deb which is a replacement for the package sudo_1.7.2p1-1ubuntu5_amd64.deb. How would that work out then? From what you said, it is changing the upstream version number. :confused:

Yeah, I do have a lot of silly questions. :D

It is changing the package name, not the upstream version number. ;) It uses the Replaces field of debian/control.

[http://www.debian.org/doc/debian-policy/ch-relationships.html#s-replaces](http://www.debian.org/doc/debian-policy/ch-relationships.html#s-replaces)

---

### Post by supremedalek on 2010-09-23
But, if you are starting from the same source and then modifying it so it would earn a different package name, how would you tell debian/control that if the original package of same debian/ubuntu version is already installed then it is ok to replace it?

You see, that is how I originally got into this mess: I setup in debian/control an entry for openssh-lpk-server. In its Replace statement I had openssh-server, which I thought would suffice to make it replace any version of opessh-server (I really could not figure out how to tell it to "replace any openssh-server that is as new as you are or older"). What I got is this:

```
root@ubuntu-x64B:~# sudo apt-get install openssh-lpk-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-server
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ssh-askpass rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed:
  openssh-lpk-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 310kB of archives.
After this operation, 831kB of additional disk space will be used.
Get:1 http://mirror.domain.com/local/ lucid/main openssh-lpk-server 1:5.3p1-3ubuntu4 [310kB]
Fetched 310kB in 0s (723kB/s)
Preconfiguring packages ...
Selecting previously deselected package openssh-lpk-server.
(Reading database ... 63827 files and directories currently installed.)
Unpacking openssh-lpk-server (from .../openssh-lpk-server_1%3a5.3p1-3ubuntu4_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/openssh-lpk-server_1%3a5.3p1-3ubuntu4_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man5/sshd_config.5.gz', which is also in package openssh-server 1:5.3p1-3ubuntu4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-lpk-server_1%3a5.3p1-3ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu-x64B:~#

```

---

### Post by Bachstelze on 2010-09-23
> **supremedalek said:**
> But, if you are starting from the same source and then modifying it so it would earn a different package name, how would you tell debian/control that if the original package of same debian/ubuntu version is already installed then it is ok to replace it?

You see, that is how I originally got into this mess: I setup in debian/control an entry for openssh-lpk-server. In its Replace statement I had openssh-server, which I thought would suffice to make it replace any version of opessh-server (I really could not figure out how to tell it to "replace any openssh-server that is as new as you are or older"). What I got is this:


Try with both Conflicts and Replaces (you can [font=monospace]apt-get source sudo[/font]) to see how sudo/sudo-ldap does it. Also make your package [font=monospace]Provides: openssh-server[/font], so that any package that depends on openssh-server won't get uninstalled

---

### Post by Yellow Pasque on 2010-09-29
This helps sometimes:
```
dch -i
```
I do my PPA like the following because Ubuntu build guide shows it that way. For example, if I want to modify gnome-applets and the latest version is 2.30.0-3ubuntu2, I make it gnome-applets-2.30.0-3ubuntu3~audiohacks1, which take precedence over ubuntu2, but won't take precedence over ubuntu3.

---

