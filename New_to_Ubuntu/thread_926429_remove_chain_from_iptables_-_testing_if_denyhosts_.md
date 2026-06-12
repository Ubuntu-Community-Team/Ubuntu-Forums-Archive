---
title: "remove chain from iptables - testing if denyhosts works."
date: 2008-09-21
forum: New to Ubuntu
---

### Post by RavUn on 2008-09-21
I added something to iptables a while back that was supposed to prevent people from being able to attempt to ssh in after 8 missed attempts, but I never tested it.  I tried testing it earlier and realized it doesn't seem to work.  Now, I've installed denyhosts and set it to purge every 5 minutes and to deny access after 3 failed attempts... and that doesn't seem to work either.

First, how can I remove the chain from iptables (and why doesn't it work if it's possible to figure that out)?
```
~$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
           tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW recent: SET name: SSH side: source 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW recent: UPDATE seconds: 600 hit_count: 8 TTL-Match name: SSH side: source 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


Secondly, does my denyhosts.conf file appear to be setup how I described?

```

       ############ THESE SETTINGS ARE REQUIRED ############

########################################################################
#
# SECURE_LOG: the log file that contains sshd logging info
# if you are not sure, grep "sshd:" /var/log/*
#
# The file to process can be overridden with the --file command line
# argument
#
# Redhat or Fedora Core:
#SECURE_LOG = /var/log/secure
#
# Mandrake, FreeBSD or OpenBSD: 
#SECURE_LOG = /var/log/auth.log
#
# SuSE:
#SECURE_LOG = /var/log/messages
#
# Mac OS X (v10.4 or greater - 
#   also refer to:   http://www.denyhosts.net/faq.html#macos
#SECURE_LOG = /private/var/log/asl.log
#
# Mac OS X (v10.3 or earlier):
#SECURE_LOG=/private/var/log/system.log
#
# Debian:
SECURE_LOG = /var/log/auth.log
########################################################################

########################################################################
#
# HOSTS_DENY: the file which contains restricted host access information
#
# Most operating systems:
HOSTS_DENY = /etc/hosts.deny
#
# Some BSD (FreeBSD) Unixes:
#HOSTS_DENY = /etc/hosts.allow
#
# Another possibility (also see the next option):
#HOSTS_DENY = /etc/hosts.evil
#######################################################################


########################################################################
#
# PURGE_DENY: removed HOSTS_DENY entries that are older than this time
#             when DenyHosts is invoked with the --purge flag
#
#      format is: i[dhwmy]
#      Where 'i' is an integer (eg. 7) 
#            'm' = minutes
#            'h' = hours
#            'd' = days
#            'w' = weeks
#            'y' = years
#
# never purge:
#PURGE_DENY = 
#
# purge entries older than 1 week
#PURGE_DENY = 1w
#
# purge entries older than 5 days
PURGE_DENY = 5m
#######################################################################

#######################################################################
#
# PURGE_THRESHOLD: defines the maximum times a host will be purged.  
# Once this value has been exceeded then this host will not be purged. 
# Setting this parameter to 0 (the default) disables this feature.
#
# default: a denied host can be purged/re-added indefinitely
PURGE_THRESHOLD = 0
#
# a denied host will be purged at most 2 times. 
#PURGE_THRESHOLD = 2 
#
#######################################################################


#######################################################################
#
# BLOCK_SERVICE: the service name that should be blocked in HOSTS_DENY
# 
# man 5 hosts_access for details
#
# eg.   sshd: 127.0.0.1  # will block sshd logins from 127.0.0.1
#
# To block all services for the offending host:
#BLOCK_SERVICE = ALL
# To block only sshd:
BLOCK_SERVICE  = sshd
# To only record the offending host and nothing else (if using
# an auxilary file to list the hosts).  Refer to: 
# http://denyhosts.sourceforge.net/faq.html#aux
#BLOCK_SERVICE =    
#
#######################################################################


#######################################################################
#
# DENY_THRESHOLD_INVALID: block each host after the number of failed login 
# attempts has exceeded this value.  This value applies to invalid
# user login attempts (eg. non-existent user accounts)
#
DENY_THRESHOLD_INVALID = 3
#
#######################################################################

