---
title: "Need help with CUPS"
date: 2015-06-06
forum: New to Ubuntu
---

### Post by torbuck on 2015-06-06
Greetings,

I am quite new with Ubuntu. I have recently configured a Ubuntu Server 14.04.2 along with CUPS 1.7.2. I am trying to share a HP USB LaserJet 1320 with CUPS on my home network. Initially, I was successful with setting up the printer in CUPS (I could perform
a successful print test from within CUPS) however I never had any luck with printing to the shared printer via a Windows 8.1 computer. I could successfully browse to the printer on my Windows PC, however anytime I tried to print, I could see the printer
status light blink, but nothing would ever print. To add further grief, it appears that I am now having some access problems from within CUPS. If I try to delete the printer from within CUPS to try another print driver, I can successfully access the CUPS web portal, select Manage Printers, select the printer queue, however when I choose delete printer from the drop down box, I get a Secure Connection Failed page, or sometimes simply a "unable to connect". 

Any ideas as to what I can do to get CUPS to function. Let me know if there are any logs I can post

Cheers,

Torbuck

---

### Post by torbuck on 2015-06-06
[FONT=verdana]Okay, appears that I fixed the Secure Connection Failed page error. I added this entry to my cupsd.conf:[/FONT]

[FONT=courier new]DefaultAuthType Basic
DefaultEncryption IfRequested[/FONT]

[FONT=verdana]I can now access the area in CUPS to delete a printer without the Secure Connection Failed page, however now when I try to delete the printer, I get a "The connection was reset" page[/FONT]

---

### Post by tgalati4 on 2015-06-06
Welcome to the forums. "Recently configured server" implies that perhaps not all system updates have been applied.  Open a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

Reboot if any kernel or xorg updates are applied.

CUPS keeps its log files in /var/log/cups.  Look through those and see what errors pop up.  Normally you need root privilege to delete printers.  Are you logged in as the primary user with root privileges?  

Try installing the printer with the HP installer:

```
which hp-toolbox
hp-toolbox
```

If it is not installed:

```
sudo apt-get install hplip
```

---

### Post by torbuck on 2015-06-07
I performed the updates as you has described and then rebooted the server. As for CUPS, I am logging into CUPS with the primary user with root privileges. Here is the CUPS access log file:

[FONT=courier new]192.168.0.192 - - [07/Jun/2015:10:24:59 -0700] "POST /admin/ HTTP/1.1" 200 100 - -
192.168.0.192 - - [07/Jun/2015:10:24:59 -0700] "POST /admin/ HTTP/1.1" 200 2653 - -
192.168.0.192 - - [07/Jun/2015:10:25:00 -0700] "POST /admin/ HTTP/1.1" 200 123 - -
localhost - - [07/Jun/2015:10:25:00 -0700] "POST /admin/ HTTP/1.1" 401 139 CUPS-Delete-Printer successful-ok
192.168.0.192 - - [07/Jun/2015:10:25:00 -0700] "POST /admin/ HTTP/1.1" 401 123 - -
192.168.0.192 - - [07/Jun/2015:10:25:00 -0700] "POST /admin/ HTTP/1.1" 200 123 - -
192.168.0.192 - - [07/Jun/2015:10:27:04 -0700] "POST /admin HTTP/1.1" 200 111 - -
localhost - - [07/Jun/2015:10:27:04 -0700] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - -
192.168.0.192 - - [07/Jun/2015:10:27:04 -0700] "POST /admin HTTP/1.1" 401 111 - -
192.168.0.192 - - [07/Jun/2015:10:27:04 -0700] "POST /admin HTTP/1.1" 200 111 - -
192.168.0.192 - - [07/Jun/2015:10:27:50 -0700] "POST /admin HTTP/1.1" 200 127 - -
localhost - - [07/Jun/2015:10:27:50 -0700] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - -
192.168.0.192 - - [07/Jun/2015:10:27:50 -0700] "POST /admin HTTP/1.1" 401 127 - -
192.168.0.192 - - [07/Jun/2015:10:27:50 -0700] "POST /admin HTTP/1.1" 200 127 - -
192.168.0.192 - - [07/Jun/2015:10:30:20 -0700] "POST /admin/ HTTP/1.1" 200 62 - -
192.168.0.192 - - [07/Jun/2015:10:30:20 -0700] "POST /admin/ HTTP/1.1" 200 12144 - -

