---
title: "cant share folders on 2nd drive"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by DrGreenBean on 2012-01-29
Hi
I do a backup from my Windows server to my PC 2nd hard drive, I want to switch my desktop OS from Win 7 to Ubuntu. I can share files on the main drive and the server can acess it, but when I share a folder on the 2nd hard drive I can only see it but not access it." Windows can not access \\cp-pc\data" The 2nd drive was ntfs but i have formated it now with ext4

Please advise

---

### Post by rgreener25 on 2012-01-29
ext4 doesnt work with windows

---

### Post by Morbius1 on 2012-01-29
Only because of this in your original post: \\cp-pc\data am I assuming that this is a Samba share on the second disk. If I'm correct can you tell us how you shared it? Posting the output of the following commands will tell us how you are set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by DrGreenBean on 2012-01-30
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[offsite]"
Processing section "[tet]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = PCSQUARE-LOCAL
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    encrypt passwords = No
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

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[offsite]
    path = /media/offsite
    read only = No
    guest ok = Yes

[tet]
    path = /media/offsite/tet
    read only = No
    guest ok = Yes

---

### Post by DrGreenBean on 2012-01-30
p@cp-pc:~$ net usershare info --long
[tet]
path=/media/offsite/tet
comment=
usershare_acl=Everyone:F,
guest_ok=y

[scan]
path=/home/cp/Scan
comment=
usershare_acl=Everyone:F,
guest_ok=y

[slave]
path=/media/offsite/slave
comment=
usershare_acl=Everyone:F,
guest_ok=y

[work]
path=/home/cp/Desktop/Work
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by DrGreenBean on 2012-01-30
I can access the Work folder which is on my desktop from the Windows PC but i cant access the slave folder which is on my 2nd hard drive

---

### Post by Morbius1 on 2012-01-30
** To be honest I don't know how you can access any shares since you have a parameter with the wrong value:
> encrypt passwords = NoGo into /etc/samba/smb.conf and change it to:
> encrypt passwords = [COLOR=Blue]**Yes**[/COLOR]Then restart samba:
```
sudo service smbd restart
```** You are using 2 different methods to create samba shares - one editing smb.conf and another using Nautilus. I would, for your own sanity's sake, use one method or the other.

** Your original post said you got an error when trying to access: \\cp-pc\data but there is no "data" share.

** What are the permissions of the following:
```
ls -al /media/offsite
```

---

### Post by DrGreenBean on 2012-01-30
Hi
I have tried both the Nautilus and Samba Server Configuration utility under System admin to try and get it to work. The data folder was just a example, both shares was created by right clicking on the folder and choosing sharing options. Encrypts passowrd I changed just to see if it makes a difference, I cahnged it back now.

The offsite drive was not mounted when I started up so i mounted it and then ran your command.
Why does it not mount auto?

Here is the result for your command
cp@cp-pc:~$ ls -al /media/offsite
ls: cannot access /media/offsite: No such file or directory
cp@cp-pc:~$ ls -al /media/offsite
total 44
drwx------ 8 cp   cp          4096 2012-01-30 08:05 .
drwxr-xr-x 6 root root        4096 2012-01-30 21:06 ..
drwx------ 2 root root       16384 2012-01-29 20:18 lost+found
drwxrwxrwx 2 cp   sambashare  4096 2012-01-29 20:21 offsite
drwxrwxrwx 2 cp   sambashare  4096 2012-01-29 20:33 one
drwxrwxrwx 2 cp   cp          4096 2012-01-30 08:05 slave
drwxrwxrwx 2 cp   sambashare  4096 2012-01-29 21:17 tet
drwx------ 4 cp   cp          4096 2012-01-29 20:27 .Trash-100

---

### Post by Morbius1 on 2012-01-30
> Encrypts passowrd I changed just to see if it makes a difference, I cahnged it back now.Change it back to:
>                               encrypt passwords = [COLOR=Blue]**Yes**[/COLOR]                      That's the default and it's that way for a reason.
>  drwx------ 8 cp   cp          4096 2012-01-30 08:05 .Fe Fi Fo Fum, I smell an ntfs partition there me thinks. There's an easy enough fix although it's a little messy in your case.

Regardless of how you set up your shares Samba cannot override Linux file permissions. I know that using Nautilus it's asks you if you want it to modify permissions and it does try to but Linux can't change permissions on an NTFS partition without doing a mount in a specific way.

You need to make the remote user look like user: cp because only that user can access the directory. You would add a line to smb.conf that looks like this:
```
force user = cp
```If you use Classic Samba sharing you would add it to the share definition like this:
> [offsite]
    path = /media/offsite
    read only = No
**[COLOR=Blue]force user = cp[/COLOR]**
    guest ok = YesIf you use the nautilus method you would add it to the [COLOR=Blue][global][/COLOR] section - right under the "workgroup" line is where I'd put it.

You are using 2 different methods on at least one target folder ( tet ) and it's anybody's guess which method Samba is listening to so either get rid on all the shares of one method or put the force user line in the [global] section and hope for the best.

---

### Post by DrGreenBean on 2012-01-31
Hi
It was a ntfs drive I then formated it with ext4. Classic Samba,nautilusI am getting confused. 
Please recommend the best way to create the shares and if you have  a link or steps for me to follow it would help. I think to do it the right way is going to be easier than to try and fix my mess

Thank you for your help, I been supporting Windows for 11 years and i must say I feel helpless in Linux

---

### Post by Morbius1 on 2012-01-31
This is a samba share created from Nautilus - it's share definition is in /var/lib/samba/usershares:
> p@cp-pc:~$ net usershare info --long
[tet]
path=/media/offsite/tet
comment=
usershare_acl=Everyone:F,
guest_ok=yThis is a Classic Samba share - it's share definition is in /etc/samba/smb.conf:
> [tet]
    path = /media/offsite/tet
    read only = No
    guest ok = Yes     In this particular case they are functionally equivalent but I think you can see that over time they might diverge since they are not connected to one another. In this case I have no idea which one Samba is listening to for direction.

I don't have a religious affiliation with either method since both of them will work. If you want to have only Nautilus-shares use whatever utility you used to create the classic samba shares and remove them. Then add the force user to the global section of smb.conf and restart samba.

If you want to use only Classic shares then go into Nautilus, right click the shared folder, then Sharing Options, and remove all the check marks. Then add force user to all the share definitions in smb.conf for all your classic shares.

---

### Post by DrGreenBean on 2012-02-01
[FONT=Arial][SIZE=2]I installed **GADMIN-samba to see if it would make it easier to edit samba. After installing it and some configuration I could not access my pc over the network at all. Removed **[/SIZE][/FONT][B][FONT=Arial][SIZE=2]GADMIN-samba restored the original samba config file and suddenly any share I create on the 2nd hard drive is working.

Not sure what changed but I will take the victory.
Thank you for your help[/SIZE][/FONT]
[/B]

---

