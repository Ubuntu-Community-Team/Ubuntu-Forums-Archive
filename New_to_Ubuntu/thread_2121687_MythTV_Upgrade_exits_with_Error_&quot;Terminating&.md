---
title: "MythTV Upgrade exits with Error &quot;Terminating&quot; Apache2"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-03-02
All I could find in the Apache2 log is:

[Sun Feb 24 09:24:18 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Sun Feb 24 21:31:23 2013] [notice] caught SIGTERM, shutting down
[Mon Feb 25 08:25:21 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Mon Feb 25 19:44:14 2013] [error] [client 127.0.0.1] File does not exist: /var/www/AuctivaBackupInfo, referer: [http://vi.raptor.ebaydesc.com/ws/eBayISAPI.dll?ViewItemDescV4&item=26094&t=1321000&tid=340&category=104233&seller=arkcSoj=1&rptdesc=1&excTrk=1&lsite=0](http://vi.raptor.ebaydesc.com/ws/eBayISAPI.dll?ViewItemDescV4&item=26094&t=1321000&tid=340&category=104233&seller=arkcSoj=1&rptdesc=1&excTrk=1&lsite=0)
[Mon Feb 25 19:48:11 2013] [error] [client 127.0.0.1] File does not exist: /var/www/AuctivaBackupInfo, referer: [http://vi.raptor.ebaydesc.com/ws/eBayISAPI.dll?ViewItemDescV4&item=2600&t=130&tid=30&category=1&seller=arkexcSoj=1&rptdesc=1&excTrk=1&lsite=0](http://vi.raptor.ebaydesc.com/ws/eBayISAPI.dll?ViewItemDescV4&item=2600&t=130&tid=30&category=1&seller=arkexcSoj=1&rptdesc=1&excTrk=1&lsite=0)
[Tue Feb 26 07:35:29 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Tue Feb 26 07:49:46 2013] [notice] SIGUSR1 received.  Doing graceful restart
[Tue Feb 26 07:49:46 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Wed Feb 27 00:20:58 2013] [notice] caught SIGTERM, shutting down
[Wed Feb 27 07:42:08 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Wed Feb 27 17:30:28 2013] [notice] caught SIGTERM, shutting down
[Wed Feb 27 17:55:51 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Wed Feb 27 17:56:19 2013] [notice] caught SIGTERM, shutting down
[Wed Feb 27 17:58:40 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Wed Feb 27 18:27:48 2013] [notice] caught SIGTERM, shutting down

Is it safe to uninstall apache2 and re-install or does something fancier need doing. Any why is there an ebay dot com in the toppish lines?

---

### Post by Mark_in_Hollywood on 2013-03-05
This problem resolved itself. Aptitude -f caught the problem and then resolved it.

---

