---
title: "found localhost:631 for cups. What else is in localhost:&lt;n&gt;"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by Sherman_Willden on 2014-04-18
I just found out that I can manage cups and printers from localhost:631. What else is available in localhost:<n> and how do I use them?

Thank you;

---

### Post by coldcritter64 on 2014-04-18
localhost or 127.0.0.1 is the name/IP-address for your installation. 
The ":631" is port number 631, one of 65536 ports, numbered from 0 to 65535, on your local installation. 
CUPS the printing service uses port number 631 and gives you access to controlling it by that localhost:<n> style of browser address. 

I'm not aware of any others using that specific address type, but many network applications allow you to access/control them through your browser, transmission bit torrent client is one that does (on a non-system port 9091, cups on port 631 is using a system port ie one numbered less than 1024).

Edit: just tested with transmission: "localhost:9091" as the address in firefox gets the web interface for transmission up. See the two attached screenshots, it is more generally used than I first realized.

---

### Post by tgalati4 on 2014-04-18
There are several services that have web interfaces.  You will have to search for them because I am not aware of a comprehensive list.  Media servers, download servers, print and file servers have web interfaces.  There are several ways to control services.  Using a web page is just one of them.

You can do a lot with CUPS through the command line as well:

tgalati4@Mint14-Extensa ~ $ apropos cups
backend (7)          - cups backend transmission interfaces
classes.conf (5)     - class configuration file for cups
client.conf (5)      - client configuration file for cups
cups-calibrate (8)   - ESP CUPS Printer Calibration Tool
cups-deviced (8)     - cups device daemon
cups-driverd (8)     - cups driver daemon
cups-genppdupdate (8) - update CUPS+Gutenprint PPD files
cups-lpd (8)         - receive print jobs and report printer status to lpd clients
cups-snmp.conf (5)   - snmp configuration file for cups
cupsaccept (8)       - accept/reject jobs sent to a destination
cupsreject (8)       - accept/reject jobs sent to a destination
cupsaddsmb (8)       - export printers to samba for windows clients
cupsctl (8)          - configure cupsd.conf options
cupsd (8)            - cups scheduler
cupsd.conf (5)       - server configuration file for cups
cupsdisable (8)      - stop/start printers and classes
cupsenable (8)       - stop/start printers and classes
cupsfilter (8)       - convert a file to another format using cups filters
cupstestdsc (1)      - test conformance of postscript files
cupstestppd (1)      - test conformance of ppd files
filter (7)           - cups file conversion filter interface
lpadmin (8)          - configure cups printers and classes
lpstat (1)           - print cups status information
mailto.conf (5)      - configuration file for cups email notifier
mime.convs (5)       - mime type conversion file for cups
mime.types (5)       - mime type description file for cups
ppdc (1)             - cups ppd compiler
ppdcfile (5)         - cups ppd compiler source file format
ppdhtml (1)          - cups html summary generator
printers.conf (5)    - printer configuration file for cups
subscriptions.conf (5) - subscriptions file for cups
system-config-printer (1) - configure a CUPS server

---

