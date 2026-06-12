---
title: "vsftpd broken after updates today"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by mocha on 2008-05-10
Is anyone else having problems with vsftpd over their LAN after updating today?  I can't even FTP into the localhost anymore.  None of my config files were changed.  All I get is authentication errors.  Please help.

---

### Post by Monicker on 2008-05-10
Show the specific error messages. Also check your logs.

```
grep -r ftp /var/log
```

---

### Post by mocha on 2008-05-10
```
/var/log/auth.log:May 10 02:04:28 garage vsftpd: PAM unable to dlopen(/lib/security/pam_smbpass.so)
/var/log/auth.log:May 10 02:04:28 garage vsftpd: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
/var/log/auth.log:May 10 02:04:28 garage vsftpd: PAM adding faulty module: /lib/security/pam_smbpass.so
```

There's just a bunch of messages like that.  vsftpd is the only ftp daemon I have installed.  Just prior to updating and rebooting I was ftp'ing between boxes.

---

### Post by Monicker on 2008-05-10
When you said you were getting authentication errors, were you talking about the information in /var/log/auth.log or something else?

What happens exactly when you try to do an ftp connection and transfer?

---

### Post by mocha on 2008-05-10
I just get 530 login incorrect errors.  It doesn't matter what FTP client I use.  It happens from both machines on the LAN.  This is really strange.  I didn't change any config files.  vsftpd.conf, /etc/shells,

---

### Post by mocha on 2008-05-10
I just figured out that I can use SFTP instead.  This is still very strange to me as to why regular FTP stopped working.  Oh well, I'm probably better off with SFTP anyway.  I'd still like to figure this out though.

---

### Post by Monicker on 2008-05-10
> **mocha said:**
> I just get 530 login incorrect errors.  It doesn't matter what FTP client I use.  It happens from both machines on the LAN.  This is really strange.  I didn't change any config files.  vsftpd.conf, /etc/shells,

Hrrm.  If you are getting that error codes, then one of the logs in /var/log should contain a record of it.  There should be more than what you posted earlier.  The default log location is /var/log/vsftpd.log.  You might check your vsftpd.conf and make sure logging is enabled.

Could it be as simple as the password being in the wrong case?

---