#######################################################################
#
# DENY_THRESHOLD_VALID: block each host after the number of failed 
# login attempts has exceeded this value.  This value applies to valid
# user login attempts (eg. user accounts that exist in /etc/passwd) except
# for the "root" user
#
DENY_THRESHOLD_VALID = 3
#
#######################################################################

#######################################################################
#
# DENY_THRESHOLD_ROOT: block each host after the number of failed 
# login attempts has exceeded this value.  This value applies to 
# "root" user login attempts only.
#
DENY_THRESHOLD_ROOT = 1
#
#######################################################################


#######################################################################
#
# DENY_THRESHOLD_RESTRICTED: block each host after the number of failed 
# login attempts has exceeded this value.  This value applies to 
# usernames that appear in the WORK_DIR/restricted-usernames file only.
#
DENY_THRESHOLD_RESTRICTED = 1
#
#######################################################################


#######################################################################
#
# WORK_DIR: the path that DenyHosts will use for writing data to
# (it will be created if it does not already exist).  
#
# Note: it is recommended that you use an absolute pathname
# for this value (eg. /home/foo/denyhosts/data)
#
WORK_DIR = /var/lib/denyhosts
#
#######################################################################

#######################################################################
#
# SUSPICIOUS_LOGIN_REPORT_ALLOWED_HOSTS
#
# SUSPICIOUS_LOGIN_REPORT_ALLOWED_HOSTS=YES|NO
# If set to YES, if a suspicious login attempt results from an allowed-host
# then it is considered suspicious.  If this is NO, then suspicious logins 
# from allowed-hosts will not be reported.  All suspicious logins from 
# ip addresses that are not in allowed-hosts will always be reported.
#
SUSPICIOUS_LOGIN_REPORT_ALLOWED_HOSTS=YES
######################################################################

######################################################################
#
# HOSTNAME_LOOKUP
#
# HOSTNAME_LOOKUP=YES|NO
# If set to YES, for each IP address that is reported by Denyhosts,
# the corresponding hostname will be looked up and reported as well
# (if available).
#
HOSTNAME_LOOKUP=YES
#
######################################################################


######################################################################
#
# LOCK_FILE
#
# LOCK_FILE=/path/denyhosts
# If this file exists when DenyHosts is run, then DenyHosts will exit
# immediately.  Otherwise, this file will be created upon invocation
# and deleted upon exit.  This ensures that only one instance is
# running at a time.
#
# Redhat/Fedora:
#LOCK_FILE = /var/lock/subsys/denyhosts
#
# Debian
LOCK_FILE = /var/run/denyhosts.pid
#
# Misc
#LOCK_FILE = /tmp/denyhosts.lock
#
######################################################################


       ############ THESE SETTINGS ARE OPTIONAL ############


#######################################################################
#
# ADMIN_EMAIL: if you would like to receive emails regarding newly
# restricted hosts and suspicious logins, set this address to 
# match your email address.  If you do not want to receive these reports
# leave this field blank (or run with the --noemail option)
#
# Multiple email addresses can be delimited by a comma, eg:
# ADMIN_EMAIL = foo@bar.com, bar@foo.com, etc@foobar.com
#
 ADMIN_EMAIL = 
#
#######################################################################

#######################################################################
#
# SMTP_HOST and SMTP_PORT: if DenyHosts is configured to email 
# reports (see ADMIN_EMAIL) then these settings specify the 
# email server address (SMTP_HOST) and the server port (SMTP_PORT)
# 
#
 SMTP_HOST = mail.yourdomain.com
SMTP_PORT = 25
#
#######################################################################

#######################################################################
# 
# SMTP_USERNAME and SMTP_PASSWORD: set these parameters if your 
# smtp email server requires authentication
#
SMTP_USERNAME=you@yourdomain.com
SMTP_PASSWORD=your_password
#
######################################################################

#######################################################################
#
# SMTP_FROM: you can specify the "From:" address in messages sent
# from DenyHosts when it reports thwarted abuse attempts
#
SMTP_FROM = DenyHosts <nobody@localhost>
#
#######################################################################

#######################################################################
#
# SMTP_SUBJECT: you can specify the "Subject:" of messages sent
# by DenyHosts when it reports thwarted abuse attempts
 SMTP_SUBJECT = Possible SSH Attack
