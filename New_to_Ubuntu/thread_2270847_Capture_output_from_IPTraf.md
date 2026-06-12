---
title: "Capture output from IPTraf"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by Sharon_Probst on 2015-03-25
I would like to capture the output from iptraf to a text file.   Is there anyway to do it.   Copy and paste doesn't work, neither does cmd&>iptraf.txt

---

### Post by sandyd on 2015-03-25
Try to use the -L option to specify where the logs should go.

From man page:
```
-L logfile
 allows you to specify an alternate log file name.   The  default log  file  name  is  based  on  either  the  interface  selected (detailed  interface  statistics,  TCP/UDP  service  statistics, packet  size  breakdown),  or  the  instance of the facility (IP traffic monitor,  LAN  station  monitor).   If  a  path  is  not specified, the log file is placed in /var/log/iptraf
```

---

