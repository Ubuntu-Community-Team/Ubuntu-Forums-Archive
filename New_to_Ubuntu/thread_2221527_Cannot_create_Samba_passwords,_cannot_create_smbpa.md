---
title: "Cannot create Samba passwords, cannot create smbpasswd"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by jltonkinson on 2014-05-02
I have a fresh install of Ubuntu (v14.04) and installed Samba (v4.1.6).  I've got one share working in guest mode.  (I can see it from my Windows 8 machine.)  However I have yet to get it working with a username and password.  (I can see the second share, but I can't open anything in it.  Always an invalid username/password.)

I have "[global] security = USER" to indicate I want user security mode.  I have also installed libpam-smbpass in order to sync Ubuntu passwords with Samba.  I believe the issue is that I do not have a /etc/samba/smbpasswd file.  I've read a lot of mixed info in this, but one of the more current documents said that a "sudo smbpasswd -a [username]" should create this file if necessary.

When I issue a "sudo smbpasswd -a sambauser" I get the message "no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory".  This certainly looks like a program exception of some kind.  I'm a little surprised because I've hardly done much to this install except add VIM and a few things.  I am an absolute newbie, but looks like I can't ignore this error.

Any ideas about my next steps?

Thanks,
Jeff

---

### Post by jltonkinson on 2014-05-02
According to [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186) this is a bug in Samba related to libpam-smbpass.  I have uninstalled this an the error message goes away.  However I still get the error "Failed to add entry for user [username]".  In other words, it doesn't appear to create the database.  Any ideas?

---

### Post by bab1 on 2014-05-02
> **jltonkinson said:**
> According to [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186) this is a bug in Samba related to libpam-smbpass.  I have uninstalled this an the error message goes away.  However I still get the error "Failed to add entry for user [username]".  In other words, it doesn't appear to create the database.  Any ideas?

If this is just a stand alone server (file server) then the database is most likely **tdbsam **.  This is good for about 200+ users.  The Samba users should be able to be displayed with this command```
sudo pdbedit -L
```

Is the user you added there?

[COLOR="#0000FF"]Edit:  This appears to be an upstream problem.  It may not be able to be cured at this time.  I'm using Ubuntu 12.04 LTS so I've not seen this in my network.  [/COLOR]

---

### Post by piotrasbl on 2014-05-02
> **jltonkinson said:**
> I have a fresh install of Ubuntu (v14.04) and installed Samba (v4.1.6).
And I believe that might be the case.
I got nowhere-near with that V4 of samba.
Please use package V2 I believe...

---

### Post by bab1 on 2014-05-02
> **piotrasbl said:**
> And I believe that might be the case.
I got nowhere-near with that V4 of samba.
Please use package V2 I believe...

If you only need sharing then either V3 (3.6 now) or v4 (4.1 now) will work.  Samba v4 is not that scary and it will work just like v3 for a standalone file server (sharing).
  S
Samba v2 will not share that  easily with Win XP/7/8.  There have been too many changes to SMB (SMB/CIFS/SMB2/SMB3).

If you need an NT style PDC then use v3.  If you need Active Directory style DC then you should use v4.

---

### Post by jltonkinson on 2014-05-02
Thank you all for your input.  This is presently a standalone installation. "sudo pdbedit -L" reported my name as a user.  So that's good.  On the other hand, I"m not able to get to the share from my NT computer using my username and password.  (Is there any way to see from the Samba-side why an attempt is rejected?)

I did try "sudo pdbedit -a smbuser", entered a password twice, and got the error message "Failed to add entry for user smbuser."  Any other ideas?

BTW.  If I were to try v3.6 as suggested by BAB1, how do I install it.  Recall this is the "newbie" section and I've only used "apt-get install" so far.

Thanks,
Jeff

---

### Post by jltonkinson on 2014-05-02
A little update.  I used samba-tool and found some errors.  Perhaps this is the root of my problem.  Haven't been able to fix them.

