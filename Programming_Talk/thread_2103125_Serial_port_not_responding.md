---
title: "Serial port not responding"
date: 2013-01-09
forum: Programming Talk
---

### Post by bavovanachte on 2013-01-09
Hi,

For my Masterproject I am developing a wireless communication system on the PCM-9562. It has 6 serial ports on board and I wish to use them for ZIGBEE communication. However, I can't seem to communicate through them using cutecom.

I have compared the data from the BIOS settings and the output from dmesg|grep ttyS. This tells me that Ubuntu recognizes the ports and the interrupt adresses match. The permissions for /dev/ttyS0 through /dev/ttyS4 are set correctly.

I am using Ubuntu 10.10 and cannot upgrade to a newer version because of driver compatibility.

Can someone please help me or point me in the right direction? I don't know what to search for in google :(

Thanks

---

