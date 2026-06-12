---
title: "how to review installed software"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by mike acker on 2012-10-17
given that ( hopefully ) all software in Ubuntu has to be installed through the Official Gate -- i.e. from the U Software Library or via sudo apt-get install -- it should be possible to review the installed software ...

can this be done from one of the logs ?  I was looking at the system log yesterday but it looks like it need to grep it, really ... to do that i need to know what to look for

to me, auditing installed software has always been a huge missing security requirement that Windows don't provide

i'm going to use "don't" improperly here because I don't know whether to say "won't " or "can't"

---

### Post by drmrgd on 2012-10-17
Depending on the information that you're looking for, there are a few ways around this.  First, definitely check out the man pages on 'dpkg'.

If you want to know about a package that's installed, you can run something like:

```
$ dpkg -l most
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  most                     5.0.0a-2.1               Pager program similar to more and less

```

You can also find out more about where components are installed by changing the lower-case 'l' to upper case:

```
dpkg -L most
/.
/usr
/usr/bin
/usr/bin/most
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/most.1.gz
/usr/share/doc
/usr/share/doc/most
/usr/share/doc/most/copyright
/usr/share/doc/most/README
/usr/share/doc/most/lesskeys.rc
/usr/share/doc/most/most-fun.txt
/usr/share/doc/most/most.rc
/usr/share/doc/most/changelog.Debian.gz
/usr/lib
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/most
```

If you don't quite know the name of the package that you want informtion about, you can pipe the 'dpkg -l' command to a grep:

```
dpkg -l | grep zip
ii  bzip2                                1.0.6-1                                   high-quality block-sorting file compressor - utilities
ii  gzip                                 1.4-1ubuntu2                              GNU compression utilities
ii  libzip2                              0.10-1ubuntu1                             library for reading, creating, and modifying zip archives (runtime)
ii  unzip                                6.0-4ubuntu1                              De-archiver for .zip files
ii  zip                                  3.0-4
```

You can also dump all of the packages that are installed on you system, which is useful in the event that you want to restore all of the packages you had in the event of a system re-install:

```
dpkg --get-selections
```

That can be stored to a text file and then later pushed into dpkg with 'set-selections' in order to re-install those packages.

Those are just a few examples of some package management.  There's a ton of other ways to get the info you need as well - and without adding any other packages to the system to do the work (which I prefer).  You might find that you get more relevant results with some other packages, which I'm sure some will recommend.  

I would definitely say, have a look at the man pages for 'apt' and 'dpkg' as you can do a lot more than just installed new packages with those utilities!

---

### Post by jerrrys on 2012-10-17
Installed software will show up in /usr/share/applications with the exception of non GUI (terminal only) packages.

---

### Post by Frogs Hair on 2012-10-17
This command will generate an A to Z list of all installed packages in the home folder.```
sudo dpkg --get-selections > installed-software
```

History in the software center will display updates and officially installed packages.

---

### Post by Mopar1973Man on 2012-10-17
Another way is to install synaptic package manager.

```
sudo apt-get install synaptic
```

Then you GUI of all the installed apps and a bit friendlier for newbies.

---

### Post by Lars Noodén on 2012-10-17
> **Frogs Hair said:**
> This command will generate an A to Z list of all installed packages in the home folder.```
sudo dpkg --get-selections > installed-software
```

History in the software center will display updates and officially installed packages.

That will give a most thorough list including also what was once installed but has been since removed.  To get just the installed package the data from dpkg has to be refined a little.

```

dpkg --get-selections | awk '$2 == "install" { print $1 }'

```

---

### Post by mike acker on 2012-10-17
thanks gang; i'll try out these items!!  i've been trying this-and-that and i want to check to be sure my notes are ok

---

### Post by newb85 on 2012-10-17
Wow.  No one suggested using the pre-installed GUI?

The Software Center can be used, as well.  Clicking "Installed" at the top and "Show ??? Technical Items" at the bottom will show you what's installed.

That said, Synaptic can be much more helpful, as Mopar1973Man pointed out.

---

