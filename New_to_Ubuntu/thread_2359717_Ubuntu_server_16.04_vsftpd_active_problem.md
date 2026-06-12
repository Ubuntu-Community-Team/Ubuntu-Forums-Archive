---
title: "Ubuntu server 16.04: vsftpd active problem"
date: 2017-04-27
forum: New to Ubuntu
---

### Post by tony19942171 on 2017-04-27
vsftp cannot active:

**_sudo service vsftpd status_**
```
&#9679; vsftpd.service - vsftpd FTP server
   Loaded: loaded (/lib/systemd/system/vsftpd.service; enabled; vendor preset: e
   Active: failed (Result: exit-code) since Thu 2017-04-27 13:27:07 CST; 3s ago
  Process: 30833 ExecStart=/usr/sbin/vsftpd /etc/vsftpd.conf (code=exited, statu
  Process: 30830 ExecStartPre=/bin/mkdir -p /var/run/vsftpd/empty (code=exited,
 Main PID: 30833 (code=exited, status=2)


Apr 27 13:27:07 ts-server systemd[1]: Starting vsftpd FTP server...
Apr 27 13:27:07 ts-server systemd[1]: Started vsftpd FTP server.
Apr 27 13:27:07 ts-server systemd[1]: vsftpd.service: Main process exited, code=
Apr 27 13:27:07 ts-server systemd[1]: vsftpd.service: Unit entered failed state.
Apr 27 13:27:07 ts-server systemd[1]: vsftpd.service: Failed with result 'exit-c


```

[U][B] sudo vim /etc/vsftpd.conf
[/B][/U]```
#my setting
listen=YES
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
allow_writeable_chroot=YES

```

[COLOR=#000000]Any help would be greatly appreciated[/COLOR]:razz:

---

