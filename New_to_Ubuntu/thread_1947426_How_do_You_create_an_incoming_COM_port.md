---
title: "How do You create an incoming COM port ?"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by suomalainen on 2012-03-26
Ubunteros,

I got a Samsung Nexus S upon which I installed Bluenmea. The read me file states:

> BlueNMEA as a RFCOMM client
---------------------------

This mode was a hack to make BlueNMEA work on Android 1.5 and 1.6.  It
is deprecated, but may still be useful if your Android handset is not
upgraded yet.  It may or may not be available on newer handsets.

Make the remote device listen for RFCOMM.  On Windows Mobile, create
an incoming COM port, and make the Bluetooth adapter visible.

In BlueNMEA, select the GPS source, and click on "connect".  It
attempts to discover nearby Bluetooth devices (no pairing required).
Click on the desired remote device.

Once connected and location information is available, BlueNMEA starts
sending NMEA records.

**QUESTION**

How do I create create an incoming COM port in Ubuntu 10.04LTS?

When I open the Bluenmea app it says:
> TCP status listening on port 4352

Thank you!

---

### Post by Frogs Hair on 2012-03-26
You can add the firewall configuration GUI from the software center and go to edit > add rule . I think what you want would be in the advanced tab . If have all the information to enter it is pretty straight forward. 

Opening ports can be done from the terminal also. [https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html) 

There may be some information in the security forum also.

---

