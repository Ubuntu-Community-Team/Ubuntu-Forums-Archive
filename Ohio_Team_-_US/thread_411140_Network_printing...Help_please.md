---
title: "Network printing...Help please"
date: 2007-04-16
forum: Ohio Team - US
---

### Post by irish1916 on 2007-04-16
I have tried to get my ubuntu printer to work in my windows network in Edgy And Fiesty. tried thru cupsys and samba. I could really use some help, it has to be something simple I can get it to work in FC,CENTOS and SUSE.But I want to use Ubuntu.Here is my last cupsd.conf file.Thanks for the help.

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Listen 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
# Allow shared printing...
Order allow,deny
Allow 192.168.1.*
</Location>
<Location /admin>
Order allow,deny
Allow @LOCAL
</Location>
<Location /admin/conf>
AuthType Basic
Require user @SYSTEM
Order allow,deny
Allow 192.168.1.*
</Location>
<Policy default>
<Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>
<Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
AuthType Basic
Require user @SYSTEM
Order deny,allow
</Limit>
<Limit CUPS-Authenticate-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>
<Limit All>
Order deny,allow
</Limit>
</Policy>
Printcap /var/run/cups/printcap
Edit/Delete Message

---

### Post by mitch.c on 2007-04-16
> **irish1916 said:**
> I have tried to get my ubuntu printer to work in my windows network in Edgy And Fiesty. tried thru cupsys and samba. I could really use some help, it has to be something simple I can get it to work in FC,CENTOS and SUSE.But I want to use Ubuntu.Here is my last cupsd.conf file.Thanks for the help.

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Listen 631
...


Here's the first thing I notice... your Listen directive should be:
```
Listen *:631
```
Otherwise things look ok.

As for printing from Windows, you don't really say what's not working, but if you don't need Samba for anything else, it's *much* easier to use IPP printing which requires *no* special cups configuration. Follow the instructions in my post here: [http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2)

For reference, here's my cupsd.conf (please note I allow access to the admin pages from any machine on my local network):
```

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
#BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
#  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
#  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
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

DefaultEncryption IfRequested
```

---

### Post by irish1916 on 2007-04-16
Thanks for the advise.Tried what you suggested, no go.My problem is from Ubuntu i can see windows on the local network but when I go to add a printer in xp I will see is my Ubuntu box and not the printer.Maybe I'll try your ipp suggestion. Been trying this for a week getting a frustrated. I'm pretty new to Linux.I'll keep at it because I've had it with MS, except gaming.Thank again for the help.

---

### Post by irish1916 on 2007-04-16
Thanks again the ipp looks like it will work.i have a cannon mp600 and i need the .inf file to load the drivers for windows. but it finds the printer.Thank you again.

---

