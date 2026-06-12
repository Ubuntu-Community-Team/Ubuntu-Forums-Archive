---
title: "Samba does not accept user/password combination"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by Anton_Sack on 2013-09-19
Hi there,

I am a total newbee to the Linux world, so please forgive me if I am asking dump questions. 

I installed Ubuntu server 13.04 and installed samba. The daemons are running and I changed the configuration so that it looks like this:
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/samba_users
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        logon drive = H:
        domain logons = Yes
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        comment = Home Directories
        valid users = %S
        read only = No


[printers]
        comment = All Printers
        path = /var/spool/samba
        read only = Yes
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        read only = Yes



```

I created user "pommes" (with home directory, too) with password "bar" and added him to my samba_users file: foo=pommes (foo is my username on the windows machine). 

When I now connect to my ubuntu server, the windows authentication window is displayed and it asks me to enter the credentials for user "MYLAPTOP\foo". Unfortunately, password "bar" is not accepted.

What am I doing wrong? Any help is greatly appreciated!

---

### Post by Azdour on 2013-09-19
Hi,

Maybe this link will help?

[http://www.cyberciti.biz/faq/adding-a-user-to-a-samba-smb-share/](http://www.cyberciti.biz/faq/adding-a-user-to-a-samba-smb-share/)

When you created the user pommes did you run smbpasswd ?

From [http://www.samba.org/samba/docs/man/manpages-3/smbpasswd.8.html:](http://www.samba.org/samba/docs/man/manpages-3/smbpasswd.8.html:)

> When run by root, smbpasswd allows new users to be added and deleted in the smbpasswd file, as well as allows changes to the attributes of the user in this file to be made. When run by root, smbpasswd accesses the local smbpasswd file directly, thus enabling changes to be made even if smbd is not running.

---

### Post by Anton_Sack on 2013-09-19
Hi Azdour,

thanks a lot! This was exactly the step I was missing out.

Cheers, mate!

---

