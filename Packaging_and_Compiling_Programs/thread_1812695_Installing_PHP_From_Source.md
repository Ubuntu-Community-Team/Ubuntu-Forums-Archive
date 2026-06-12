---
title: "Installing PHP From Source"
date: 2011-07-26
forum: Packaging and Compiling Programs
---

### Post by waffleguy4 on 2011-07-26
Hi,

I am having problems with my current version of PHP 5.3.5 that is in the Ubuntu Repository, as is documented here: [https://bugs.php.net/bug.php?id=54676](https://bugs.php.net/bug.php?id=54676)

I would like to upgrade to the latest - PHP 5.6 - the source can be downloaded from here:
[http://www.php.net/downloads.php#v5](http://www.php.net/downloads.php#v5)

However I have very little experience compiling in Linux from source and am worried about messing up dependencies. I would really appreciate advice on how to compile it.

I am running Ubuntu 11.04. Thanks for all your help!!

---

### Post by fdrake on 2011-07-26
download, make executable and run with sudo:
i am assuming you want to use php on apache.
```
sudo ./apache_php.sh
```

---

### Post by waffleguy4 on 2011-07-26
fdrake, thanks for the script. however it does not install the latest version of php, it only installs the latest version that is in the Ubuntu Repository.

The version currently in the repository has a documented bug with the Soap client. I really need to use Soap for a project.

---

### Post by SevenMachines on 2011-07-26
Does the documented bug have a patch? You might be just as easy applying the fix to the repository version

---

### Post by waffleguy4 on 2011-07-26
I don't know if there is a patch or not, but I read from another person experiencing the same problem that the latest version of php from php.net has fixed the problem. So yea, it would be nice to update the repository but that's outside of my Linux knowledge.

---

### Post by SevenMachines on 2011-07-27
If theres a bug in the natty version it might be worth looking at the current bug list to see if its there on the [php bug list on launchpad ]("https://bugs.launchpad.net/ubuntu/+source/php5?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")
or reporting a new bug
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

You could build from source and do a local install of a new version so you have two versions installed, the repository version and the new version. Or, you could update the system version with the [new one from oneiric]("https://launchpad.net/ubuntu/+source/php5"), obviously dependencies would need to be updated manually too so it might be straightforward to download and use the newer version or it may be a bit of a pain depending. 

Why I ask about the patch/bug report is that its the best way to both verify the bug and fix it for everyone on natty. If you can provide a link or more details/a bug report I'm sure some php people will be happy to fix it up.

---

### Post by waffleguy4 on 2011-07-27
Thanks, I've made a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/817034](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/817034)

I know its possible to install other versions of PHP and I don't mind upgrading to the latest version from php.net or downgrading to an older version. I just need the SOAP protocol to work. 

Does anyone have instructions on how to compile php on your own and install/fix needed dependencies. This is the part that is outside my knowledge.

---

### Post by SevenMachines on 2011-07-28
Since the repository and new versions are close its probably fine just to get build dependencies with
> $ sudo apt-get build-dep php5Then as usual, for an install to local
> $ ./configure 
$ make
$ sudo make install #or checkinstall

---

