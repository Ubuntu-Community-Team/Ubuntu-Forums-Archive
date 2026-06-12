---
title: "What is my system doing?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by bodam on 2008-04-30
I just built my ubuntu 8.04 laptop and I was reviewing the auth.log file and I see the same set of entries over and over again (posted below).  They occur every hour.  Can someone tell me what it's doing?  I see that whatver it's trying is failing every time.

Apr 30 02:17:01 bodam-laptop CRON[5155]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 30 02:17:01 bodam-laptop CRON[5155]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 30 02:17:01 bodam-laptop CRON[5155]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 30 02:17:01 bodam-laptop CRON[5155]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 30 02:17:01 bodam-laptop CRON[5155]: pam_unix(cron:session): session closed for user root
Apr 30 03:17:01 bodam-laptop CRON[16659]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 30 03:17:01 bodam-laptop CRON[16659]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 30 03:17:01 bodam-laptop CRON[16659]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 30 03:17:01 bodam-laptop CRON[16659]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 30 03:17:01 bodam-laptop CRON[16659]: pam_unix(cron:session): session closed for user root
Apr 30 04:17:01 bodam-laptop CRON[28019]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 30 04:17:01 bodam-laptop CRON[28019]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 30 04:17:01 bodam-laptop CRON[28019]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 30 04:17:01 bodam-laptop CRON[28019]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 30 04:17:01 bodam-laptop CRON[28019]: pam_unix(cron:session): session closed for user root
Apr 30 05:17:01 bodam-laptop CRON[6999]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 30 05:17:01 bodam-laptop CRON[6999]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 30 05:17:01 bodam-laptop CRON[6999]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 30 05:17:01 bodam-laptop CRON[6999]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 30 05:17:01 bodam-laptop CRON[6999]: pam_unix(cron:session): session closed for user root

---

### Post by Monicker on 2008-04-30
Known bug:

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990")

---

### Post by master5o1 on 2008-04-30
cron is a scheduled job runner...

Basically they are the logs for certain jobs put on the 'cronjob' list.

---

### Post by bodam on 2008-04-30
> **Monicker said:**
> Known bug:
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990)


Thanks....The discussion was a little over my head:  Should I:


[LIST=1]
[*]Ignore it and just wait for a patch (maybe)
[*]Comment out the reference lines in /etc/pam.d/common-password
[*]Install libpam-smbpass
[/LIST]

---

### Post by Monicker on 2008-04-30
> **bodam said:**
> Thanks....The discussion was a little over my head:  Should I:


[LIST=1]
[*]Ignore it and just wait for a patch (maybe)
[*]Comment out the reference lines in /etc/pam.d/common-password
[*]Install libpam-smbpass
[/LIST]


You can safely ignore it if you don't mind the log entries.  If you would rather not be distracted by it, installing limpam-smbpass will not hurt anything. 

*I reread the bug ticket.  I think I would just comment out the line, instead of installing another package, if it bothers you*

---