[/FONT][FONT=verdana]The above log doesn't seem indicative to what I am experiencing. I'm still having this problem where when I try to delete the existing printer
queue, I'm taken to a "page cannot be displayed". I am performing this via from my browser on my Windows PC (tried both Firefox and IE). I typically
don't use IE, but when I tried, I was prompted with logon credentials to delete the printer. I entered in my admin account and still got the "this page
cannot be displayed".  One other thing I should point out is that the page and error logs are 0kb, so no log is getting created. The only log that
is getting created is the access log. 

Here is my CUPS config file:

[FONT=courier new]#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#[/FONT][/FONT] 
[FONT=courier new]# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn[/FONT]
 
[FONT=courier new]# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0[/FONT]
 
[FONT=courier new]# Only listen for connections from the local machine.
Port 631
Listen /var/run/cups/cups.sock[/FONT]
 
[FONT=courier new]# Show shared printers on the local network.
Browsing Off
BrowseLocalProtocols dnssd[/FONT]
 
[FONT=courier new]# Default authentication type, when authentication is required...
DefaultAuthType Basic
DefaultEncryption IfRequested[/FONT]
 
[FONT=courier new]# Web interface setting...
WebInterface Yes[/FONT]
 
[FONT=courier new]# Restrict access to the server...
<Location />
  Order allow,deny
Allow all
</Location>[/FONT]
 
[FONT=courier new]# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
Allow all
</Location>[/FONT]
 
[FONT=courier new]# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
Allow all
</Location>[/FONT]
 
[FONT=courier new]# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default[/FONT]
 
[FONT=courier new]  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  <Limit All>
    Order deny,allow
  </Limit>
</Policy>[/FONT]
 
[FONT=courier new]# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default[/FONT]
 
[FONT=courier new]  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>[/FONT]
 
[FONT=courier new]  <Limit All>
    Order deny,allow
  </Limit>
</Policy>[/FONT]
 
[FONT=courier new]#
#
[/FONT]
[FONT=courier new]
[FONT=Verdana]I am interested if the [FONT=Courier New]Only listen for connections from the local machine[/FONT] [FONT=verdana]entry needs to be modified. Also, from Googling  various forums, I have been mucking with the SAMBA config file to get this to work, but thinking I have
done something in SAMBA that could have caused this grief. Here is my SAMBA config file:

[FONT=courier new]#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. [/FONT][/FONT][/FONT][/FONT]
[FONT=courier new]#======================= Global Settings =======================[/FONT]
[FONT=courier new][global]
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 log file = /var/log/samba/log.%m
 path = /var/spool/samba
 workgroup = MY WORKGROUP NAME
 passwd program = /usr/bin/passwd %u
 obey pam restrictions = yes
 usershare allow guests = yes
 panic action = /usr/share/samba/panic-action %d
 syslog = 0
 server role = standalone server
 dns proxy = no
 unix password sync = yes
 guest account = PRIMARY ADMIM ACCOUNT WITH ROOT PRIVLIEGES
 printer = HP_LaserJet_1320_series
 server string = %h server (Samba, Ubuntu)
 map to guest = bad user
 passdb backend = tdbsam
 public = yes
 max log size = 1000
 pam password change = yes[/FONT]
