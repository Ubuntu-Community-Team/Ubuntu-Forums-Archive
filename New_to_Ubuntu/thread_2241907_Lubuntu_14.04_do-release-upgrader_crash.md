---
title: "Lubuntu 14.04 do-release-upgrader crash"
date: 2014-08-29
forum: New to Ubuntu
---

### Post by wimpy2 on 2014-08-29
On startup I got a message "Sorry, Ubuntu 14.04 has experienced an internal error." 
 The "Details" included
> 
Package
ubuntu-release-upgrade-core 1:0.220.4
ProblemType
Crash
Title
do-release-upgrade crashed with System Error :E-Sub-process /usr/bin/dpkg returned an errorcode (1)
I would be grateful for any help in obtaing a "fix" for this.
Update: I ran Synaptic to see if there was a problem with the upgrade package . There wasn't but on exit I was warned that there were marked packages to uninstall. This was news to me, I hadn't marked anything. The details  refered to a debian themes package so I told it to go ahead and remove it. I did a "sudo apt-get update" and that seemed to work OK. I ran the software updater, which found a number of packages needing updates. After these updates, I rebooted and this time there are no internal error messaged and everything seems to be fine. I'll mark this as "Solved".

---

