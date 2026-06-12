---
title: "Updating from 'proposed'"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by Sleetstorm on 2013-04-03
Hey,
Im trying to use an update released by Launchpad to fix a bug I encountered.I have no idea if what I found is actually the fix or something else.And I don't understand the lingo that these launchpad guys are using either.

This is the bug [https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1073626](https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1073626)

This is what I found [https://launchpad.net/ubuntu/+source/xdiagnose/3.2.3](https://launchpad.net/ubuntu/+source/xdiagnose/3.2.3)

If anyone could fill me in on what it is that I'm supposed to be doing now it would be much appreciated.

---

### Post by ibjsb4 on 2013-04-03
Are you running quantal 12.10?  If so, to install xdiagnose 3.2.3 open a terminal and enter:

```
sudo apt-get update

sudo apt-get install xdiagnose
```

[http://packages.ubuntu.com/quantal-updates/xdiagnose](http://packages.ubuntu.com/quantal-updates/xdiagnose)

---

### Post by Sleetstorm on 2013-04-04
I run 12.10.
Xdiagnose is already installed. Do I need to deinstall it and then reinstall?

When I type sudo apt-get update I need to give my password then theres a lot of downloads.

When I then type sudo apt-get install xdiagnose it says illegal command.

---

### Post by schragge on 2013-04-04
You should enable the repository *quantal-proposed* as described at [uwiki]Testing/EnableProposed[/uwiki] (change *precise* to *quantal* in the commands shown on that page) and install a newer version of *xdiagnose* from there. If this doesn't help then just delete the file
*/usr/share/apport/apport-gpu-error-intel.py* and you won't be bothered with these error messages at least until the next regular update of the package which hopefully will fix the problem.

---

