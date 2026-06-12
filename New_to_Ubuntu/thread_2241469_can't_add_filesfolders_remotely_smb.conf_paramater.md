---
title: "can't add files/folders remotely smb.conf paramaters"
date: 2014-08-26
forum: New to Ubuntu
---

### Post by michael211 on 2014-08-26
Hello, I'm an extreme noob to anything linux, so please excuse any noob like things.  I am running Ubuntu Server 14.04.1, and have samba running as a file server.  I have created a share called [owners] and have made the only permitted people people who are members of the @owners group, as well as made them the admin users.  On our machines running windows 8 on the local network, I can access the share and create folders and save files to it.  However, on remote connections I cannot.  Now, I don't know if it makes a difference or not, but I have not attempted to install putty on a remote computer and access the share; I have only downloaded ES File Explorer on my Galaxy S5 and have successfully connected to the share remotely, but I cannot create folders or files.  I don't know if you need to see all of the smb.conf file to help me, so here it is.

```
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
   workgroup = WORKGROUP
   security = user
# server string is the equivalent of the NT Description field
      server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

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
   encrypt passwords = true
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
   usershare allow guests = no

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

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
[owners]
   comment = Ubuntu File Server Share
   path = /srv/samba/owners
   browsable = yes
   guest ok = no
   read only = no
   writeable = yes
   create mask =  0775
   directory mask = 0775
   valid users = @owners
   admin users = @owners
   write list = @owners
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
   guest ok = yes
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

 

```

---

### Post by TheFu on 2014-08-26
Please post the output from **testparm** on the server and **smbtree**. It would be ideal if a client machine could run smbtree too, but ... perhaps there is a **net use** command equiv?  These commands will let us see what the system sees.

Putty is an ssh client, not SMB/CIFS client. Different protocols completely.

Local file permissions may or may not matter to CIFS/samba connections. It depends on the settings. Samba runs as root, so it has complete access to the files and can be completely controlled by the allowed users/groups settings.

---

### Post by michael211 on 2014-08-27
OK, so I'm not sure how to get the information from the testparm and the smbtree (not even sure what smbtree is) into here since I am running Ubuntu Server from the Command Line.  However, I think I figured out the problem.  Here's what I think is happening and the solution I used that worked:

Well, to be honest, I'm not sure what exactly is happening because I was able to create a folder on a client machine (all client machines on the network are running windows 8) located on the network.  I was then able to create a folder using ES File Explorer logging in as the same user that created the "New Folder" on the client machine, but could not create a new folder in the share created on the server or in the folder created on the client machine.

My solution was to go onto the Ubuntu machine and execute the following command

```
sudo chown -R mlyon:owners /srv/samba/owners
```

This made it where I could create new folders in the owners share created on the Ubuntu machine and in the "New Folder" created on the client machine as long as I was signed in under any one of the 3 members of the group @owners.  But, from this point on, I was not able to create any folders inside of folder created by a different user without re-running the above command.

It seems to me there is an issue with ownership.  Is there a way to have any folders created in a share and its sub-folders share the ownership permissions set to that share before the new folder was created?

I am very interested in not just receiving an answer and solution, but some tutorials or articles or other reading materials which would help me understand why the presented solution works.

As for the testparm and smbtree, I ran them both, and the smbtree seems to show the network environment.  Under Ubuntu which is the server name on the network it shows 

\\Ubuntu[INDENT]\IPC$
\print$
\owners
[/INDENT]

Ok, I figured out how to get the testparm results on here:

```
[global]
      server string = %h server (Samba, Ubuntu)
      server role = standalone server
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
      wins support = Yes
      panic action = /usr/share/samba/panic-action %d
      idmap config * : backend = tdb

[owners]
      comment = Ubuntu File Server Share
      path = /srv/samba/owners
      valid users = @owners
      admin users = @owners
      write list = @owners
      read only = No
      create mask = 0775
      directory mask = 0775

[printers]
      comment = All Printers
      path = /var/spool/samba
      create mask = 0700
      guest ok = Yes
      printable = Yes
      print ok = Yes
      browseable = No

[print$]
      comment = Printer Drivers
      path = /var/lib/samba/printers
 

```

---

### Post by TheFu on 2014-08-27
Love the attitude - learning is the only way this stuff will get easier!

I've never used Win8. Sorry. For research - is there anything funny about Win8 CIFS connection authentication requirements compared to earlier releases? I dunno - worth checking.

Never used any other authentication method besides 
```
   security = user
```
I didn't see that in the global settings. Also, did you initialize the smbpasswd database with smbpasswd command for each user? It is only needed once to create the userid inside the DB, after that password management is automatic thanks to the **unix password sync = yes** option.

I've never used **write users** or **admin users** settings either.

