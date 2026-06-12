---
title: "Howto: Ubuntu server as an Active Directory member server"
date: 2006-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by mhinrichsen on 2006-10-19
**[SIZE="6"]Overview:[/SIZE]**

The key advantages of Active Directory membership are secure central user management, authentication, and single sign-on for the clients accessing the server. Once an Ubuntu Samba server is integrated with Active Directory, share level and file level permissions can be set using the AD users and groups without requiring local account mapping. Using Winbind, the Linux server sees the domain users and groups transparently. Accountants will love this; using a Samba server you avoid paying OS licensing fees on the server and client access license fees. My goal is to implement Samba-Active Directory integration on a single domain using Winbind with Kerberos on a Linux operating system that is free with free updates for at least 3 years.  I selected the Ubuntu Dapper Drake 6.06 Server distribution because it is a Debian downstream distribution which has a reputation for being stable and promises to be Free “forever.” My objective is to make the process transparent (and chocked full of tricks) so that I may reproduce the integration anytime and to make it available to other Ubuntu users. 

[SIZE="6"]**Preliminaries:**[/SIZE]

It is assumed that a functioning Active Directory domain is in place.  The DNS house must also be in order along with a solid Internet connection for updates and installs.  The key pieces needed on the Linux server are NTP, Kerberos Samba & Winbind. The current version of Samba 3.02 on Ubuntu supports Winbind with Kerberos. Winbind supplies the users, groups, & passwords from the AD domain and Kerberos supplies the AD authentication mechanisms for Winbind. Because you will use the Shell to do most of the configuration work on the Ubuntu server, make sure you know how to use VI or VIM to modify files.


**[SIZE="6"]Getting the Ubuntu Dapper Drake 6.06 Server ready:[/SIZE]**

