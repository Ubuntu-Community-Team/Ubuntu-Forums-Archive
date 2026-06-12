---
title: "Ubuntu Shut Itself Down After Months Of Uptime"
date: 2016-05-22
forum: New to Ubuntu
---

### Post by kazz2 on 2016-05-22
14.04.4 LTS has been running steady but shut itself down, apparently, the other day. I've looked in dmesg and dmesg.0 for any signs and, while much of it's gibberish to me, I have some errors and failures. I believe they're ACPI-related, perhaps, IIRC from when I built it?

The last backup log on the system is dated 5/20 (today's 5/22). It runs in the early morning hours. And the log looks a-OK.

dmesg: [http://paste.ubuntu.com/16619008/](http://paste.ubuntu.com/16619008/)

dmesg.0: [http://paste.ubuntu.com/16619044/](http://paste.ubuntu.com/16619044/)

What else should I be looking at and how can I get date & time on my dmesg output?

Thanks!

---

### Post by him610 on 2016-05-22
Unexplained system shutdowns are sometimes caused by hardware problems, or possibly, a power outage. If your system were connected to a UPS, it might maintain its power through a brief power outage.
Several years ago, a friend of mine found his system had inexplicably shutdown. After some investigation, he discovered that a faulty CPU cooling fan allowed the CPU to overheat which in turn caused the system to shutdown.

---

### Post by kazz2 on 2016-05-22
Thank you for your reply. The system is connected to a UPS that has been in service for some time. Shouldn't there be a log of some kind that has date and time that at least stops logging so I can see exact date and time? Let alone a log that explains a shutdown were it orderly?

---

### Post by mastablasta on 2016-05-23
dmesg only shows errors on boot.

kernel.log, error.log... check the others out see what and when it was last logged. if it was poower outage and ups didn't kick in then it won't show much in logs. overheatign is porbabyl also not logged. at least not automatically.

---

### Post by mörgæs on 2016-05-23
Is it a desktop or server?

---

### Post by kazz2 on 2016-05-23
> **mastablasta said:**
> dmesg only shows errors on boot.

kernel.log, error.log... check the others out see what and when it was last logged. if it was poower outage and ups didn't kick in then it won't show much in logs. overheatign is porbabyl also not logged. at least not automatically.

Thanks for the insight.

kern.log is empty. kern.log.1 has nothing earlier than the 22nd. I'll assume kern.log.2.gz may have something in it but I don't know my tar commands well enough to spit that out here without looking it up.

syslog is empty. But syslog.1 has some activity from the 20th: [http://paste.ubuntu.com/16632018/](http://paste.ubuntu.com/16632018/)

I don't know what "[COLOR=#000000]org.freedesktop.systemd" is. But I don't use any desktop, just command line. I'm not certain it created any issues, however.

[/COLOR]The kills start with plexmediaserver so I'm willing to throw rocks at that. I need to check for an update anyway. That's pretty much the main function of the server. Is 'TERM' signal mean terminal or terminate?

Thanks!

> **mörgæs said:**
> Is it a desktop or server?

Server 14.04.4 LTS

---

### Post by kurt18947 on 2016-05-23
Something to check re the UPS. Try unplugging it with the PC running but no doing anything of consequence. The machine should continue to operate if the UPS is doing its job. The battery may be tired or there may be another hardware malfunction which prevents the UPS picking up the load. Any mains power interruption, no matter how brief would cause a reboot. I had one desktop UPS that would interrupt power and cause a reboot even though the mains power was fine.

---

### Post by mörgæs on 2016-05-23
Though it's impressive when a server runs month after month I don't think one should be aiming for that. Have you taken into account security updates which need a reboot?

---

