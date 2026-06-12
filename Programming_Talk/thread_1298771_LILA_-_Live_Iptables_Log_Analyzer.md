---
title: "LILA - Live Iptables Log Analyzer"
date: 2009-10-23
forum: Programming Talk
---

### Post by Scandium on 2009-10-23
Hi,    When I was looking for a tool that analyzes iptables log files I couldn't find anything suitable for me. So I wrote a python script that does the job.    Now I'd like to have some feedback (questions, comments, bugs, wishes etc.). I'd be happy if you give it a try and tell me whether you like it or not.    You have to set up some things manually. You need a MySQL table for example. And if you want to have reverse DNS (can be disabled) it is greatly recommended to install pdnsd as a local dns (caching) server for better results. (easy setup). If you do, it will take some time (depending on the log size) to receive the hostnames. The tool saves the DNS hostnames, so next time an identical IP is found, the lookup will be instant.    All needed options can be configured in the config file or via command line parameter.  A feature overview and more detailed information is included in the tarball README and INSTALL file.    WWW: [https://sourceforge.net/projects/lilalog/](https://sourceforge.net/projects/lilalog/)    Thanks for your time.

---

