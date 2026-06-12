---
title: "[SOLVED] NIC settings - change from full to 1/2 duplex"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by nightwatch1954 on 2008-07-11
I'm having problems with my internet connection. My ISP ran diagnostics and tells me that my DSL speed, etc. is fine. They suggested that I change my NIC from full to 10 1/2 duplex. However, they had no one versed in linux who could tell me how to accomplish this. Any advice will be appreciated. 

Running Ubuntu 7.10 (newly upgraded) NIC is Realtek RTL-8139/8139C/8139C+ Driver 8139too

Browser was working fine before upgrade now pretty slow. Can't play Dark Orbit due to the browser lag which is tragic.

---

### Post by bab1 on 2008-07-11
In most modern installations half duplex is auto sensed.  I doubt this is the problem.  Run the command:
```
top
```
at the command line.   See what is using the most CPU cycles.

Cut and paste the "load average" stats (at top right).

---

### Post by nightwatch1954 on 2008-07-11
Ran the command and these are the load average stats

 ```
load average: 0.78, 0.82, 0.57
```

---

### Post by nightwatch1954 on 2008-07-14
The more I fiddled with it the more convinced I was that the problem was related to the Flash plugin. Anyway, I upgraded from 7.10 to 8.04 and that solved the problem. No more slow Firefox. :)

---

