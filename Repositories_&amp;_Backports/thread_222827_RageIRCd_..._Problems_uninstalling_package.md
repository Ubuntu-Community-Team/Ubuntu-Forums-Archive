---
title: "RageIRCd ... Problems uninstalling package"
date: 2006-07-25
forum: Repositories &amp; Backports
---

### Post by DarkHorizon on 2006-07-25
Hey all,

I was a problem removing a package which half-failed to install in the first place. Here is the output:

[FONT="Lucida Console"]root@zeus:~# apt-get remove -y rageircd
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  rageircd
0 upgraded, 0 newly installed, 1 to remove and 96 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 1544kB disk space will be freed.
(Reading database ... 79209 files and directories currently installed.)
Removing rageircd ...
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "stop" failed.
dpkg: error processing rageircd (--remove):
 subprocess pre-removal script returned error exit status 1
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 rageircd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@zeus:~#
[/FONT]

After editing [FONT="Lucida Console"]/etc/rageircd/rageircd.conf[/FONT] ServerInfo block "name" variable to my system's hostname, I was able to uninstall the application by using the same command as above.

I don't know if this will be useful to anyone, but just in case... this is the fix!

---

### Post by accludetuner on 2007-04-23
thanks, this worked for me.  It was causing all kinds of other apps to fail durring install/uninstall and it is good to finally be rid of this issue ;)

---

### Post by hard2hack on 2007-06-27
Thank You So Much!!

---

