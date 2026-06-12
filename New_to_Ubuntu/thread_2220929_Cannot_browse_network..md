---
title: "Cannot browse network."
date: 2014-04-29
forum: New to Ubuntu
---

### Post by paul1945 on 2014-04-29
Installed Ubuntu 14.04 and am unable to browse the Windows network.
I think it is because Ubuntu attached itself to "workgroups" rather than "mshome" to which the computers of the network are connected; "workgroups" is used by two network printers; the other computers are on "mshome".
 Changed "workgroups" in smb.conf to "mshome" but now nothing lists.
How do I change Ubuntu 14.04 to link to "mshome"?
Any help would be appreciated. Thanks, Paul.

---

### Post by papibe on 2014-04-29
Hi paul1945.

Did you restart samba? If not, you would need to do it:
```
sudo service smbd restart
```
After that, could you post the result of this command?
```
smbtree
```
Regards.

---

### Post by paul1945 on 2014-04-30
Thanks for that, this is what comes up: 

paul@hermes-III:~$ smbtree
Enter paul's password: 
Conversion error: Incomplete multibyte sequence()
Conversion error: Incomplete multibyte sequence()
paul@hermes-III:~$

---

### Post by bab1 on 2014-04-30
> **paul1945 said:**
> Thanks for that, this is what comes up: 

paul@hermes-III:~$ smbtree
Enter paul's password: 
Conversion error: Incomplete multibyte sequence()
Conversion error: Incomplete multibyte sequence()
paul@hermes-III:~$

Use more debugging like this ```
smbtree -d3
```

You can have multiple workgroups.  Click on the "Windows Networks" Icon and drill down.

---

### Post by paul1945 on 2014-05-01
Sorry about the delay, it appears that I downloaded and installed the Chinese language version in error, so I have just re-installed the correct version of Ubuntu 14.04 LTS.
Anyhow, the problem persists and it appears that the stumbling block is MSHOME as the network printer shows up fine in the file manager under WORKGROUPS. Unfortunately my other computers are all connected under MSHOME, which I cannot browse under Ubuntu.
Equally "GNOME Commander" also complains it cannot open the network, and wants to know if the smb module is installed. 
Anyhow, here is the smbtree -d3 output:
```

paul@Hermes-III:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.7 bcast=192.168.1.255 netmask=255.255.255.0
Enter paul's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name MSHOME WORKGROUP<0x1d>
E2BIG: convert_string(UTF-8,CP850): srclen=17 destlen=16 - 'MSHOME WORKGROUP'
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb82e3990] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME WORKGROUP<0x1b>
E2BIG: convert_string(UTF-8,CP850): srclen=17 destlen=16 - 'MSHOME WORKGROUP'
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb82e3970] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name ##__MSBROWSE__#<0x1>
Got a positive name query response from 192.168.1.7 ( 192.168.1.7 )
Got a positive name query response from 192.168.1.3 ( 192.168.1.3 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb82e4138] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.7 ( 192.168.1.7 )
Connecting to 192.168.1.7 at port 445
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
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.7 ( 192.168.1.7 )
Connecting to 192.168.1.7 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\RNPD41B03              
name_resolve_bcast: Attempting broadcast lookup for name RNPD41B03<0x20>
Got a positive name query response from 192.168.1.15 ( 192.168.1.15 )
Connecting to 192.168.1.15 at port 445
Connecting to 192.168.1.15 at port 139
Server requested LM password but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
Server requested PLAINTEXT password but 'client plaintext auth = no' or 'client ntlmv2 auth = yes'
    \\NPI80D256              
name_resolve_bcast: Attempting broadcast lookup for name NPI80D256<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb82f6bd0] mpx_fde[(nil)] fd[12] - disabling
resolve_hosts: Attempting host lookup for name NPI80D256<0x20>
resolve_hosts: getaddrinfo failed for name NPI80D256 [Name or service not known]
resolve_lmhosts: Attempting lmhosts lookup for name NPI80D256<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name NPI80D256<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
    \\HERMES-III             Hermes-III server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name HERMES-III<0x20>
Got a positive name query response from 192.168.1.7 ( 192.168.1.7 )
Connecting to 192.168.1.7 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\HERMES-III\Hewlett-Packard-HP-LaserJet-M2727nf-MFP    Hewlett-Packard HP LaserJet M2727nf MFP
        \\HERMES-III\LANIER-LP440c-SP-C811DNCMD:PS    LANIER LP440c/SP C811DNCMD:PS
        \\HERMES-III\IPC$               IPC Service (Hermes-III server (Samba, Ubuntu))
        \\HERMES-III\Downloads          Home Directories
        \\HERMES-III\PUBLIC             Home Directories
        \\HERMES-III\print$             Printer Drivers
MSHOME
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.3 ( 192.168.1.3 )
Connecting to 192.168.1.3 at port 445
Connecting to 192.168.1.3 at port 139
convert_string_talloc: Conversion error: Incomplete multibyte sequence()
Conversion error: Incomplete multibyte sequence()
Connecting to 192.168.1.3 at port 445
Connecting to 192.168.1.3 at port 139
convert_string_talloc: Conversion error: Incomplete multibyte sequence()
Conversion error: Incomplete multibyte sequence()
paul@Hermes-III:~$
```