jeff@AssistDevUbuntu:/etc/samba$ sudo samba-tool dbcheck --cross-ncs --reset-well-known-acls --fix
 ERROR(<type 'exceptions.ValueError'>): uncaught exception - unable to parse dn string
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/dbcheck.py", line 120, in run
    reset_well_known_acls=reset_well_known_acls)
  File "/usr/lib/python2.7/dist-packages/samba/dbchecker.py", line 69, in __init__
    self.infrastructure_dn = ldb.Dn(samdb, "CN=Infrastructure," + samdb.domain_dn())

I am a competent C programmer, but I'm not that familiar with Python.  When I look at the lines in question, they don't look right to me.  Is it possible that the installed Python code has a problem?

Thanks,
Jeff

---

### Post by bab1 on 2014-05-02
> **jltonkinson said:**
> Thank you all for your input.  This is presently a standalone installation. "sudo pdbedit -L" reported my name as a user.  So that's good.  On the other hand, I"m not able to get to the share from my NT computer using my username and password.  (Is there any way to see from the Samba-side why an attempt is rejected?)

If you have the Samba server installed then also have all the Samba client side routines installed.  You can Be both the client and the server from the Ubuntu host.  We can test with that.  
> 
I did try "sudo pdbedit -a smbuser", entered a password twice, and got the error message "Failed to add entry for user smbuser."  Any other ideas?

Are you trying to add a user named *smbuser*?  I don't know if it matters but every Samba user has to also have an Ubuntu account.  I'd add the Ubuntu user first, then try and add the Samba user.
> 
BTW.  If I were to try v3.6 as suggested by BAB1, how do I install it.  Recall this is the "newbie" section and I've only used "apt-get install" so far.

Thanks,
Jeff
At this point you would have to install Ubuutu 13.10 or less to have the Samba v3 package available.   Ubuntu 12.04 is what I would (and do) use.  This doesn't meant that what you have won't work.  IMO the Samba v4 will work just will Samb v3.

You problems seem to be in the configuration right now.

---

### Post by bab1 on 2014-05-02
> **jltonkinson said:**
> A little update.  I used samba-tool and found some errors.  Perhaps this is the root of my problem.  Haven't been able to fix them.

jeff@AssistDevUbuntu:/etc/samba$ sudo samba-tool dbcheck --cross-ncs --reset-well-known-acls --fix
 ERROR(<type 'exceptions.ValueError'>): uncaught exception - unable to parse dn string
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/dbcheck.py", line 120, in run
    reset_well_known_acls=reset_well_known_acls)
  File "/usr/lib/python2.7/dist-packages/samba/dbchecker.py", line 69, in __init__
    self.infrastructure_dn = ldb.Dn(samdb, "CN=Infrastructure," + samdb.domain_dn())

I am a competent C programmer, but I'm not that familiar with Python.  When I look at the lines in question, they don't look right to me.  Is it possible that the installed Python code has a problem?

Thanks,
Jeff
The tool you are using is for checking LDAP installation on a full blown Active Directory Samba installation.  The tool is NOT FOR USE on a stand alone Samba server.

Python is an OOP language.  Your C skills are almost useless in interpreting the code.  The code is grumping because you don't have the LDAP database installed.

Let's concentrate on the share you are trying to configure.  Post all the output using ```
 blocks.  To do this click on the [SIZE=4]#[/SIZE] icon at the to of the reply editor and place the text in between the [code] blocks.

From Ubuntu post the output of [CODE]cat /etc/samba/smb.conf
```
and the output of ```
smbtree -d3
```

---

### Post by jltonkinson on 2014-05-02
> **bab1 said:**
> The tool you are using is for checking LDAP installation on a full blown Active Directory Samba installation.  The tool is NOT FOR USE on a stand alone Samba server.
That's interesting.  In general, how does one learn these dark secrets?  Is there documentation somewhere?  In any case, thanks for the enlightenment.

> **bab1 said:**
> Python is an OOP language.  Your C skills are almost useless in interpreting the code.  
I'm sure you didn't mean to insult me, but my pride bristles.:(  I mostly program in C# which is a cross between C++ and Java - the OO is not a problem.  However I must confess in one of the lines of code that threw the exception, shown below, I find the "verbose=verbose" odd.  
```
chk = dbcheck(samdb, samdb_schema=samdb_schema, verbose=verbose,
                          fix=fix, yes=yes, quiet=quiet, in_transaction=started_transaction,
                          reset_well_known_acls=reset_well_known_acls)
