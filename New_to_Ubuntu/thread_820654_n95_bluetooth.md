---
title: "n95 bluetooth"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-06-06
I have just brought a bluetooth dongle, and it work straight out the box :-) only problem is my N95 phone wont send to my pc, my PC will send to the N95 perfectly!
I have enable sending like receive file from remote devices etc, but it still not working! Any help would be useful!

---

### Post by sayakb on 2008-06-06
That is a bug with Hardy. 
[https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/211252](https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/211252)

In Gutsy, it worked by installing a package called **obexpushd**. That does not work with Hardy. Google about downgrading the bluetooth applet to the Gutsy version, if that works for you.

---

### Post by sayakb on 2008-06-06
This may work:
Switch on bluetooth on N95.
Right click on the bluetooth-applet icon and select Browse device. 
Select the phone from the list and press Connect.
Enter passkey on both devices. The phone contents will open up like an USB device.

---

### Post by ibizatunes on 2008-06-06
thanks, i think i will wait till the bug gets fixed.....
i can copy any pic via the browse buttun

---

