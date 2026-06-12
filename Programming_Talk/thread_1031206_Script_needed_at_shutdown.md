---
title: "Script needed at shutdown"
date: 2009-01-05
forum: Programming Talk
---

### Post by oygle on 2009-01-05
I would like to run a script at shutdown, to append the syslog, or even write the contents to a database, so that I can collect the firewall logs. I see from the syslogs, that any intrusions are recorded in several of the log files, and that there are also some archives in other .gz files. But, I just want to append the (firewall intrusion) logs for each day to a file.

Is there an easy script to do this, and how does the script get executed automatically, at shutdown ?

Oygle

---

### Post by ajmorris on 2009-01-05
> **oygle said:**
> I would like to run a script at shutdown, to append the syslog, or even write the contents to a database, so that I can collect the firewall logs. I see from the syslogs, that any intrusions are recorded in several of the log files, and that there are also some archives in other .gz files. But, I just want to append the (firewall intrusion) logs for each day to a file.

Is there an easy script to do this, and how does the script get executed automatically, at shutdown ?

Oygle

Hi there,
a simple bash script added to your shutdown runlevel should do the trick... i.e:
```
#!/bin/bash
cat "path to firewall intrusion log" >> "path to collection file"
```

then chmod a+x <script>
then place the script in /etc/init.d
and either use update-rc.d to place the symlink for this script in the runlevel 0 directory (the halt runlevel) or manually place a symlink in /etc/rc0.d to the script.


AJ

---

### Post by oygle on 2009-01-06
Thanks ajmorris. That will be what I need.

The firewall (firestarter) doesn't seem to create its own logs, it must just read either /var/log/kern.log or /var/log/messages or /var/log/syslog , to create the GUI display. For example in /var/log/syslog and entry may be:

> 
Jan  6 19:41:20 ***** kernel: [ 1405.862157] Inbound IN=ppp0 OUT= MAC= SRC=220.233.***.*** DST=220.233.***.*** LEN=60 TOS=0x00 PREC=0x00 TTL=60 ID=2774 DF PROTO=TCP SPT=4849 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 


(I have asterisked out part of the IP addresses above).

No doubt I have to add grep, something like ..

```
$ grep "IN=ppp0" /var/log/syslog
```

Hmm, but that goes back a few days, so I'm going to have duplicates.

This part of the entry ..

[ 1405.862157]

looks like a timestamp though, so as long as it is unique, I can check that for duplicates somehow.

Thanks,

Oygle

---

