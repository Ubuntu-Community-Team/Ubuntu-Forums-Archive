---
title: "Samba"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by kevin34ct on 2013-05-21
Ok so when it comes to Linux I am a total noob.  I am running Ubuntu 12.04LTS with Xubuntu GUI.  I have replaced Thunar with Nautilus.  I have Samba installed and also the Nautilus Share installed.  I can create a share in Nautilus which does show up on a Windows machine on my network, but when I try to connect to the share, I get You do not have permission to access.  I was hoping to get the same sharing capabilty that Windows to Windows has.  I am using Windows 7 Pro on another machine.  I wish I could change to Linux on it, but , the TV Tuner card doesn't have a really good Linux support Driver (CETON InfiniTV4).  I use shares just for the reason that I process home videos and photos on my Linux system and share them on my HTPC (Win Machine) The HTPC drive is almost full so until I can save up some money I just want to share it from my Linux machine.  I have read through so many tutorials on how to set up Samba and I've seen in one of them that Samba is broken in 12.04 (not sure about that one).  I need a simple way of getting permission.  Do I need to set up a user account on the Linux machine?  I don't want to have to use passwords.  Please help a noob with this.  

P.S.  If I get detailed instructions I can follow them, I'm not computer illiterate, just Linux challenged. :)

---

### Post by dino99 on 2013-05-21
try that howto: [http://askubuntu.com/questions/82998/can-see-samba-shares-but-not-access-them](http://askubuntu.com/questions/82998/can-see-samba-shares-but-not-access-them)

---

### Post by kevin34ct on 2013-05-21
> **dino99 said:**
> try that howto: [http://askubuntu.com/questions/82998/can-see-samba-shares-but-not-access-them](http://askubuntu.com/questions/82998/can-see-samba-shares-but-not-access-them)

I tried it.  Windows is still telling me there is no permission.

---

### Post by Morbius1 on 2013-05-21
Without some information all of us are just guessing. Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by kevin34ct on 2013-05-21
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Videos]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
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
    name resolve order = wins lmhosts host wins bcast
    dns proxy = No
    wins support = Yes
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

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Videos]
    comment = Videos
    path = /media/DC50BD2B50BD0CF0/Users/Kevin/Videos
    valid users = kevin
    read only = No
-------------------------------------------------------------

[Videos]
path=/media/DC50BD2B50BD0CF0/Documents and Settings/Kevin/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Windows]
path=/media/DC50BD2B50BD0CF0
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Desktop]
path=/home/kevin/Desktop
comment=
usershare_acl=Everyone:R,
guest_ok=y

---

### Post by Morbius1 on 2013-05-21
You've got a mix and match of shares defined the Classic way in smb.conf and some defined through Nautilus and it's somewhat messy when it comes to who can access what. Given your requirement:
>  I need a simple way of getting permission.  Do I need to set up a user  account on the Linux machine?  I don't want to have to use passwords.
I would suggest the following:
Edit smb.conf as root:
```
gksu leafpad /etc/samba/smb.conf
```
Add a line - right under the workgroup line - in the [global] section:
```
force user = kevin
```
While you're in there you might want to fix this:
> name resolve order = wins lmhosts host wins bcast
Whoever suggested putting wins first was on drugs plus you have it stated twice. [COLOR=#0000cd]If that actually works leave it alone but if you have a problem actually seeing the share you might consider changing it to this[/COLOR]:
```
name resolve order = bcast host lmhosts wins
```
[COLOR=#0000cd] *Like I said if you can see the shares from the other machines then leave it alone otherwise I'd change it.*[/COLOR]
Then restart samba:
```
sudo service smbd restart
```
Wait a good 5 minutes for things to settle down then try to access your shares.

As a side issue is this Classic share:
> [Videos]
    comment = Videos
    path = /media/DC50BD2B50BD0CF0/Users/Kevin/Videos
    valid users = kevin
    read only = No
"valid users" will require you to add kevin to the samba password database. If you don't want to use passwords I'd just get rid of it or change it to allow guest access. If you want to require passwords then let samba know who kevin is:
```
sudo smbpasswd -a kevin
```

---

### Post by kevin34ct on 2013-05-23
Thanks for the great instructions.  It now works.  I have 2 way access to my HTPC.  Bye, Bye windows (not for good though, will still use once in a while).

---

