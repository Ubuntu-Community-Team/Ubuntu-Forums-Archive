---
title: "MySQL won't start"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by dorpcat on 2011-09-28
I installed mysql yesterday but removed it with remove --purge,  autoremove and autoclean. Today I'm reinstalling mysql and the server  isn't starting.


Here's the tail end of the installation text. Things go downhill when it goes on about /etc/mysql not existing on my computer.

```

Selecting previously deselected package mysql-server-5.1.
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.49-1ubuntu8.1_amd64.deb) ...
egrep: /etc/mysql/: No such file or directory
Selecting previously deselected package libhtml-template-perl.
Unpacking libhtml-template-perl (from .../libhtml-template-perl_2.9-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up libnet-daemon-perl (0.43-1) ...
Setting up libplrpc-perl (0.2020-2) ...
Setting up libdbi-perl (1.611-1) ...
Setting up libdbd-mysql-perl (4.016-1) ...
Setting up mysql-client-core-5.1 (5.1.49-1ubuntu8.1) ...
Setting up mysql-client-5.1 (5.1.49-1ubuntu8.1) ...
Setting up mysql-server-core-5.1 (5.1.49-1ubuntu8.1) ...
Setting up mysql-server-5.1 (5.1.49-1ubuntu8.1) ...
110928 16:04:10 [Note] Plugin 'FEDERATED' is disabled.
110928 16:04:10  InnoDB: Started; log sequence number 0 755080
110928 16:04:10  InnoDB: Starting shutdown...
110928 16:04:16  InnoDB: Shutdown completed; log sequence number 0 755080
start: Job failed to start
Setting up libhtml-template-perl (2.9-1) ...

```Do I just remove mysql, create the /etc/mysql directory and move on or does this require more attention?

---

### Post by dorpcat on 2011-09-28
Okay I figured out the issue. There were some lingering bits of mysql that were making my computer have kittens and not able to restart the service.

For those of you with similar problems, open up Synaptics, look for installed items and peruse until you find mysql and remove that stuff and all associated stuff. Now you can do a clean install.

HTH.

---

