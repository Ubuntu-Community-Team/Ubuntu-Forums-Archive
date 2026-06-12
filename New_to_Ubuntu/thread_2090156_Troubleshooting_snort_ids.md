---
title: "Troubleshooting snort ids"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by termvrl on 2012-12-01
hi all,

i have install snort ids on ubuntu 10.04, running on virtual box.
i follow this this guide [www.snort.org/assets/158/snortinstallguide293.pdf]("http://ubuntuforums.org/www.snort.org/assets/158/snortinstallguide293.pdf")
my problem is i have no data on my snortreport.

i have done a few troubleshooting:-
1) I able to get "Commencing packet processing" on my snort. i concluded that my snort is running well.
2)  I have done, tcpdump on my sniffing interface (eth1) and i managed to  sniff all traffic on my LAN. There is no porblem with network  card/sniffing interface.

i think my problem is on barnyard, it cannot forward the log to database.
In  my snort.conf, i already put "output unified2: filename snort.u2, limit  128". and i managed to get file snort.u2.xxxx in my /var/log/snort. but  when i vi the file, its empty.
i dont know how to troubleshoot barnyard2.

Attach is my screenshot.
Need help. Thanks.

---

