---
title: "apt-get upgrade errors (12.04.1)"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by rakemm on 2012-10-06
Hi,
When i run an apt-get upgrade I can see it go through the process of downloading and installing files but then the screen fills with:

FATAL: Module index: unexpected error: EOF
Try re-running depmod.

Any idea what the issue is?
This is on an Ubuntu 12.0.4.1 server edition running in XenServer.

If i reboot after this finishes the VM fails to start with errors like:

modprod : FATALL Module index: unexpected error:EOF
tey re-running depmod

An error occured mounting /boot
mount: unknown filesystem type 'ext2'
mountall: mount /boot [604] terminated with status 32
mountall: Filesystem could not be mounted: /boot
Press S to skip mounting or M for manual recovery

Cheers.

---

### Post by DuckHook on 2012-10-07
Wow. If you are running a XenServer VM, I suspect that your problem is way beyond the scope of the *Absolute Beginner* forum. I would suggest posting on the *Server Platform* forum. You can also try the Citrix support forum.

---

### Post by TanHannah on 2012-10-07
Hi. I upgraded my Ubuntu 10 to Ubuntu 12.04, while it was installing & unpackaging the downloads, the electricity shut down and my pc too.. When i opened it again, the user accounts won't show and it won't stop load.. When i pressed the escape button there was a fail process, "Ubuntu user accounts was not found" what should I do?? It won't open & it kept on loading.. Please answer.. Thank you :)

---

### Post by DuckHook on 2012-10-07
Ouch. An update is already critical enough, but a full system upgrade is a super-critical process that cannot survive a power outage. Did you back up all of your critical data before upgrading? If so, then you can install 12.04 from scratch and reload all of your data. It may take some time to replace all of your old apps, but this is far and away the simplest solution rather than trying to hunt down all the corrupted files and configurations resulting from the power outage. If you did not back up your data before upgrading, then I'm afraid that I don't have the knowledge to help you. Perhaps the gurus in this forum have some better insights?

---

### Post by TanHannah on 2012-10-07
It says:

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start S25bluetooth
* Stopping Start this job to wait until portmap is started or fails to s[OK]
* (the * here is color red) PulseAudio configured for per-user sessions
* Starting NSM status monitor
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service S90binfmt-support start
* Starting Start this job to wait until portmap is started or falls to s[OK]
* Stopping Start this job to wait until portmap is started or falls to s[OK]
initctl: Unknown job: S90binfmt-support

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start S90binfmt-support
* Starting NSM status monitor [OK]
* Starting Start this job to wait until portmap is started or fails to s[OK]
* Starting Start this job to wait until portmap is started or fails to s[OK]
* Starting NSM status monitor [OK]
* Starting NSM status monitor [fail]
* Stopping NSM status monitor [OK]
* Starting anac(h)ronistic cron [OK]
* Stopping anac(h)ronistic cron [OK]
* Checking battery state [OK]
* Stopping System V runlevel compatibility [OK]


What's the meaning of this?? Please help me. T__T

---