#
######################################################################

######################################################################
#
# SMTP_DATE_FORMAT: specifies the format used for the "Date:" header
# when sending email messages.
#
# for possible values for this parameter refer to: man strftime
#
# the default:
#
#SMTP_DATE_FORMAT = %a, %d %b %Y %H:%M:%S %z
#
######################################################################

######################################################################
#
# SYSLOG_REPORT
#
# SYSLOG_REPORT=YES|NO
# If set to yes, when denied hosts are recorded the report data
# will be sent to syslog (syslog must be present on your system).
# The default is: NO
#
#SYSLOG_REPORT=NO
#
#SYSLOG_REPORT=YES
#
######################################################################

######################################################################
#
# ALLOWED_HOSTS_HOSTNAME_LOOKUP
#
# ALLOWED_HOSTS_HOSTNAME_LOOKUP=YES|NO
# If set to YES, for each entry in the WORK_DIR/allowed-hosts file,
# the hostname will be looked up.  If your versions of tcp_wrappers
# and sshd sometimes log hostnames in addition to ip addresses
# then you may wish to specify this option.
# 
#ALLOWED_HOSTS_HOSTNAME_LOOKUP=NO
#
######################################################################

###################################################################### 
# 
# AGE_RESET_VALID: Specifies the period of time between failed login
# attempts that, when exceeded will result in the failed count for 
# this host to be reset to 0.  This value applies to login attempts 
# to all valid users (those within /etc/passwd) with the 
# exception of root.  If not defined, this count will never
# be reset.
#
# See the comments in the PURGE_DENY section (above) 
# for details on specifying this value or for complete details 
# refer to:  http://denyhosts.sourceforge.net/faq.html#timespec
#
AGE_RESET_VALID=5m
#
######################################################################

###################################################################### 
# 
# AGE_RESET_ROOT: Specifies the period of time between failed login
# attempts that, when exceeded will result in the failed count for 
# this host to be reset to 0.  This value applies to all login 
# attempts to the "root" user account.  If not defined,
# this count will never be reset.
#
# See the comments in the PURGE_DENY section (above) 
# for details on specifying this value or for complete details 
# refer to:  http://denyhosts.sourceforge.net/faq.html#timespec
#
AGE_RESET_ROOT=25d
#
######################################################################

###################################################################### 
# 
# AGE_RESET_RESTRICTED: Specifies the period of time between failed login
# attempts that, when exceeded will result in the failed count for 
# this host to be reset to 0.  This value applies to all login 
# attempts to entries found in the WORK_DIR/restricted-usernames file.  
# If not defined, the count will never be reset.
#
# See the comments in the PURGE_DENY section (above) 
# for details on specifying this value or for complete details 
# refer to:  http://denyhosts.sourceforge.net/faq.html#timespec
#
AGE_RESET_RESTRICTED=25d
#
######################################################################


###################################################################### 
# 
# AGE_RESET_INVALID: Specifies the period of time between failed login
# attempts that, when exceeded will result in the failed count for 
# this host to be reset to 0.  This value applies to login attempts 
# made to any invalid username (those that do not appear 
# in /etc/passwd).  If not defined, count will never be reset.
#
# See the comments in the PURGE_DENY section (above) 
# for details on specifying this value or for complete details 
# refer to:  http://denyhosts.sourceforge.net/faq.html#timespec
#
AGE_RESET_INVALID=10d
#
######################################################################


######################################################################
#
# RESET_ON_SUCCESS: If this parameter is set to "yes" then the
# failed count for the respective ip address will be reset to 0
# if the login is successful.  
#
# The default is RESET_ON_SUCCESS = no
#
#RESET_ON_SUCCESS = yes
#
#####################################################################


######################################################################
#
# PLUGIN_DENY: If set, this value should point to an executable
# program that will be invoked when a host is added to the
# HOSTS_DENY file.  This executable will be passed the host
# that will be added as its only argument.
#
#PLUGIN_DENY=/usr/bin/true
#
######################################################################


