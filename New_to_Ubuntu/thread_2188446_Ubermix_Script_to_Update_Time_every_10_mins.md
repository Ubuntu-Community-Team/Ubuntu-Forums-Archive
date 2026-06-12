---
title: "Ubermix Script to Update Time every 10 mins"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by sushidot on 2013-11-17
Hello-

I am helping with a school project where we are trying to get a bunch of old laptops refurbished and running ubermix.

Was wondering if someone could help me or point me to the right resource for writing a simple script that will update the 
time on the machine every 10 minutes, as many of these machines have bad bios batteries.

Thanks.

---

### Post by SeijiSensei on 2013-11-17
I don't know what "ubermix" is, so my answer applies to standard Ubuntu installations.

One method is to run a script from /etc/crontab or /var/spool/cron/root that executes ntpdate periodically like this:

```

#!/bin/bash

ntpdate 0.ubuntu.pool.ntp.org
hwclock --systohc


```

Run ntpdate from the command prompt with sudo to make sure it can reach the NTP server.  The hwclock command writes the current system time to the compter's hardware clock.  You might consider running the Network Time Protocol daemon, ntpd, on a reliable local server that has Internet access.  Then that server can provide a central time source for your network.

On this lubuntu 13.10 machine with a vanilla installation, ntpd was running by default.  If you get the "socket in use" error when running ntpdate, that indicates ntpd is running.  Run "sudo grep ntpd /var/log/syslog" to see what it reports.  That's the other alternative to the script above.  The NTP server list is in /etc/ntp.conf.  Usually they are [0-3].ubuntu.pool.ntp.org.  In that case you don't need to do anything special to synchronize time, but I'd run the hwclock command periodically to update the hardware clock.  If the battery is entirely dead, it will obviously fail, but it's worth trying.

---

