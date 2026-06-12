---
title: "how to display syslog messages"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by dreamedboy21 on 2008-09-08
hello to all,

I am using ubuntu hardy and I am new on it.I want to send the logs to syslog server from C application,I have found some useful documents how to do it but I dont know how to display the log messages,how can i see the logs,where are they being kept, I will be grateful to have answer..

---

### Post by HalPomeranz on 2008-09-08
The file /etc/syslog.conf controls where your syslog messages will end up.  For example, suppose this file contained a configuration line like:

```

local0.info                    /var/log/mylogs

```

That would mean that all log messages sent to the "LOCAL0" facility that have priority "info" or higher would be put into the /var/log/mylogs file.  While the default syslog.conf file that comes with Ubuntu handles most of the common log facilities, you may have to add your own configuration lines to this file if you want the logs from your application to go to some special location.

Note that if you make changes to /etc/syslog.conf, you must tell the syslog daemon to reload its configuration files.  "sudo /etc/init.d/sysklogd reload" will do this for you.

Log files written by syslog are just simple text files.  So you can look at them using a command-line tool like "less" or "more", or you can use your favorite text editor or browser.

---