######################################################################
#
# PLUGIN_PURGE: If set, this value should point to an executable
# program that will be invoked when a host is removed from the
# HOSTS_DENY file.  This executable will be passed the host
# that is to be purged as its only argument.
#
#PLUGIN_PURGE=/usr/bin/true
#
######################################################################

######################################################################
#
# USERDEF_FAILED_ENTRY_REGEX: if set, this value should contain
# a regular expression that can be used to identify additional
# hackers for your particular ssh configuration.  This functionality
# extends the built-in regular expressions that DenyHosts uses.
# This parameter can be specified multiple times.
# See this faq entry for more details:
#    http://denyhosts.sf.net/faq.html#userdef_regex
#
#USERDEF_FAILED_ENTRY_REGEX=
#
#
######################################################################




   ######### THESE SETTINGS ARE SPECIFIC TO DAEMON MODE  ##########



#######################################################################
#
# DAEMON_LOG: when DenyHosts is run in daemon mode (--daemon flag)
# this is the logfile that DenyHosts uses to report its status.
# To disable logging, leave blank.  (default is: /var/log/denyhosts)
#
DAEMON_LOG = /var/log/denyhosts
#
# disable logging:
#DAEMON_LOG = 
#
######################################################################

#######################################################################
# 
# DAEMON_LOG_TIME_FORMAT: when DenyHosts is run in daemon mode 
# (--daemon flag) this specifies the timestamp format of 
# the DAEMON_LOG messages (default is the ISO8061 format:
# ie. 2005-07-22 10:38:01,745)
#
# for possible values for this parameter refer to: man strftime
#
# Jan 1 13:05:59   
#DAEMON_LOG_TIME_FORMAT = %b %d %H:%M:%S
#
# Jan 1 01:05:59 
#DAEMON_LOG_TIME_FORMAT = %b %d %I:%M:%S
#
###################################################################### 

#######################################################################
# 
# DAEMON_LOG_MESSAGE_FORMAT: when DenyHosts is run in daemon mode 
# (--daemon flag) this specifies the message format of each logged
# entry.  By default the following format is used:
#
# %(asctime)s - %(name)-12s: %(levelname)-8s %(message)s
#
# Where the "%(asctime)s" portion is expanded to the format
# defined by DAEMON_LOG_TIME_FORMAT
#
# This string is passed to python's logging.Formatter contstuctor.
# For details on the possible format types please refer to:
# http://docs.python.org/lib/node357.html
#
# This is the default:
#DAEMON_LOG_MESSAGE_FORMAT = %(asctime)s - %(name)-12s: %(levelname)-8s %(message)s
#
#
###################################################################### 

 
#######################################################################
#
# DAEMON_SLEEP: when DenyHosts is run in daemon mode (--daemon flag)
# this is the amount of time DenyHosts will sleep between polling
# the SECURE_LOG.  See the comments in the PURGE_DENY section (above)
# for details on specifying this value or for complete details
# refer to:    http://denyhosts.sourceforge.net/faq.html#timespec
# 
#
DAEMON_SLEEP = 30s
#
#######################################################################

#######################################################################
#
# DAEMON_PURGE: How often should DenyHosts, when run in daemon mode,
# run the purge mechanism to expire old entries in HOSTS_DENY
# This has no effect if PURGE_DENY is blank.
#
DAEMON_PURGE = 1h
#
#######################################################################


   #########   THESE SETTINGS ARE SPECIFIC TO     ##########
   #########       DAEMON SYNCHRONIZATION         ##########


#######################################################################
#
# Synchronization mode allows the DenyHosts daemon the ability
# to periodically send and receive denied host data such that 
# DenyHosts daemons worldwide can automatically inform one
# another regarding banned hosts.   This mode is disabled by
# default, you must uncomment SYNC_SERVER to enable this mode.
#
# for more information, please refer to: 
#        http:/denyhosts.sourceforge.net/faq.html#sync 
#
#######################################################################


#######################################################################
#
# SYNC_SERVER: The central server that communicates with DenyHost
# daemons.  Currently, denyhosts.net is the only available server
# however, in the future, it may be possible for organizations to
# install their own server for internal network synchronization
#
# To disable synchronization (the default), do nothing. 
#
# To enable synchronization, you must uncomment the following line:
#SYNC_SERVER = http://xmlrpc.denyhosts.net:9911
#
#######################################################################

