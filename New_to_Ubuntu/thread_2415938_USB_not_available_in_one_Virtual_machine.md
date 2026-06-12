---
title: "USB not available in one Virtual machine"
date: 2019-04-03
forum: New to Ubuntu
---

### Post by zak100 on 2019-04-03
Hi,
I have installed two VMs. On one (i.e. Mobisec) USB is not available but USB is available on another one. I have used the following command:
 [INDENT]


sudo adduser zulfi vboxusers
[sudo] password for zulfi: 
The user `zulfi' is already a member of `vboxusers'.[/INDENT] 

My virtual Box version is 5.2.18 Ubuntu r123745
& Virtual Machine version is: Mobisec 1.1.iso

Somebody please guide me.

Zulfi.

---

### Post by TheFu on 2019-04-03
USB devices can only be exclusively locked by 1 running OS at a time.  Trying to have 2 VMs running concurrently with both having access to the same physical hardware isn't possible.  
There was a bug: [https://www.virtualbox.org/ticket/18059](https://www.virtualbox.org/ticket/18059) which requires reinstalling vbox, if I'm reading it correctly.

---

### Post by zak100 on 2019-04-04
Hi,
Thanks. I tried with only one VM but still USB is disable. Reinstallation is very difficult for me. Kindly suggest some other solution. I tried google drive but it asks for installation of updated browser. I tried installing different browsers but they don't work.

Zulfi.

---

### Post by TheFu on 2019-04-04
[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

No idea what google drive or a new browser has to do with accessing USB storage.  Best to ask different questions in new threads.

---

