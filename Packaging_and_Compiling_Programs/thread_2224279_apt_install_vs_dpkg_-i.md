---
title: "apt install vs dpkg -i"
date: 2014-05-15
forum: Packaging and Compiling Programs
---

### Post by William_LePera on 2014-05-15
I am trying to install a package that was converted from .rpm to .deb format using alien -g and dpkg-deb -b.  If I use dpkg, it installs successfully:

```
 # dpkg -i foo.deb
Selecting previously unselected package foo.
(Reading database ... 89786 files and directories currently installed.)
Preparing to unpack foo.deb ...
Unpacking foo ...
Setting up foo ...
...return code:  0
#
```

However, if I try apt install with the same package, it doesn't work:

```
# apt install foo.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package foo.deb
E: Couldn't find any package by regex 'foo.deb'
```

If I use "./foo.deb" instead of "foo.deb", I get literally thousands of lines of output

```
root@c61f3bc1s10vm1:/install/ppe# apt install ppe_rte_license-2.1.0.0-1420b.ppc64le.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'account-plugin-yahoojp' for regex '.'
Note, selecting 'camlzip' for regex '.'
Note, selecting 'ceph-fuse' for regex '.'
Note, selecting 'dvd+rw-tools' for regex '.'
Note, selecting 'gnome-commander-data' for regex '.'
Note, selecting 'gweled' for regex '.'
Note, selecting 'libannotation-indexer-java-doc' for regex '.'
Note, selecting 'libboost-timer-dev' for regex '.'
Note, selecting 'libdune-istl-dev' for regex '.'
Note, selecting 'libfile-keepass-perl' for regex '.'
.
.
.
E: Release 'foo.deb' for 'account-plugin-aim' was not found
E: Release 'foo.deb' for 'empathy' was not found
E: Release 'foo.deb' for 'telepathy-haze' was not found
E: Release 'foo.deb' for 'mcp-account-manager-uoa' was not found
.
.
.
```

and install ultimately fails.

I am new to Ubuntu/Debian packaging and think I must be missing one or more steps.  Most of the information I found about Debian packaging dealt with taking over an existing package or creating one from scratch. In my case, my rpm is for an architecture (ppc64) other than the system where the conversion is done (x86_64), so simply using alien to do the complete conversion won't work.

Is there something else I need to do to get apt install working?

Thanks

---

### Post by steeldriver on 2014-05-15
Do you mean apt install, or apt**-get** install?

The apt-get command is for getting packages from a (usually remote) repository - if you are looking for a commandline tool to install a local .deb package (like dpkg -i) with  its dependencies (like apt-get) then the tool you're looking for is probably gdebi

```

DESCRIPTION
       gdebi  lets you install local deb packages resolving and installing its
       dependencies. apt does the  same,  but  only  for  remote  (http,  ftp)
       located packages.

```

---

### Post by William_LePera on 2014-05-19
Thank you for your response.  I installed gdebi and it does most of what I want.  However it doesn't seem to take multiple .deb packages on the command line.  Does Debian/Ubuntu offer similar functionality as the "rpm" command, such that multiple .deb files can be specified on a single command line, and assuming all the necessary dependencies were met in the given files, have the packages installed in the correct order to satisfy the dependencies?  For example, if I have two rpm files with the following dependencies:

```
foo_A.rpm: no dependencies
foo_B.rpm: requires foo_A
```

I can use the "rpm" command and give the file names in any order.  rpm will figure out that foo_A must be installed before foo_B and install them that way.  If I try this with gdebi, it looks like only the first package name is processed.  Is there a way to give multiple .deb package names on the gdebi command line and have the command parse the dependencies and install in the correct order?  If not, will another utility provide this functionality?

Or must I pack all my .debs into a local repository and let apt handle it?  Based on what I've been able to find on the web so far, it's looking like this might be where I end up.

---

### Post by ian-weisser on 2014-05-19
apt-get cannot use a filename (foo.deb)
dpkg can use a filename.

apt is intended for use with known and trusted repositories. If the 'foo' package is in the repo, apt knows how to download it, where to download it to, what it's dependencies are, etc. Apt can install multiple packages in one command, and automatically handles dependency resolution.

dpkg cannot do any of those things. dpkg is supreme at installing and uninstalling individual packages, and maintaining the database (that apt also uses) of known packages.

I think you are on the right track. If you want to install one custom package, dpkg can handle it. It you have lots of custom packages, you should indeed set up a small repository for apt to use.

---

### Post by ian-weisser on 2014-05-19
(Meh) Silly double-posting network connection!

---

