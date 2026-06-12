---
title: "Cisco Packetracer on Ubuntu 12.04 LTS"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by Newbeatontheblock on 2013-02-21
Hi all,
I tried installing packettracer for cisco but something is going wrong here . My specs are

OS Ubuntu 12.04 LTS
Laptop hardware -  
Aspire 5538G
Memory 3.9 Gib 
Processor Amd Athlon X2 Dual Core Processor L310 x2
Graphics : Vesa M: 92
OS type - 32- Bit

I have tried the following 
* first i download packettracer
* Then i did Extract that .gz file. with archive manager which gives me errors 
3. Right clicked on Insall(shell script) file and selected properties and then i went  permission tab and selected “allow 
file executing file as program”. Then i clicked on close button.


Then i tried to install this with Sudo apt-get

But this isnt working either
I have tried with several versions of packettracer

Any one had similar issues ?

---

### Post by alphacrucis2 on 2013-02-21
Apt-get is for installing packages from online repos. If you had a deb file you would install it using dpkg. The file you downloaded should be able to be read by the archive manager unless the file is corrupt. Was a readme file included?

---

### Post by Newbeatontheblock on 2013-02-23
Hi
There was no readme file included.
I m gonna try to download it from a different source

Thanks and regards

---

