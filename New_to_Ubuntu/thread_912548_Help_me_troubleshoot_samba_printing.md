---
title: "Help me troubleshoot samba printing"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by ant2ne on 2008-09-06
Symptom: Win XP Clients can connect to the print server. Can see the Printer. Can connect and install the printer. Clients appear to send the print job to the printer, but nothing prints. The 0 never turns into a 1. 

Samba Server Prints just fine.


Here is my smb.conf
```
[global]
server string  = PrintServer
workgroup = CYGNEHOME
browseable = yes
load printers = yes
guest ok = yes
browse list = yes
printcap name = cups
printing = cups
load printers = yes
# GUEST HANDLES
guest account = guest
map to guest = guest

[Temp]
path = /home/shares/temp
read only = no



#GLOBAL PRINTER SECTION
[printers]
comment = All Printers
browseable = yes
printable = yes
writable = no
public = yes
guest ok = yes
path = /var/spool/samba


#SPECIFIC PRINTER SECTION
[Officejet_J3600_series]
print ok = yes
printable = yes
printing = cups
path = var/spool/samba
#PRINT COMMANDS

#PRINT DRIVER STORE (NOT SET UP YET)
[print$]
comment = Printer Drivers Share
path = /var/lib/samba/drivers
write list = ant2ne, mandi
```

[Officejet_J3600_series] was the chosen name because it is the name that is displayed in System -> Administration -> Printing

---

### Post by ant2ne on 2008-09-12
Got nothing for me?  Am I posting in the wrong section?

---

