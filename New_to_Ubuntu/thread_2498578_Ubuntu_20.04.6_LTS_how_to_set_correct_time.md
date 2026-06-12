---
title: "Ubuntu 20.04.6 LTS: how to set correct time ?"
date: 2024-06-20
forum: New to Ubuntu
---

### Post by maketopsite on 2024-06-20
```
maketopsite@maketopsite:~$ timedatectl
               Local time: Thu 2024-06-20 08:39:02 CEST
           **Universal time: Thu 2024-06-20** **06:39:02 UTC** 
                 RTC time: Thu 2024-06-20 06:39:02     
                Time zone: Europe/Vienna (CEST, +0200)  
System clock synchronized: no                           
              NTP service: n/a                          
          RTC in local TZ: no                           
maketopsite@maketopsite:~$ 

```
Universal time should be: Thu 2024-06-20 08:39:02 UTC

```
# timedatectl set-ntp yes
Failed to set ntp: NTP not supported
# 

```

```
# systemctl status ntp.service
&#9679; ntp.service - Network Time Service
     Loaded: loaded (/lib/systemd/system/ntp.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2024-06-20 06:06:19 CEST; 2h 23min ago
       Docs: man:ntpd(8)
    Process: 9028 ExecStart=/usr/lib/ntp/ntp-systemd-wrapper (code=exited, status=0/SUCCESS)
   Main PID: 9064 (ntpd)
      Tasks: 2 (limit: 9228)
     Memory: 2.6M
     CGroup: /system.slice/ntp.service
             &#9492;&#9472;9064 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 105:110

Jun 20 08:27:32 maketopsite ntpd[9064]: Soliciting pool server XXXX
Jun 20 08:27:42 maketopsite ntpd[9064]: Soliciting pool server XXXX
Jun 20 08:28:16 maketopsite ntpd[9064]: Soliciting pool server XXXX
Jun 20 08:28:22 maketopsite ntpd[9064]: Soliciting pool server XXXX
Jun 20 08:28:31 maketopsite ntpd[9064]: Soliciting pool server XXXX
Jun 20 08:28:36 maketopsite ntpd[9064]: Soliciting pool server XXXX
Jun 20 08:28:49 maketopsite ntpd[9064]: Soliciting pool server XXXX
Jun 20 08:29:22 maketopsite ntpd[9064]: Soliciting pool server XXXX
Jun 20 08:29:28 maketopsite ntpd[9064]: Soliciting pool server XXXX
Jun 20 08:29:38 maketopsite ntpd[9064]: Soliciting pool server XXXX
```

---

### Post by TheFu on 2024-06-20
Set the TZ environment variable and /etc/timezone file correctly.

There are 2 places to set the time. For the GUI and for the full OS.  Both are dependent on the timezone system setting, TZ environment variable and locale settings.

20.04 time is when lots of things changed.  I remember that the default method introduced wasn't accurate enough for my needs and that RH had decided to use a different solution, so I implemented that - chrony - as a replacement for ntpd.

My notes on this are:

```
# Fix time sync stuff
sudo systemctl disable systemd-timesyncd.service
sudo systemctl mask systemd-timesyncd.service
sudoedit /etc/chrony/chrony.conf  # point at your time server. I run an internal time server here that gets the correct time from GPS signals.
sudo systemctl restart chrony
chronyc sources

# set the server timezone
$ echo "America/New_York" | sudo tee /etc/timezone
sudo timedatectl set-timezone "America/New_York"

```

Of course, YMMV. Use at your own risk.  My BIOS clocks always use UTC.

---

### Post by ActionParsnip on 2024-06-20
What is the output of
```

egrep -v '^$|^\#' /etc/chrony/chrony.conf

```

---

### Post by TheFu on 2024-06-20
> **ActionParsnip said:**
> What is the output of
```

egrep -v '^$|^\#' /etc/chrony/chrony.conf

```

Assuming you are asking me?

```
$ egrep -v '^$|^\#' /etc/chrony/chrony.conf
confdir /etc/chrony/conf.d
server 172.22.22.20           iburst 
sourcedir /run/chrony-dhcp
sourcedir /etc/chrony/sources.d
keyfile /etc/chrony/chrony.keys
driftfile /var/lib/chrony/chrony.drift
ntsdumpdir /var/lib/chrony
logdir /var/log/chrony
maxupdateskew 100.0
rtcsync
makestep 1 3
leapsectz right/UTC

```
I only clean up the "server" to point at my internal time server.  The default examples are fine, I think.
```
$ chronyc sources
MS Name/IP address         Stratum Poll Reach LastRx Last sample               
===============================================================================
^* istar                         3   6   377    19   -230ns[-3843ns] +/-   22ms
```
close enough.  230 nanosec is 0.0000230s. Definitely close enough for my needs.  My main goal is to have all the systems on the LAN have very close times, mainly for log timerstamps and troubleshooting needs.  My VPS systems are all sub-second matched with my internal LAN needs even without using the same GPS time source.

Oh - almost forgot.  istar's IP is 172.22.22.20.

---

### Post by maketopsite on 2024-07-20
solved - ntpd was blocked by firewall

---

