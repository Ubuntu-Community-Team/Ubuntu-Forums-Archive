---
title: "Syslog-ng using Ubuntu 15.04"
date: 2016-09-23
forum: New to Ubuntu
---

### Post by johndoeph on 2016-09-23
Hi,
I'm a newbie in using an Ubuntu 15.04 OS.

I was asked to install a syslog-ng to receive logs from other server.

So, As of now, I have already installed the syslog-ng and it's working perfectly.

My problem is I can't get exact or legit way to receive logs from other server.

I edited the etc/syslog-ng/syslog-ng.conf

Here's the added content:
sources s_dts { udp(ip(SERVER IP HERE) port(514)); };

destination d_dts { file("/var/log/dts.log"); };

log { source(s_dts); destination(d_dts); };

But after saving the file, and running service syslog-ng restart, I'm always getting this error:

Job for syslog-ng.service failed. See "systemctl status syslog-ng.service" and "journalctl -xe" for details.

I hope you could help me with this issue.

Regards,
John

---

### Post by ajgreeny on 2016-09-23
15.04 is no longer supported and you will therefore probably not be able to get any really useful help here as the repos are now moved to an end-of-life archive and no longer updated.  Your security, particularly for a server, is therefore at risk.

You should upgrade to a supported version which at present is either 16.04, or possibly downgrading to 14.04, depending on the hardware you are running.  Foe either of those I recommend a clean install after backing up all your personal files.

---

