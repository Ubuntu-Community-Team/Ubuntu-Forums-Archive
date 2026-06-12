---
title: "Ubuntu 12.04 Server + Proftpd"
date: 2013-12-17
forum: New to Ubuntu
---

### Post by ggallian on 2013-12-17
Basically I have tried numerous options to get FTP working on our existing Ubuntu box which is running 12.04 LTS.
I have tried the following:
Pureftpd
Proftpd
Gadmin

I am able to install ProFTPD, login but cannot upload files, create directories or create files.
I have changed groups, permissions, and even directories.

I have even set-up a new ubuntu 12.04 server (fresh install) with only Proftpd.
I cannot seem to be able to upload/create files or folders.

Keep getting Access is Denied every time.

Wondering if someone can assist me with this.
I did set the Default_Root to ~ and /var/ftp with another folder called "web".
Doesn't seem to work.

Not sure if my configuration is wrong?
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes, reload proftpd after modifications, if
# it runs in daemon mode. It is not required in inetd/xinetd mode.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                on
# If set on you can experience a longer connection delay in many cases.
IdentLookups            off

ServerName            "Debian"
ServerType            standalone
DeferWelcome            off

MultilineRFC2228        on
DefaultServer            on
ShowSymlinks on

TimeoutNoTransfer        600
TimeoutStalled            600
TimeoutIdle            1200

DisplayLogin welcome.msg
DisplayChdir .message true
ListOptions "-l"

#DenyFilter            \*.*/

# Use this to jail all users in their homes 
DefaultRoot /var/ftp/

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell        off

# Port 21 is the standard FTP port.
Port                21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress        1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances            30

# Set the user and group that the server normally runs at.
User                proftpd
Group                nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022
# Normally, we want files to be overwriteable.
AllowOverwrite            on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd        off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder            mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile            off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

# Logging onto /var/log/lastlog is enabled but set to off by default
#UseLastlog on

# In order to keep log file dates consistent after chroot, use timezone info
# from /etc/localtime.  If this is not set, and proftpd is configured to
# chroot (e.g. DefaultRoot or <Anonymous>), it will use the non-daylight
# savings timezone regardless of whether DST is in effect.
#SetEnv TZ :/etc/localtime

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://www.securityfocus.com/bid/11430/discuss
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

#
# Useful to keep VirtualHost/VirtualRoot directives separated
#
#Include /etc/proftpd/virtuals.con

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                ftp
#   Group                nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias            anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser    on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell        off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients            10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin            welcome.msg
#   DisplayChdir        .message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

# Include other custom configuration files
Include /etc/proftpd/conf.d/

<IfModule mod_facts.c>
FactsAdvertise off
</IfModule>


```

Any suggestions or help?
By the way same error when I login as root (for testing).

---

### Post by sandyd on 2013-12-17
This isnt proftpd, but try this (note, all commands below require you to be in root, if you arent, run "sudo -i")
```

apt-get remove proftpd*
apt-get install pure-ftpd
cd /etc/pure-ftpd
ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/10_puredb
echo "no" > /etc/pure-ftpd/conf/PAMAuthentication

```
Now, lets create a user.
here, I assume that
/home/ggallian is owned by ggallian:ggallian
ggallian has a uid/gid of 1001/1001
```

pure-pw useradd ggallian -D /home/ggallian -u 1001 -g 1001
```
Enter in the password when it asks

Build the pure-pw db
```

pure-pw mkdb
service pure-ftpd restart

```

There are other options avaliable, you can run
```
pure-pw
```to get them

---

### Post by ggallian on 2013-12-17
thanks SandyD,

Unfortunately I am getting access denied using the instructions above.
When I ran the command: 
ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/10_puredb
I received an error stating 10_puredb did not exist, so instead I used the cp command.
Not sure if that caused any problems.

Thanks,

---

### Post by sandyd on 2013-12-17
> **ggallian said:**
> thanks SandyD,

Unfortunately I am getting access denied using the instructions above.
When I ran the command: 
ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/10_puredb
I received an error stating 10_puredb did not exist, so instead I used the cp command.
Not sure if that caused any problems.

Thanks,
Can you post the output of
```

tree /etc/pure-ftpd
```?
You may have to install 'tree' if it isnt done already

---

### Post by ggallian on 2013-12-18
thanks again for your help, much appreciated! 
Please see the image below of the tree structure of pureftpd.
[IMG]http://s23.postimg.org/bf2lf6lsb/tree_pureftpd.png[/IMG]

---

