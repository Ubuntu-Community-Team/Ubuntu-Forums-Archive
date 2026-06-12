---
title: "display syslog messages on ubuntu"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by dreamedboy21 on 2008-09-08
hi to all,

I am using ubuntu hardy and I want to send the logs to the syslog server from C application,how can i see the messages,how can i display log file.I am new on linux,thats why I dont know where the log files.I will be grateful to have answer.

---

### Post by porchrat on 2008-09-08
in terminal one can type "dmesg"...that prints out the syslog.

Alternatively you can view all the logs from the menus by going to "System" --> "Administration: --> "System logs"

hope that helps

---

### Post by babylon2233 on 2008-09-08
If you mean you want to find the syslog log file, you can find inside /var/log directory.

---

### Post by manivel on 2009-05-19
i am using ubuntu 8.0.4..1 LTS version and i have directly connected ADSL modem system address 172.16.1.35  and modem address 172.16.1..30. i configured remote sys log of modem and as same time confiure here also (ubuntu )

1. /etc/default/syslogd

SYSLOGD="-r"

but not remote log file received mu ubuntu box can u help me,

---