---

### Post by bab1 on 2014-05-01
> **paul1945 said:**
> Sorry about the delay, it appears that I downloaded and installed the Chinese language version in error, so I have just re-installed the correct version of Ubuntu 14.04 LTS.
Anyhow, the problem persists and it appears that the stumbling block is MSHOME as the network printer shows up fine in the file manager under WORKGROUPS. Unfortunately my other computers are all connected under MSHOME, which I cannot browse under Ubuntu.
Equally "GNOME Commander" also complains it cannot open the network, and wants to know if the smb module is installed. 
Anyhow, here is the smbtree -d3 output:

```
paul@Hermes-III:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.7 bcast=192.168.1.255 netmask=255.255.255.0
Enter paul's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name MSHOME WORKGROUP<0x1d>
E2BIG: convert_string(UTF-8,CP850): srclen=17 destlen=16 - 'MSHOME WORKGROUP'
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb82e3990] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME WORKGROUP<0x1b>
E2BIG: convert_string(UTF-8,CP850): srclen=17 destlen=16 - 'MSHOME WORKGROUP'
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb82e3970] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name ##__MSBROWSE__#<0x1>
Got a positive name query response from 192.168.1.7 ( 192.168.1.7 )
Got a positive name query response from 192.168.1.3 ( 192.168.1.3 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb82e4138] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.7 ( 192.168.1.7 )
Connecting to 192.168.1.7 at port 445
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
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.7 ( 192.168.1.7 )
Connecting to 192.168.1.7 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\RNPD41B03              
name_resolve_bcast: Attempting broadcast lookup for name RNPD41B03<0x20>
Got a positive name query response from 192.168.1.15 ( 192.168.1.15 )
Connecting to 192.168.1.15 at port 445
Connecting to 192.168.1.15 at port 139
Server requested LM password but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
Server requested PLAINTEXT password but 'client plaintext auth = no' or 'client ntlmv2 auth = yes'
    \\NPI80D256              
name_resolve_bcast: Attempting broadcast lookup for name NPI80D256<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb82f6bd0] mpx_fde[(nil)] fd[12] - disabling
resolve_hosts: Attempting host lookup for name NPI80D256<0x20>
resolve_hosts: getaddrinfo failed for name NPI80D256 [Name or service not known]
resolve_lmhosts: Attempting lmhosts lookup for name NPI80D256<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name NPI80D256<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
    \\HERMES-III             Hermes-III server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name HERMES-III<0x20>
Got a positive name query response from 192.168.1.7 ( 192.168.1.7 )
Connecting to 192.168.1.7 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\HERMES-III\Hewlett-Packard-HP-LaserJet-M2727nf-MFP    Hewlett-Packard HP LaserJet M2727nf MFP
        \\HERMES-III\LANIER-LP440c-SP-C811DNCMD:PS    LANIER LP440c/SP C811DNCMD:PS
        \\HERMES-III\IPC$               IPC Service (Hermes-III server (Samba, Ubuntu))
        \\HERMES-III\Downloads          Home Directories
        \\HERMES-III\PUBLIC             Home Directories
        \\HERMES-III\print$             Printer Drivers
MSHOME
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.3 ( 192.168.1.3 )
Connecting to 192.168.1.3 at port 445
Connecting to 192.168.1.3 at port 139
convert_string_talloc: Conversion error: Incomplete multibyte sequence()
Conversion error: Incomplete multibyte sequence()
Connecting to 192.168.1.3 at port 445
Connecting to 192.168.1.3 at port 139
convert_string_talloc: Conversion error: Incomplete multibyte sequence()
Conversion error: Incomplete multibyte sequence()
paul@Hermes-III:~$
```

