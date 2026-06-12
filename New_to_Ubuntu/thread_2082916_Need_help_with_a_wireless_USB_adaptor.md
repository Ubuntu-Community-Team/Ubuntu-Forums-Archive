---
title: "Need help with a wireless USB adaptor"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by slightlyvalid on 2012-11-10
I have a DWA-130 adapter rev.A1.

It came with a CD and I opened it with wine. 
After I install the drivers from the CD it prompts me to put in the USB adapter and press next. It never seems to recognize the USB stick I put in.

I'm running Version 11.04 and have no access to the internet. That's why I need the adapter. 

Any help?

---

### Post by squakie on 2012-11-10
Just a couple things:

- with the device plugged in, open a terminal and type:

lsusb <press enter>

post the output back here in a reply.


- Wine won't recognize USB devices

- You don't install a Windows driver to Wine - it's not going to do any good

What we need to do is find a Linux driver for you.  The lsusb (list devices on the USB busses) will do is identify the adapter to us - by manufacturer and product id (the xxxx:xxxx).  This will help us in trying to help you find a driver.

---

### Post by NikTh on 2012-11-10
> **slightlyvalid said:**
> 
I'm running Version 11.04 and have no access to the internet. That's why I need the adapter. 

Hi , 

Ubuntu 11.04 is EOL. => [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) not supported anymore. 
I suggest you to download and install a newer version of Ubuntu. 12.04 LTS is a good version (supported until April 2017 due to Long Term Support). 

You can find it here: [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Newer supported version means : Newer Kernel , newer packages , better hardware support . Maybe your USB Wifi Dongle , will plug n play in 12.04 LTS. 


Thanks

---

