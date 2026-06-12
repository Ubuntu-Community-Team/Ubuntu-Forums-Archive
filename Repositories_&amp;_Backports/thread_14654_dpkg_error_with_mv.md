---
title: "dpkg error with mv"
date: 2005-02-08
forum: Repositories &amp; Backports
---

### Post by ryanknapper on 2005-02-08
I certainly hope this hasn't been answered recently, as I searched quite a bit before asking.
After trying to use the latest ATI drivers (with which I have been unsuccessful), dpkg has stopped working.  As you can see in the following code, it passes erroneous options to *mv*, which then reports an error and aborts the entire process.  This happens within Synaptic as well as the command line.
Any assistance would be greatly appreciated.

> root@moose:/var/cache/apt/archives # dpkg --remove gdesklets-data
(Reading database ... 69999 files and directories currently installed.)
Removing gdesklets-data ...
mv: missing file argument
Try `mv --help' for more information.
dpkg: error processing gdesklets-data (--remove):
 subprocess pre-removal script returned error exit status 123
Errors were encountered while processing:
 gdesklets-data
root@moose:/var/cache/apt/archives # dpkg -i ./ubuntu-calendar_4.10_all.deb
mv: invalid option -- r
Try `mv --help' for more information.
dpkg: error processing ./ubuntu-calendar_4.10_all.deb (--install):
 subprocess rm cleanup returned error exit status 1
Errors were encountered while processing:
 ./ubuntu-calendar_4.10_all.deb
root@moose:/var/cache/apt/archives #


---

### Post by ryanknapper on 2005-02-08
Upon further testing, for installation *dpkg* is trying to pass the options **-rf /root/.Trash**.  Removal passes **-f /root/.Trash**.

---

### Post by ryanknapper on 2005-02-08
I also appear to be having issues when compiling.  Perhaps something has happened to my *mv* command?

> root@moose:/bin # mv --version
mv (coreutils) 5.0.91

[SIZE=1]Edit: Spelling[/SIZE]

---

