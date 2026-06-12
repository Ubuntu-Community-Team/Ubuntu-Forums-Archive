---
title: "kicked me out into &quot;low graphics mode&quot;"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by RotorRick on 2011-10-19
5 year old laptop, ubuntu 10.04 LTS

Yesterday i came back to the computer only to see a message saying "operating in low graphics mode", and some options (restart, low graphics...that sort of thing). This morning I woke to the same thing. So I did a complete restart/reboot, and it's running normally right now (I'm typing this from the same computer).

I suspect it's hardware that's the issue, but I don't know much about that. 
Help! I dunno if my laptop could be saved/fixed, or whether the whole thing is toast!

Any ideas?

---

### Post by TeoBigusGeekus on 2011-10-19
When was the last time you had your laptop cleaned from dust?

---

### Post by 2F4U on 2011-10-19
Maybe a look into the system log /var/log/messages gives more information about what happened. Try to find the date when the problem happened.

---

### Post by RotorRick on 2011-10-19
> Oct 18 15:28:02 rick-laptop kernel: [   23.931465] sd 2:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Oct 18 15:28:02 rick-laptop kernel: [   23.932052] sd 2:0:0:0: [sdb] Attached SCSI disk
Oct 18 15:28:03 rick-laptop kernel: [   23.995259] ses 2:0:0:1: Attached Enclosure device
Oct 19 00:14:42 rick-laptop pulseaudio[1458]: ratelimit.c: 540 events suppressed
Oct 19 00:37:54 rick-laptop pulseaudio[1458]: ratelimit.c: 525 events suppressed
Oct 19 00:42:52 rick-laptop pulseaudio[1458]: ratelimit.c: 500 events suppressed
Oct 19 01:51:14 rick-laptop pulseaudio[1458]: ratelimit.c: 199 events suppressed
Oct 19 06:04:45 rick-laptop pulseaudio[1458]: ratelimit.c: 86 events suppressed
Oct 19 06:05:47 rick-laptop pulseaudio[1458]: ratelimit.c: 86 events suppressed
Oct 19 06:08:24 rick-laptop pulseaudio[1458]: ratelimit.c: 87 events suppressed
Oct 19 06:09:41 rick-laptop pulseaudio[1458]: ratelimit.c: 568 events suppressed
Oct 19 06:28:53 rick-laptop pulseaudio[17338]: pid.c: Stale PID file, overwriting.
Oct 19 06:28:54 rick-laptop pulseaudio[17338]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-agjky1tOeQ: Connection refused
Oct 19 06:28:56 rick-laptop bonobo-activation-server (rick-17359): could not associate with desktop session: Failed to connect to socket /tmp/dbus-agjky1tOeQ: Connection refused
Oct 19 07:04:09 rick-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="792" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Oct 19 08:35:52 rick-laptop kernel: Kernel logging (proc) stopped.
Oct 19 08:37:22 rick-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.

Does this help??

---

### Post by RotorRick on 2011-10-20
Hmm, things seem to be back to normal now. Two possibilities:

1)  it might have been that temporary bug from the update discussed this week, and I've updated it since then, so maybe the bug was overwritten with better code? Fixed anyway.

2)  I switched my "screensaver preferences" to "blank screen", after an experiment with the "Matrix" screensaver...which I love, but not so much that I want to risk instability. I suspect perhaps my laptop might strain to render that fancier screensaver, if it's already doing many tasks...either the Ram isn't enough, or maybe it starts to overheat the vid card? I dunno.

So while I have no idea which one, I suspect that one of those two conditions was the cause. It appears like things are nice and stable again, 

Thanks to all the developers of Ubuntu and Linux!

---

