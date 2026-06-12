---
title: "maxon bp3-ext on ubuntu 8.04"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by gnulund on 2008-07-11
how do i connect using a usb maxon bp3-ext modem.
some forums suggest using ppp but i can't find the ppp utility.
help please

---

### Post by cariboo on 2008-07-11
THe ppp daemon is part of the standard installation, what you are looking for is **kppp** or **gnome-ppp**. Both are in the repositories and can be installed using Add/Remove Programs or Synaptic Package Manager.

Jim

---

### Post by dweh on 2009-06-23
EUREKA!! re bp3 ext and Telstra (AU)  
after NO help from Telstra Bigpond whatsover  .... we discovered this simple solution quite by accident ...
 bring up "mobile broadband" tab (ubuntu connection options) 
then hit ADD
the option to select then is Telstra (UMTS/HSDPA
now enter your user name and password 
then Change the APN to 'telstra.bigpond
 Bingo !!  it should work now!

---

### Post by technocynic on 2009-07-30
I have followed those instructions but still can not connect.

I'm using eeebuntu.

The modem only seems to be recognised if it is connected prior to start-up. When I attempt to connect, I get a "GSM network disconnected" message. I have tested the modem on another (Mac) machine and it works ok.

any suggestions?

---

### Post by technocynic on 2009-07-30
sorted, i hope

combination of a typo and a misunderstanding

---

### Post by brotell on 2009-09-21
Im having the same problem tried the suggested solutions but all I get is gsm network disconnected.
any ideas

Terry

---

