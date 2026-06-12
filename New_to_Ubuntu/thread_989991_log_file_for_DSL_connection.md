---
title: "log file for DSL connection?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by tomcheng76 on 2008-11-22
Hi, i created a DSL connection (pppoe) in NetworkManager Applet 0.7.0.
which log file is used for storing the connection log?
I don't mind to install additional software package for the logging.

sudo plog showed nothing.
OS is Ubuntu 8.10 AMD64 ,thanks :)

---

### Post by lswb on 2008-11-22
If you don't have a separate ppp log configured "plog" will just show the last few pertinent lines from /var/log/syslog, which has just about everything in it. From a command line you can run

grep "pppd" /var/log/syslog 

to see what's currently logged. If you want more detailed info, check the appropriate file in /etc/ppp/peers for the DSL connection and make sure it has "debug" appearing on a line by itself somewhere.

What I like to do when debugging or testing a new ppp connection is open a separate terminal window and run "plog -f" or "tail -f /var/log/syslog" Then you can see the log entries appear as you try various things from another terminal or window.

---

### Post by tomcheng76 on 2008-11-22
thanks for your reply
[grep "pppd" /var/log/syslog] have what i wanted.

Btw, i cannot find a corresponding file for my DSL connection in /etc/ppp/peers.

When i was using [sudo pppoeconf] in Hardy, it had.

Now, none of the files in /etc/ppp/peers is storing my isp login name and password.

where is the new location ?

---

### Post by lswb on 2008-11-22
Network Manager probably keeps its own files separately, sorry but I'm not sure where that is.

Also when using authentication, the user/password info may be kept in /etc/ppp/chap-secrets or pap-secrets rather than directly in the peers file.

---

### Post by tomcheng76 on 2008-11-23
thanks lswb :-)

---

