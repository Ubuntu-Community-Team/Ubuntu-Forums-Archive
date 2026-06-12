---
title: "HOWTO: Home print server using CUPS (using X11 or console based  only)"
date: 2010-01-15
forum: Outdated Tutorials &amp; Tips
---

### Post by frenchn00b on 2010-01-15
Howto: Home print server using CUPS

working way:

**Server:**

>  apt-get install -f cups printconf lynx 
 apt-get install -f  cupsys pnm2ppa cups-pdf  printconf lynx  

If you would like something automatic, for installing, and working for local printer :
> apt-get install  printconf      #                      0.7.9.1                        automatically configures USB and parallel pr

wait installation

get the PPD file here of your printer, and copy it into /etc/cups/
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

then go into xterm:
as user
lynx localhost:631
> This will start the cups server. Next, you'll need to add a printer by using the web interface. To do this, open a web browser and type in localhost:631. If your server is started, a page should load with links to various tasks. Click the first link Do Administration Tasks. A dialog will pop up asking for username and password. You need to log in as root and use your root password to access the administration menu.
Once logged in, click add printers and follow the prompts to set up your printer. When the printer is added, click on the "Configure Printer" to set page size and printing quality. Finally, click "Print Test Page". If a test page prints, you're almost ready to go on to Step 2.

and finally active it as server
 [X] Share published printers connected to this 
I have made change in cupsd.conf
as 
i 
```
 [X] Share published printers connected to this  # Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  AuthType None
  Deny From None
  Allow From All
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
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

```

```
Administration

     Home       Administration       Classes       Documentation/Help       Jobs       Printers

   Printers

      Add Printer Find New Printers Manage Printers

   Classes

      Add Class Manage Classes

   Jobs

      Manage Jobs


                                                             Server

                                                                Edit Configuration File View Access Log View Error Log View Page Log

                                                                Basic Server Settings:

                                                                [X] Show printers shared by other systems
                                                              **  [X] Share published printers connected to this **system
                                                                         [ ] Allow printing from the Internet
                                                                [ ] Allow remote administration
(NORMAL LINK) Use right-arrow or <return> to activate.
  Arrow keys: Up and Down to move.  Right to follow a link; Left to go back.
 H)elp O)ptions P)rint G)o M)ain screen Q)uit /=search [delete]=history list

```
(X11 alternative, type: firefox "localhost:631")
 



commands are : 

```
lpstat -v    #to see all the printers installed  
lpq -a     #to see the queue for printing
lp -d MYPRINTRE      document.pdf    # to print it
lprm JOBID      # to delete a job, seen from lpq -a[/QUOTE]

```

/etc/cups/cupsd.conf
> # Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  AuthType None
  Deny From None
  Allow From All
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
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


**Client:**
To add printers on the client: 
> apt-get install system-config-printer   xprint-common
then type 
> sudo system-config-printer-tui  # for a text based tool
sudo system-config-printer # for a GUI tool (run cmd from xterm as above)
 
For more permissions for clients, to let them free:
> apt-get install visudo sudo
then 
> visudo
and add for /usr/bin/system-config-printer:
> frenchnoob ALL=(ALL) NOPASSWD: /usr/bin/system-config-printer
frenchnoob ALL=(ALL) NOPASSWD: /usr/bin/system-config-printer-tui
frenchnoob ALL=(ALL) NOPASSWD: /usr/bin/kprinter

(frenchnoob shall be replaced by your username (non root))

For X11, KDE client for printing:
> apt-get install kdeprint

> sudo kprinter
***Could anyone complete this HOWTO with the SAMBA, sharing over the windows platforms ?***

---

### Post by frenchn00b on 2010-01-16
OK, too complicated ? I made more easy the installation. 
so try my program : 
```
wget http://easyldap.exofire.net/files/installer/easyldap-installer.sh
sudo sh easyldap-installer.sh
```

screenshot: [1]("http://easyldap.exofire.net/files/installer/20100116shot_30-printing.jpg")  [2]("http://easyldap.exofire.net/files/installer/shot01.jpg")

---

### Post by samhdaniel on 2010-01-17
After you install Samba on your print server, rename the default /etc/samba/smb.conf and substitute one like this:

[global]
        workgroup = (your workgroup name here without parens)
        netbios name = (your server name here without parens)
        server string = print server
        security = share
;       domain master = yes
;       preferred master = yes
;       local master = yes
;       wins support = yes
;       wins proxy = yes
;       os level = 65
;       printing = cups
        printcap name = cups
;       load printers = yes

[printers]
        comment = All Printers
;       browseable = yes
        path = /var/spool/samba
        printable = yes
        public = yes
;       writable = No
        create mask = 0700

Lines that start with a ; are commented out. I left them in my smb.conf to make adding new capabilities easier. They can be deleted without affecting the print server.

On the Windows side, use the add new printer wizard to search for network printers, and select the one you want. You will probably have to install a driver on the Windows box for the printer you selected. You can usually get them from the manufacturers website.

---

### Post by cagey_cretin on 2010-06-24
> then go into xterm:
as user
lynx localhost:631

Configuration file "/etc/lynx.cfg" is not available.

---

### Post by frenchn00b on 2010-06-25
> **cagey_cretin said:**
> Configuration file "/etc/lynx.cfg" is not available.

type lynx [www.google.com](www.google.com)

lynx does work for ur machine?

---

