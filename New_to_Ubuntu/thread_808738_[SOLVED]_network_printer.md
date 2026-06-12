---
title: "[SOLVED] network printer"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-05-26
I'm trying to setup a printer over a network. I am on Linux Ubuntu 8.04 and my printer is an HP PSC 2110 All-in-one printer. I tried numerous times to properly set it up, but I've had no luck.

Any help is greatly appreciated

---

### Post by iaculallad on 2008-05-26
> **JimmyJim said:**
> I'm trying to setup a printer over a network. I am on Linux Ubuntu 8.04 and my printer is an HP PSC 2110 All-in-one printer. I tried numerous times to properly set it up, but I've had no luck.

Any help is greatly appreciated

Post your /etc/cups/cupsd.conf file.

Code:

> cat /etc/cups/cupsd.conf

---

### Post by JimmyJim on 2008-05-26
> **iaculallad said:**
> Post your /etc/cups/cupsd.conf file.

Code:

LogLevel warning
SystemGroup lpadmin
# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
DefaultAuthType Basic
<Location />
  Allow all
  # Restrict access to the server...
  Order allow,deny
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>


Is this what you wanted? Thanks again.

---

### Post by JimmyJim on 2008-05-26
Oh, I should have mentioned. The printer is connected to a computer that uses Windows XP Home Edition. I'm not sure if that makes a difference.

---

### Post by lklk on 2008-05-26
Print the configuration page from the printers menu. If it has an IP address listed for itself go to system>administration>printing. Next select new printer. Chose AppSocket/HP JetDirect and type in the IP from the configuration page, you should leave the port set to 9100 unless you know it is different. Click forward and select the correct drivers.

*Some HP printers display their IP on the lcd when they are in stand by. This works for me at school and we have all HP printers. The printers get there IPs through DHCP.

Edit:
Just read your second post I missed earlier. Try my method but it is for stand alone network printers. Make sure you have Samba install correctly and that you can see shared folders from the XP machine.

---

### Post by iaculallad on 2008-05-26
> **JimmyJim said:**
> Oh, I should have mentioned. The printer is connected to a computer that uses Windows XP Home Edition. I'm not sure if that makes a difference.

Aahhh... I'm guessing the printer is connected to an Ubuntu machine so I ask for your CUPS config file and probably ask you to post the result of this **cat /var/log/cups/error_log**.
You could try this [link]("http://ubuntuforums.org/showthread.php?t=347730") for windoze printer sharing.

---

### Post by JimmyJim on 2008-05-26
> **iaculallad said:**
> Aahhh... I'm guessing the printer is connected to an Ubuntu machine so I ask for your CUPS config file and probably ask you to post the result of this **cat /var/log/cups/error_log**.
You could try this [link]("http://ubuntuforums.org/showthread.php?t=347730") for windoze printer sharing.

I looked at that link and the link for Redmon in step 3 doesn't work :confused:

---

### Post by iaculallad on 2008-05-26
> **JimmyJim said:**
> I looked at that link and the link for Redmon in step 3 doesn't work :confused:

If that doesn't work for you, try [this]("http://www.smartcomputing.com/editorial/article.asp?article=articles%2F2006%2Fs1702%2F56s02%2F56s02.asp") :-)

---

### Post by JimmyJim on 2008-05-26
> **iaculallad said:**
> If that doesn't work for you, try [this]("http://www.smartcomputing.com/editorial/article.asp?article=articles%2F2006%2Fs1702%2F56s02%2F56s02.asp") :-)

Thanks but it says "To view the full text of any article published in Smart Computing, PC Today, First Glimpse or Computer Power User magazine, you must be a paid subscriber to one of these publications." :(

---

### Post by iaculallad on 2008-05-26
Hope this would work:
[http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html](http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html)

**Use the The Ubuntu 5.10 Machine (Print Client)** for client setting.
**The Windows XP Machine (The Print Server)** for print server setting.

---

### Post by JimmyJim on 2008-05-26
> **iaculallad said:**
> Hope this would work:
[http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html](http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html)

**Use the The Ubuntu 5.10 Machine (Print Client)** for client setting.
**The Windows XP Machine (The Print Server)** for print server setting.

It worked! 

.. so far anyway, thanks a lot! :)

---

### Post by iaculallad on 2008-05-26
You're welcome and Good luck. Go Ubuntu

---

### Post by JimmyJim on 2008-05-26
One small problem: I'm trying to have the Windows XP firewall open a port for the the Linux connection. I tried that last step on the blog that you posted; I looked in the log file and I could not find the port that I should be using. Any idea as to what I should do? Thanks

It worked until I reactivated the Windows Firewall

---

### Post by JimmyJim on 2008-05-26
Ah, never mind. I looked through a long list of numbers and found the port. It just wasn't clear. It now works. Thanks a lot :)

---

### Post by iaculallad on 2008-05-26
> **JimmyJim said:**
> One small problem: I'm trying to have the Windows XP firewall open a port for the the Linux connection. I tried that last step on the blog that you posted; I looked in the log file and I could not find the port that I should be using. Any idea as to what I should do? Thanks

It worked until I reactivated the Windows Firewall

CUPS printing port should be 631.

---

