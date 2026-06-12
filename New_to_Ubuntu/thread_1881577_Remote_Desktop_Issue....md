---
title: "Remote Desktop Issue..."
date: 2011-11-15
forum: New to Ubuntu
---

### Post by d4m1r on 2011-11-15
Hey guys, started having issue yesterday connecting to my Windows XP machine at work so I thought I'd leave it until today but I am still seeing it....I connect through a Cisco VPN (using vpnc and network manager it connects perfectly fine everytime), but it is the RDP function that is not working.

Have tried the default Terminal Server Client, Gnome RDP, and most recently Remmina RDP but none of the will connect :( Adding my work PC's DNS + IP to my /etc/hosts file didn't work either...

Terminal server error = [COLOR=Red]ERROR: getaddrinfo: Name or service not known[/COLOR][COLOR=Black]

Thought my PC could be offline but I tried to connect to my Cisco VPN and RDP to my Windows XP machine under my Windows 7 partition and it worked just fine...Any ideas?](*,)
[/COLOR]

---

### Post by collisionystm on 2011-11-15
> **d4m1r said:**
> Hey guys, started having issue yesterday connecting to my Windows XP machine at work so I thought I'd leave it until today but I am still seeing it....I connect through a Cisco VPN (using vpnc and network manager it connects perfectly fine everytime), but it is the RDP function that is not working.

Have tried the default Terminal Server Client, Gnome RDP, and most recently Remmina RDP but none of the will connect :( Adding my work PC's DNS + IP to my /etc/hosts file didn't work either...

Terminal server error = [COLOR=Red]ERROR: getaddrinfo: Name or service not known[/COLOR][COLOR=Black]

Thought my PC could be offline but I tried to connect to my Cisco VPN and RDP to my Windows XP machine under my Windows 7 partition and it worked just fine...Any ideas?](*,)
[/COLOR]


Yeah there could be some kind of RDP authentication turned on that only allows Windows Clients. Server 2008 has this feature.


Can you ping your XP machine by its hostname? Have you tried to remote desktop the ip address instead of the hostname?

---

### Post by d4m1r on 2011-11-15
1)There isn't a "allow windows only" feature for XP as far as I am aware, or its not enabled atleast because I've been connecting within my Ubuntu partition just fine for the past 2 months.

2)No I can't ping the hostname (says its unknown) but I think that is a VPN limitation (the way I have it configured)

3)When I try to connect using the IP, terminal server client says: [COLOR=Red]Error: <my ip> unable to connect[/COLOR]

---

### Post by collisionystm on 2011-11-15
not a vpn limitation. it would say host unreachable if it was working

can you ping the ip

---

### Post by d4m1r on 2011-11-15
> **collisionystm said:**
> not a vpn limitation. it would say host unreachable if it was working

can you ping the ip

Yep, sorry you are right. I might be teksavy but Cisco/VPN stuff confuses me...Anyway, if I was actually connected to the VPN, I should be able to access internal website through my own browser (don't need RDP for that) but even they won't load. Also, when I ping internal hostnames, it says [COLOR=Red]ping: unknown host[/COLOR]

This is very strange because I get the window that says it was connected successfully and the network manager icon changes to indicate I am connected to a VPN. I know the settings are all correct because the Cisco VPN uses a .pcf file for the settings and I import the one that works under my Windows 7 partition but something isn't working with the same settings under Ubuntu...Where could the issue be? ](*,)

Tried unistalling vpnc (cisco plugin for network manager) and terminal server client, then restarting my PC, and reinstalled them but same issue...

---

### Post by collisionystm on 2011-11-15
> **d4m1r said:**
> Yep, sorry you are right. I might be teksavy but Cisco/VPN stuff confuses me...Anyway, if I was actually connected to the VPN, I should be able to access internal website through my own browser (don't need RDP for that) but even they won't load. Also, when I ping internal hostnames, it says [COLOR=Red]ping: unknown host[/COLOR]

This is very strange because I get the window that says it was connected successfully and the network manager icon changes to indicate I am connected to a VPN. I know the settings are all correct because the Cisco VPN uses a .pcf file for the settings and I import the one that works under my Windows 7 partition but something isn't working with the same settings under Ubuntu...Where could the issue be? ](*,)

Tried unistalling vpnc (cisco plugin for network manager) and terminal server client, then restarting my PC, and reinstalled them but same issue...


It is probably a PPTP Vpn and it is setup to tunnel all traffic from your computer through the VPN. You will only be able to ping hostnames on the DNS Server at your work. If you know the IP address of your work computer, I suggest you try to ping that and see if you get a response ( didnt see that you tried that yet). 

Find out if you can ping the IP address of your work computer. Most important thing.

---

### Post by d4m1r on 2011-11-15
> **collisionystm said:**
> It is probably a PPTP Vpn and it is setup to tunnel all traffic from your computer through the VPN. You will only be able to ping hostnames on the DNS Server at your work. If you know the IP address of your work computer, I suggest you try to ping that and see if you get a response ( didnt see that you tried that yet). 

Find out if you can ping the IP address of your work computer. Most important thing.

Cisco VPN is a custom connection (vpnc), not windows PPTP. I know the IP of my work PC, but when I ping it when "connected" to the VPN within Ubuntu, it says [COLOR=Red]ping: sendmsg: Operation not permitted[/COLOR]

[COLOR=Black]I am able to ping it just fine within Windows using the same settings and the Cisco VPN client.[/COLOR]

---

### Post by d4m1r on 2011-11-16
Does anyone else connect from a Ubuntu machine to Windows (specifically through a Cisco setup)?](*,)

Anyone heard of a VPN "connecting" but not being able to ping any internal IPs?

---

### Post by jaime256 on 2011-11-20
I just tried doing a remote desktop on my windows 7 pro too and also tried the ones you have tried and I still can't seem to connect either. I was connecting fine with the zorin distro. Now I have the gnome shell setup as well, but ubuntu 11.10 seems to be crapping this thing out apparently. Here's another one I just tried which looks nice too, but I still can't connect. I already have my windows machine set up to allow remote desktop. Try KRDC. You can find it in the sofware center if it doesn't work, it's this version of Ubuntu that's causing the problem. I don't know what, but all the programs can't be broken. Just a thought. I'm glad I was connecting to it before or I would be going mad right about now.

---