All documentation is here: [https://www.samba.org/samba/docs/](https://www.samba.org/samba/docs/)
I haven't used any samba-v4 stuff and it doesn't look like you are either, so the 3.x docs should be fine.

Might be useful to verify the members of the "owners" group - hopefully it does NOT have an '@' in the /etc/groups file.  An easy way to check is to login via ssh at 1 of the user, the run **id**.

Also - if you'd post the output from** ls -al /srv/samba/owners** that would be helpful. The owner, group and group sticky bits are important.

---

### Post by michael211 on 2014-08-27
As an entrepreneur/business owner, there's no other attitude to have - you have to wear all the hats until you can afford to bring on someone to wear some of them!

Is there specific place in global section that should be? Because that's the security type I am supposed to be using, and in my first post, you can see it right under the **workgroup = WORKGROUP**.

I followed a few different tutorials and combined them all together, so somethings may be redundant, like the **write users **and **admin users **settings.  The way I understood the **write users**, **admin users**, **valid** **users** settings to work is that **write users **gives them permission to write, **valid users** gives them permission to access the files, and **admin users **gives them r/w permissions.  So, if if I wanted to give members of the group owners r/w permissions to a share, but only let members of the sales group to have read permissions, I would set the **valid users** to @sales, @owners and set the **admin users **to @owners.

Let me explain what I'm trying to accomplish, and maybe you can tell me if I'm going about it the wrong way with this.

I am preparing for the company's growth, and trying to implement a file structure based on the departments we will have: sales, production, call center, office staff.

I am looking to have a share for each of those departments where, depending on the share, all users would have read access to them, or only members of the department's group would have read access and members of the owners group would have r/w permissions.  And certain users would have r/w access to certain sub-folders.  For example:

There would be a sales share with numerous sub-folders, all of the outside sales people would be member of the group @sales and have read privileges so they can access all of the files and folders in the sales share.  There would be a "New Appointments" folder in the sales share with sub-folders for each sales person that members of the @callcenter group and the appropriate sales person would have r/w privileges to and then there would be a "Job Quotes" folder in the sales share with sub-folders for each sales person that the appropriate sales person would have r/w privileges to.

The owners share is the only share that only the owners of the company would have access to.

Hopefully I did a good enough job explaining what I am trying to accomplish.

---

### Post by TheFu on 2014-08-27
testparm shows which settings are actually being used, not what the file says. Humans can easily miss things, which it why I insist on seeing the tool's output instead of looking at files.

When I need complex controls over file permissions, I do NOT use samba.  Call it personal limitation, if you like.  We have people use sftp to login and manage central storage for our company. Then full UNIX file/directory permissions rule and it is clear what permissions are provided by group, user, other. If you need more complex permissions, there are ACLs. Users get used to it quickly and winscp is a nice tool.

Permissions for samba appear to be by share-name - so for every different group of users or different permissions, I'd think that a different share would be needed.  That is unless you start using Samba4 features.  I could be wrong - hopefully Bab1 will show up and clarify.

It really sounds like you want/need a more complete document management solution - something like Alfresco.

Or perhaps a CRM tool like vTiger (or sugarcrm) is really what you need? It will integrate with Alfresco and with an email system.

I had systems setup with all of those, but our sales folks all left and we didn't replace them. They never seemed to understand that document management systems maintain file versions for us, so there isn't any reason to add -v1, -v2, -v3 and create new documents.

Just checked my working samba system here - the testparm doesn't show **security = user** either. Interesting.

**id** output look correct?

---

### Post by bab1 on 2014-08-28
> **michael211 said:**
> ...
Is there specific place in global section that should be? Because that's the security type I am supposed to be using, and in my first post, you can see it right under the **workgroup = WORKGROUP**.

I followed a few different tutorials and combined them all together, so somethings may be redundant, like the **write users **and **admin users **settings.  

If I may provide an alternative to this thought.  You should really take the time to read the official documentation and learn what all the options are.  There are many tutorials and forum posts that are inaccurate observations.  Following these can cause no end to your troubles. 
> 
The way I understood the **write users**, **admin users**, **valid** **users** settings to work is that **write users **gives them permission to write, **valid users** gives them permission to access the files, and **admin users **gives them r/w permissions.  So, if if I wanted to give members of the group owners r/w permissions to a share, but only let members of the sales group to have read permissions, I would set the **valid users** to @sales, @owners and set the **admin users **to @owners.

This is not quite right.  For instance the "admin user" causes all actions to be run by root on the users behalf.  What his really means is that all users in the @owners group function as root including taking ownership of the file or directory.  This messes up the file system permissions as no user other than root can access these files.  The "valid user" are the only users that can be authenticated to the share (who are you).  The "write list" allow those users read and write permissions the share, but they should have that anyway.  Only the Linux permissions can give authorization (you have the right) and the Samba share definition can't add back additional rights.

All of this is available on the host (computer) that is running Samba.  The man page for the smb.conf file lists all the definitions.  See this for all the details```
man smb.conf
```   
> 

Let me explain what I'm trying to accomplish, and maybe you can tell me if I'm going about it the wrong way with this.

I am preparing for the company's growth, and trying to implement a file structure based on the departments we will have: sales, production, call center, office staff.

It's a very good idea to set up the Linux file system with thought for expansion.  On the other hand, don't confuse the file system structure with the Samba share structure (see below).  
> 
I am looking to have a share for each of those departments where, depending on the share, all users would have read access to them, or only members of the department's group would have read access and members of the owners group would have r/w permissions.  And certain users would have r/w access to certain sub-folders.  For example:

There would be a sales share with numerous sub-folders, all of the outside sales people would be member of the group @sales and have read privileges so they can access all of the files and folders in the sales share.  There would be a "New Appointments" folder in the sales share with sub-folders for each sales person that members of the @callcenter group and the appropriate sales person would have r/w privileges to and then there would be a "Job Quotes" folder in the sales share with sub-folders for each sales person that the appropriate sales person would have r/w privileges to.

The owners share is the only share that only the owners of the company would have access to.

Hopefully I did a good enough job explaining what I am trying to accomplish.
I get the idea.  The Linux file structure might look something like this ```

/srv/samba/
     leads/
      quotes/
      sales/
      owners/

```
Remember this is just an example.  I don't expect this to be what you ultimately use.  The Samba shares SHOULD NEVER be nested inside another share.  Each share should be thought of as  the root of a distinct Linux file system. You will never get the permissions correct without resorting to arcane and unnecessary complications.  Using the above file system The shares would look like this ```

//SERVER-NAME/leads

//SERVER-NAMEquotes

//SERVER-NAME/sales

//SERVER-NAME/owners

```...in fact wherever you place the data in the file system the Samba resource is always //SERVER-NAME/SHARE-NAME.

If you want the appointments for all sales to be read only that can be accomplished by a group, but you can't then allow certain subdirectories to them be read + write for all or some of the users.  Security is really a 3 part notion:  Authentication (who) -- Authorization (permission) -- Auditing.  If you have multiple users then the relevant file system permissions will be the group permissions.

Is this a testbed server that you are using to flesh out the final structure.  Can we test some ideas on it.  Hopefully it's not a production server that can't be completely redone.

---

### Post by bab1 on 2014-08-28
> **TheFu said:**
> testparm shows which settings are actually being used, not what the file says. Humans can easily miss things, which it why I insist on seeing the tool's output instead of looking at files.

Not quite so.  The tool testparm is for validating the smb.conf file.  From the man pages```
       testparm is a very simple test program to check an smbd(8) configuration file for internal
       correctness. If this program reports no problems, you can use the configuration file with
       confidence that smbd will successfully load the configuration file.


```
If you want to see ALL the parameters (both default and user modified) you should use this   ```
testparm -sv
```

The smb.conf file does NOT state all the parameters that Samba users.  It is mainly used for the alterations from the defaults that the Samba daemon (smbd) uses
> 
Just checked my working samba system here - the testparm doesn't show **security = user** either. Interesting.

That's because you don't need to state that in the smb.conf file.  It is the default setting.  See the man page.

---

### Post by TheFu on 2014-08-28
> **bab1 said:**
> That's because you don't need to state that in the smb.conf file.  It is the default setting.  See the man page.

Just goes to prove that defaults change over time. ;)  I've been using the same basic smb.conf since  .... er ... 1996-ish.

RTFM goes for me as well. ;)

---

### Post by michael211 on 2014-08-28
> [COLOR=#000000]It really sounds like you want/need a more complete document management solution - something like Alfresco.[/COLOR]

[COLOR=#000000]Or perhaps a CRM tool like vTiger (or sugarcrm) is really what you need? It will integrate with Alfresco and with an email system.[/COLOR]

That might be what we need, but bab1 seems to have some ideas, so I'm going to see what they want to try.

> [COLOR=#000000]I get the idea. The Linux file structure might look something like this[/COLOR][COLOR=#000000]Code:
/srv/samba/
     leads/
      quotes/
      sales/
      owners/[/COLOR]
[COLOR=#000000]Remember this is just an example. I don't expect this to be what you ultimately use. The Samba shares SHOULD NEVER be nested inside another share. Each share should be thought of as the root of a distinct Linux file system. You will never get the permissions correct without resorting to arcane and unnecessary complications. Using the above file system The shares would look like this[/COLOR][COLOR=#000000]Code:
//SERVER-NAME/leads

//SERVER-NAMEquotes

//SERVER-NAME/sales

//SERVER-NAME/owners[/COLOR]
[COLOR=#000000]...in fact wherever you place the data in the file system the Samba resource is always //SERVER-NAME/SHARE-NAME.[/COLOR]

If I'm understanding correctly, I can have different shares, like

```
/srv/samba/owners/
/srv/samba/sales/
/srv/samba/office/
```

each having their own permissions and sub-folders that share the permissions of their parent share, but I couldn't have

```
/srv/samba/sales/appointments/frank/
/srv/samba/sales/appointments/jeff/
```

and have permissions for the sales share set at read only for members of the sales group and then the folder for frank be r/w for only frank without "resorting to arcane and unnecessary complications?"

> [COLOR=#000000]Is this a testbed server that you are using to flesh out the final structure. Can we test some ideas on it. Hopefully it's not a production server that can't be completely redone.[/COLOR]

It can be redone as many times as is necessary, and I'm willing to test any ideas you have.

What prompted this is that we have a WD My Cloud NAS device, and no one has really monitored it, so it is all messed up.  We have some things saved in triplicate and even quadruplicate in multiple different places.  Some files are missing from the drive, but luckily we have them saved on other devices.  So, I decided one of the computers with decent hardware we are no longer using would make a decent server for us, and I knew we could keep people from accidentally deleting things, and accessing things they don't need to have access to, and as mentioned earlier, we want to plan for growth and know we eventually want a server for when we expand into surrounding states and have multiple offices going.

Anyways, we are currently using the WD NAS and the server can be used as a testbed server for the time being before moving all the files over and putting it to full use.

---

### Post by bab1 on 2014-08-28
> **michael211 said:**
> That might be what we need, but bab1 seems to have some ideas, so I'm going to see what they want to try.

Document management systems do not really affect how the Samba server is configured.  The "engineering" design should reflect the business practices (e.g. document flow).  That is the file system structure and file and directory permissions should take into consideration the users document security and  system limitations.  Can you give me an idea of how the appointments data is secured.  Do all sales people see all the appointments?  Who is allowed to make changes to this information?  What other user besides sales need to see this salesman/appointment data?  Do managers need to see this data?  Do they need to be able to change it?
> 

If I'm understanding correctly, I can have different shares, like

```
[COLOR="#008000"][B]/srv/samba/owners/
/srv/samba/sales/
/srv/samba/office/[/B][/COLOR]
```

These are not [COLOR="#0000FF"]shares[/COLOR].  These are the [COLOR="#008000"]**file system structure**[/COLOR].  There are important differences when it comes to making design choices for your Samba file server.
> 
each having their own permissions and sub-folders that share the permissions of their parent share, but I couldn't have

```
/srv/samba/sales/appointments/frank/
/srv/samba/sales/appointments/jeff/
```

You set [COLOR="#008000"]**file system**[/COLOR] permissions on these; **not** Samba [COLOR="#0000FF"]share permissions[/COLOR].  In essence, you should not change the file system ownership in subdirectories that are part of a Samba share.  The ownership and permissions should be consistent from the file system root of the Samba share down to the last file is that structure.  An example might help.  The file structure might be ```
/srv/samba/sales/appointments
```...the subdirectories of **frank **and **jeff** should have the same owners and permissions so you don't need a separate share for each.  If you do want to keep them separate then don't have a share starting at */srv/samba/sales/appointments*.  Start each share at the file system root of```
[COLOR="#008000"]**/srv/samba/sales/appointments/frank**[/COLOR]

[COLOR="#008000"][B]
/srv/samba/sales/appointments/jeff[/B][/COLOR]
 
```

The shares would be something like this```

[COLOR="#0000FF"]//SERVER-NAME/frank-appointments[/COLOR]

[COLOR="#0000FF"]//SERVER-NAME/jeff-appointments[/COLOR]

```
Each user has his own private appointment share.
> 

and have permissions for the sales share set at read only for members of the sales group and then the folder for frank be r/w for only frank without "resorting to arcane and unnecessary complications?"

Yes.  The [COLOR="#008000"]**file structure**[/COLOR] does not have to reflect the [COLOR="#0000FF"]SHARE-NAME[/COLOR] exactly.
> 

It can be redone as many times as is necessary, and I'm willing to test any ideas you have.

What prompted this is that we have a WD My Cloud NAS device, and no one has really monitored it, so it is all messed up.  We have some things saved in triplicate and even quadruplicate in multiple different places.  Some files are missing from the drive, but luckily we have them saved on other devices.  So, I decided one of the computers with decent hardware we are no longer using would make a decent server for us, and I knew we could keep people from accidentally deleting things, and accessing things they don't need to have access to, and as mentioned earlier, we want to plan for growth and know we eventually want a server for when we expand into surrounding states and have multiple offices going.


Anyways, we are currently using the WD NAS and the server can be used as a testbed server for the time being before moving all the files over and putting it to full use.

I will be out for most of the day today.  I will respond to your observations and questions this evening when I get back.

---

### Post by TheFu on 2014-08-28
I'd use shared calendaring for appointments.  Any communications server that supports "enterprise calendaring" can do this - with shared read-only, delegated/rw-shared or private appointments.  Plus most allow multiple calendars per person.  I know Zimbra handles this stuff easily.

Trying to use network shares for anything other than documents is a bad idea, IMHO.  Perhaps those really aren't appointments, but paperwork around an on-site visit?  After all, avoiding "arcane and unnecessary complications" is part of the goal.

---

### Post by bab1 on 2014-08-28
> **TheFu said:**
> I'd use shared calendaring for appointments.  Any communications server that supports "enterprise calendaring" can do this - with shared read-only, delegated/rw-shared or private appointments.  Plus most allow multiple calendars per person.  I know Zimbra handles this stuff easily.

Trying to use network shares for anything other than documents is a bad idea, IMHO.  Perhaps those really aren't appointments, but paperwork around an on-site visit?  After all, avoiding "arcane and unnecessary complications" is part of the goal.

I agree!  That was exactly what I was trying to say.  The share is really for data (history or supporting docs).  A calendaring database is much more suited for the user.  In addition I thing the user should have his own area to use as they please.  If you make this too structured you will loose employee creativity.  Take it from someone who has managed employees for over 25 years, "the employee is the most valuable asset".

Now I gotta go for the day.  ;-)

---

### Post by michael211 on 2014-08-28
> **bab1 said:**
> I agree!  That was exactly what I was trying to say.  The share is really for data (history or supporting docs).  A calendaring database is much more suited for the user.  In addition I thing the user should have his own area to use as they please.  If you make this too structured you will loose employee creativity.  Take it from someone who has managed employees for over 25 years, "the employee is the most valuable asset".

Now I gotta go for the day.  ;-)

Yes, we are using this for documents.  I guess it might help if I explain the current process.  

Nate, a guy in our call center calls a prospect and sets a sales appointment for Dave, our salesperson.  Nate then makes up a physical folder stapling the lead sheet to it, and printing off the required paperwork based on what type of project the appointment is for.  He then places the folder in a wall file assigned to Dave.  Dave goes on the appointment, and for simplicity sake, we'll say it's a one call close, so he sells it.  Dave brings the folder and puts it in the administrative office in a wall file for "new jobs to enter."  Suzanne, the secretary handles entering all of the administrative data and printing off the paperwork the production department is going to need; she then takes the folder to the bookkeeper who enters the customer & job into QuickBooks and then places the folder in the "release to production" wall file.  The Project Manager does their thing and then files it in the filing cabinet in the "jobs in progress" drawer until the work is completed then they process it for completion and put it into the drawer for "jobs completed."

There is a lot of ink and paper gone through with this process, so we are converting it to a digital process as much as possible to cut some of the ink and paper overhead, and to streamline it.

Essentially, with the permissions, I am looking to make it fairly "idiot proof" to ensure there is no deleting of files accidentally.  

> [COLOR=#000000]These are not [/COLOR][COLOR=#0000FF]shares[/COLOR][COLOR=#000000]. These are the [/COLOR][COLOR=#008000]**file system structure**[/COLOR][COLOR=#000000]. There are important differences when it comes to making design choices for your Samba file server.[/COLOR]

So, if I'm understanding correctly, (while this might not be the correct or ideal setup) the shares I am talking about having would be:

```

//UBUNTU/sales
//UBUNTU/owners
//UBUNTU/production
//UBUNTU/callcenter
etc...

```

and the sales share would be located at and have a file structure like this:
```

/srv/samba/sales/[INDENT]forms/[/INDENT]
[INDENT=2]someform.docx[/INDENT]
[INDENT]Scheduled Appointments/[/INDENT]
[INDENT=2]Dave/


[/INDENT]

```

As for the calendar, we have a CRM service we use that is designed specifically for Home Improvement Contractors, and it is quite sufficient in the calendar and scheduling aspect of things.  We are just looking for a way to bring some of our processes into the 21st century and digitize them as well as streamlining them.

I see this starting to take a turn towards you walking me through setting it all up, and I do not want that.  Guidance, would be great, step by step instructions via a forum is in no way fair to you.  I very much appreciate all the time and information both of you have put in thus far.  Hopefully, there is enough information here now that you could recommend a resource to implement what we're trying to do.  My request then would be to just point me towards reading material to learn how to implement it, and I'll return with questions as they come up and I get stuck.  I have not yet had a chance to read the (from what I gather they're called) man pages as I don't really have much time during the work day to sit in front of the computer and read that (I've been working on this one post for about 2 hours now), but I can read at home and after the work day.  Is there a command that might put the man page into a file I can print from my windows computer?  I have not yet installed any print drivers on Ubuntu.

---

### Post by TheFu on 2014-08-28
man pages are online (google it), but may not be exactly the same version as what is running on your system. 

The official documentation is at samba.org. Sorry, thought I'd already provided that.

---

### Post by michael211 on 2014-08-28
> **TheFu said:**
> man pages are online (google it), but may not be exactly the same version as what is running on your system. 

The official documentation is at samba.org. Sorry, thought I'd already provided that.

Thanks, I'll google it.  You may have already provided it, and I just missed it in everything else that was written.

Going back through the thread, I see you did provide a link.  Thanks!

---

### Post by bab1 on 2014-08-28
> **michael211 said:**
> Yes, we are using this for documents.  I guess it might help if I explain the current process.  

Nate, a guy in our call center calls a prospect and sets a sales appointment for Dave, our salesperson.  Nate then makes up a physical folder stapling the lead sheet to it, and printing off the required paperwork based on what type of project the appointment is for.  He then places the folder in a wall file assigned to Dave.  Dave goes on the appointment, and for simplicity sake, we'll say it's a one call close, so he sells it.  Dave brings the folder and puts it in the administrative office in a wall file for "new jobs to enter."  Suzanne, the secretary handles entering all of the administrative data and printing off the paperwork the production department is going to need; she then takes the folder to the bookkeeper who enters the customer & job into QuickBooks and then places the folder in the "release to production" wall file.  The Project Manager does their thing and then files it in the filing cabinet in the "jobs in progress" drawer until the work is completed then they process it for completion and put it into the drawer for "jobs completed."

There is a lot of ink and paper gone through with this process, so we are converting it to a digital process as much as possible to cut some of the ink and paper overhead, and to streamline it.

Essentially, with the permissions, I am looking to make it fairly "idiot proof" to ensure there is no deleting of files accidentally.  



So, if I'm understanding correctly, (while this might not be the correct or ideal setup) the shares I am talking about having would be:

```

//UBUNTU/sales
//UBUNTU/owners
//UBUNTU/production
//UBUNTU/callcenter
etc...

```

and the sales share would be located at and have a file structure like this:
```

/srv/samba/sales/[INDENT]forms/[/INDENT]
[INDENT=2]someform.docx[/INDENT]
[INDENT]Scheduled Appointments/[/INDENT]
[INDENT=2]Dave/


[/INDENT]

```


Save yourself some grief.  Never use spaces in directory names on a Linux host.  It just adds to the complexity when administering the data (scripts and backups for example). 
> 

As for the calendar, we have a CRM service we use that is designed specifically for Home Improvement Contractors, and it is quite sufficient in the calendar and scheduling aspect of things.  We are just looking for a way to bring some of our processes into the 21st century and digitize them as well as streamlining them.

I see this starting to take a turn towards you walking me through setting it all up, and I do not want that.  Guidance, would be great, step by step instructions via a forum is in no way fair to you.  I very much appreciate all the time and information both of you have put in thus far.  Hopefully, there is enough information here now that you could recommend a resource to implement what we're trying to do.  My request then would be to just point me towards reading material to learn how to implement it, and I'll return with questions as they come up and I get stuck.  I have not yet had a chance to read the (from what I gather they're called) man pages as I don't really have much time during the work day to sit in front of the computer and read that (I've been working on this one post for about 2 hours now), but I can read at home and after the work day.  Is there a command that might put the man page into a file I can print from my windows computer?  I have not yet installed any print drivers on Ubuntu.

The best beginners guide to deployment I've seen is *[Samba by Example ]("https://www.samba.org/samba/docs/man/Samba-Guide/")*  The examples are good even if the specifics are a little dated.  The smb.conf man page is located online [here]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  It is always updated by Samba.org.   There are even Samba4 updates.  As all of this is available at the local host's command line, that is the latest version you need to make a readable text file in the home directory of the user logged into the server you can do these two simple commands (apply it to any command)```
cd 

man testparm >> testparm.txt
```...now you can print the file tesparm.txt that was created in your home directory.

---

### Post by michael211 on 2014-08-29
Thanks, the Samba by Example has been great!  I have only been reading it so far; I figure I'll read it all, then do the first few implementations one at a time resetting the machine and starting over between each one just to see exactly how each one operates on our network.  After talking to my dad, I agree with him, we would only want one person (the sales manager) to be able to move the folder throughout the file structure as I said above.  With this in mind, if I'm understanding what I'm reading in *Samba by Example*, the smb.conf **valid users **and **write users** could be set like this:

```

[sales][INDENT]valid users = @sales, @owners[/INDENT]
[INDENT]write users = salesmanagername, @owners[/INDENT]

```

If I'm understanding correctly, this would allow only members of the sales and owners group to access the sales share and only the sales manager and the owners group to have r/w access.

I was wondering what this line does:
```

mkdir -p /data/{accounts, finsvcs}

```

I'm not sure what the **-p** does.  I am assuming it has something to do with the fact that accounts & finsvs are in {} and that the **-p**&#8203; is necessary in order to create both directories at the same time.

Scratch that, I took a guess I could find a man page for **mkdir**, so I googled **mkdir **man page and found the answer.

---

### Post by TheFu on 2014-08-29
**man mkdir** will explain the -p option better than I could.  Manpages found thru google may not be correct for your commands on your system.  Best to check locally for this stuff.  Whenever a command gets installed on a system, the manpage for that command is installed too.

---

### Post by bab1 on 2014-08-29
> **michael211 said:**
> Thanks, the Samba by Example has been great!  I have only been reading it so far; I figure I'll read it all, then do the first few implementations one at a time resetting the machine and starting over between each one just to see exactly how each one operates on our network.  After talking to my dad, I agree with him, we would only want one person (the sales manager) to be able to move the folder throughout the file structure as I said above.  With this in mind, if I'm understanding what I'm reading in *Samba by Example*, the smb.conf **valid users **and **write users** could be set like this:

```

[sales][INDENT]valid users = @sales, @owners[/INDENT]
[INDENT]write users = salesmanagername, @owners[/INDENT]

```

If I'm understanding correctly, this would allow only members of the sales and owners group to access the sales share and only the sales manager and the owners group to have r/w access.

Red the man page for smb.conf.  There is no share parameter "write users"
> 

I was wondering what this line does:
```

mkdir -p /data/{accounts, finsvcs}

```

I'm not sure what the **-p** does.  I am assuming it has something to do with the fact that accounts & finsvs are in {} and that the **-p**&#8203; is necessary in order to create both directories at the same time.


Scratch that, I took a guess I could find a man page for **mkdir**, so I googled **mkdir **man page and found the answer.
Don't assume anything.  As @TheFu has said; the answer is in the appropriate man page (e.g. man mkdir)

It would also help your creditability if you do the work BEFORE you post here; have us respond, and then tell us "never mind"

---

### Post by michael211 on 2014-08-29
Well, I'm on my phone, so I won't quote, but I see what I did with "write users" vs "write list." That's what I get for trying top go by memory AND post before doing the work myself. Thanks for not coddling me and just fixing my mix-up for me! Also, I didn't realize there was a man page for each command and not just system files. From now on, if I have a question about anything I'll just search for a man page first.

---

### Post by bab1 on 2014-08-29
> **michael211 said:**
> Well, I'm on my phone, so I won't quote, but I see what I did with "write users" vs "write list." That's what I get for trying top go by memory AND post before doing the work myself. Thanks for not coddling me and just fixing my mix-up for me! Also, I didn't realize there was a man page for each command and not just system files. From now on, if I have a question about anything I'll just search for a man page first.

Each command is a separate tool for the Linux kernel and most are in the man page system.  There are other HTML man pages.  That are not installed by default.  Even the command man has its own man page.  See```
man man
```

The tools and the kernel make up the distro  Te addition of the desktop management system is what most folks see.  I have 4 machines at home that have no GUI.  The are 3 Ubuntu and 1 Debian.  My laptop is Lubuntu and I have an Ubuntu workstation also.

---

### Post by michael211 on 2014-09-02
OK, due to a family emergency, I wasn't able to work on this over the weekend, but I just finished the "Drafting Office" setup and am currently resetting the computer.

Everything seemed to work properly after I was done.  The following commands did not work though.  I'll put the messages I got under the command:

```

sudo chkconfig smb on
chkconfig - command not found

sudo /etc/rc.d/init.d/smb restart
-bash: no such file or directory

```

I did take note to one thing during the steps, it says the samba version I'm using is 4.1.6, so I'm not sure if maybe the commands above are not part of 4.1.6.

When I did

```
man chkconfig
```

it told me there was no manuals found.

Once the server is reset, I will do the "Charity Administration Office" setup and report any problems I encounter.  Reading through the next setup, I noticed I will be setting up printers.  This got me thinking about problems we had with one of our printers that is shared.  It is an HP that has wireless capability.  Our network is a cable gateway supplied by our cable company, and a gigabit switch.  Before I got to the office, they had the printer connected wirelessly to the network, I changed that because it was taking forever for files to print.  The problem we then had was a couple computers would show the printer offline, and we had to restart the printer in order for those computers to communicate with it.  Now, I'm wondering, would setting up the printer sharing part of samba help relieve these problems?

---

### Post by bab1 on 2014-09-03
> **michael211 said:**
> OK, due to a family emergency, I wasn't able to work on this over the weekend, but I just finished the "Drafting Office" setup and am currently resetting the computer.

Most folks following this thread have no idea what "Drafting Office" set up means.  It took me a few minutes before I realized what  what you were talking about.  I'd leave references to specific from Samba by Example out of the general conversation.
> 

Everything seemed to work properly after I was done.  The following commands did not work though.  I'll put the messages I got under the command:

```

sudo chkconfig smb on
chkconfig - command not found

sudo /etc/rc.d/init.d/smb restart
-bash: no such file or directory

```
Remember, I said " examples are good even if the specifics are a little dated"  You should only read the text for the examples and ideas.> 
I did take note to one thing during the steps, it says the samba version I'm using is 4.1.6, so I'm not sure if maybe the commands above are not part of 4.1.6.

This is why I said not to take the tutorial too literally.  For the most part the smbd and nmbd daemons (Samba server) work the same in Samba4.1 as they did in Samba3.6 but there are little details that don't.
> 

When I did

```
man chkconfig
```

it told me there was no manuals found.

Once the server is reset, I will do the "Charity Administration Office" setup and report any problems I encounter.  

There is no need to set Samba to automatically start.  That is all done at the install now.  In fact there really aren't run levels in Ubuntu anymore.  That is all legacy stuff.  I suggest strongly that you just read the chapters and try to understand the concepts.
> 
Reading through the next setup, I noticed I will be setting up printers.  This got me thinking about problems we had with one of our printers that is shared.  It is an HP that has wireless capability.  Our network is a cable gateway supplied by our cable company, and a gigabit switch.  Before I got to the office, they had the printer connected wirelessly to the network, I changed that because it was taking forever for files to print.  The problem we then had was a couple computers would show the printer offline, and we had to restart the printer in order for those computers to communicate with it.  Now, I'm wondering, would setting up the printer sharing part of samba help relieve these problems?
Printers are not something that needs Samba to work.  If you store the printer drivers on a Samba server then the printer shares should be used.  Linux does not share printers the same way as Windows does.

Now that you have had a taste of "going it alone" (by your own request):  I suggest you finish reading the next couple of chapters while taking notes.  Then you can ask questions here.  There is no need for you to actually configure Samba to try  it out.  

After that I will show you (a) how to create the file system to hold the file shares, (b) how to set up permissions for shared data, and (c) how to make the shares and restart the Samba daemons.

Remember, the Samba by Example is just an intro and the basic concepts.  It should not be taken literally.

---

### Post by michael211 on 2014-09-08
> **bab1 said:**
> Most folks following this thread have no idea what "Drafting Office" set up means.  It took me a few minutes before I realized what  what you were talking about.  I'd leave references to specific from Samba by Example out of the general conversation.
Got it, I will keep specifics from the article out of general conversation!

> Now that you have had a taste of "going it alone" (by your own request):  I suggest you finish reading the next couple of chapters while taking notes.  Then you can ask questions here.  There is no need for you to actually configure Samba to try  it out.  

After that I will show you (a) how to create the file system to hold the file shares, (b) how to set up permissions for shared data, and (c) how to make the shares and restart the Samba daemons.

Remember, the Samba by Example is just an intro and the basic concepts.  It should not be taken literally.

Yes, going it alone helped I believe because before coming here with questions, I remembered (and hopefully got into a habit of) checking the man pages for commands if I had problems.

Some things I noticed in the next two chapters:

1.  Several times there is a reference to *eth0 *and on my machine the ethernet card is identified as *p5p1*.
2.  When it said to mount the file system, I looked up what disks were attached and noticed that one of them is not recognized.  It is recognized in BIOS, so I am wondering if Ubuntu does not use NTFS since that was the last filesystem it was formatted for.
3.  Is the DHCP configuration necessary considering we have a gateway provided by our ISP?

---

### Post by bab1 on 2014-09-08
> **michael211 said:**
> 
Some things I noticed in the next two chapters:

1.  Several times there is a reference to *eth0 *and on my machine the ethernet card is identified as *p5p1*.

Either of these are references are to a working Network Interface Card (NIC).  The names may be different but the card is the same.
> 
2.  When it said to mount the file system, I looked up what disks were attached and noticed that one of them is not recognized.  It is recognized in BIOS, so I am wondering if Ubuntu does not use NTFS since that was the last filesystem it was formatted for.

NTFS is usable with Ubuntu but not a preferred partition format.  Disks attached physically is not the same as a partition that is mounted.  In the world of Linux a disk is a physical device (a hard drive) and a partition is an alloted section of the drive.  You mount the file system on the partition to the existing local file system.  The partition can be physically located in the local host but it is not absolutely the case.  You can mount a portion of a remote file system to the local file system via Samba.  In fact, that is what we ultimately want to accomplish. 
> 
3.  Is the DHCP configuration necessary considering we have a gateway provided by our ISP?
For Samba's needs the only thing needed is that the local machine as a working IP address.  The gateway is the LOCAL IP address of the device that the ISP usually provides.  This address is on the same network as all of the rest of the devices in your LAN.  The ISP does not control this arrangement.  The ISP only supplies the IP address of the WAN side of the above device (the router).

---

### Post by michael211 on 2014-10-15
Not sure if anyone is following this thread anymore...

Sorry for the long hiatus, but we had a lot of things go on and this took a back burner.

I had another go at it alone and am pretty pleased with my results.  Everyone is able to access what they were intended to access and unable to access what they are not intended to access.

The problem I am having is that no one is able to add/delete files/folders.  Here is the results of my testparm

```
[global]	server string = %h server (Samba, Ubuntu)
	server role = standalone server
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


[office]
	path = /nehi/office
	valid users = @office, @owners
	write list = @owners
	read only = No


[owners]
	path = /nehi/owners
	valid users = @owners
	write list = @owners
	read only = No


[production]
	path = /nehi/production
	valid users = @production, @owners
	write list = @production, @owners
	read only = No


[sales]
	path = /nehi/production
	valid users = @sales, @owners
	write list = @owners, smgr
	read only = No


[call_center]
	path = /nehi/call_center
	valid users = @callcenter, @owners, smgr
	write list = @owners, smgr
	read only = No



```

After fixing this issue the next step for me is to make the shares accessible remotely.

Thanks for all the help!!!

---

### Post by michael211 on 2014-10-16
I'm wondering if a:```
sudo chown -R nobody:no group /nehi 
```
would do the trick or if that's the wrong way to do it.

---

### Post by bab1 on 2014-10-17
> **michael211 said:**
> I'm wondering if a:```
sudo chown -R nobody:no group /nehi 
```
would do the trick or if that's the wrong way to do it.
That won't help.  You need to add user-group inheritance on the share directory and add *force group = <user-group> * to the share definition.  See my example in the thread below. 

[http://ubuntuforums.org/showthread.php?t=2211174&page=3]("http://ubuntuforums.org/showthread.php?t=2211174&page=3")

---

### Post by michael211 on 2014-10-20
Everything is working great now!!!  Thanks so much for your help!!!  I am including the results of my testparm because I want to make sure there's nothing redundant or that may cause conflicts.  Also, do you have any recommendations for maximum security at least on the owners share because we would like to store our quickbooks file there, but that has loads of personal info of our subcontractors, employees, owners, customers and the company financials?

```
[global]	server string = %h server (Samba, Ubuntu)
	server role = standalone server
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


[office]
	path = /nehi/office/
	valid users = @office, @owners
	write list = @owners
	force group = office
	create mask = 0664
	force directory mode = 02775


[owners]
	path = /nehi/owners/
	valid users = @owners
	write list = @owners
	read only = No


[production]
	path = /nehi/production/
	valid users = @production, @owners
	write list = @production, @owners
	force group = production
	create mask = 0664
	force directory mode = 02775


[sales]
	path = /nehi/sales/
	valid users = @sales, @owners
	write list = @owners, smgr
	force group = sales
	read only = No
	create mask = 0664
	force directory mode = 02775


[call_center]
	path = /nehi/call_center/
	valid users = @callcenter, @owners, smgr
	write list = @owners, smgr
	force group = callcenter
	read only = No
	create mask = 0664
	force directory mode = 02775



```

---

### Post by bab1 on 2014-10-20
> **michael211 said:**
> Everything is working great now!!!  Thanks so much for your help!!!  I am including the results of my testparm because I want to make sure there's nothing redundant or that may cause conflicts.  
I see one thing that is not correct.  The *force directory mode * should be ***2775*** not 02775

Why no masks for the owners share?  I would think you need group inheritance and creation masks for that share also.
> 


```

[owners]
	path = /nehi/owners/
	valid users = @owners
	write list = @owners
	read only = No

```
Also, do you have any recommendations for maximum security at least on the owners share because we would like to store our quickbooks file there, but that has loads of personal info of our subcontractors, employees, owners, customers and the company financials?


Nothing is 100% secure, but if you have the Linux file permissions and ownerships  correct (user=root and group=owners) and the share will only allow @owners then you should be reasonably secure.  Is the server physically secured?  If the hardware can be accessed then no data is secure.

---

### Post by michael211 on 2014-10-21
> **bab1 said:**
> I see one thing that is not correct.  The *force directory mode * should be ***2775*** not 02775

Not sure why, but it seems like the testparm appended a 0 on the 2775 because when I went to fix this, they were all 2775.

> Why no masks for the owners share?  I would think you need group inheritance and creation masks for that share also.

I will go ahead and add the masks, not sure why I didn't in the first place.

> Nothing is 100% secure, but if you have the Linux file permissions and ownerships  correct (user=root and group=owners) and the share will only allow @owners then you should be reasonably secure.  Is the server physically secured?  If the hardware can be accessed then no data is secure.

As you said, nothing is 100% secure, but the server is locked in our office in the supply closet sans mouse, keyboard, and monitor.

One last thing, could you point me in the direction of information showing what would be the best way to backup the server?  We have a NAS device we were previously using and I would like to backup the server to that device.

---

### Post by bab1 on 2014-10-22
> **michael211 said:**
> 
I will go ahead and add the masks, not sure why I didn't in the first place.

Just to be complete; the file system group ownership needs to be set also.
> 
As you said, nothing is 100% secure, but the server is locked in our office in the supply closet sans mouse, keyboard, and monitor.

One last thing, could you point me in the direction of information showing what would be the best way to backup the server?  We have a NAS device we were previously using and I would like to backup the server to that device.
I'm probably the wrong person to ask about that.  I use a non-gui app called rsnapshot.  It is really rsync with a perl script wrapper.  I have added my own scripts to satisfy my own needs.  It's fast and efficient.  All the files are backed up by copying them to the backup drive via ssh.  I can just copy back what I need when disaster strikes.

---

### Post by michael211 on 2014-10-22
> **bab1 said:**
> Just to be complete; the file system group ownership needs to be set also.

Yes, that was already done, the only thing not done was the masks.

> **bab1 said:**
> I'm probably the wrong person to ask about that.  I use a non-gui app called rsnapshot.  It is really rsync with a perl script wrapper.  I have added my own scripts to satisfy my own needs.  It's fast and efficient.  All the files are backed up by copying them to the backup drive via ssh.  I can just copy back what I need when disaster strikes.

That's fine, you've been more than enough help, and I tremendously grateful!  I will do some searching and if I can't find anything, I'll post another thread on here!

---

