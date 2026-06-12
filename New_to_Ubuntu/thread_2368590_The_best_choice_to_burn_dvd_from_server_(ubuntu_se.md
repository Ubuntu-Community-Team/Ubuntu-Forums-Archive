---
title: "The best choice to burn dvd from server (ubuntu server)"
date: 2017-08-12
forum: New to Ubuntu
---

### Post by sed_faster on 2017-08-12
Hello folks,

I have a server without Ethernet. On my desktop to burn data in dvd I use the software "xfburn", but on environment server (ubuntu server) I only use terminal to burn data in dvd. Once I haven't internet on this pc, ubuntu server, how should I install software to burn data in dvd? And which software should I choose?

I know I will need download all the package this software to install on ubuntu server. Right?

Thanks

---

### Post by TheFu on 2017-08-12
You should connect the server to the LAN that the desktop is on and access the internet.  Skip the DVD.  Heck, I'd use a flash drive before burning DVDs all the time.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by sed_faster on 2017-08-12
On environment where I have the server I can't access internet. This network it is restricted. I am thinking download all dependencies to my disk and upload to this server and install program, as a simply executable on windows. Do you understand? (Sorry, but my english it isn't good and I can explain wrong somthing). thanks

---

### Post by TheFu on 2017-08-12
**Air-gapped** patching is hard.  OTOH, if it is truly air-gapped, then I wouldn't worry about patching unless there was a specific issue that needed to be resolved.

BTW, I've worked in air-gapped networks for a few years, but we didn't have Linux on that LAN.  We also had a lab where we tested all hardware, software and interactions before loading anything into the air-gapped production network.

---

### Post by sed_faster on 2017-08-12
Ok....Which best option to the software to burn DVD from terminal? And how they works? I am thinking some a basic command like this "software path/to/folder /media/driveDVD".
Thanks

---

### Post by deadflowr on 2017-08-12
> **Edgar_Oliveira said:**
> Ok....Which best option to the software to burn DVD from terminal? And how they works? I am thinking some a basic command like this "software path/to/folder /media/driveDVD".
Thanks

Probably wodim.
See: [https://help.ubuntu.com/community/CdDvd/Burning#Burning_a_CD_on_the_Command_Line_with_wodim]("https://help.ubuntu.com/community/CdDvd/Burning#Burning_a_CD_on_the_Command_Line_with_wodim")

---

### Post by sed_faster on 2017-08-14
Thanks,

---