```


As you requested in your generous offer of help, here is the content of smb.conf (I used samba-tool testparm to weed out the comments.)  ```
[global]
    workgroup = WORKGROUP
    netbios name = LOCKDOC
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    security = USER
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    lock directory = /var/run/samba/locks
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    invalid users = root, bin, daemon, adm, sync, shutdown, halt, mail, news, uucp, operator

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

[Public]
    comment = Unsecured File Server
    path = /srv/samba/public
    read only = No
    create mask = 0755
    guest ok = Yes

[Vault]
    comment = Secured file server
    path = /srv/samba/vault
    read only = No
    create mask = 0755

```


And the output of  smbtree -d3 (was I to do this as root?) ```
jeff@AssistDevUbuntu:/var/lib/samba/private$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.254.21 bcast=192.168.254.255 netmask=255.255.255.0
Enter jeff's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Connecting to 192.168.254.21 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
Connecting to 192.168.254.21 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\LS410DA56              LinkStation
Connecting to 192.168.254.47 at port 445
Connecting to 192.168.254.47 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4f69b8bdd0] mpx_fde[(nil)] fd[12] - disabling
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\LS410DA56\IPC$               IPC Service (LinkStation)
        \\LS410DA56\NAS_Garage         
        \\LS410DA56\share              recovered
        \\LS410DA56\info               LinkStation Utilities
        \\LS410DA56\lp                 Network Printer for Windows
    \\LOCKDOC                AssistDevUbuntu server (Samba, Ubuntu)
Connecting to 192.168.254.21 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\LOCKDOC\print$             Printer Drivers
        \\LOCKDOC\Public             Unsecured File Server
        \\LOCKDOC\Vault              Secured file server
        \\LOCKDOC\IPC$               IPC Service (AssistDevUbuntu server (Samba, Ubuntu))
MSHOME
Connecting to 192.168.254.42 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
Connecting to 192.168.254.42 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'

```

Thanks again for your generous help.
-Jeff

---

### Post by jltonkinson on 2014-05-03
> **bab1 said:**
> If you have the Samba server installed then also have all the Samba client side routines installed.  You can Be both the client and the server from the Ubuntu host.  We can test with that.  

Thanks for the suggestion.  I used **smbclient **with my "Vault" share and it prompted me for a password and worked just fine.  I also added a Unix username (per your suggestion) and then was able to add a Samba username (using pdbedit).  Using **smbclient -U=newuser** also worked!

So the problem now seems to be limited to passwords from Windows.  I guess that's progress!
-Jeff

---

### Post by bab1 on 2014-05-03
> **jltonkinson said:**
> That's interesting.  In general, how does one learn these dark secrets?  Is there documentation somewhere?  In any case, thanks for the enlightenment.

There is no comprehensive online documentation of Samba4 by Samba.org.  The only thing available is the Samba Wiki.  As Linux in general is fast moving with no regard to backwards compatibility you just have to get into the flow of things and ask a lot of questions.  With that being said you have to be careful of the answers.  Folks with a lot of background will answer but so will those who started just yesterday.  
> 


I'm sure you didn't mean to insult me, but my pride bristles.:(  I mostly program in C# which is a cross between C++ and Java - the OO is not a problem.  However I must confess in one of the lines of code that threw the exception, shown below, I find the "verbose=verbose" odd.  
```
chk = dbcheck(samdb, samdb_schema=samdb_schema, verbose=verbose,
                          fix=fix, yes=yes, quiet=quiet, in_transaction=started_transaction,
                          reset_well_known_acls=reset_well_known_acls)
```

No I didn't mean to insult you.  Your question is in the context of the "Absolute Beginners Section"  :-)
> 

As you requested in your generous offer of help, here is the content of smb.conf (I used samba-tool testparm to weed out the comments.)  ```
[global]
    ...
[COLOR="#FF0000"]    invalid users = root, bin, daemon, adm, sync, shutdown, halt, mail, news, uucp, operator
[/COLOR]

[Public]
    comment = Unsecured File Server
    path = /srv/samba/public
    read only = No
[COLOR="#FF0000"]    create mask = 0755[/COLOR]
    guest ok = Yes


