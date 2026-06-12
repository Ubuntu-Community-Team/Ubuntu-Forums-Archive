---
title: "CUPS print server with two NICS"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by bindatype on 2008-07-30
I am trying to set up a CUPS print server using Hardy. The PC has two NICS, eth0 faces a network with address 172.16.0.* and eth1 faces a local network 192.168.12.*. The PC hosts a DHCP server on eth1 and the only client is an OKI c5300 printer. 

          [PC]--(eth0)---------other machines on the 172.16.0.* block
            |  172.16.0.1  
            |
          (eth1)
            |
            |
         Printer (192.168.12.100)

Ideally, the other machines on 172.16.0.* will be able to access the printer on eth1 thru CUPS.    

Presently I can print to the printer from the PC but none of the other machines can see or connect to the printer. The two NICS aren't bridged but I don't think that is necessary. I can see the CUPS server via [http://172.16.0.1:631](http://172.16.0.1:631) on the eth0 side and CUPS can print to the printer on the eth1 side.

Any thoughts?


Here is a snippet of the cupsd.conf file:

# Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Allow remote access
Listen 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
DefaultEncryption IfRequested
<Location />
  Allow localhost
  Allow 172.16.0.1
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  Allow localhost
  Allow 172.16.0.1
  # Allow remote administration...
  Order allow,deny
  Allow localhost
  Allow @LOCAL
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Allow localhost
  Allow 172.16.0.1
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>

---