[FONT=courier new]## Browsing/Identification ###[/FONT]
[FONT=courier new]# Change this to the workgroup/NT-domain name your Samba server will part of[/FONT]
[FONT=courier new]# server string is the equivalent of the NT Description field[/FONT]
[FONT=courier new]# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no[/FONT]
[FONT=courier new]# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z[/FONT]
[FONT=courier new]# This will prevent nmbd to search for NetBIOS names through DNS.[/FONT]
[FONT=courier new]#### Networking ####[/FONT]
[FONT=courier new]# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0[/FONT]
[FONT=courier new]# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes[/FONT]
[FONT=courier new] 
#### Debugging/Accounting ####
[FONT=Verdana][FONT=verdana] 
[FONT=courier new]# This tells Samba to use a separate log file for each machine
# that connects[/FONT]
[FONT=courier new]# Cap the size of the individual log files (in KiB).[/FONT]
[FONT=courier new]# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no[/FONT]
[FONT=courier new]# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.[/FONT]
[FONT=courier new]# Do something sensible when Samba crashes: mail the admin a backtrace[/FONT]
[FONT=courier new]
####### Authentication #######[/FONT]
[FONT=courier new]# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.[/FONT]
[FONT=courier new]# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  [/FONT]
[FONT=courier new]
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.[/FONT]
[FONT=courier new]# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<[EMAIL="kahan@informatik.tu-muenchen.de"]kahan@informatik.tu-muenchen.de[/EMAIL]> for
# sending the correct chat script for the passwd program in Debian Sarge).[/FONT]
[FONT=courier new]# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.[/FONT]
[FONT=courier new]# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections[/FONT]
[FONT=courier new]########## Domains ###########[/FONT]
[FONT=courier new]#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#[/FONT]
[FONT=courier new]# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = [\\%N\profiles\%U]("file://\\%N\profiles\%U")
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = [\\%N\%U\profile]("file://\\%N\%U\profile")[/FONT]
[FONT=courier new]# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = [\\%N\%U]("file://\\%N\%U")[/FONT]
[FONT=courier new]# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd[/FONT]
[FONT=courier new]# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u[/FONT]
[FONT=courier new]# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u[/FONT]
[FONT=courier new]# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g[/FONT]
[FONT=courier new]############ Misc ############[/FONT]
[FONT=courier new]# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m[/FONT]
[FONT=courier new]# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash[/FONT]
[FONT=courier new]# Setup usershare options to enable non-root users to share folders
# with the net usershare command.[/FONT]
[FONT=courier new]# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100[/FONT]
[FONT=courier new]# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones[/FONT]
[FONT=courier new]#======================= Share Definitions =======================[/FONT]
[FONT=courier new]# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as [\\server\username]("file://\\server\username")
;[homes]
;   comment = Home Directories
;   browseable = no[/FONT]
[FONT=courier new]# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes[/FONT]
[FONT=courier new]# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700[/FONT]
[FONT=courier new]# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700[/FONT]
[FONT=courier new]# By default, [\\server\username]("file://\\server\username") shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to [\\server\username]("file://\\server\username")
# This might need tweaking when using external authentication schemes
;   valid users = %S[/FONT]
[FONT=courier new]# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes[/FONT]
[FONT=courier new]# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700[/FONT]
[FONT=courier new][printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   use client driver = yes
   create mask = 0700[/FONT]
[FONT=courier new]# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin[/FONT]
[FONT=courier new]
[NUCmedia]
 path = /mnt/NUCStorage/
 writeable = yes

[FONT=verdana]Let me know if you see anything wonky

Thanks![/FONT][/FONT]
[/FONT][/FONT][/FONT]

---

### Post by tgalati4 on 2015-06-07
Open a local browser on the server:  [http://localhost:631](http://localhost:631)

Click on the "Administration" tab.  Under "Server Settings" on the right column is a checkbox for "Allow Remote Administration".  Check that then restart the server (which I believe happens automatically).  If you are still having problems, check the "Save debugging information for troubleshooting".  Warning:  this generates A LOT of output, so only use it when all else fails.

Now try performing some admin duties from another machine on the same network and on a different network.

---

