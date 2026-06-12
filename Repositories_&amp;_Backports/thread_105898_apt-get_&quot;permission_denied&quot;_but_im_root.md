---
title: "apt-get &quot;permission denied&quot; but im root"
date: 2005-12-19
forum: Repositories &amp; Backports
---

### Post by herot on 2005-12-19
why would i get this error
```

Setting up netkit-inetd (0.10-10.1ubuntu2) ...
/var/lib/dpkg/info/netkit-inetd.postinst: line 41: /etc/init.d/inetd: Permission denied
dpkg: error processing netkit-inetd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netkit-inetd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@example:~ #

```

---

### Post by earobinson on 2005-12-19
could you post all the output (starting form the command being entered?

are you runing synaptic or something else at the same time (only one program may use apt-get at a time.

---

### Post by herot on 2005-12-19
ok here is total output from fresh login:

```

root@example:~ # apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security Release [19.6kB]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Get:3 http://au.archive.ubuntu.com breezy Release.gpg [189B]
Get:4 http://au.archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://au.archive.ubuntu.com breezy Release
Hit http://au.archive.ubuntu.com breezy-updates Release
Hit http://au.archive.ubuntu.com breezy/main Packages
Hit http://au.archive.ubuntu.com breezy/restricted Packages
Hit http://au.archive.ubuntu.com breezy/main Sources
Hit http://au.archive.ubuntu.com breezy/restricted Sources
Hit http://au.archive.ubuntu.com breezy/universe Packages
Hit http://au.archive.ubuntu.com breezy/universe Sources
Hit http://au.archive.ubuntu.com breezy-updates/main Packages
Hit http://au.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://au.archive.ubuntu.com breezy-updates/main Sources
Hit http://au.archive.ubuntu.com breezy-updates/restricted Sources
Fetched 19.8kB in 12s (1625B/s)
Reading package lists... Done
root@example:~ # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up netkit-inetd (0.10-10.1ubuntu2) ...
/var/lib/dpkg/info/netkit-inetd.postinst: line 41: /etc/init.d/inetd: Permission denied
dpkg: error processing netkit-inetd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netkit-inetd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@example:~ #

```

and no, im not running synaptic... this is straight from terminal

---

### Post by herot on 2006-01-20
hmmmm i guess they have forgotten me...

(i did a reinstall to fix it, but i would still like to know what happened or what i could have done to fix it without a reinstall...)

---

### Post by hillbilly on 2006-01-20
Iam not sure. Is this because your inetd daemon is running while you are trying to install the netkit-inetd ? Maybe if you could download the package onto your system. stop inetd and then install the program it might work.
Not sure how you can do this through synaptic though. 
Just clutching at straws here bud !!

---

### Post by aysiu on 2006-01-20
[QUOTE=herot]
and no, im not running synaptic... this is straight from terminal[/QUOTE] That wasn't the question. The question was whether or not you had Synaptic open *separately* while you're running all this stuff (what you're posting) in a terminal.

My guess is that you don't, though, since you were able to apt-get update.

By the way, why are you using a root terminal instead of just doing ```
sudo apt-get update
```?

---

