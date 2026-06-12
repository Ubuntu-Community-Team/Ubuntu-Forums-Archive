---
title: "Network share on second drive"
date: 2020-07-19
forum: New to Ubuntu
---

### Post by ausrock on 2020-07-19
Hi all,
I'm new to Linux, lots to learn,
I'm building a new server, with 2 x RAIDed mirrored drives (4 drives in total). The Linux operating system is installed on the first 1TB mirror with Windows VM running in Virtual Box. The 2nd mirror is a big 8TB container for storage.
I can share a folder on the network for Windows VM if the share resides in my Home folder, but the goal is to share the Linux formated 8TB storage on the second RAID. 
Using the GUI I can share a folder on the 8TB and see it in Windows network area of life, but I receive "an access denied" message on the 8TB regardless of correct credentials, what am I missing?
Is it Samba, drive permissions or something else?
Thanks in advance

---

### Post by Morbius1 on 2020-07-19
Not enough information to answer the question. Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by ausrock on 2020-07-19
testparm -s is
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


net usershare info --long is

[home cloud]
path=/home/datanational/home cloud
comment=
usershare_acl=Everyone:F,
guest_ok=y

[rsync]
path=/media/datanational/Share/rsync
comment=
usershare_acl=Everyone:F,
guest_ok=y

[rbs]
path=/media/datanational/Share/rbs
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Share]
path=/media/datanational/Share
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by Morbius1 on 2020-07-20
The problem are your mount points. They are all under /media/datanational for the second "drive". Linux will apply special permissions to the /media/datanational directory ( which is a user name ) such that only datanational can access what is under it.

One way to fix this is to change your mount points to be one level up from where it is now - /media/Share for example - then change your share defintions to match the new mount points.

Another way to fix this is to make all of your client users appear to be datanational. Then it will get past the /media/datanational issue. You would do that by editing /etc/samba/smb.conf and right under the workgroup = WORKGROUP line add this one:
```
force user = datanational
```
Then restart smbd:
```
sudo service smbd restart
```
Everything the remote user does will be done as datanational - for these samba shares.

---

