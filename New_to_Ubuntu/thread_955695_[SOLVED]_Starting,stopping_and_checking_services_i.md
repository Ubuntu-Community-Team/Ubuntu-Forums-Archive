---
title: "[SOLVED] Starting,stopping and checking services in ubuntu"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by remy06 on 2008-10-22
Hi all,

Need some tips on the following:

1)how to actually start a service or script at boot time?

2)how to stop a service and how to ensure it does not start again at boot time?

3)how to check for current running service or to see if a service is currently running?

I wish to learn this via the command line.I have read that redhat has something like chkconfig that allows user to configure services to start/stop at different runlevels etc.Does ubuntu have something like this?

Pls advice.Thanks!

---

### Post by billgoldberg on 2008-10-22
1)how to actually start a service or script at boot time?

System -> preferences -> sessions

2)how to stop a service and how to ensure it does not start again at boot time?

I use "killall servicename".

Remove the service from "sessions".

3)how to check for current running service or to see if a service is currently running?

Use the "top" command.

Or "system -> preferences -> system monitor".

---

### Post by Nxion on 2008-10-22
Here is something I found very useful. Hope it helps.
[URL="https://help.ubuntu.com/community/BootServices"]
https://help.ubuntu.com/community/BootServices[/URL]

---

### Post by Sarmacid on 2008-10-22
To start/stop/check for services, you can do this

```
/etc/init.d/servicename start
/etc/init.d/servicename stop
/etc/init.d/servicename status
```

Also to check if a service is running, you can run

```
pgrep -l servicename
```

---

### Post by kostkon on 2008-10-22
If you mean system services, then *System -> Administration -> Services*. If you mean apps/processes that start when your session starts (i.e. when you login) then *System -> Preferences -> Sessions*.

For what is currently running: *System -> Administration -> System Monitor*.

---

### Post by oldos2er on 2008-10-22
> **remy06 said:**
> I have read that redhat has something like chkconfig that allows user to configure services to start/stop at different runlevels etc.Does ubuntu have something like this?
  

 sysv-rc-conf

---

### Post by Nxion on 2008-10-22
Check this one out too.
[URL="http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html"]
http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html[/URL]

---

### Post by remy06 on 2008-10-22
hi all,

Thanks again!Will study the tips provided and ask again if im unsure.

Nxion,

The links are helpful too.

:)

---

