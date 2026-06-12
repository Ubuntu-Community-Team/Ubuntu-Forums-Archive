---
title: "java page on apache web server not working"
date: 2009-09-12
forum: Programming Talk
---

### Post by magic_din on 2009-09-12
I have installed the apache2 web server, tomcat6, java and mod_jk . I have mapped the jsp page to the tomcat server. Using the following values for workers.properties: 
worker.list=ajp13_worker
worker.ajp13_worker.port=8009
worker.ajp13_worker.host=localhost
worker.ajp13_worker.type=ajp13
worker.ajp13_worker.lbfactor=1
worker.loadbalancer.type=lb
worker.loadbalancer.balance_workers=ajp13_worker
and uri map as :
/*.jsp=ajp13_worker

While in the logfile at apache logfile area [mod_jk.log] :

[Sat Sep 12 08:57:00 2009] [3288:2764633952] [debug] jk_map_read_property::jk_map.c (492): Adding property '/*.jsp' with value 'ajp13_worker' to map.
....
....
....
[Sat Sep 12 13:53:44 2009] [8204:2764633952] [debug] jk_map_to_storage::mod_jk.c (3195): missing uri map for 127.0.1.1:/index.jsp


Can anyone just me why I am getting the missing uri map while using the urimap I have programmed .jsp pages to go to tomcat and be handled by tomcat6.

---

