---
title: "System clock is off"
date: 2022-04-03
forum: New to Ubuntu
---

### Post by psychohermit on 2022-04-03
Greetings,

Newbie here trying to get the clock to synchronize.  Running ubuntu 20.04.3 LTS.

I have installed systemd.timesyncd. And opened outbound port 37 tcp and udp.

```

glenn@LinuxBox:~$ sudo systemctl status systemd-timesyncd
[sudo] password for glenn: 
&#9679; systemd-timesyncd.service - Network Time Synchronization
     Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; v>
     Active: active (running) since Sun 2022-04-03 03:58:42 PDT; 4h 24min ago
       Docs: man:systemd-timesyncd.service(8)
   Main PID: 4991 (systemd-timesyn)
     Status: "Idle."
      Tasks: 2 (limit: 6087)
     Memory: 1.3M
     CGroup: /system.slice/systemd-timesyncd.service
             &#9492;&#9472;4991 /lib/systemd/systemd-timesyncd

Apr 03 03:58:42 LinuxBox systemd[1]: Starting Network Time Synchronization...
Apr 03 03:58:42 LinuxBox systemd[1]: Started Network Time Synchronization.

```

```

glenn@LinuxBox:~$ timedatectl
               Local time: Sun 2022-04-03 08:26:39 PDT     
           Universal time: Sun 2022-04-03 15:26:39 UTC     
                 RTC time: Sun 2022-04-03 15:26:40         
                Time zone: America/Los_Angeles (PDT, -0700)
System clock synchronized: no                              
              NTP service: active                          
          RTC in local TZ: no                              

```

What's the trick to get the time to synchronize?  The man pages are less than helpful.

Thanks in advance,
--glenn

---

### Post by TheFu on 2022-04-03
Did you edit the timesyncd.conf file to tell it where to get official times from? Normally, you'd want at least 3 sources.
the man page for timesyncd.conf explains the different settings. I suspect only 2 lines need to be changed.

I found timesyncd not to work so well for my needs, so I purged it and replaced with chrony.  Chrony is the replacement for the old ntpd which has been used for 30+ yrs.  Since I've purged timesyncd, I don't have manpages for it easily available. Sorry.

Time is one of those things that should just work and be millisecond accurate, unlike how MS-Windows does it, which is only +-5min accurate.

---

### Post by psychohermit on 2022-04-03
I set NTP=ntp.canonical.com and restarted timesyncd.  No Joy.

Thanks,
--glenn

---

### Post by TheFu on 2022-04-03
Time sync requires some time, since changing the clock immediately isn't done.  It slowly skews to the correct time. Also, 1 source isn't sufficient.

I told you that I didn't use timesyncd due to issues and suggested an alternative which I know DOES work. Sorry if this isn't helpful.

---

### Post by psychohermit on 2022-04-04
Hi TheFu,

I installed chrony and it was unable to be set enabled.

There's no man page for chrony?

```

glenn@LinuxBox:~$ sudo systemctl enable chronyd
Failed to enable unit: Refusing to operate on alias name or linked unit file: chronyd.service

```

Thanks,
--glenn

---

### Post by TheFu on 2022-04-04
chronyd won't work if timesyncd is still there and enabled.  You can **mask** it or **purge** it, but it cannot be running.
Chrony has a client and a server.  Most users would only use the client, chronyc.

in the /etc/chrony/chrony.conf, ensure:
```
pool pool.ntp.com        iburst maxsources 4
pool 0.ubuntu.pool.ntp.org iburst maxsources 1
pool 1.ubuntu.pool.ntp.org iburst maxsources 1
pool 2.ubuntu.pool.ntp.org iburst maxsources 2
```
lines exist, replacing other other pool lines.
I don't remember any other changes needed for a pure client.  I actually run a chrony server on my LAN so that all the clients are synched against it. That makes troubleshooting issues much easier because the logs for all systems have matched times.

From a client:
```
$ chronyc sources
210 Number of sources = 1
MS Name/IP address         Stratum Poll Reach LastRx Last sample               
===============================================================================
^* romulus                       3   7   377    11    -13us[  -87us] +/-   33ms

```

From my server, romulus, 
```
$ chronyc sources
210 Number of sources = 5
MS Name/IP address         Stratum Poll Reach LastRx Last sample               
===============================================================================
^? algo145                       0  10     0     -     +0ns[   +0ns] +/-    0ns
^- 38.229.52.9                   2  10   377   929  -2992us[-3012us] +/-  131ms
^* 138.197.15.27                 2  10   377   558   -873us[ -894us] +/-   48ms
^+ 168.61.215.74                 3  10   377   239  -1220us[-1220us] +/-   48ms
^+ network190-139.c1d.net        2  10   377   838   +793us[ +773us] +/-   75ms

```

---

### Post by psychohermit on 2022-04-04
Thank you for turning me onto chrony.  It hooked right up and synchronized.

```

  glenn@LinuxBox:~$ sudo systemctl enable chronyd
[sudo] password for glenn: 
Failed to enable unit: Refusing to operate on alias name or linked unit file: chronyd.service

```

How do I ensure that it's running after a reboot. 
I shut down my laptop because hibernating would be wear on my SSD.

Thanks,
--glenn

---

### Post by TheFu on 2022-04-04
It is a proper systemd service, so treat it like every other service. Just be 100% certain that timesyncd is masked or purged, so they don't conflict.

---

### Post by psychohermit on 2022-04-04
Chronyc was not included in the chrony package.  Chronyd hooked up and synchronized my time.

I am unable to enable chronyd in systemctl.

```

glenn@LinuxBox:~$ sudo systemctl start chronyc
[sudo] password for glenn: 
Failed to start chronyc.service: Unit chronyc.service not found.
glenn@LinuxBox:~$ sudo systemctl enable chronyd
Failed to enable unit: Refusing to operate on alias name or linked unit file: chronyd.service

```

Thanks,
--glenn

---

### Post by TheFu on 2022-04-04
I use tab completion for services. It is _found_ and works here with the **systemctl start** command.

Pro Tip: Use tab completion 100% more often so trivial issues like this aren't a big deal.

You can always search for all the .service files on the system to get the name too, if tab completion doesn't work on a barebones server setup.

---

### Post by ActionParsnip on 2022-04-04
[https://opensource.com/article/20/6/time-date-systemd](https://opensource.com/article/20/6/time-date-systemd)

---

### Post by psychohermit on 2022-04-04
Got it, thanks for the assist.
--glenn

---

