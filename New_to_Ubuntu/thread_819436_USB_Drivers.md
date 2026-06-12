---
title: "USB Drivers"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-06-05
I have an IO Gear USB/Serial adapter I use to interface a GPS to my notebook. The driver which came with the adapter is for a Windows application. I went to the company's website & found a Linux 'Redhat' driver download for the adapter. Is it possible to use the Redhat driver with Ubuntu 7.10 ?

---

### Post by Duck2006 on 2008-06-05
> **CoCoKnots said:**
> I have an IO Gear USB/Serial adapter I use to interface a GPS to my notebook. The driver which came with the adapter is for a Windows application. I went to the company's website & found a Linux 'Redhat' driver download for the adapter. Is it possible to use the Redhat driver with Ubuntu 7.10 ?

Yes, this may help.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by CoCoKnots on 2008-06-05
Thanks Duck2006, A lot of great information... I'm still not certain about the compatibility of Redhat with Ubuntu. Is there any harm if I download the Redhat driver & try it ?

---

### Post by Duck2006 on 2008-06-05
No, no harm, If it does not work for you just uninstall it.

---

### Post by CoCoKnots on 2008-06-05
OK... I downloaded a file from the vendor. Now I really feel dumb. It's a zip  file called GUC232A_redhat.zip . How do I un-zip it to access it? I assume I need to use 'System>Admin.>Syn.Pgk.Mgr after I access the file to install it?

---

### Post by Duck2006 on 2008-06-05
Look for p7zip full, in your Syn.Pgk.Mgr

---

### Post by CoCoKnots on 2008-06-05
OK, I have it... Now, How do I use it ?

---

### Post by Duck2006 on 2008-06-05
Click on the downloaded file and extract the folder to where you want it.

---

### Post by cariboo on 2008-06-05
You should just be able to double click on the file, and File Roller should open and it is pretty self evident from there. As far as your GPS is concerned, plug it in, and then have a look at dmesg. in a terminal type:

```
dmesg
```

The last 3 or 4 lines should have info about your GPS here is an example when I plug in mine:

```
 2578.934893] usb 2-2: new full speed USB device using ohci_hcd and address 3
[ 2579.139151] usb 2-2: configuration #1 chosen from 1 choice
```

Here is the output of lsusb

```
jimk@intrepid:~$ lsusb
Bus 002 Device 003: ID 091e:0003 Garmin International GPSmap (various models)
Bus 002 Device 002: ID 0665:5161  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

From here you can do a search on Google and see if anybody has had any success  wiht your model of GPS. Be sure to also do a search on the device ID number

Good luck

Jim

---

### Post by Rhubarb on 2008-06-05
My experience with a few different branded serial to usb adapters has been good (perhaps yours is good too).

I've found that a usb to serial device automatically appears as /dev/ttyUSB0
or similar.

A good way to test if this is true is to install gtkterm from the ubuntu repositories, then tell it to check /dev/ttyUSB0 at your desired baud rate, then you should see (depending on what you've connected up to it) something in your gtkterm window.

Edit:  to get GPS working is a different matter, I have had success getting a bluetooth NMEA transmitting GPS unit fine in Ubuntu 8.04 with gpsd.

---

### Post by CoCoKnots on 2008-06-05
I now have a file on my desktop titled 'GUC232A' Inside this folder are three more files called Redhat7_3, Redhat8 & Redhat9 ???:confused:

---

### Post by CoCoKnots on 2008-06-05
Thanks everyone... Looks like I'll be working on this for a little while. You may see me on again later. Thanks Again...

---

### Post by Duck2006 on 2008-06-05
> **CoCoKnots said:**
> I now have a file on my desktop titled 'GUC232A' Inside this folder are three more files called Redhat7_3, Redhat8 & Redhat9 ???:confused:

Not sure as to witch one to use, have a look in the foldes and see it there is a read me file or a text file.

---

### Post by ssinfod on 2008-06-26
Hi, 

I am using Ubuntu 8.04 (Hardy Heron) and I also have the GUC232A USB-Serial converter.

I have installed gtkterm (thanks rhubarb) and the GUC232A is working fine.

I did NOT have to install any driver. The driver is built in Ubuntu (8.04).

I hope this helps.

---

