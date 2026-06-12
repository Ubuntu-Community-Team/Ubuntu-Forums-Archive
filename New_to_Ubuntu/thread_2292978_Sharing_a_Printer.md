---
title: "Sharing a Printer?"
date: 2015-09-01
forum: New to Ubuntu
---

### Post by logix-2006 on 2015-09-01
I was wondering how I would go about sharing a printer with my Windows PCs. 

I already have a samba drive setup. I modified the conf file after following a guide I found online, but my Windows PCs still can't find the printer

Here's my config file:
```

[global]
workgroup = HOME
netbios name =myDrive
server string = myPi
security = share
load printers = yes
printing = cups
printcap name = cups
disable spoolss = no
log file = /var/log/samba/samba.log
syslog = 0
max log size = 100
dns proxy = no
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE
use sendfile = yes
aio read size = 16384
aio write size = 16384
deadtime = 30
usershare max shares = 0
guest account = root


[myDrive]
path = /media
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes


[printers]   
browseable = yes   
printable = yes   
public = yes   
create mode = 0700   
guest only = yes   
use client driver = yes
guest account = smbprint   
path = /home/smbprint   

```

The printer automatically installed when I plugged it in, although printing doesn't seem to work. The printer lights up when I send it a job, but it never prints. It says: "Ready" while the linux says "pending"

but I won't be printing from the linux side, so it doesn't really matter if the linux PC can't print. Only the Windows PCs need to be able to print

When I try to add the printer I can't find it on the Windows site.

Here's the cupsd.conf
```
##
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#


# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn


# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0


# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock


# Show shared printers on the local network.
Browsing On
BrowseLocalProtocols dnssd


# Default authentication type, when authentication is required...
DefaultAuthType Basic


# Web interface setting...
WebInterface Yes


# Restrict access to the server...
<Location />
  Order allow,deny
</Location>


# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>


# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>


# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default


  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>


  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>


  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>


  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>


  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>


  <Limit All>
    Order deny,allow
  </Limit>
</Policy>


# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default


  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>


  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>


  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>


  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>


  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>


  <Limit All>
    Order deny,allow
  </Limit>
</Policy>


#
#



```

---

### Post by TheFu on 2015-09-02
```
# Only listen for connections from the local machine.
Listen localhost:631
```

Fix that to start.  You should get printing from the Linux machine working first just to know that it works.
Also - cups has a webpage for management. [http://ip:631](http://ip:631) will display it AFTER you fix the localhost line.

For a desktop: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
For servers: [https://help.ubuntu.com/14.04/serverguide/cups.html](https://help.ubuntu.com/14.04/serverguide/cups.html)

---