#######################################################################
#
# SYNC_INTERVAL: the interval of time to perform synchronizations if
# SYNC_SERVER has been uncommented.  The default is 1 hour.
# 
#SYNC_INTERVAL = 1h
#
#######################################################################


#######################################################################
#
# SYNC_UPLOAD: allow your DenyHosts daemon to transmit hosts that have
# been denied?  This option only applies if SYNC_SERVER has
# been uncommented.
# The default is SYNC_UPLOAD = yes
#
#SYNC_UPLOAD = no
#SYNC_UPLOAD = yes
#
#######################################################################


#######################################################################
#
# SYNC_DOWNLOAD: allow your DenyHosts daemon to receive hosts that have
# been denied by others?  This option only applies if SYNC_SERVER has
# been uncommented.
# The default is SYNC_DOWNLOAD = yes
#
#SYNC_DOWNLOAD = no
#SYNC_DOWNLOAD = yes
#
#
#
#######################################################################

#######################################################################
#
# SYNC_DOWNLOAD_THRESHOLD: If SYNC_DOWNLOAD is enabled this parameter
# filters the returned hosts to those that have been blocked this many
# times by others.  That is, if set to 1, then if a single DenyHosts
# server has denied an ip address then you will receive the denied host.
# 
# See also SYNC_DOWNLOAD_RESILIENCY
#
#SYNC_DOWNLOAD_THRESHOLD = 10
#
# The default is SYNC_DOWNLOAD_THRESHOLD = 3 
#
#SYNC_DOWNLOAD_THRESHOLD = 3
#
#######################################################################

#######################################################################
#
# SYNC_DOWNLOAD_RESILIENCY:  If SYNC_DOWNLOAD is enabled then the
# value specified for this option limits the downloaded data
# to this resiliency period or greater.
#
# Resiliency is defined as the timespan between a hackers first known 
# attack and its most recent attack.  Example:
# 
# If the centralized   denyhosts.net server records an attack at 2 PM 
# and then again at 5 PM, specifying a SYNC_DOWNLOAD_RESILIENCY = 4h 
# will not download this ip address.
#
# However, if the attacker is recorded again at 6:15 PM then the 
# ip address will be downloaded by your DenyHosts instance.  
#
# This value is used in conjunction with the SYNC_DOWNLOAD_THRESHOLD 
# and only hosts that satisfy both values will be downloaded.  
# This value has no effect if SYNC_DOWNLOAD_THRESHOLD = 1 
#
# The default is SYNC_DOWNLOAD_RESILIENCY = 5h (5 hours)
#
# Only obtain hackers that have been at it for 2 days or more:
#SYNC_DOWNLOAD_RESILIENCY = 2d
#
# Only obtain hackers that have been at it for 5 hours or more:
#SYNC_DOWNLOAD_RESILIENCY = 5h
#
#######################################################################

```

I made sure denyhosts was running.  I try sshing in and get this:

```

***********@X.X.X.X's password: 
Permission denied, please try again.
***********@X.X.X.X's password: 
Permission denied, please try again.
***********@X.X.X.X's password: 
Permission denied (publickey,password).

```
But, I try again and it still let's me attempt to log on as many times as I wish.

---

### Post by RavUn on 2008-09-22
I checked my hosts.deny and it has my ip address listed (sshd: x.x.x.x) and hosts.allow has nothing in it.  I don't know why it's still letting me ssh in.  I erased the line that had my ip address in hosts.deny and it adds it again when I input the incorrect info.  There's also another ip address in there I don't recognize... so someone may be trying to brute force into my PC, as well.  

auth.log shows:
```

Sep 20 12:10:06 xxx sshd[15143]: Failed password for invalid user webmaster from 124.30.120.200 port 39287 ssh2

```

There are several attempts from that IP address and they're trying various usernames on various ports.  I'd like to know how to block them.  I've disabled ssh for now.

---

### Post by Peter09 on 2008-09-22
Check whats in your hosts.allow. Is that has been configured to let local addresses in? 

Hoave a look at syslog, you will need to run it as sudo, the denyhosts log file will give you some idea of what it is doing.

---