```
The first item in red should be in the share definition.  I wouldn't bother at all.  Those users are not capable of logging in and are not Samba users anyway.

The second item is more a recommendation.  if you are going to have multiple users then you need to deal with multiple creators (owners).  You need to give rw permissions to an inherited common user group and provide the proper permissions.  > 

And the output of  smbtree -d3 (was I to do this as root?)

No.  A regualar user can request a mapping list of all the shares.
> 
 ```
jeff@AssistDevUbuntu:/var/lib/samba/private$ smbtree -d3
....
[COLOR="#FF0000"]MSHOME
Connecting to 192.168.254.42 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
Connecting to 192.168.254.42 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'[/COLOR]

```

Thanks again for your generous help.
-Jeff
I assume this is a Win95/98 host or something like it.

---

### Post by jltonkinson on 2014-05-04
I've started reading the 900 page Samba 3.2 manual.  Wow!  Very well written.  Very thorough.

I added a Unix/Samba user that matches one of my WIndows 8 logins.  Exact same username and password on all 3.  From Windows 8 under this user I could browse my secured share no problem.  Didn't even prompt me for a password.  Yahoo.

However when I log in from a different Windows login, and attempt to enter a password, it doesn't work.  More precisely from a Windows command prompt (terminal):
```
**net view \\lockdoc** 
*Displayed my shares* [I]including
Vault     Disk    Secured file server
[/I]
**net use x: \\lockdoc\Vault**
Enter the user name for 'lockdoc':  **[Username that worked]**
Enter the password for lockdoc:  **[Password that worked]**
System error 1219 has occurred.

Multiple connectios to a server or shared resource by the same user, using more than one user name, are not allowed.  Disconnect all previous connections to the server or shared resource and try again.
```

I rebooted the Ubuntu computer just to be sure there were no existing connections.  Tried again with the exact same results.  Is the authentication different when typing in username and password vs. taking it right from the Windows login?  Not sure if this is a Windows problem or a Samba problem.

Thanks,
Jeff

---

### Post by bab1 on 2014-05-05
> **jltonkinson said:**
> I've started reading the 900 page Samba 3.2 manual.  Wow!  Very well written.  Very thorough.

I added a Unix/Samba user that matches one of my WIndows 8 logins.  Exact same username and password on all 3.  From Windows 8 under this user I could browse my secured share no problem.  Didn't even prompt me for a password.  Yahoo.

However when I log in from a different Windows login, and attempt to enter a password, it doesn't work.  More precisely from a Windows command prompt (terminal):
```
**net view \\lockdoc** 
*Displayed my shares* [I]including
Vault     Disk    Secured file server
[/I]
**net use x: \\lockdoc\Vault**
Enter the user name for 'lockdoc':  **[Username that worked]**
Enter the password for lockdoc:  **[Password that worked]**
System error 1219 has occurred.

Multiple connectios to a server or shared resource by the same user, using more than one user name, are not allowed.  Disconnect all previous connections to the server or shared resource and try again.
```

I rebooted the Ubuntu computer just to be sure there were no existing connections.  Tried again with the exact same results.  Is the authentication different when typing in username and password vs. taking it right from the Windows login?  Not sure if this is a Windows problem or a Samba problem.

Thanks,
Jeff
Samba is capable of handling multiple logins.  Windows passes the logged in user name and I believe this is the problem.  Google reveals[ some info]("https://www.google.com/search?q=multiple+samba+logins&btnG=Go!") on the subject.

---

### Post by jltonkinson on 2014-05-06
FYI.

All is now working and it turns out that there was nothing wrong with the installation or configuration.  While BAB1 provided a lot of help, the crux of the issue was:
> The tool you are using is for checking LDAP installation on a full blown  Active Directory Samba installation.  The tool is NOT FOR USE on a  stand alone Samba server.
I first add users:  ```
sudo useradd [username] -p [password]
``` and then I add the same users as samba users:  ```
sudo pbedit -a [username] -t 
```
The logging in problem was probably that once you log in, Windows doesn't readily change that username.  So far I've just been logging out of WIndows if I want to change usernames.

So thanks again to BAB1 for helping out a newbie.

---