•	Make sure your workstations and servers system clocks are in Sync (to within the default 5 minutes.) If they are not, trust me, the Kerberos authentication and ticket passing will not work and you will get some unexpected results. THIS IS VERY IMPORTANT. So do yourself a favor and make sure. I recommend that you setup an NTP server on your network and use it to synchronize your system clocks. This is easy just go to [http://www.ntp.org](http://www.ntp.org) for instructions and Windows Client. This can and should be done on your Window Servers to make sure your system clocks are synchronized and stay synched. Be sure to use the NTP server pools which will make the process very efficient. YOU HAVE BEEN WARNED.
•	Install the Ubuntu server using the CD or DVD base installs. Once the server is up and running and you have set the fixed IP, test the Internet connection and make sure you can Ping the IP Address of the key Windows Domain Controllers. 
•	Just to make life easy, you might want to enable the root account access so that you do not need to prefix every command with sudo. If you do this you will not have to sudo everything. Once the root account access is enabled the password will be the same as the password used for sudo. To enable root account access type the following:

root@ubuntuserver:/#sudo passwd root

•	Next you will need to modify the repositories /etc/apt/sources.list to include universe and multiverse repositories. This is important because some of the key packages needed, such as krb5-user, are found there.  Backup, and then Modify the /etc/apt/sources.list to include at least the following lines:

[FONT="Courier New"]deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe[/FONT]
•	Run the following command to download the local repository lists:

root@ubuntuserver:/#sudo apt-get update

•	Update system updates:

root@ubuntuserver:/#sudo apt-get upgrade

•	I recommend installing the packages below using the following command:

root@ubuntuserver:/#sudo apt-get install  samba smbfs smbclient smbldap-tools winbind krb5-user krb5-config krb5-doc libkrb53 libpam-krb5 ntp-server ntp sun-java5-jre swat apache2 inetutils-inetd ssh

•	As part of the installation of krb5-conf you will be prompted to enter the default realm information. It will see your current AD Realm.

You will enter the Active Directory domain server such as DCSERVER.LOCALDOMAIN.NET. Kerberos is case sensitive so the realm is entered in upper case. Do not worry too much here because you will later modify the /etc/krb5.conf file to the correct settings.

[SIZE="6"]**Configure and Test NTP :**[/SIZE]

•	Next, configure your NTP service. Review the design suggestions found on the ntp.org website. I present an example that works well for tier-two US-based servers. To duplicate my example modify the /etc/ntp.conf file to look use settings such as:

root@ubuntuserver:/#sudo vim /etc/ntp.conf

[FONT="Courier New"]# /etc/ntp.conf, configuration for ntpd

# ntpd will use syslog() if logfile is not defined
logfile /var/log/ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.your-provider.example


#use your local NTP server –You may want to set this first
server dcserver.localdomain.net


#For the U.S. Pools:
server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org


# pool.ntp.org maps to more than 100 low-stratum NTP servers.
# Your server will pick a different set every time it starts up.

# ... and use the local system clock as a reference if all else fails
# NOTE: in a local network, set the local stratum of *one* stable server
# to 10; otherwise your clocks will drift apart if you lose connectivity.
server 127.127.1.0
fudge 127.127.1.0 stratum 13

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1 nomodify

# Clients from this (example!) subnet have unlimited access,
# but only if cryptographically authenticated
#restrict 192.168.123.0  mask  255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
broadcast 192.168.1.0

# If you want to listen to time broadcasts on your local subnet,
# de-comment the next lines. Please do this only if you trust everybody
# on the network!
#disable auth
#broadcastclient[/FONT]

•	Once ntp is configured restart it with the following command:

root@ubuntuserver:/#sudo /etc/init.d/ntp-server restart


[SIZE="6"]**Configure /etc/hosts**[/SIZE]

Just to be safe even if your DNS servers are working perfectly, it is a wise to add the kdc server to your local /etc/hosts file. This will make everything work much faster (MAKE SURE YOU USE YOUR IP ADDRESS AND FQDN FOR YOUR DC:

[FONT="Courier New"]192.168.1.100 	dcserver.localdomain.net	dcserver[/FONT]

[SIZE="6"]**Configure and Test Kerberos**[/SIZE]

Given that the Active Directory domain server is dcserver.localdomain.net,(USE YOUR REALM) The following is the /etc/krb5.conf used to configure the MIT Kerberos that we have installed:

**Configure Keberos**

[FONT="Courier New"][logging]

	default = FILE:/var/log/krb5.log
        kdc = FILE:/var/log/krb5kdc.log
	admin_server = FILE:/var/log/kadmin.log


[libdefaults]
	default_realm = LOCALDOMAIN.NET
	dns_lookup_realm = false
	dns_lookup_kdc = true

[appdefaults]
 pam = {
	debug = false
	ticket_lifetime = 36000
	renew_lifetime = 36000
	forwardable = true
	krb4_convert = false
 }[/FONT]

**Testing Kerberos**

root@ubuntuserver:/#sudo kinit [email]Administrator@LOCALDOMAIN.NET[/email]
[FONT="Courier New"]Password for [email]Administrator@LOCALDOMAIN.NET[/email]: ********[/FONT]
Check if ticket request was valid using the klist command: 

root@ubuntuserver:/#sudo klist

[FONT="Courier New"]Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [email]Administrator@LOCALDOMAIN.NET[/email]

Valid starting 		Expires		Service principal
10/18/06 15:43:51		10/19/06 01:43:55	KRBTGT/LOCALDOMAIN.NET@LOCALDOMAIN.NET
	  Renew until	10/19/06  15:43:51

Kerberos 4 ticket cache: /tmp/tkt0
Klist: You have no tickets cached[/FONT]
root@ubuntuserver:/#

At this point, your base Kerberos installation and configuration is operating correctly. You can release the ticket by issuing the kdestroy command.


[SIZE="6"]**Join the AD Domain**[/SIZE]

Configure the Samba file /etc/samba/smb.conf  -Below is an example of  Global and share settings that will work for your testing purposes on a single domain. Just create the /home/data directory using the following command:

root@ubuntuserver:/#sudo mkdir /home/data

Then modify the smb.conf file:

root@ubuntuserver:/#sudo vim /etc/samba/smb.conf

[FONT="Courier New"]#/etc/samba/smb.conf
[global]

   workgroup = LOCALDOMAIN
   realm = LOCALDOMAIN.NET
   server string = %h server (Samba %v, Ubuntu)
   wins server = 192.168.1.100
   password server = DCSERVER
   enable privileges =Yes
   allow trusted domains = No
   dns proxy = no
   name resolve order = host wins bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
   log level = 3
   security = ADS
   encrypt passwords = true
   socket options = TCP_NODELAY
   time server = Yes
   map to guest = nobody
   idmap uid = 16777217-33554431
   idmap gid = 16777217-33554431
   winbind enum users = yes
   winbind enum groups = yes
   printcap name = cups
   printing = cups
   cups options = raw
   template shell = /bin/bash



#======================= Share Definitions =======================
[data]
   comment = Share Data
   path = /home/data
   read only = No
   create mask = 0775
   directory mask = 0775
   browsable = Yes
   public = Yes 
   writeable = Yes
   force create mode = 0775
   force directory mode = 0775
   force security mode = 0775
   guest ok = no
   inherit permissions = yes
   nt acl support = yes

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700[/FONT]

**Check the configuration using testparm:**

root@ubuntuserver:/#sudo testparm

Be sure to stop and start the Winbind services and restart the samba service after modifying and testing the /etc/samba/smb.conf file by executing the following commands:

root@ubuntuserver:/#sudo /etc/init.d/winbind stop
root@ubuntuserver:/#sudo /etc/init.d/samba restart
root@ubuntuserver:/#sudo /etc/init.d/winbind start


The next step is to make sure the time is synchronized with the domain by typing:

root@ubuntuserver:/#sudo net time set


It is now the moment of truth. Type the following to add the linux server to the AD Domain:

root@ubuntuserver:/#sudo net ads join –U Administrator
Administrator’s password:******

[FONT="Courier New"]Using short domain name – LOCALDOMAIN
Joined ‘Ubuntuserver’ to realm ‘LOCALDOMAIN.NET’[/FONT]

Success! The computer ‘Ubuntuserver’ will now appear as a machine account under “Computers” in your AD console. 

[LIST]
[/LIST]Now, stop Samba & Winbind for the next steps using the following:


root@ubuntuserver:/#sudo /etc/init.d/winbind stop
root@ubuntuserver:/#sudo /etc/init.d/samba stop


[SIZE="6"]**Setup Winbind Authentication**[/SIZE]

[SIZE="6"]**Setup Authentication by modifying the file: /etc/nsswitch.conf**[/SIZE]


root@ubuntuserver:/#sudo vim /etc/nsswitch.conf


[FONT="Courier New"]# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind

hosts:          files dns wins
networks:       files dns

protocols:      files
services:       files
ethers:         files
rpc:            files
netgroup: 	files
publickey:	nisplus
automount: 	files
aliases:	files nisplus[/FONT]


Save your changes, and start samba and Winbind in the following order:


root@ubuntuserver:/#sudo /etc/init.d/samba start
root@ubuntuserver:/#sudo /etc/init.d/winbind start


Verify that Winbind is working.  Use the Winbind utility wbinfo to list users and groups from the AD Domain Controller.

root@ubuntuserver:/#sudo wbinfo –u
[FONT="Courier New"]LOCALDOMAIN\Administrator
LOCALDOMAIN\Guest
LOCALDOMAIN\Mhinrichsen
LOCALDOMAIN\User
…[/FONT]

root@ubuntuserver:/#sudo wbinfo –g
[FONT="Courier New"]LOCALDOMAIN\Domain Computers
LOCALDOMAIN\Admins
LOCALDOMAIN\Guests
LOCALDOMAIN\Domain Users
…[/FONT]

Verify that logins and passwords are coming from the AD Domain Controller as well as the local files:

root@ubuntuserver:/#sudo getent passwd


If Winbind is working you will see the LOCALDOMAIN\ prefix. If not you will probably just see the local accounts on the linux server. 

The final Winbind test is to run net ads info to display the AD server information.

root@ubuntuserver:/#sudo net ads info

[FONT="Courier New"]LDAP server: 192.168.1.100
LDAP server name: DCSERVER
Realm: LOCALDOMAIN.NET
Bind Path: dc=LOCALDOMAIN, dc=NET
LDAP port: 389
Server time: Wed, 18 Oct 2006 18:02:18 EDT
KDC server: 192.168.1.100
Server time offset: 0
root@ubuntuserver:/#[/FONT]
[B][SIZE="6"]

[SIZE="6"]Configure PAM to use Winbind for workstations authentication[/SIZE][/B][/SIZE]

PAM configuration for samba is accomplished by modifying files in the /etc/pam.d directory. The following files need to be modified: 

/etc/pam.d/samba
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-password
/etc/pam.d/common-session

It is important to make a copy of these files prior to modification. Here is what each of these files should look like after modification:

root@ubuntuserver:/#vim /etc/pam.d/samba

[FONT="Courier New"]@include common-auth
@include common-account
@include common-session
@include common-password[/FONT]

root@ubuntuserver:/#vim /etc/pam.d/common-account

[FONT="Courier New"]#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account	required	pam_unix.so[/FONT]

root@ubuntuserver:/#vim /etc/pam.d/common-auth

[FONT="Courier New"]#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth	required	pam_env.so
auth	required	pam_unix.so[/FONT]

root@ubuntuserver:/#vim /etc/pam.d/common-password

[FONT="Courier New"]#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define  the services to be
#used to change user passwords.  The default is pam_unix

# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# (Add `md5' after the module name to enable MD5 passwords)
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs. Also the "min" and "max" options enforce the length of the
# new password.
password   sufficient pam_windbind.so
password   required   pam_unix.so nullok obscure min=4 max=8 md5

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
# password required	  pam_cracklib.so retry=3 minlen=6 difok=3
# password required	  pam_unix.so use_authtok nullok md5[/FONT]

root@ubuntuserver:/#vim /etc/pam.d/common-session

[FONT="Courier New"]#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).  The default is pam_unix.
#
session 	required	pam_limits.so
session	required	pam_unix.so[/FONT]

At this point check to make sure you can logon to another terminal session such as tty2. Just type Alt-F2 and make sure you can still login as root then go back by typing Alt-F1. Once this is accomplished I recommend restarting the server at this point just to make sure there are no errors during startup and to get a clean environment for testing.  

[SIZE="6"]**Applying ownership & permissions to the shared directory**[/SIZE]

To set the ownership and group permissions on the shared directory /home/data use the chmod and chown commands. Note: use valid users and groups from the real domain

root@ubuntuserver:/#chown –R ‘localdomain\administrator:localdomain\Domain Users’ /home/data

[SIZE="6"]**Final Test with a Windows XP/2000/NT workstation**[/SIZE]

Test a connection to the Ubuntu server from the Windows XP workstation by clicking on start-run in the open box type\\ubuntuserver and then click OK. A window should open showing the \\ubuntuserver\data share and the Printers and Faxes icon. If you open the share the permission at the directory level should match the user and group settings applied previously. 

**[SIZE="6"]Recap[/SIZE]**

If everything works, your Samba server is a member of the Active Directory domain and the accounts can be used to apply permissions to objects on the Ubuntu Linux Server. The central account database is available to the Samba server along with the local accounts such as root, etc. Also, this process will work for other Linux distributions using tools other than apt for the install on non-Debian based distros as long as you are using MIT Kerberos . Of course, you can still use a secure shell and many other tools to connect to the server and do admin work on the server using local accounts without being forced to use AD accounts.  It’s called the best of both worlds! 


Michael Hinrichsen
Solution Designers, Inc.
[email]mh@solutiondesignersinc.com[/email]

---

### Post by kpm on 2006-12-11
Thanks for this tutorial, I am working my way through... Found a typo in this bit, 'libpa-krb5' should be 'libpam-krb5'
> **mhinrichsen said:**
> 
&#8226;	I recommend installing the packages below using the following command:
root@ubuntuserver:/#sudo apt-get install  samba smbfs smbclient smbldap-tools winbind krb5-user krb5-config krb5-doc libkrb53 libpa-krb5 ntp-server ntp sun-java5-jre swat apache2 inetutils-inetd ssh

---

### Post by rverrips on 2007-01-02
Thanks, nice walk-thru ... Do you have an updated one for using Ubuntu 6.10 (i.e. Edgy) instead - I have some driver issues with my server on 6.06 which has been resolved in 6.10 - However I can't seem to find any of the krb5 packages for 6.10?

---

### Post by rpr on 2007-01-23
Very nice tutorial and works perfect on ubuntu edgy.
I have one question:

Is it normal that you can't set permissions using the windows explorer on a windows client.

---

### Post by jim22 on 2007-01-29
Thanks mhinrichsen, works great on Debian Etch.

rpr: yes that's normal, acl is not turned on by default (needed for windows permissions instead of standard *nix user,group,world)

For ext3:
add acl to your mount options in /etc/fstab for the filesystem that contains the share, eg:
```
/dev/hda5            /home                   ext3    noatime,acl   0  2
```

and then either reboot or remount the filesystem:
```
mount -v -o remount /home
```

This should now work fine, you won't be able to remove the user,group,world permissions, but you can restrict them and add permissions.


Hope this helps
Jim

---

### Post by mahalie on 2007-01-30
Wow! Great tutorial!! I've been using Linux approximately 4 days and yet managed to add my new server to our AD Domain.  Thanks for being so explicit, besides vi commands the only thing I had to look up was how to reboot the server. (Yep, I'm *that *new).

Now I just need to read up on chmod and chown. Thanks again, this is really helping me "infect" my workplace with Linux fever :D

---

### Post by rverrips on 2007-01-30
> **rverrips said:**
> Thanks, nice walk-thru ... Do you have an updated one for using Ubuntu 6.10 (i.e. Edgy) instead - I have some driver issues with my server on 6.06 which has been resolved in 6.10 - However I can't seem to find any of the krb5 packages for 6.10?

Duh, it's called following step one and enabling multiverse and universe repo's ... works fine on Edgy Server, and even tested it on a Feisty Herd-1 box!

---

### Post by rverrips on 2007-02-04
Ok, so this works beautifully for my server on domain1.something.foo

However, howto set it up so that users from a trusted sister domain domain2.something.foo can also access it (The server is joined to domain1) 

Thanks

---

### Post by mhinrichsen on 2007-02-16
You should try setting the following in the Global section of the smb.conf:

allow trusted domains = yes

Thanks

---

### Post by mhinrichsen on 2007-02-16
Acknowledged and corrected in the HOWTO

Thanks!

---

### Post by rverrips on 2007-02-16
> **mhinrichsen said:**
> You should try setting the following in the Global section of the smb.conf:

allow trusted domains = yes


Yup, worked like a charm, thanks!

---

### Post by davidm on 2007-03-01
Thanks for the clear tutorial. You saved lots of us countless hours of work!

David

---

### Post by bloodniece on 2007-03-01
When I run:
```
net ads join &#8211;U Administrator

```

I get:
```
[2007/03/01 14:57:56, 0] libads/kerberos.c:ads_kinit_password(164)
  kerberos_kinit_password root@MYDOMAIN.LOCAL failed: Client not found in Kerberos database
[2007/03/01 14:57:56, 0] utils/net_ads.c:ads_startup(191)
  ads_connect: Client not found in Kerberos database

```


I just have a local domain: MYDOMAIN.LOCAL
Windows Server 2003 Domain Controller running DHCP, DNS, Kerberos, AD, etc . . .

Can this work?

---

### Post by skarab on 2007-03-07
When I attempt to login via the TTY, I get:

```
Mar  7 06:34:42 myhost login[xxxx]: Authentication service cannot retrieve authentication info.
```

I am running Ubuntu 6.10 server, and I'm able to reach the share after authenticating via a Windows machine.

I receive a different error when attempting to authenticate via ssh:

```
Mar  7 06:44:27 myhost sshd[xxxx]: Failed password for MYDOMAIN\\username from x.x.x.x port xxx ssh2
```

Any ideas?

---

### Post by mhinrichsen on 2007-04-09
A single local domain will work fine. It may be that the password is incorrect or there is a dns problem. Make sure you use your administrator account and the correct password. Thanks.

---

### Post by mhinrichsen on 2007-04-09
> **bloodniece said:**
> When I run:
```
net ads join &#8211;U Administrator

```

I get:
```
[2007/03/01 14:57:56, 0] libads/kerberos.c:ads_kinit_password(164)
  kerberos_kinit_password root@MYDOMAIN.LOCAL failed: Client not found in Kerberos database
[2007/03/01 14:57:56, 0] utils/net_ads.c:ads_startup(191)
  ads_connect: Client not found in Kerberos database

```


I just have a local domain: MYDOMAIN.LOCAL
Windows Server 2003 Domain Controller running DHCP, DNS, Kerberos, AD, etc . . .

Can this work?
A single local domain will work fine. It may be that the password is incorrect or there is a dns problem. Make sure you use your administrator account and the correct password. Thanks

---

### Post by mhinrichsen on 2007-04-09
> **skarab said:**
> When I attempt to login via the TTY, I get:

```
Mar  7 06:34:42 myhost login[xxxx]: Authentication service cannot retrieve authentication info.
```

I am running Ubuntu 6.10 server, and I'm able to reach the share after authenticating via a Windows machine.

I receive a different error when attempting to authenticate via ssh:

```
Mar  7 06:44:27 myhost sshd[xxxx]: Failed password for MYDOMAIN\\username from x.x.x.x port xxx ssh2
```

Any ideas?
This may seem simplistic but check the PAM settings.

---

### Post by 416hammy on 2007-04-16
Noob having issues here...

[COLOR="Red"][INDENT]administrator@UBUNTU-6.10-WORKSTATION:~$ sudo net ads join –U Administrator
root's password: 
[2007/04/16 16:44:00, 0] utils/net_ads.c:ads_startup(191)
  ads_connect: No such file or directory
administrator@UBUNTU-6.10-WORKSTATION:~$ sudo /etc/init.d/winbind stop
sudo: /etc/init.d/winbind: command not found
administrator@UBUNTU-6.10-WORKSTATION:~$ [/INDENT][/COLOR]

I haven't the foggiest clue how to troubleshoot this. :confused:

---

### Post by brechtvb on 2007-04-17
I managed to get the ubuntu server into the domain. but there were errors with the ticked during the net ads command.

I can get a ticket manualy with the kinit command

wbinfo -u administrator takes a loooong time so pressed ctrl-c

net ads info works fine

sudo getent passwd works also fine

now i rebooted the server, try to login with a domain account, the login fails. Is there a special syntax with a prefix to use domain account?

a local account is no problem

does anyone have a clue ?

---

### Post by brechtvb on 2007-04-17
I managed to get it working

my winbind config was far from correct

i suggest in using this one:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

### Post by EvilMarshmallow on 2007-04-26
When I try to run 

```
sudo kinit Administrator@MYDOMAIN
```

All I get is this message:

```
kinit(v5): KRB5 error code 68 while getting initial credentials
```

What did I miss?

---

### Post by rpr on 2007-05-06
Working on Feisty too.

---

### Post by BadSquishy on 2007-05-13
I've set up a test rig using the FileServerOnLVMOnRaid1 documentation over at Ubuntu Community Docs and this howto.  It shows up on the network and I've been able to copy files back and forth between it and a couple of Windows XP boxes on the network.  Thank you for this well written document.  

I've noticed a typo and a couple of discrepancies while working through this howto, so I thought I'd help improve the document.  

First, I wanted to just point out a couple of minor issues with the smb.conf file as shown.  I've set up a workgroup samba server for my home network before I started this test rig so I've previously done some reading of official samba howto and the smb.conf man page.  In the [data] share section there is the stanza "read only = no" and "writeable = yes".  These are inverted synonyms, so only one needs to be used for a given share.  Secondly this share has the stanzas "public = yes" and "guest ok = no" which are synonymous and actually contradict each other.  In this instance we want to delete the "public = yes" stanza because we do not want public access to the share.  

Secondly I noticed a simple typo.  In the section on PAM configuration, the part about modifying the common-password file has the word "pam_windbind.so" where it should be "pam_winbind.so"

Thanks again for the easy to follow howto.  My next step is to add on access virus scanning to the samba share.  If anyone know where this is documented for Ubuntu please point me to it.  I'm currently planning on adapting the virus scanning portions of the Gentoo Samba3/CUPS/ClamAV HOWTO from the Gentoo Linux Official Documentation.  If it works I'll post a thread on this forum.  

Regards,

---

### Post by jim0112 on 2007-06-16
To echo the other comments - nice how-to! The only thing I will say is - remember to set the FQDN of the Linux box before joining the domain, otherwise the DNS name in AD will be 'localhost', when you would really like it to be linuxbox.localdomain.net.

This might sound obvious, but I forgot, and consequently felt pretty dumb! 

(There's lots of info out there on how to configure the hostname in various places, e.g. [http://www.cpqlinux.com/hostname.html](http://www.cpqlinux.com/hostname.html).)

---

### Post by aztektum on 2007-07-06
> **jim22 said:**
> Thanks mhinrichsen, works great on Debian Etch.

i want to do this with a test debian etch system at work. did you use the same ubuntu repos though? or just the debian equivalents?

---

### Post by drewdown on 2007-07-11
I followed your FAQ and everything appeared to go smoothly.  I was able to join the computer to the domain, see all the accounts and groups.  But when I do the chown &#8211;R &#8216;netcordia\Administrator:netcordia\Domain Users'  /home/data command it goes to a ">" prompt. 

IE: admin@computer-name:/$ chown &#8211;R &#8216;domain\james.brown:domain\Domain Users'  /home/data
>


I am unable to hit that share from an XP machine, login prompt comes up and asks me for a username/password.  

But no matter what I put it I cannot browse the share.  Any idea why?

---

### Post by janpo on 2007-07-18
I was banging my head against the same issue, but found help in post #20
I just stuck an additional "auth sufficient pam_winbind.so" in /etc/pam.d/common-auth
( besides in common-account and common-password, dunno if it's required, bit it works )

---

### Post by mattcarus on 2007-09-06
I've gone through the process and the server is up and running on the domain and visible from windows clients. I'm struggling setting permissions though. I have a single share (called data) which is located at /home/data and has permissions 0777. I have made the /etc/fstab change (added acl as an option) but I can't change permissions/ownership from the windows client. Help!

Thanks in advance,
Matt

---

### Post by kpm on 2007-09-07
Hi, it has been some time since I first set up a server using this guide.  The first time went pretty much without a hitch, but I am getting a strange error that I can't find much out about in all my Google'n this time round...

It comes right at the point where I run the command 'testparm' after editing the smb.conf file:
"WARNING: passdb expand explicit = yes is deprecated"

Here is the full response to 'testparm' and the dump:

sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[data]"
Processing section "[printers]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
        workgroup = TOPLEVELDOMAIN
        realm = TOPLEVELDOMAIN.SECONDLEVELDOMAIN
        server string = %h server (Samba %v, Ubuntu)
        security = ADS
        allow trusted domains = No
        password server = domainControllerServer
        enable privileges = Yes
        log level = 3
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = host wins bcast
        time server = Yes
        printcap name = cups
        dns proxy = No
        wins server = 10.2.0.10
        idmap uid = 16777217-33554431
        idmap gid = 16777217-33554431
        template shell = /bin/bash
        printing = cups
        cups options = raw
        print command =
        lpq command = %p
        lprm command =

[data]
        comment = Share Data
        path = /home/data
        read only = No
        create mask = 0775
        force create mode = 0775
        force security mode = 0775
        directory mask = 0775
        force directory mode = 0775
        inherit permissions = Yes

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

Thanks for the help

---

### Post by kpm on 2007-09-07
Now when I try to join AD I get the following error, many of them...

[2007/09/07 13:11:32, 0] libads/kerberos.c:get_service_ticket(356)
get_service_ticket: kerberos_kinit_password SERVERNAME$@TLD.SLD@TLD.SLD failed: Preauthentication failed

Any ideas where I messed up??

---

### Post by bensode on 2007-10-01
I would suggest making one modification to the guide.  At the NET ADS JOIN command, you may not use dotted accounts.  In our AD setting (common a lot of places now) we use firstnane.lastname for user accounts in Windows.  For some odd reason issueing the net ads join command with a dotted account resulted in an ambiguous error.  Using the Administrator account or a single name admin account worked like a charm.  Thanks for the guide -- works great for 7.04.

---

### Post by Dimitri Street on 2007-10-22
Excellent guide.

I have successfully connected to the domain and I can see users, groups and passwords in the AD.

I can not logon to the server as a user from AD with

[email]username@DOMAIN.COM[/email]
password

Can someone point me to the right error log?

---

### Post by ddoctor on 2007-10-28
Hi,

I just wanted to point out a solution I had to a problem, which would be handy to include in the howto. 

sudo net ads join -U METNET\Administrator
gives this error:

Using short domain name -- METNET
Failed to set servicePrincipalNames. Please ensure that
the DNS domain of this server matches the AD domain,
Or rejoin with using Domain Admin credentials.
Deleted account for 'MOTHERSHIP' in realm 'METNET.LOCAL'
Failed to join domain: Type or value exists


This can be solved by editing /etc/hosts. There's a line in there for the local host something like:
192.168.0.4 machinename

this should be changed to:
192.168.0.4 machinename.domain.com machinename


Thanks to Dr. Hinrich Eilts for this solution ([http://www.mail-archive.com/samba@lists.samba.org/msg78822.html](http://www.mail-archive.com/samba@lists.samba.org/msg78822.html))

---

### Post by ddoctor on 2007-10-31
Hi,

I've tried this so many times its not funny. I've had some fails, some successes. Here are some answers/hints for you guys.


drewdown:
I'd suggest splitting this:
chown –R ‘domain\james.brown:domain\Domain Users' /home/data
into 2 statements:

chown -R 'domain\james.brown' /home/data
chgrp -R 'domain\Domain users' /home/data



Dimitri Street:
Try logging on as: DOMAIN\username
instead of username@DOMAIN
and use the shorthand version of the domain.
Also, ensure "winbind use default domain = yes", for this to work.

The username@domain (actually: username@REALM) syntax is supported (basically required) by Kerberos, but I'm not sure on the winbind support for this.

The samba 3.2 preview release notes support for logging on as "userPrincipalName" ([http://us4.samba.org/samba/ftp/pre/WHATSNEW-3-2-0pre1.txt](http://us4.samba.org/samba/ftp/pre/WHATSNEW-3-2-0pre1.txt)). I think this is the [email]username@domain.com[/email] syntax. 


bensode:
I have also had some trouble joining the domain using a user other than "Administrator". As is good practise, I disable "Administrator" and use a different username. Sometimes it works, sometimes it doesn't. Haven't tried with a dotted name, though, but yeah agree it should be added to the guide.


kpm:
Your Kerberos configuration is screwed. Review your krb5.conf and try and try and pass these tests before attempting to join the domain:
1. > kinit [email]username@domain.com[/email]
(enter password)
should give no errors
> klist
should list one ticket
> kdestroy
> klist
should list no tickets.

2. wbinfo -u and wbinfo -g should give you a list of your domain users and groups respectively.


kpm:
Re "passdb expand explicit = yes" is deprecated issue.
I think you may have had this setting in your smb.conf. I've had some trouble with testparm caching data before. Ironically, restarting samba and winbind daemons fixes it... ironic because you don't want to restart them to test the parameters :)


mattcarus:
I think there are some acl settings you need to add in smb.conf, maybe in the share settings. Not sure.



janpo:
I think pam_winbind.so is not required in common-session. I've got it in the other 3. However, this doesn't let me SSO to windows shares, so it might be needed there, too. I'll post results when I check that.

Also, I think your common-session requires a "pam_unix.so sufficient" in there. Sufficient means: if it passes, stop processing and succeed. So, if pam_unix.so and pam_winbind.so are in there, both "sufficient", the first one to pass will be the auth mechanism used. I also recommend putting a "pam_deny.so required" afterwards, to explicitly fail the logins if neither auth mechanism works. Here are my pam files:


common-auth:
auth        required      pam_env.so
auth        sufficient    pam_unix.so nullok try_first_pass
auth        sufficient    pam_winbind.so use_first_pass
auth        required      pam_deny.so

common-account (this might be dodgy):
account required pam_unix.so 
account [default=bad success=ok user_unknown=ignore] pam_winbind.so

common-password (might be dodgy - haven't tested pwd changes):
password sufficient pam_winbind.so 
password required pam_unix.so nullok obscure md5

common-session:
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
session required pam_unix.so 
session optional pam_foreground.so 


skarab:
You need to check your /etc/pam.d/sshd file. It may not be configured to use pam_winbind... or maybe its not including the other files. Be careful with it, though. As for the tty login, I think similar goes for the /etc/pam.d/login file.


416hammy:
I have had this issue, too... but can't remember how I fixed it. :) Sorry. Like all these problems, it's krb5.conf, smb.conf, nssswitch.conf and /etc/pam.d/*




Cheers,
DDoctor

---

### Post by danharper on 2008-03-13
I just have a few quaestions, 

I can't get my shares to work unless I set the actual directory permissions to 777.

eg, chmod -R 777 /home/data

tried chmod -R 755 /home/data along with chown, when I view the permissions of the shares in winodws I can see the groups I have added with chown but I can't modify the permissions or write to the directories.

I had used chown, but how do I add domain admins to have read and write permissions to the folder

Whta are the uids

Cheers Dan

---

### Post by collins_ on 2008-03-18
Thank you for your tutorial, but i didn't success because I can't import AD users thanks to winbind (but no problem for AD groups).
I'm able to have a correct answer with ''getent group'' and find AD groups, but i find no AD users with ''getent passwd''.
Of course I follow each state of your tutorial and I'm able to join my AD server.
 If someone have an idea ?

I put all my files and checks in this file : [http://cestouam.free.fr/megonfle.txt]("http://cestouam.free.fr/megonfle.txt")

I use a standard Gutsy Gibbon 

Thanks in advance,
Collins

------------------------------
NEWS : I relaunched the old-fashion debian installed on this computer, I did again all states of your tutorial and it works now :D :D :D, ubuntu will be for an other day...

---

### Post by jeculek on 2008-03-24
HI, Thanks for the great howto.
I tried to do everything according to the tutorial however after I configured winbind it didn't seem to work as planned. Here's my nsswitch.conf

passwd = compat winbind
group = compat winbind
shadow = compat winbind

hosts = files dns
networks = files
protocols = db files 
services = db files 
ethers = db files 
rpc = db files 
netgroup = files

I start samba/winbind and -
wbinfo -u works great as well as wbinfo -g but when I try  #getent passwd# it shows only local users,  any clues what I might have missed in configuration?

---

### Post by Keymaster on 2008-06-24
Rumor has it that this tutorial is the first step to getting openafs working on a Windows Domain.  I'm using Ubuntu 6.06 set up exactly like you described in the tutorial (minus IPs and domain name).  My ultimate goal is to get it so that when an XP Pro machine on the domain is logged into it has access to an AFS server that authenticates from active directory accounts.  I have seen this done at work, and am trying to set it up as an experiment.  here is what Im hoping for based on my jobs setup:
my 7 xp pro stations use MIT Kerberos For Windows and OpenAFS Client (both found at OpenAFS.org) to automap AFS drives that each different user has a personal storage space on. (ie other users only see their files when they log on not everyones)  So far my setup is as follows:
7 XP Pro stations with MIT KFW and OpenAFS Client installed (client fails to authenticate since AFS server isnt installed yet)  These stations joined the domain before the ubuntu server was setup (if that makes a difference)
my main server is Windows 2003 Enterprise edition with active directory setup on a domain.  The ubuntu server just added (finished your guide literally 2 minutes ago)  If you can provide a guide for AFS from this point on you'd be my idol for the month!  I know nothing about AFS, and very little about linux servers.  I know a decent amount of Server 2k3.  Thanks in advance.

---

### Post by iblazev on 2008-07-08
Thanx for the great howto:) 
I used it on Hardy and it worked well BUT that was yesterday. Today  I tried to open share on Ubuntu server and nothing happens (except error that I don't have permissions which is funny since everything was ok the night before).
I checked again wbinfo for users and groups and everything is as it was yesterday. Then I restarted winbind and samba as in tutorial and nothing changes. 
What else to try? 
Don't think that anyone else played with config files cause only I have the root pass. 
If anyone has any ideas, that would be nice:)

---

### Post by mhinrichsen on 2008-08-25
Check NTP. The clocks must be synched within 5 minutes for  Kerberos to work.

Michale

---

### Post by jim_harriger on 2008-11-25
Great write-up here! 

I'm trying to make this work at home, but with a few twists: i'm using Hardy ubuntu, and my AD domain controllers are Windows Server 2008. my DNS and ntp situation is clean (my AD server is NTP source, not ubuntu, but that shouldn't make a difference, should it?), but when i try to get a ticket, i get this:

kinit(v5): KDC reply did not match expectations while getting initial credentials

in addition, even though i have these lines in my krb5.conf, i get no logs in /var/log.

[logging]
        default = FILE:/var/log/krb5.log
        kdc = FILE:/var/log/krb5kdc.log
        admin_server = FILE:/var/log/kadmin.log

any ideas what i've done wrong here? is a daemon that needs to be started? any more information that might help? thanks, all!

Jim Harriger

---

### Post by aphexvw on 2009-07-07
great write up.

I have followed the above and can authenticate on ads.
I can see individual printers when i add them through samba.

Is there a way to inherit all printers shared out onto the ad?

---

### Post by izaakrach on 2010-01-07
This was a great tutorial but I still didn't get it to work.  I'm using Karmic Server and when I attempt to join AD I get the following error:

[2010/01/06 21:39:58,  0] libads/sasl.c:819(ads_sasl_spnego_bind)
  kinit succeeded but ads_sasl_spnego_krb5_bind failed: Invalid credentials
Failed to join domain: failed to connect to AD: Invalid credentials

When I run klist I get the following result:

Valid starting     Expires            Service principal
01/06/10 00:30:29  01/06/10 10:30:48  krbtgt/PHARMACY.NVBOP@PHARMACY.NVBOP
    renew until 01/07/10 00:30:29

This looks like a valid ticket to me but I'm no expert.  

My AD server netbios name is NVBOP-DB
My domain is pharmacy.nvbop
All of my windows machines joined successfully 

This is my krb5.conf
********************************************************
[logging]

default = FILE:/var/log/krb5.log
kdc = FILE:/var/log/krb5kdc.log
admin_server = FILE:/var/log/kadmin.log


[libdefaults]
default_realm = PHARMACY.NVBOP
dns_lookup_realm = false
dns_lookup_kdc = true

[appdefaults]
pam = {
debug = false
ticket_lifetime = 36000
renew_lifetime = 36000
forwardable = true
krb4_convert = false
}
****************************************************


This is my smb.conf
*********************************************************
#/etc/samba/smb.conf
[global]

workgroup = PHARMACY
realm = PHARMACY.NVBOP
server string = %h server (Samba %v, Ubuntu)
wins server = 10.0.0.201
password server = NVBOP-DB
enable privileges =Yes
allow trusted domains = No
dns proxy = no
name resolve order = host wins bcast
log file = /var/log/samba/log.%m
max log size = 1000
log level = 3
security = ADS
encrypt passwords = true
socket options = TCP_NODELAY
time server = Yes
map to guest = nobody
idmap uid = 16777217-33554431
idmap gid = 16777217-33554431
winbind enum users = yes
winbind enum groups = yes
printcap name = cups
printing = cups
cups options = raw
template shell = /bin/bash

[data]
comment = Share Data
path = /home/data
read only = No
create mask = 0775
directory mask = 0775
browsable = Yes
public = Yes
writeable = Yes
force create mode = 0775
force directory mode = 0775
force security mode = 0775
guest ok = no
inherit permissions = yes
nt acl support = yes
[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
public = no
writable = no
create mode = 0700
******************************************************
Any help is greatly appreciated in advance.

---

### Post by Pritamsng on 2010-02-10
thanks

---

