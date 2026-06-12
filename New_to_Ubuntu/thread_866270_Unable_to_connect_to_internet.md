---
title: "Unable to connect to internet"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Mutant Human on 2008-07-21
Whenever i start internet connect manager in the latest kubuntu,it says unable to find 'etc/resolv.conf' file.Please ask your admin to write it.
I have got a conexant HSF softv92 modem.I have tried to have the driver from  different sources which after installing successfully does not let me to connect to internet.My modem is present in COM3 port so which port i should select.
Please help me in this Regard,
Thanks.

---

### Post by alphaniner on 2008-07-21
First things first, do you have an '/etc/resolv.conf' file?

---

### Post by Mutant Human on 2008-07-22
No i dont have this file.How to create and what it does?

---

### Post by decoherence on 2008-07-22
To create it, press Alt F2 and type

gksudo gedit /etc/resolv.conf

Give it your password (resolv.conf is a protected file) and put in something similar to this

nameserver 208.67.222.222
nameserver 208.67.220.220

Those are the IPs for OpenDNS, which you can use. Or you can put your ISP's supplied DNS servers in there.

The purpose of the file is to resolve internet names in to IP addresses, ie., ubuntuforums.org to 91.189.94.12

EDIT: I just realized you're using kubuntu and not ubuntu... when you press Alt F2, instead of 

gksudo gedit /etc/resolv.conf

try

kdesudo kedit /etc/resolv.conf

or maybe 

kdesudo kate /etc/resolv.conf

I really don't know from KDE... hopefully a kubuntu user can let us know if this is wrong.

---

### Post by Mutant Human on 2008-07-25
sudo kate /etc/resolv.conf

This command worked for me in Kubuntu.
I have got Conexant HSF Soft v92 modem.I want a full functional open source free driver for it.I don't want a proprietary driver by linuxant.
So please help in this step also.

---

### Post by phidia on 2008-07-25
> **Mutant Human said:**
> 
I have got Conexant HSF Soft v92 modem.I want a full functional open source free driver for it.I don't want a proprietary driver by linuxant.
So please help in this step also.

I think you will want to go [here]("http://www.linmodems.org/") and get the scanmodem tool so you can ID the chipset-then follow the guides there.
There's also an [Ubuntu Community Doc on dial up modems]("https://help.ubuntu.com/community/DialupModemHowto").

---

