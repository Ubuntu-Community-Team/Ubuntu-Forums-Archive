---
title: "Samba share not working on some computers"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by alexdtennant on 2014-02-17
Hello all, I have a strange problem with my samba shares.

I am using ubuntu 13.04 

If I set "guest ok = yes" for the shares I need in /etc/samba/smb.conf then none of the linux machines on the network can access them, I get an "Unable to mount location" popup
 if I disable "guest ok" I can access the shares with a password.

The set-up is working on one windows machine as intended but other windows machines can't access any of the folders. 

Even the host machine cannot access the "guest ok = yes" shares through the nautilus network interfaces

Here is the output of $ testparm -s 

```
Load smb config files from /etc/samba/smb.confrlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[scan]"
Processing section "[tv]"
Processing section "[it]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[scan]
    comment = scans and temp
    path = /srv/scan
    write list = tvshare
    read only = No
    create mask = 0777
    force security mode = 0777
    directory mask = 0777
    force directory mode = 0777
    force directory security mode = 0777
    guest ok = Yes


[tv]
    comment = tv
    path = /srv/tv
    write list = tvshare
    read only = No
    create mask = 0777
    force security mode = 0777
    directory mask = 0777
    force directory mode = 0777
    force directory security mode = 0777
    guest ok = Yes


[it]
    comment = software and backups
    path = /srv/it
    write list = company
    read only = No
    create mask = 0770
    security mask = 0770
    force security mode = 0770
    directory mask = 02770
    force directory mode = 02770
    directory security mask = 02770
    force directory security mode = 02770
```

these are the file permissions of my share folders:

```
drwxrws---  3 root     company  4096 Feb 17 10:59 it
drwsrwxrwx 10 alex     tvshare  4096 Feb 17 09:33 scan
drwxrwxrwx  4 alex     tvshare  4096 Feb 17 15:07 tv
```


This setup used to work I have recently expanded and rebuilt the raid10 array everything was stored on, when I recreated all the shares everything seems to have failed.

Any help would be greatly appreciated.

---

### Post by alexdtennant on 2014-02-17
Hello All

I have solved this issue.

The problem was the folder that contains the shared folders. The permissions on the folder were set to:

drwx------   6 alex alex  4096 Feb 17 13:50 srv

they should have been:

drwxr-xr-x   6 root root  4096 Feb 17 13:50 srv

this allows network users to open the shared folders.

The only reason it was working with the non guest user was because the user I was logging in with was the owner of the /srv folder.

Hopefully this helps anyone having the same problems.

---

