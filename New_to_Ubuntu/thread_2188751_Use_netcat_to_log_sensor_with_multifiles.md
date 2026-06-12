---
title: "Use netcat to log sensor with multifiles"
date: 2013-11-18
forum: New to Ubuntu
---

### Post by uxv2712 on 2013-11-18
Hi all,

In my application I have a sensor that sent data by udp, and I want to log these data. I don't want a big log file, but some "small" files of X Mb. 
The idea is to have a script that listens the udp port,  logs the first X Mb, incrementes the next file's name with current time and logs the next X Mb, and so on.

Does anyone has the experience of netcat such use ?

Thanks for your help

---

### Post by TheFu on 2013-11-18
netcat doesn't support any security, so I will never use it.

You can let **logrotate** manage log file sizes too. Much easier than writing a special tool just for that.

If you want to log data and know exactly how large the data will be, use RRD files or use SNMP and let another server remotely monitor the information.

For non-trivial RRD examples, check out SysUsage or the CPAN module.

I'd highly recommend the logrotate solution. It is fairly easy ... should be under 5 minutes to learn, understand and implement.

---

### Post by tgalati4 on 2013-11-18
For local (LAN) use, you can use *logger* with the appropriate *netcat* to put diagnostics into your syslog.  This gives you timestamps and log rotation.  Grep on your netcat marker to extract the data.  *Logger* can also redirect to another machine's syslog, but as *TheFu* pointed out, it's lack of security makes it only appropriate within a trusted LAN.

---

