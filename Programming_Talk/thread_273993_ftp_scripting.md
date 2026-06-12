---
title: "ftp scripting"
date: 2006-10-09
forum: Programming Talk
---

### Post by dyol on 2006-10-09
hi guys as a newbie,to linux and scripting may u help,with ftp scripting- i nid to come up with script that measure the time it takes to transfer files between server and clients-iam using proftpd gproftpd-but i dont know how-help

---

### Post by amo-ej1 on 2006-10-09
```

time wget ftp://127.0.0.1/file

```

man time 
-> time measures how long it takes to execute the following commant

man wget
-> wget behaves like a http/ftp/https client which allows you to get a file from a remote server.

---

### Post by dyol on 2006-10-10
thanks amoe-ihave made the script to log into the server by adding username/paswwd and do the copying of files and it giving me output.So now this script i want it to run for say a day or for a certain period then i will take the output and make a graph-iam testing file tranfer between Ethernet and PLC-so how will i make this run for day copying the same file and sending the stats to a file so that i can graph the output of how it behaved during the day.

---

