---
title: "Disable reverse DNS in Apache"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by cullingworth on 2012-11-06
I want to disable reverse DNS in apache2.
I have done the folowing steps.

In apache2/apache2.conf file ,HostnameLookups is set as OFF

Tcpdump session confirmed thatApache was doing double reverse lookups even though the HostnameLookupsdirective was clearly turned off.

No hostnames insites-available/*
still the same problem.
version of apache is

dpkg -l | grep apache2
ii apache2-mpm-prefork 2.2.16-6+squeeze4 Apache HTTP Server - traditional non-threaded model
ii apache2-utils 2.2.16-6+squeeze4 utility programs for webservers
ii apache2.2-bin 2.2.16-6+squeeze4 Apache HTTP Server common binary files
ii apache2.2-common 2.2.16-6+squeeze4 Apache HTTP Server common files

apache2 -l
Compiled in modules:
core.c
mod_log_config.c
mod_logio.c
prefork.c
http_core.c
mod_so.c

Regardless of the setting, when mod_authz_host is used for controlling access by hostname, a double reverse lookup will be performed. I have disabled mod-authz_host still the same problem.
I have compiled with -DMINIMAL_DNS option also. still the same.
please help....

---

