---
title: "HP Device Manager unable to communicate with discovered device"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by alabamatoy on 2013-03-14
12.04LTS.  HP K80 printer.  device shows up both in lsusb and in the "discovered devices" in the HP Device Manager.  I ran the device manager under gksudo, same results.  The GUI app sees the device ("1 device found") but then its tells me "unable to communicate with the device.  Please check the device and try again."  Device is fine, works like a champ on same box in XP.

Any advice?

---

### Post by alabamatoy on 2013-03-14
When I exit hp device manager, it tells me  Error: Unable to communicate with device (code=12): hpfax:/usb/OfficeJet_K80?serial=MY27TD6093OH

---

### Post by sully101 on 2013-03-16
Is this what we are talking about ? [http://hplipopensource.com/hplip-web/models/officejet/officejet_k80.html]("http://hplipopensource.com/hplip-web/models/officejet/officejet_k80.html"). Did you do the "Wizard" install or the "Manual" install? Have you ran ```
sudo hp-setup
```

---

### Post by alabamatoy on 2013-03-16
> **sully101 said:**
> Is this what we are talking about ? [http://hplipopensource.com/hplip-web/models/officejet/officejet_k80.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_k80.html). Did you do the "Wizard" install or the "Manual" install? Have you ran ```
sudo hp-setup
```

Yes, and I really dont recall a "Wizard" versus a "Manual" install, but I imagine if there were a choice, I chose "Wizard".

And when I run the sudo hp-setup I get ```
HP Linux Imaging and Printing System (ver. 3.13.3)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
error: Unable to communicate with device (code=12): hpfax:/usb/OfficeJet_K80?serial=MY27TD6093OH
error: Unable to communicate with the device. Please check the device and try again.

```

So it finds the device, gets the serial number, then claims it cannot commo with the device.

---

### Post by sully101 on 2013-03-16
Have you tried passing explicit options to hp-setup? more infomation can be found on the hp-setup command by typing ```
man hp-setup
``` in the command line. There are some examples at the bottom of the manual.
eg. sudo hp-setup -i 001:002 where 001:002 are the numbers you get from lsusb
     sudo hp-setup -i US12345678A where US12345678A is the serial number

---

### Post by alabamatoy on 2013-03-16
> **sully101 said:**
> eg. sudo hp-setup -i 001:002 where 001:002 are the numbers you get from lsusb


```
doc@upstairsPC-Linux:~$ sudo hp-setup -i 03f0:0711
[sudo] password for doc: 

HP Linux Imaging and Printing System (ver. 3.13.3)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)

 
--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)

Enter number 0...1 for connection type (q=quit, enter=usb*) ? 0

Using connection type: usb

error: Invalid device URI: 
Using device: hp:/usb/OfficeJet_K80?serial=MY27TD6093OH


Setting up device: hp:/usb/OfficeJet_K80?serial=MY27TD6093OH



---------------------
| PRINT QUEUE SETUP |
---------------------

warning: One or more print queues already exist for this device: OfficeJet_K80, OfficeJet_K80_2, OfficeJet_K80_3, OfficeJet_K80_4.

Would you like to install another print queue for this device (y=yes, n=no*, q=quit) ?
```

I have tired this numerous times now, so I have several queues setup for the same printer, none of which work.

---

### Post by sully101 on 2013-03-16
I would try and remove those print cues in gui mode```
sudo hp-setup -r
```then retry the "sudo hp-setup -i 03f0:0711"

---

### Post by sully101 on 2013-03-16
Try the serial number option ```
sudo hp-setup -i MY27TD6093OH
``` Seems it might support this better than the usb option. As a side note have you installed all the required packages?

```
sudo apt-get install libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-1.0-0-dev wget python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane
```

---

### Post by alabamatoy on 2013-03-17
> **sully101 said:**
> Try the serial number option ```
sudo hp-setup -i MY27TD6093OH
``` Seems it might support this better than the usb option.

Same result, everything seems to work until the last step when it says it cannot communicate with the device.

 > **sully101 said:**
> As a side note have you installed all the required packages?

```
sudo apt-get install libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-1.0-0-dev wget python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane
```

Result of that command:
```
doc@upstairsPC-Linux:~$ sudo apt-get install libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-1.0-0-dev wget python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsane is already the newest version.
libsane set to manually installed.
libsane-dev is already the newest version.
libtool is already the newest version.
libusb-1.0-0-dev is already the newest version.
python is already the newest version.
python-dbus is already the newest version.
python-dbus set to manually installed.
python-dev is already the newest version.
python-imaging is already the newest version.
python-imaging set to manually installed.
python-notify is already the newest version.
python-notify set to manually installed.
python-qt4 is already the newest version.
python-qt4-dbus is already the newest version.
python-reportlab is already the newest version.
python-reportlab set to manually installed.
sane-utils is already the newest version.
sane-utils set to manually installed.
wget is already the newest version.
wget set to manually installed.
xsane is already the newest version.
build-essential is already the newest version.
cups is already the newest version.
cups set to manually installed.
cups-bsd is already the newest version.
cups-client is already the newest version.
ghostscript is already the newest version.
ghostscript set to manually installed.
libcups2 is already the newest version.
libcups2 set to manually installed.
libcups2-dev is already the newest version.
libcupsimage2-dev is already the newest version.
libdbus-1-dev is already the newest version.
libsnmp-dev is already the newest version.
policykit-1 is already the newest version.
policykit-1 set to manually installed.
policykit-1-gnome is already the newest version.
policykit-1-gnome set to manually installed.
python-gobject is already the newest version.
python-gobject set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libjpeg-turbo8-dev : Conflicts: libjpeg62-dev but 6b1-2ubuntu1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


```

---

### Post by sully101 on 2013-03-17
> **alabamatoy said:**
> Same result, everything seems to work until the last step when it says it cannot communicate with the device.

Have you unplugged the printer from the usb port then pluged it in again after the install of hplip? Some infomation may be gained by doing a ```
tail -f | dmesg
``` in the terminal and unpluging then repluging the usb port and watching the terminal window to see what happens. NB [ctrl]+c to stop the code running in the terminal.
Have you tried the hplip that is in the "Software centre", did it work or where did it fail? Did you remove the "Software centre" one first before installing this one?

> libjpeg-turbo8-dev : Conflicts: libjpeg62-dev but 6b1-2ubuntu1 is to be installed My understanding is that libjpeg-turbo8-dev replaces libjpeg62-dev so just to check you have all the required packages you could re-run the line without libjpeg62-dev ```
sudo apt-get install libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libsnmp-dev libtool libusb-1.0-0-dev wget python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane

```

---

### Post by trundlenut on 2013-03-17
Was the printer connected to the PC when you installed hplip.  I recall some message during installation that said to disconnect any usb printers before continuing (though I could be imagining it).  Also have you installed the latest version from teh website, rather than the version in the ubuntu repositories?

Does the hplip websit offer any information on the compatibility of your printer with the hplip software?

---

### Post by alabamatoy on 2013-03-19
> **sully101 said:**
> Have you tried the hplip that is in the "Software centre", did it work or where did it fail? Did you remove the "Software centre" one first before installing this one?

OK, this fixed the problem.  I dont understand why.  I quit the HPLIP that I had DLed from HP site and installed, ran the software center version and installed it, and everything works.  I dont understand why, but its fixed.

Thank you !!!!!

---

### Post by sully101 on 2013-03-19
Glad to hear it :)

---

