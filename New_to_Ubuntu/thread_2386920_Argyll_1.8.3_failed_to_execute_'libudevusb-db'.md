---
title: "Argyll 1.8.3 failed to execute '/lib/udev/usb-db'"
date: 2018-03-12
forum: New to Ubuntu
---

### Post by lmplattanzio on 2018-03-12
Hi there,


I have installed Argyll 1.8.3 + repack 2 and Dispcalgui 3.1.0.0-1 from the Software Center (Lubuntu 16.04) but I cannot get my Spider5 to work. 
I checked the syslog and I found the following errors:
failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:10.2/usb4/4-2': No such file or directory
failed to execute '/lib/udev/usb-db' 'usb-db /devices/pci0000:00/0000:00:10.2/usb4/4-2/4-2:1.0': No such file or directory


The information I found about these errors refer to an old bug wich is supposed to have been already solved a few year ago.


quote


This bug was fixed in the package argyll - 1.4.0-8ubuntu5


---------------
argyll (1.4.0-8ubuntu5) saucy; urgency=low


  * Use hwdb builtin, instead of the obsolete usb-db in the udev
    rules. (LP: #1200185)
 -- Dmitrijs Ledkovs <email address hidden> Thu, 29 Aug 2013 22:55:30 +0100


Changed in argyll (Ubuntu):
status:	Confirmed &#8594; Fix Released


unquote


How can I correct this error? 


Regards
Luigi

---

