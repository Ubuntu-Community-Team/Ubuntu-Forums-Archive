---
title: "Networking  Printing/file sharing"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by c-weeda on 2013-11-10
Hey im Newish to Ubuntu,

I have A slowish Laptop that i Installed Ubuntu 12.04 LTS on all is working faster, i now have a propper wireless setup at home.  Im trying to get all PC's and printer connected.  I have 2 PC's running Win 7 (64-bit) 1 laptop and 1 old PC (media server type thing) both running Ubuntu 12.04 LTS, and a MP620 printer, All the windows PC's and printer work fine and networked fine.  However i want to Use the Old PC as a media/Data storage PC so i need full access to that machine from all PC's and i want the Laptop and 2 win7 PC's to access shared files from each other and the access the printer.

Network setup is as follows

Internet - Router - Wired - Powerline Adaptor - Switch - Win 7 PC 1
[INDENT=9]  - Win 7 PC 2
  - MP 620 Printer[/INDENT]
[INDENT=2]      
      - Wireless - Ubuntu Laptop
[/INDENT]
[INDENT=3]            - Ubuntu PC (Media / Data)[/INDENT]
[INDENT=4]    - Kindle Fire
[/INDENT]


Any Help, Suggestions, comments. insults gladly appreciated
Thanks in advance
Zoobone

---

### Post by TheFu on 2013-11-10
Don't use wireless for a server.

To a human "surfing the internet" wireless seems stable and fast. 
To a computer, trying to access files, wireless is like being in a frothy ocean with constantly changing bandwidth, constantly changing speeds .... not good for a server.  Further, all wifi devices are sharing bandwidth.  WiFi-N is much better at sharing than prior methods. My wifi knowledge was gained when "G" was the main protocol - basically every added device halves the available bandwidth.  So, 100Mbps connection with 1 device would be 50Mbps for it.  2 devices means they both get 25Mbps, 3 devices and they each get 12.5Mbps ... for surfing, these are all fast enough. For a server - no way.  Plus, all wifi has interference based on the location of each device and the AP.  Moving a client device 1 foot can make a huge difference.

I have never used wireline adapters - how is the bandwidth - stable like wired CAT5e ethernet?  If so, get another wireline network adapter for the server.

For a file server, NFS is usually best between UNIX/Linux/OSX machines, but don't use it over wifi.
For Windows clients, CIFS shares are usually best - samba.

Insulted? ;)  I can try harder, if you like.

---