You should post the output using ```
 blocks as I have above.  It preserves the text formatting and makes it easier to read,  To that you click on the [SIZE=5]# [/SIZE]icon at the top of the advanced editor and place the text between the blocks.  

 I see an error tha needs to be addressed.  See here[CODE]name_resolve_bcast: Attempting broadcast lookup for name [COLOR="#FF0000"]MSHOME WORKGROUP[/COLOR]<0x1b>
E2BIG: convert_string(UTF-8,CP850): srclen=17 destlen=16 -[COLOR="#FF0000"] 'MSHOME WORKGROUP'[/COLOR]
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb82e3970] mpx_fde[(nil)] fd[7] - disabling
```

Post the output of ```
cat /etc/samba/smb.conf
```

---

### Post by paul1945 on 2014-05-01
Sorry, am not conversant in all the features of the posting editor.
But thanks for that.
Anyhow, here it is:

```
paul@Hermes-III:~$ sudo cat /etc/samba/smb.conf
[sudo] password for paul: 
Sorry, try again.
[sudo] password for paul: 
#
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
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME WORKGROUP
name resolve order = bcast host lmhosts wins

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
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
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = yes
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
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[PUBLIC]
path = /home/paul/Downloads
valid users = paul
read only = no
create mask = 0775

[Downloads]
path = /home/paul/Downloads
create mask = 0775
browseable = yes
writable = yes
valid users = paul


paul@Hermes-III:~$ 


```

---

### Post by bab1 on 2014-05-01
> **paul1945 said:**
> Sorry, am not conversant in all the features of the posting editor.
But thanks for that.
Anyhow, here it is:

```
paul@Hermes-III:~$ sudo cat /etc/samba/smb.conf
[sudo] password for paul: 
Sorry, try again.
[sudo] password for paul: 
#
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
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME WORKGROUP
name resolve order = bcast host lmhosts wins

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
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
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = yes
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
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[PUBLIC]
path = /home/paul/Downloads
valid users = paul
read only = no
create mask = 0775

[Downloads]
path = /home/paul/Downloads
create mask = 0775
browseable = yes
writable = yes
valid users = paul


paul@Hermes-III:~$ 


```

The ***first*** problem is this```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = [COLOR="#FF0000"]MSHOME [/COLOR][COLOR="#0000FF"]WORKGROUP[/COLOR]
```...you can have one ***or*** the other, *not both*.

The setting is only for the primary group.  This only means which one is displayed *alongside* the "Windows Network".  The other one is displayed inside the "Windows Network" icon.  Edit the smb.conf file to fit your situation.

