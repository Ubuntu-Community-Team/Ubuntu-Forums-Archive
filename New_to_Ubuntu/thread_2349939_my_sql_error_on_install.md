---
title: "my sql error on install"
date: 2017-01-19
forum: New to Ubuntu
---

### Post by a.dusty.trail on 2017-01-19
```
Selecting previously unselected package mysql-client-5.7.
(Reading database ... 137982 files and directories currently installed.)
Preparing to unpack .../mysql-client-5.7_5.7.17-0ubuntu0.16.04.1_armhf.deb ...
Unpacking mysql-client-5.7 (5.7.17-0ubuntu0.16.04.1) ...
Selecting previously unselected package mysql-server-5.7.
Preparing to unpack .../mysql-server-5.7_5.7.17-0ubuntu0.16.04.1_armhf.deb ...
Unpacking mysql-server-5.7 (5.7.17-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (229-4ubuntu13) ...
Setting up mysql-client-5.7 (5.7.17-0ubuntu0.16.04.1) ...
Setting up mysql-server-5.7 (5.7.17-0ubuntu0.16.04.1) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Renaming removed key_buffer and myisam-recover options (if present)
Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.7
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.7 (5.7.17-0ubuntu0.16.04.1) ...
Renaming removed key_buffer and myisam-recover options (if present)
Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.7
```

systemctl status mysql.service  responded

```
systemctl status mysql.service
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: inactive (dead) (Result: exit-code) since Thu 2017-01-19 17:54:27 PST; 3min 28s ago
  Process: 5864 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAILURE)

Jan 19 17:54:27  systemd[1]: mysql.service: Unit entered failed state.
Jan 19 17:54:27  systemd[1]: mysql.service: Failed with result 'exit-code'.
Jan 19 17:54:27  systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Jan 19 17:54:27  systemd[1]: Stopped MySQL Community Server.
Jan 19 17:54:27  systemd[1]: mysql.service: Start request repeated too quickly.
Jan 19 17:54:27  systemd[1]: Failed to start MySQL Community Server.
```

journalctl -xe responded
```
Jan 19 17:59:37 com.canonical.indicator.application[1377]:(process:1535): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
```


how can i get this fixed so i can install mysql?
or do i have to wait untill the package is repaired?
its a fresh install on lubuntu arm

---

### Post by cariboo on 2017-01-20
Did you try:

```
sudo apt install -f
```

in a terminal?

---

### Post by a.dusty.trail on 2017-01-20
Sure
And it gave the exact same error.

---

### Post by Thiras on 2017-01-21
You may try purge it first. Then install again.

Do NOT forget to take backup before purging. It can lead to data loss.

```
sudo apt purge mysql-server

sudo apt install mysql-server
```

---

### Post by a.dusty.trail on 2017-01-21
Been there failed at that.
The only thing I have not tried yet is starting fresh from a clean install.
But that should not really be necessary as I don't have 20 packages installed yet

---

