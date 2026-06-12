---
title: "Samba shares - Windows machine can see but not access shared Ubuntu folders"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by jsolanov on 2012-10-25
Hello all. I am a neophite in the Linux OS. By God's infinite mercy I was able to install and configure the Karmic Koala version, got the samba shares working the way I wanted (multi user setup, with all clients windows OS, different versions - different levels of access, nothing too complicated). Over time I was able to update the Linux version without any hassles, but when the 12.1 version came out I had a problem with the GRUB. I had to download the software and do a local upgrade. Long story short, the files are there, but the samba setup is not. 

Tried to reinstall it (and did) but I am unable to get the thing working. I started up small, created a user in Linux, then created the same user in Samba, assigned passwords, created the share and I was static with joy when I could see it from my windows machine, but when I went to log in and entered the p/l combo, I got the error message "Windows can not access \\Xxxxx\xxxxx you do not have permission to get access".... etc.

I have searched high and low for a solution. I have implemented many offered in this and other forums but have been unable to resolve the issue, including disabling the firewall in the Linux machine. I do not want to "force" an user because not all users have the same privileges, and in any case, up to now it's just the one which does not work, so no point. My business is suffering because of it. Any help will be greatly appreciated.

Below the output from testparm, for your reference:

> Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[ISVCA]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = INCOLAB
    server string = ISVCA (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[ISVCA]
    path = /home/ISVCA
    valid users = jsolano
    read only = No


---

### Post by s1baker on 2012-10-25
I have been recently ( just the past few days ) trying to get my windows machine connected to where I could share a folder on my Ubuntu machine and I keep getting that error message. I finally got it working and I don't know much about it, but I discovered that I needed to do several things, so a few suggestions:

1. I also had to disable my firewall to get the window machine and samba on Ubuntu to recognize each other. After I disabled the firewall, I had to restart samba:

```
sudo service smbd restart
sudo service nmbd restart
```

2. I also found out that I had to edit my /etc/samba/smb.conf file. I had to place 'force user = (my home folder name here)'
just below [global]

---

### Post by s1baker on 2012-10-25
sorry, did not at first see your post where you do not want to use 'force user ='

---

