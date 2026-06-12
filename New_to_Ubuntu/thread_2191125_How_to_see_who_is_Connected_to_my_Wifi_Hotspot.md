---
title: "How to see who is Connected to my Wifi Hotspot?"
date: 2013-12-01
forum: New to Ubuntu
---

### Post by rabbyx7xafc on 2013-12-01
I have created a wifi hotspot in my ubuntu 12.04 by going to the Network-->Wireless-->use hotspot...
the wifi hotspot is running fine and i can now connect my phone and ipod with wifi..
but what i want to know is that how to see who or what devices are connected to my wifi hotspot network??



sorry for being a noob :(

---

### Post by cogset on 2013-12-02
Well,since no one has chimed in yet,I'll tell you what little I know:
-you can see open sockets in your system with **ss** ,for instance **ss -ap** will show all sockets and which processes are using them,** ss -ar** will try to resolve host names-read the man for more uses.
**-netstat** can give you a lot more info,you really should read the man page to see what it can display,however a widely used option would be```
sudo netstat -altupn 
```(or **-tulnap**,whichever is easier to remember) which will show all tpc and udp connections (including listening) and the programs which are using them,and with the**  -c** option that information will be printed continuously every second.
-**iptraf** is a tool for network statistics that will show (and eventually log) your network traffic (as far as I can remember,it's not installed by default)
-**lsof c**an also show active connections using ```
lsof +r -i
```
-**wireshark** is a (very) complex tool that can analyze and also decode packets,as long as you can master it (which I can't).It is an interesting tool nonetheless,at least it can give you the hang of what is going on in your network.

---

### Post by rabbyx7xafc on 2013-12-02
> **cogset said:**
> Well,since no one has chimed in yet,I'll tell you what little I know:
-you can see open sockets in your system with **ss** ,for instance **ss -ap** will show all sockets and which processes are using them,** ss -ar** will try to resolve host names-read the man for more uses.
**-netstat** can give you a lot more info,you really should read the man page to see what it can display,however a widely used option would be```
sudo netstat -altupn 
```(or **-tulnap**,whichever is easier to remember) which will show all tpc and udp connections (including listening) and the programs which are using them,and with the**  -c** option that information will be printed continuously every second.
-**iptraf** is a tool for network statistics that will show (and eventually log) your network traffic (as far as I can remember,it's not installed by default)
-**lsof c**an also show active connections using ```
lsof +r -i
```
-**wireshark** is a (very) complex tool that can analyze and also decode packets,as long as you can master it (which I can't).It is an interesting tool nonetheless,at least it can give you the hang of what is going on in your network.


hey thanks a lot for your response! really apreciate it!

of all the things you mentioned, i found iptraf the most useful! a really nice and simple way to see my network traffic.

but what i am looking  for is a way to see what Devices are connected through my wifi (ie mobile, ipods other laptops)... a client list of sorts...
and a way to disconnect or remove unwanted clients... i could do that very easily in winodws by using a software called connectify! 
is there a way like that in ubuntu... to see a list of all the devices that are connected with me, and to monitor, or disconnected unwanted clients?

thanks in advance :)

---

### Post by cogset on 2013-12-02
If I'm not mistaken (I just use a plain desktop pc connected to a router,so I have no experience about Wifi hotspots) you are possibly looking for something in the GUI showing all connected devices,so on my system (I'm still using an older interface) that could be in the file manager (Nautilus),something like "Network" in the left column-or maybe you could search for "network" in your dash home.

---

### Post by philinux on 2013-12-02
> **cogset said:**
> If I'm not mistaken (I just use a plain desktop pc connected to a router,so I have no experience about Wifi hotspots) you are possibly looking for something in the GUI showing all connected devices,so on my system (I'm still using an older interface) that could be in the file manager (Nautilus),something like "Network" in the left column-or maybe you could search for "network" in your dash home.

Yes in 13.10 nautilus shows under network > Browse Network.

Sat at my laptop using that above shows my desktop pc. However that maybe because it's got a shared printer connected to it. I does not show my mobile which is using the router wifi connection.

---

### Post by erasmusp on 2013-12-02
I could also recommend WiFiGuard by Softperfect. They have a Windows and Linux version of this package that monitors your network and alerts you on any unknown IPs/MACs that connects to it. As per their site: "A free spe*cial*ised net*work scan*ner for keep*ing your WiFi secure. It runs through your net*work at set in*ter*vals and re*ports immedi*ately if it has found any new con*nected de*vices that could pos*sibly belong to an in*truder."

More info and download: [http://www.softperfect.com/download/](http://www.softperfect.com/download/)

Cheers,
Phill

---

### Post by philinux on 2013-12-02
Sorted now. With this I can see all the connections including my phone etc etc.

[http://itsfoss.com/how-to-find-what-devices-are-connected-to-network-in-ubuntu/](http://itsfoss.com/how-to-find-what-devices-are-connected-to-network-in-ubuntu/)

---

### Post by rabbyx7xafc on 2013-12-02
> **erasmusp said:**
> I could also recommend WiFiGuard by  Softperfect. They have a Windows and Linux version of this package that  monitors your network and alerts you on any unknown IPs/MACs that  connects to it. As per their site: "A free spe*cial*ised net*work  scan*ner for keep*ing your WiFi secure. It runs through your net*work at  set in*ter*vals and re*ports immedi*ately if it has found any new  con*nected de*vices that could pos*sibly belong to an in*truder."

More info and download: [http://www.softperfect.com/download/](http://www.softperfect.com/download/)

Cheers,
Phill



Just installed wifiguard and it lets me see all the devices that are connected to my wifi in a neat GUI... but it does not have the option to disconnect any of the devices that are connected to my wifi... thats what im looking for... a way to disconnect specific clients...
any ideas?

---

### Post by rabbyx7xafc on 2013-12-02
> **philinux said:**
> Sorted now. With this I can see all the connections including my phone etc etc.

[http://itsfoss.com/how-to-find-what-devices-are-connected-to-network-in-ubuntu/](http://itsfoss.com/how-to-find-what-devices-are-connected-to-network-in-ubuntu/)


i can scan the network connection with nmap but cant disconnect specific clients that are connected to my wifi... :/

---

