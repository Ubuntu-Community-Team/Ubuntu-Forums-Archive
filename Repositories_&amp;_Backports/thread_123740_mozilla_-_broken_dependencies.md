---
title: "mozilla - broken dependencies"
date: 2006-01-30
forum: Repositories &amp; Backports
---

### Post by towsonu2003 on 2006-01-30
this should be experienced by others as well, but I couldn't find the relevant post :(

problem: trying to install mozilla (metapackage). Broken dependencies. I actually need just the browser...

attachment: sources.list

errors (apt-get in simulation mode): 
```

username@ubuntu:~$ sudo apt-get -s install mozilla
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  **mozilla**: Depends: **mozilla-browser** (**= 2:1.7.12-0ubuntu2**) but 2:1.7.12-1ubuntu1 is to be installed
           Depends: **mozilla-mailnews** (**= 2:1.7.12-0ubuntu2**) but it is not going to be installed
           Depends: **mozilla-psm** (**= 2:1.7.12-0ubuntu2**) but 2:1.7.12-1ubuntu1 is to be installed
E: **Broken packages**
username@ubuntu:~$ sudo apt-get -s install mozilla-browser
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  mozilla-psm
The following NEW packages will be installed:
  **mozilla-browser**
0 upgraded, **1 newly installed**, 0 to remove and 0 not upgraded.
Inst mozilla-browser (2:1.7.12-1ubuntu1 Ubuntu:5.10/breezy-updates)
Conf mozilla-browser (2:1.7.12-1ubuntu1 Ubuntu:5.10/breezy-updates)

```
it looks like mozilla-browser will install but not the mozilla suite. so:

1. will I miss features / break anything (dependency hell? general apt-get breakage?) if I just install the mozilla-browser?
2. this looks like a bug. Should I file a bug for mozilla (or look for an existing one) and deal with it, or just install mozilla-browser and get over with it (which goes back to the first question)?

thanks.

---

### Post by towsonu2003 on 2006-01-30
okay I got this and this and this is **solved** (more of a workaround):
[http://ubuntuforums.org/showthread.php?t=114042&highlight=install+mozilla-browser](http://ubuntuforums.org/showthread.php?t=114042&highlight=install+mozilla-browser)
which links to
[https://launchpad.net/distros/ubuntu/+source/mozilla/+bug/6387](https://launchpad.net/distros/ubuntu/+source/mozilla/+bug/6387)

basically you add universe and multiverse to your breezy-update line in sources.list (detailed in second link above). 

it seems the correct keyword was: install mozilla-browser ;)

---

