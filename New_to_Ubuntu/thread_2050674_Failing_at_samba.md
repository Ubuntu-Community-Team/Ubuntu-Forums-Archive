---
title: "Failing at samba"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by Firenter on 2012-08-31
Hi forums!

I wanted to repurpose my old laptop to a home fileserver with samba. I thought that with the little knowledge I had from using ubuntu in schools a little bit and the simple guide on the website I could do it.
But obviously I failed. I cannot place files into the folder I designated as share like in the guide nor can I access it from windows without it asking for a password.
Can you guys help me on this?

---

### Post by Morbius1 on 2012-08-31
No one can help you without you providing more information. Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by Firenter on 2012-09-01
Here's the output for testparm:

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
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

[share]
    comment = Corthout Home Share
    path = /srv/samba/share
    read only = No
    create mask = 0755
    guest ok = Yes

```And I get nothing when I do net usershare.

---

### Post by Morbius1 on 2012-09-01
> [share]     comment = Corthout Home Share     path = /srv/samba/share     read only = No     create mask = 0755     guest ok = YesWhat are the permissions of the target folder:
```
ls -al /srv/samba/share
```In order for a guest to actually have write access to that share the target folder permissions have to be set to allow it:
```
 sudo chmod 0777 /srv/samba/share
```

---

### Post by Firenter on 2012-09-01
Right I did that now, nobody nogroup now has full controll of the folder and I changed the 0755 in the config file to 0777.
But my windows machine is still asking for a password...
Do I have to like log in to the server with that?

---

### Post by sandyd on 2012-09-01
> **Firenter said:**
> Here's the output for testparm:

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
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

[share]
    comment = Corthout Home Share
    path = /srv/samba/share
    read only = No
    create mask = 0755
    guest ok = Yes

```And I get nothing when I do net usershare.

try adding
```

browseable = yes

```
under [share].

and
```

security = share

```
under [global]

---

### Post by Morbius1 on 2012-09-01
> **Firenter said:**
> Right I did that now, nobody nogroup now has full controll of the folder and I changed the 0755 in the config file to 0777.
But my windows machine is still asking for a password...
Do I have to like log in to the server with that?
There's only one HowTo in all the universe that would have you create a shared folder and set it owned by nobody and that's this one or someone pimping this one: [https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html)

[COLOR=Blue][I]**Side note**: Just remember that HowTo is for a Server with a big "S" not a peer - to - peer type of samba server that most folks set up where Ed want's to share a folder with Edna.

[/I][COLOR=Black]That share will only work under the following conditions:

** The client machine is running Linux.

** The Windows user was never given a samba password.

Unlike Linux, a Windows client passes the user's login user name and password when it tries to access the share even if the share ( like the one you created ) doesn't require it. If there is no match to that user in the Samba password database on the Linux system the combination of these 2 lines in smb.conf[/COLOR][/COLOR][COLOR=Blue][COLOR=Black] will convert the Windows user to the guest user account which by default is: "nobody" :
[/COLOR][/COLOR]> security = user ( which is the modern standard default )
map to guest = Bad User
[COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR]If however there is a match to the user name but not a match to the samba password then you will in fact be asked for credentials to access a guest share. 

[COLOR=Blue]**You have 2 options:**[/COLOR]

*** [1] Make changes to the Samba password database and the share definition***
** Make the samba password match the Windows user's login password exactly:
```
sudo smbpasswd -a windows-user-name
```** And change the share definition you have to this:
> [share]
    comment = Corthout Home Share
    path = /srv/samba/share
    read only = No
    [COLOR=Blue]**force user = nobody**[/COLOR]
    guest ok = YesNote: You will no longer need the create mask line since everyone who access ( remotely ) the share will be converted to nobody. 

*** [2] Remove any reference to the windows user from the samba password database:***
```
sudo smbpasswd -x windows-user-name
```Now when the Windows user tries to access the share there won't be a matching user name, the windows user will be converted to nobody just like his Linux brother, and both will have access to the folder since it's owned by nobody.

Option 2, although not stated as such was the premise of the HowTo you are using. It's the only way it will work as presented.

---

### Post by Firenter on 2012-09-01
Just quick question, do I replace "windows-user-name" with my windows username or do I keep that?

---

### Post by Morbius1 on 2012-09-01
Change it to the actual Windows user name.

---

### Post by Firenter on 2012-09-01
Thank you very much for this! Now I'll be able to save some harddrive space on my other laptop :D

---

