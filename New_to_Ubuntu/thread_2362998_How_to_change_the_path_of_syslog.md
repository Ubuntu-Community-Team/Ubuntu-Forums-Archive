---
title: "How to change the path of syslog ?"
date: 2017-06-05
forum: New to Ubuntu
---

### Post by amsats on 2017-06-05
I want to change the path of syslog from /var/log to opt.
I have made changes in the configuration file and then restarted the syslog service still it is not working.

---

### Post by TheFu on 2017-06-05
I have never heard of anyone doing this in my decades running and admining Unix systems. The filesystem hierarchy standards spell out that /var/log/ is where system log files are to be placed.  Numerous processes will expect this. [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/var.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/var.html)
 
There are alternatives, however, if you just want log files written to different storage, provided they *appear* to still be located in /var/log/.

a) Assume you make a directory /opt/log.  Now boot a liveCD and move all content from /var/log to /opt/log.  Next create a symbolic link from /var/log to /opt/log.  Reboot into the normal OS. Be happy.  This is a hack solution.

b) You could mount additional storage directly onto /var/log/ after moving the files as in 'a' above. This is a little better solution.

c) Use rsyslog or the built-in systemd remote logging capabilities to send the log files to another system. I don't think this will work on the same box. I have never setup remote logging, but thousands of enterprises work this way, so it is definitely ready to be used.

I'm assuming the reason to do this is purely due to storage considerations. That might not be true.

---

### Post by amsats on 2017-06-05
Thanks

---