The ***second*** problem is the homes definition shown below```
;[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

```...if you are not going to use the [homes] share then you need to place comments (using a [SIZE=3]; [/SIZE] or a [SIZE=3]#[/SIZE] at the beginning of each line.

The ***third*** problem I see is these 2 share definitions```
[PUBLIC]
path = /home/paul/Downloads
valid users = paul
read only = no
create mask = 0775

[Downloads]
path = /home/paul/Downloads
create mask = 0775
browseable = yes
writable = yes
valid users = paul
```...You have 2 definitions pointing to the same directory.  Let's delete one of them.  If this is to be a private share then all you need is to not explicitly allow the guest user.  That would allow only the Samba users access.  If you want to limit this to specific user then you use valid users.  Delete  the share that you don't want and refine the one you are keeping.

All of the terms used in the smb.conf file are listed in the man pages.  From the terminal do this to see them```
man smb.conf
```

---

### Post by paul1945 on 2014-05-02
Thanks for all that, it's appreciated.
As far as the smb.conf is concerned, I changed everything as suggested, and got this:
```
paul@Hermes-III:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.7 bcast=192.168.1.255 netmask=255.255.255.0
Enter paul's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Connecting to 192.168.1.3 at port 445
Connecting to 192.168.1.3 at port 139
convert_string_talloc: Conversion error: Incomplete multibyte sequence()
Conversion error: Incomplete multibyte sequence()
Connecting to 192.168.1.3 at port 445
Connecting to 192.168.1.3 at port 139
convert_string_talloc: Conversion error: Incomplete multibyte sequence()
Conversion error: Incomplete multibyte sequence()
paul@Hermes-III:~$ 

```
And it looks as though things have not changed.
I have a couple of comments that may help:
1. Maybe the scan by Ubuntu 14.04 is not persistent (long) enough, as a scan with one of the Windows machines suggests that some of the servers take a few seconds to come up.
2. I have a ".gvfs" directory in "/home/paul/".  I recall using this directory to access the different mounted servers when running Ubuntu 13.10, but in this install it is marked root and I cannot access it.
3. When I set "Workgroups" instead of "MSHOME" in smb.conf, "Workgroups" shows under "Windows Network" when browsing through the file system and so does "MSHOME". In this case I can only browse "Workgroups" however (it only has some printers), not "MSHOME" (to which my computers are linked), it locks me out. If I set "MSHOME" nothing shows up at all under "Windows Networks"
4. I am using the same smb.conf as I used on Ubuntu 13.10 - apart from the changes suggested above - and that worked fine on that version. So obviously something is different in this version. As it is a clean install, due to a failed upgrade and the subsequent installation of the wrong variant, the problem must be inherent in the install.
Thanks, Paul.

---

### Post by bab1 on 2014-05-02
> **paul1945 said:**
> Thanks for all that, it's appreciated.
As far as the smb.conf is concerned, I changed everything as suggested, and got this:
```

[COLOR="#FF0000"]convert_string_talloc: Conversion error: Incomplete multibyte sequence()
Conversion error: Incomplete multibyte sequence()[/COLOR]

```
And it looks as though things have not changed.

Things have changed.  We are down to one problem only.  The problem is noted above in red.  It is unusual.  If you google the term you will find minimal information.  What you do find is a reference to an internal bug that was taken care off in 2012.  This shouldn't affect 13.04/13.10/14.04 at all.  It involve users with that use non ASCI characters.  What language are you using for the system.
> 
I have a couple of comments that may help:
1. Maybe the scan by Ubuntu 14.04 is not persistent (long) enough, as a scan with one of the Windows machines suggests that some of the servers take a few seconds to come up.

This is not a timing issue see my comments above.
> 
2. I have a ".gvfs" directory in "/home/paul/".  I recall using this directory to access the different mounted servers when running Ubuntu 13.10, but in this install it is marked root and I cannot access it.

The developers moved the gvfs directory.  I believe it is now under /run or some such.
> 
3. When I set "Workgroups" instead of "MSHOME" in smb.conf, "Workgroups" shows under "Windows Network" when browsing through the file system and so does "MSHOME". In this case I can only browse "Workgroups" however (it only has some printers), not "MSHOME" (to which my computers are linked), it locks me out. If I set "MSHOME" nothing shows up at all under "Windows Networks"

See the above problem.  We can't do anything until we resolve that issue.
> 
4. I am using the same smb.conf as I used on Ubuntu 13.10 - apart from the changes suggested above - and that worked fine on that version. So obviously something is different in this version. As it is a clean install, due to a failed upgrade and the subsequent installation of the wrong variant, the problem must be inherent in the install.
Thanks, Paul.
I agree.  The problem may be the language pack.  I would file a bug report at Launchpad regarding this issue.

If I was you I would revert back to the version of Ubuntu that Samba works on and wait until at least Ubuntu 14.04.1.  I use Ubuntu 12.04 right now.  I have a test machine running 14.04.  I have found enough problems that I won't be using it yet.

---

### Post by paul1945 on 2014-05-02
Hello BAB1,
The language I am using is English (US) - with Australian settings; the latter of which only affects the date display.
re. 1. Thanks for that comment, that does in the possibility that a simple extended timing loop may help.
re. 2. I have found the directory; it's in /run/user/1000/gvfs 
As far as reverting back is concerned, I use the machine for both work and study. I have already invested days of work in getting it all set up and running; I am now on the high seas and will have to keep bailing water, as I simply don't have time to start all over again.
Regards, Paul.

---

### Post by bab1 on 2014-05-02
> **paul1945 said:**
> Hello BAB1,
The language I am using is English (US) - with Australian settings; the latter of which only affects the date display.

I wonder if the "Australian settings" have caused a problem.  The error looks to be due to extended characters.  None of this stuff is ASCI anymore.
> 
re. 1. Thanks for that comment, that does in the possibility that a simple extended timing loop may help.
re. 2. I have found the directory; it's in /run/user/1000/gvfs

post the output of ```
ls -al /run/user/1000 
```
>  
As far as reverting back is concerned, I use the machine for both work and study. I have already invested days of work in getting it all set up and running; I am now on the high seas and will have to keep bailing water, as I simply don't have time to start all over again.
Regards, Paul.
I understand.  I hope you understand that this is the very first time that Samba4 is the default in Ubuntu.  We are less than a moth into this distro.  In fact this is still in development as far as Ubuntu is concerned.  The stable version will be released in July.

I've not seen this problem myself.  I will try and help.  I think you might also look to the samba.org mailing lists for help.

---

### Post by paul1945 on 2014-05-04
Again thanks for the information.
Please find below the listing of /run/user/1000/

```
paul@Hermes-III:~$ sudo ls -al /run/user/1000/
[sudo] password for paul: 
ls: cannot access /run/user/1000/gvfs: Permission denied
total 8
drwx------ 9 paul paul 240 May  4 13:39 .
drwxr-xr-x 3 root root  60 May  4 13:39 ..
drwx------ 2 paul paul  60 May  4 14:01 dconf
d????????? ? ?    ?      ?            ? gvfs
drwx------ 2 paul paul  40 May  4 13:39 gvfs-burn
drwx------ 2 paul paul 120 May  4 13:39 keyring-NrFutq
drwx------ 2 paul paul  80 May  4 13:39 pulse
drwx------ 2 paul paul  40 May  4 13:39 unity
drwx------ 3 paul paul  60 May  4 13:39 upstart
-rw-r--r-- 1 paul paul   5 May  4 13:39 upstart-dbus-bridge.1117.pid
-rw-r--r-- 1 paul paul   5 May  4 13:39 upstart-file-bridge.1117.pid
lrwxrwxrwx 1 root root  17 May  4 13:39 X11-display -> /tmp/.X11-unix/X0
paul@Hermes-III:~$
```

I have also have found that I can mount shares on my network through Gigolo, except for one share which is a little NAS that runs a Linux variant called Snake-OS (and a cut-down version of Samba), because it times out. So timing is a problem with one member of my network. Regards, Paul.

---

### Post by bab1 on 2014-05-04
> **paul1945 said:**
> Again thanks for the information.
Please find below the listing of /run/user/1000/

```
paul@Hermes-III:~$ [COLOR="#FF0000"]sudo ls -al /run/user/1000/[/COLOR]
[sudo] password for paul: 
ls: cannot access /run/user/1000/gvfs: Permission denied
total 8
drwx------ 9 paul paul 240 May  4 13:39 .
drwxr-xr-x 3 root root  60 May  4 13:39 ..
drwx------ 2 paul paul  60 May  4 14:01 dconf
d????????? ? ?    ?      ?            ? gvfs
drwx------ 2 paul paul  40 May  4 13:39 gvfs-burn
drwx------ 2 paul paul 120 May  4 13:39 keyring-NrFutq
drwx------ 2 paul paul  80 May  4 13:39 pulse
drwx------ 2 paul paul  40 May  4 13:39 unity
drwx------ 3 paul paul  60 May  4 13:39 upstart
-rw-r--r-- 1 paul paul   5 May  4 13:39 upstart-dbus-bridge.1117.pid
-rw-r--r-- 1 paul paul   5 May  4 13:39 upstart-file-bridge.1117.pid
lrwxrwxrwx 1 root root  17 May  4 13:39 X11-display -> /tmp/.X11-unix/X0
paul@Hermes-III:~$
```

When you use sudo you are running the command as the root user (see red above).  This is **not** what we need to do.  When you are browsing you are doing that as the user paul.  I you state you can't browse the shares then we need to test as the user not as root.
> 
I have also have found that I can mount shares on my network through Gigolo, except for one share which is a little NAS that runs a Linux variant called Snake-OS (and a cut-down version of Samba), because it times out. So timing is a problem with one member of my network. Regards, Paul.
Gigolo also uses gvfs libraries so it should be the same.  My guess is that the cut down version of Samba is Samba v2.

Let's restate what the problem is now.  Are the shares that you can't brows on the NAS that is running Snake-OS (and a cut-down version of Samba)?

Post the output of ```
ls -al /run/user/1000/
```... no sudo this time.

---

### Post by paul1945 on 2014-05-04
Sorry, I should have stuck to the directions without embellishment.
As far as my network access is concerned, I cannot browse the network at all through the Ubuntu file manager, when I click on "browse network" it shows the "MSHOME" folder, but if I click on that it is empty.
I can connect to a server with that facility by typing in "smb://server/" where the server is the respective machine name, and select a directory, which will then mount, but as I said I cannot do this with the little Linux NAS, it comes up with an error:
```
Oops! Something went wrong.
Unhandled error message: failed to retrieve share list from server: connection timed out.
```
As the NAS is my hub for storing information and automatic record updating, that can be accessed by both my and my wife's computer, this is a problem.
I also have an old notebook that has Linux installed and I have no problems mounting the shares of that machine.
Anyhow, here is the listing, done correctly this time, I hope:
```
paul@Hermes-III:~$ ls -al /run/user/1000
total 8
drwx------ 9 paul paul 240 May  5 10:27 .
drwxr-xr-x 3 root root  60 May  5 10:27 ..
drwx------ 2 paul paul  60 May  5 10:29 dconf
dr-x------ 4 paul paul   0 May  5 10:27 gvfs
drwx------ 2 paul paul  40 May  5 10:27 gvfs-burn
drwx------ 2 paul paul 120 May  5 10:27 keyring-wKhguQ
drwx------ 2 paul paul  80 May  5 10:27 pulse
drwx------ 2 paul paul  40 May  5 10:27 unity
drwx------ 3 paul paul  60 May  5 10:27 upstart
-rw-r--r-- 1 paul paul   5 May  5 10:27 upstart-dbus-bridge.1126.pid
-rw-r--r-- 1 paul paul   5 May  5 10:27 upstart-file-bridge.1126.pid
lrwxrwxrwx 1 root root  17 May  5 10:27 X11-display -> /tmp/.X11-unix/X0
paul@Hermes-III:~$ 

```

---

### Post by bab1 on 2014-05-05
> **paul1945 said:**
> Sorry, I should have stuck to the directions without embellishment.

Yes indeed.  Since we were looking for user response of the user *paul * we need to see the reaction from commands as that user. 
> 

...here is the listing, done correctly this time, I hope:
```
paul@Hermes-III:~$ ls -al /run/user/1000
total 8
drwx------ 9 paul paul 240 May  5 10:27 .
drwxr-xr-x 3 root root  60 May  5 10:27 ..
drwx------ 2 paul paul  60 May  5 10:29 dconf
dr-x------ 4 [COLOR="#008000"]**paul**[/COLOR] paul   0 May  5 10:27 [COLOR="#0000FF"]**gvfs**[/COLOR]
drwx------ 2 paul paul  40 May  5 10:27 gvfs-burn
drwx------ 2 paul paul 120 May  5 10:27 keyring-wKhguQ
drwx------ 2 paul paul  80 May  5 10:27 pulse
drwx------ 2 paul paul  40 May  5 10:27 unity
drwx------ 3 paul paul  60 May  5 10:27 upstart
-rw-r--r-- 1 paul paul   5 May  5 10:27 upstart-dbus-bridge.1126.pid
-rw-r--r-- 1 paul paul   5 May  5 10:27 upstart-file-bridge.1126.pid
lrwxrwxrwx 1 root root  17 May  5 10:27 X11-display -> /tmp/.X11-unix/X0
paul@Hermes-III:~$ 

```

The listing is fine.  It shows the gvfs directory (highlighted in [COLOR="#0000FF"]**blue **[/COLOR]and the user [paul (highlighted in [COLOR="#008000"]**green**[/COLOR]).
> 

As far as my network access is concerned, I cannot browse the network at all through the Ubuntu file manager, when I click on "browse network" it shows the "MSHOME" folder, but if I click on that it is empty.

I am using Ubuntu 12.04 so I don't necessarily *see *what you see.  Don't you see an icon named "Windows Network"?  If you do what happens if you click on that icon?
> 
I can connect to a server with that facility by typing in "smb://server/" where the server is the respective machine name, and select a directory, which will then mount,

This tells me that the Samba file server element is working.  The part that is not working is the Samba browsing element.  Samba is a suite of protocols not just one monolithic application.
> 
 but as I said I cannot do this with the little Linux NAS, it comes up with an error:
```
Oops! Something went wrong.
Unhandled error message: failed to retrieve share list from server: connection timed out.
```

This is really the heart of the of your problem.  This part exactly:  *failed to retrieve share list from server*.  This is what is known as the Master Browse List.  The MBL holds all the share information.  This list is what all the sharing clients need to retrieve before they can browse the network.
> 
As the NAS is my hub for storing information and automatic record updating, that can be accessed by both my and my wife's computer, this is a problem.
I also have an old notebook that has Linux installed and I have no problems mounting the shares of that machine.
 
I tend to look at these things as either clients or servers.  Is what you are saying this:  The NAS is always a server for your both your Ubuntu host (named Hermes-III)  and your wife's Windows host. You also have a notebook with some Linux distro installed that can also mount the NAS shares.

Let's start over with a simple issue.  Is the normal use pattern like this: The NAS is on all the time, all the other machines are off when not being used.  The MASTER BROWSER is any machine in the network that participates is sharing that is up (running) and wins the internal election.  If the machine is turned off the MBL is passed on to a different elected machine.

I'm trying to see which machine is the MB.  What is the output from Hermes-III of this command```

smbclient -L Hermes-III

``` 
If you get an error using your password try again with no password, just hit enter at that prompt.  When I do that I get this```

Domain=[CAMPO] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	public          Disk      Shared Data
	IPC$            IPC       IPC Service (malibu server (Samba, Ubuntu))
	PDF             Printer   PDF
	HP-LaserJet-2200 Printer   LaserJet 2200
	bab              Disk      Home Directories
Domain=[CAMPO] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	MALIBU               malibu server (Samba, Ubuntu)
	MANILA               manila server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	CAMPO                 [COLOR="#FF0000"]MANILA[/COLOR]


```

In this case the host *malibu* is using the MB that resides on *manila* in (red above)

---

### Post by paul1945 on 2014-05-05
> **bab1 said:**
> The listing is fine.  It shows the gvfs directory (highlighted in [COLOR=#0000FF]**blue **[/COLOR]and the user [paul (highlighted in [COLOR=#008000]**green**[/COLOR]).
I guess that's a start.
> **bab1 said:**
> I am using Ubuntu 12.04 so I don't necessarily *see *what you see.  
Don't you see an icon named "Windows Network"?  If you do what happens if you click on that icon?
You are right, that is what I see, if I click on that it is blank. No "MSHOME" no nothing. Got myself confused with a previous config, sorry about that.
> **bab1 said:**
> Is what you are saying this:  The NAS is always a server for your both your Ubuntu host (named Hermes-III)  and your wife's Windows host. You also have a notebook with some Linux distro installed that can also mount the NAS shares.
Correct. We have three desktops and two laptop/notebook computers. My notebook is a hobby machine I use to try to learn Linux and is very ancient (it has Salix OS installed); it is a cast-off of my wife. One desktop is a dedicated business machine. None of these have any problem mounting the NAS shares, and neither did this Ubuntu machine until I installed version 14.04. 

> **bab1 said:**
> Let's start over with a simple issue.  Is the normal use pattern like this: The NAS is on all the time, all the other machines are off when not being used.  
That's it.
> **bab1 said:**
> The MASTER BROWSER is any machine in the network that participates is sharing that is up (running) and wins the internal election.  If the machine is turned off the MBL is passed on to a different elected machine.
You're probably right but I am not sure.
> **bab1 said:**
> I'm trying to see which machine is the MB.  What is the output from Hermes-III of this command: smbclient -L Hernes-III
Here it is:
```

paul@Hermes-III:~$ smbclient -L hermes-III
Enter paul's password: 
Domain=[MSHOME] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (Hermes-III server (Samba, Ubuntu))
    Downloads       Disk      
    print$          Disk      Printer Drivers
    HP-Deskjet-930c Printer   HP Deskjet 930c
    LANIER-LP440c-SP-C811DNCMD:PS Printer   LANIER LP440c/SP C811DNCMD:PS
    Lexmark-E260dn  Printer   Lexmark E260dn
    Hewlett-Packard-HP-LaserJet-M2727nf-MFP Printer   Hewlett-Packard HP LaserJet M2727nf MFP
Domain=[MSHOME] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Server               Comment
    ---------            -------
    GWYDION              gwydion
    HERMES-III           Hermes-III server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    MSHOME               GWYDION
paul@Hermes-III:~$ 

``` 
This machine can obviously see the NAS. I wonder why it stubbornly refuses to mount the share.
Regards, Paul.

---

### Post by paul1945 on 2014-05-05
Just as a ps, found that I could not get into the "Downloads" directory of the Ubuntu 14.04 machine from any other machine. Managed to solve this problem by setting up Samba file sharing for my name and by setting the Samba password, courtesy a set of instructions I found on the Forum. But as far as browsing and the other issues of the Ubuntu 14.04 machine are concerned, there no change there. Paul.

---

### Post by bab1 on 2014-05-05
> **paul1945 said:**
> 
```

paul@Hermes-III:~$ smbclient -L hermes-III
Enter paul's password: 
Domain=[MSHOME] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (Hermes-III server (Samba, Ubuntu))
    Downloads       Disk      
    print$          Disk      Printer Drivers
    HP-Deskjet-930c Printer   HP Deskjet 930c
    LANIER-LP440c-SP-C811DNCMD:PS Printer   LANIER LP440c/SP C811DNCMD:PS
    Lexmark-E260dn  Printer   Lexmark E260dn
    Hewlett-Packard-HP-LaserJet-M2727nf-MFP Printer   Hewlett-Packard HP LaserJet M2727nf MFP
Domain=[MSHOME] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Server               Comment
    ---------            -------
    GWYDION              gwydion
    HERMES-III           Hermes-III server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    MSHOME               GWYDION
paul@Hermes-III:~$ 

``` 
This machine can obviously see the NAS. I wonder why it stubbornly refuses to mount the share.
Regards, Paul.
I think it can mount the the shares directly.  It just can't provide the MBL so you can browse to the share to mount it.  These are 2 different things (browsing network vs mounting a specific share).

What do you get with this```
smbclient -L gwydion
```

At this point I am looking for reasons that the MBL can't be see by Hermes-III.  Maybe Hemes-III can't see gwydion at all during this process.  Are your machines set to have a fixed IP address?  What is the IP address of Hermes-III and gwydion?

From Hemes-III what is the output of this```
cat /etc/hosts
```

---

### Post by paul1945 on 2014-05-05
> **bab1 said:**
> What do you get with this
smbclient -L gwydion
```
paul@Hermes-III:~$ smbclient -L gwydion
Enter paul's password: 
Conversion error: Incomplete multibyte sequence()
protocol negotiation failed: NT_STATUS_INVALID_PARAMETER
paul@Hermes-III:~$ 

```

> At this point I am looking for reasons that the MBL can't be see by Hermes-III.  Maybe Hemes-III can't see gwydion at all during this process.  Are your machines set to have a fixed IP address?  What is the IP address of Hermes-III and gwydion?
The addresses are reserved in the Router, and are also set within gwydion; the Windows machines and hermes-III are set on auto and get the IP address allocated by the Router: 
gwydion = 192.168.1.3
hermes-III = 192.168.1.7

> From Hemes-III what is the output of this:
cat /etc/hosts
```
paul@Hermes-III:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    Hermes-III

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
paul@Hermes-III:~$ 

```

---

### Post by paul1945 on 2014-05-12
Just an update.
Including:
```
preferred master = Yes 
domain master = Yes
```
into the [global] section of smb.conf
has made my network and its servers visible and accessible for browsing in Ubuntu 14.04.
Except for my NAS which runs SnakeOS, a cut down Linux system; this shows with the other servers but Ubuntu 14.04 refuses to allow me to access this.
As this NAS is the hub of my network, this is rather problematic.
The strange part is that I can access the NAS via FTP and HTTP from Ubuntu 14.04, but if I try to browse it from the file manager it comes up with:
```
 Failed to retrieve share list from server; connection timed out
```
So if anyone has any idea of how to solve this problem, I would be grateful.
By the way, the little NAS shows up and is browseable from all the other machines on my network, including a notebook that runs Salix Linux.

---

### Post by mperrin on 2014-08-17
I was getting the same "Failed to retrieve share list..." error on a Ubuntu 14.04 box but a Linux Mint 17 machine (based on 14.04) was working perfectly. The smb.conf files were the same but I discovered that Mint had installed samba (the server) and samba-dsdb-modules by default. They were not installed by default on the Ubuntu machines. After installing those packages the Ubuntu box was able to browse the network shares. I can't explain why.

---

