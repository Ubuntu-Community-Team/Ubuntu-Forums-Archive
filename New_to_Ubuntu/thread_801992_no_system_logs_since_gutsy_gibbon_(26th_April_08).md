---
title: "no system logs since gutsy gibbon (26th April 08)"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by philphil on 2008-05-21
When I go to System-->Administration-->System log and click on a log file 'syslog', 'user.log', 'daemon.log' ...etc...I can see the last entry that was made in each of the files was on the 26th April 08, the day I installed Hardy Heron, I have nothing since then.  

Have the names of the log files changed in Hardy Heron and my System Log Manager hasn't been updated to reflect that?  If so, how do I do it? If not, what's the problem???

---

### Post by randallecook on 2008-05-21
You might try looking at the log files directly from the filesystem. Open a terminal window, enter 'cd /var/log', then do 'ls -oh', and see what is there. Look for modification dates, file sizes, etc. and make sure they look reasonable.

To view the last few lines of a file, use tail: 'tail /var/log/messages'. You might need to be root to view some of the logs, so you can preface all commands with sudo to give yourself the proper privileges.

It is also possible that Hardy created a new set of log files in a new location, which the GUI viewer does not know about. A command like 'find /var -name messages' might help. They've got to be there somewhere.

Randall

---

### Post by philphil on 2008-05-21
Thanks for your reply Randall.

```

phil@phil-laptop:/var/log$ sudo find /var -name messages
/var/log/messages

```

not much to report there.

```

phil@phil-laptop:/var/log$ tail /var/log/messages
Apr 26 05:59:06 phil-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Apr 26 05:59:17 phil-laptop kernel: [92471.820000] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.2 DST=192.168.0.255 LEN=263 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=243
Apr 26 05:59:17 phil-laptop kernel: [92471.820000] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.2 DST=192.168.0.255 LEN=240 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=220
Apr 26 05:59:42 phil-laptop kernel: [92497.092000] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.2 DST=192.168.0.255 LEN=263 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=243
Apr 26 05:59:42 phil-laptop kernel: [92497.092000] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.2 DST=192.168.0.255 LEN=263 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=243
Apr 26 05:59:51 phil-laptop kernel: [92505.964000] ip6_tables: (C) 2000-2006 Netfilter Core Team
Apr 26 05:59:53 phil-laptop kernel: [92507.376000] nfsd: last server has exited
Apr 26 05:59:53 phil-laptop kernel: [92507.376000] nfsd: unexporting all filesystems
Apr 26 05:59:53 phil-laptop kernel: [92507.380000] RPC: failed to contact local rpcbind server (errno 5).
Apr 26 05:59:53 phil-laptop exiting on signal 15

```

so the file definitely hasn't been updated since then.

Doing an 'ls -oh --sort=time' shows me that some files in that directory have been updated but none of the ones I'm looking for like syslog...

Any other suggestions?

---

### Post by randallecook on 2008-05-21
Log files are modified often, so perhaps searching across your entire filesystem for files modified since booting would reveal their location. Yes, such a search might take a while, but really only a few minutes on modern hardware.

Randall

---

