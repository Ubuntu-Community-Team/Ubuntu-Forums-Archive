---
title: "Crash Log?"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by PlayLoud on 2012-09-08
I am running Ubuntu 12.04. The computer is a new Core i7 3770k running at 4.5GHz.

On occasion, my computer will seem to lock up (no signal to monitor, no power to mouse/keyboard). If I power cycle the computer, everything seems to work again without trouble. The computer is running Folding@home 24/7. Usually the only way I even notice it has frozen up, is noticing a dip in my Folding@home score.

I have tested the system for stability with the overclock, running MPrime for 24 hours (and also the Intel Burn Test for about an hour when I had Windows installed on here).

The only reason I can think of for this is the ambient temp. This has only happened when it gets to about 85F in my room. While the temps on the CPU haven't been a problem (maxing out at low 80's C, even in the heat), I suspect that may be part of the problem.

I am not a Linux Guru (I only use it for Folding@home and Samba), and was wondering if there is some sort of crash log I can run/check to get some more information on the lockup.

Thanks,
PlayLoud

---

### Post by sandyd on 2012-09-08
Look in these files (and the ones that are gziped - i.e. dmesg.1.gz)

/var/log/dmesg
/var/log/kern.log
/var/log/syslog

---

### Post by PlayLoud on 2012-09-08
Thank you for your reply Sandyd.

My last folding@home workunit received credit at 7am, meaning it was probably finished at about 3:30am to 6:30am. I restarted the system 6:40pm.

This is the only log that I can find an entry in the time frame the crash would have happened. Unfortunately, I don't know what it means.

syslog.1
> [SIZE=1][COLOR=Red]Sep  8 00:17:57 Skynet kernel: [651115.055253] usb 5-1.1.2.1: USB disconnect, device number 66
Sep  8 00:17:58 Skynet kernel: [651115.502198] usb 5-1.1.2.4: USB disconnect, device number 67
Sep  8 00:18:01 Skynet kernel: [651118.549846] xhci_hcd 0000:02:00.0: WARN Event TRB for slot 1 ep 0 with no TDs queued?
Sep  8 01:17:01 Skynet CRON[15411]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  8 02:17:01 Skynet CRON[15443]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  8 03:17:01 Skynet CRON[15475]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  8 04:17:01 Skynet CRON[15520]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  8 05:17:01 Skynet CRON[15552]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)[/COLOR]
[COLOR=Blue]Sep  8 18:40:04 Skynet kernel: imklog 5.8.6, log source = /proc/kmsg started.
Sep  8 18:40:04 Skynet rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="900" x-info="http://www.rsyslog.com"] start
Sep  8 18:40:04 Skynet rsyslogd: rsyslogd's groupid changed to 103
Sep  8 18:40:04 Skynet rsyslogd: rsyslogd's userid changed to 101
Sep  8 18:40:04 Skynet rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Sep  8 18:40:04 Skynet kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  8 18:40:04 Skynet kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  8 18:40:04 Skynet kernel: [    0.000000] Linux version 3.2.0-29-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 (Ubuntu 3.2.0-29.46-generic 3.2.24)
Sep  8 18:40:04 Skynet kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=442f5366-e9be-46dd-aae1-819ab1d9d05e ro quiet splash vt.handoff=7[/COLOR][/SIZE]The kern.log has nothing in this time frame, and the dmesg has no time stamp, so I don't know what to look for.

---

### Post by HangingClowns on 2012-10-28
> **PlayLoud said:**
> Thank you for your reply Sandyd.

My last folding@home workunit received credit at 7am, meaning it was probably finished at about 3:30am to 6:30am. I restarted the system 6:40pm.

This is the only log that I can find an entry in the time frame the crash would have happened. Unfortunately, I don't know what it means.

syslog.1
The kern.log has nothing in this time frame, and the dmesg has no time stamp, so I don't know what to look for.

I'm having the same issue. The dmesg has no timestamp, and I just see crons running until around midnight, then no logs. You ever figure out what the problem is? Machine is on, actually, for us, but if I press the restart button, it will restart and everything is normal.

I'm just running an nginx server, with about 2 vms started by vagrant.

---

