---
title: "iptables"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by larry Gaminde on 2008-07-03
I have been trying to add a log file to Iptables.rules I cannot get any log files to  log even if their right out of Iptables HowTo web pages

I have sites that are trying to relay mail through my server so I block there addresses. this works but I wanted to know if they were still trying, so I tried this

-A INPUT -s 216.129.0.0/16 -j LOG --log-prefix "Denied Site: " --log-level 7
-A INPUT -s 216.129.0.0/16 -j DROP
I used my own Ip address with no results, nothing I add from any book or web site works

I also put this log file in with no results.
-A LOGNDROP -p tcp -m limit --limit 5/min -j LOG --log-prefix "Denied TCP: " --log-level 7
-A LOGNDROP -p udp -m limit --limit 5/min -j LOG --log-prefix "Denied UDP: " --log-level 7
-A LOGNDROP -p icmp -m limit --limit 5/min -j LOG --log-prefix "Denied ICMP: " --log-level 7
-A LOGNDROP -j DROP

---

