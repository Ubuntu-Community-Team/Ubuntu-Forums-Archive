---
title: "ubuntu 14.04.3 samba setting problems"
date: 2015-11-06
forum: New to Ubuntu
---

### Post by dvks on 2015-11-06
Appreciate any help I can get, wasted a lot of time and can't resolve it.
I just installed Ubuntu 14.04.3, samba is set as stand alone no LDAP. It used to work great on UBUNTU 12.04 right out of the box, it is not my experience with UBUNTU 14.04.3.
When I use Nautilus I can't see shares from other MS-Windows 10 & 7 on the network (and they can't see my system) 
The windows systems can see each other
However when I run   sbmtree    command line I can see the windows systems shares tree, so it does not look like a network issue but more authentication & setup issue

Is there a systematic way to debug it?
Appreciate help

my smb.conf :

[global]
   workgroup = KEYSCANUS.COM
   security = user
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
#### Networking ####

   interfaces = 192.168.0.0/24 eth0
   bind interfaces only = yes

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 3
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   server role = standalone

   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Domains ###########


############ Misc ############
   usershare allow guests = yes


#======================= Share Definitions =======================

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[share]
   comment = KSNAS share on KSNAS93
   path = /var/www/temp
   browseable = yes
   read only = no
   guest ok = yes

---

### Post by bab1 on 2015-11-06
> **dvks said:**
> ...

Is there a systematic way to debug it?

Yes there is.  Reviewing the smb.conf file is a start.  :-)

FYI:  When posting text output from the terminal you should wrap the output in [noparse]```
  
```[/noparse] blocks. This is easily done by clicking on the **[SIZE=4]# [/SIZE]** icon at the top of the "Advanced" editor that you use to reply with.

> 

my smb.conf :

```
[global]
   workgroup = KEYSCANUS.COM
   security = user
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
#### Networking ####

   interfaces = 192.168.0.0/24 eth0
   bind interfaces only = yes

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 3
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   server role = standalone

   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Domains ###########


############ Misc ############
   usershare allow guests = yes


#======================= Share Definitions =======================

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[share]
   comment = KSNAS share on KSNAS93
   path = /var/www/temp
   browseable = yes
   read only = no
   guest ok = yes
```
I would not have a dot (. )  the WORKGROUP name.

Since you do not have guest access your users must be both Linux users (/etc/passwd) and Samba users (smbpasswd -a).  Has this been done?  The directory that you have shared is normally restricted.  Have you set the appropriate ownership and permissions there?

Post the output this command from the Samba server's terminal```
smbtree -d3
```

---

### Post by dvks on 2015-11-07
Bab1 thanks for taking the time to help, greatly appreciated.

1. Your comment on how to post from a terminal is appreciated.

2. Yes my users are defined both on Linux and samba and there are proper permissions for the required folder.

3. Your comment regarding the "dot" on the workgroup name was the main problem, once removed I could start having the cross Windows-Ubuntu samba working.

4. At this point I can access from Windows 7 and from Window 10 the shares on UBUNTU 14.04.3 system. From the UBUNTU system I can access the shares on the Windows 7 system but I can only see the Windows 10 machine but can't get the list of shared folders on the machine. 
When I try to access the Windows 7 machine using Nautilus I get a prompt for the username/password (or supply it directly on the command line for the smbtree) but when I try to access the Windows 10 I do not get the prompt for password instead I get a message:  "Unable to access location, Failed to retrieve share list from server. Connection refused" 
I assume that that I have here a Windows10 setting problem and not UBUNTU setting issue. Maybe the port (139, 445) are blocked on Widows10 by default and need to open them.

Anyway at this point I the original issue is resolved, thanks again for your help.

---

### Post by bab1 on 2015-11-07
I think you should mark this thread as *resolved *.  My guess is that this is a Windows10 setting that you need to configure.  A quick search brought up [**this**]("https://techjourney.net/cannot-connect-to-cifs-smb-samba-network-shares-shared-folders-in-windows-10/").

---

