---
title: "Networking problems (Static IP...)"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by Amjad14 on 2013-01-20
Hello every one! 

Actually I have some troubles trying to configure my network as static. 

Everything works fine when I use DHCP protocol but when I change my interface file (/etc/network) to static (see below) then reboot , it doesn't work :/ I've already purged network-manager.

auto eth0
iface eth0 inet static
    address 172.20.46.75
    netmask 255.255.252.0
    network 172.20.46.0
    broadcast 172.20.47.255
    gateway 172.20.47.254

(I'm sure that this adresses are correct)
  
I also inserted manually the DNS servernames in the resolv.conf and added in interfaces the information below but none of this methods worked.

     dns-nameservers 155.69.24.8
     dns-nameservers 155.69.5.5
     dns-search ntu.edu.sg

As you can see i'm connected through my university network, while being connected to internet using dhcp i noticed that I can't ping google or any other ip a part from the ips present in my subnet and the dns servers, i always get "search timed out"... Is this related to the first problem? because of some configuration in the university routers that doesn't allow static ips ? firewalls?

Thanks in advance for the answers!

---

### Post by chadk5utc on 2013-01-20
Not sure how the network is configured for the University. as for ping it can be blocked/disabled within firewall rules. Typically static assignments are done outside of the dhcp server range so they do not cause address conflicts on the network. Is there any reason your trying to set a static address?

---

### Post by Amjad14 on 2013-01-20
I'm trying to set a static ip on my raspberry pi to use it as a server. 
 so if typically static assignments are done outside of the dhcp server range, what are the reasons that don't let the static ip assignement work? 
I'm experimenting the static ip assignement on my computer (ubuntu 12.1) before doing it on the rasp. I change my interfaces configuration then reboot but still cannot access to internet.

---

### Post by chadk5utc on 2013-01-20
> **Amjad14 said:**
> I'm trying to set a static ip on my raspberry pi to use it as a server. 
 so if typically static assignments are done outside of the dhcp server range, what are the reasons that don't let the static ip assignement work? 
I'm experimenting the static ip assignement on my computer (ubuntu 12.1) before doing it on the rasp. I change my interfaces configuration then reboot but still cannot access to internet.
Networks can be set up many different ways and for many reasons one of which is in an attempt to prevent rouge servers or access points from causing issues to the rest of the network. Based on the information you gave with an address and subnet of
> 
 172.20.46.75
 255.255.252.0
Calculated shows there are 1022 possible ip addresses. What I would do then is set your ubuntu machine for dhcp the run the following command in a terminal so you do not have to reboot
> sudo /etc/init.d/networking restart check that you are truly connected to the web then I would copy the information and change it back to static making sure that the > 
auto eth0
iface eth0 inet static
address your ip
netmask 255.255.252.0
gateway 172.20.47.254
 are all correct and should work. With all this keep in mind that if the network manager detects an unauthorized server on the network they can block it completely and youll have further connectivity issues. Further a better option in your case would be to check out a service like DynDNS

---

### Post by Amjad14 on 2013-01-20
> **chadk5utc said:**
> Networks can be set up many different ways and for many reasons one of which is in an attempt to prevent rouge servers or access points from causing issues to the rest of the network. Based on the information you gave with an address and subnet of

Calculated shows there are 1022 possible ip addresses. What I would do then is set your ubuntu machine for dhcp the run the following command sudo /etc/init.d/networking restart                       in a terminal so you do not have to reboot, check that you are truly connected to the web then I would copy the information and change it back to static making sure that the  are all correct and should work.

This is exactely what i have done, when i use the command ifconfig it provides all the information that i entered in the interfaces file, but it still doesn't work. 
I noticed that when i launch firefox it doesn't tell directly that there is internet connexion but takes a long time loading before it tells me that firefox cannot reach the server. 
And btw I discovered a EPIC bug in my system, whenever i use the command "sudo /etc/init.d/networking " , the OS stops working , the graphic turns off and even the terminal is blocked... :confused:
  
> **chadk5utc said:**
> With all this keep in mind that if the network manager detects an unauthorized server on the network they can block it completely and youll have further connectivity issues. Further a better option in your case would be to check out a service like DynDNS
Hmm... Maybe the problem comes from the network manager limitations...

---

### Post by chadk5utc on 2013-01-20
This is very possible. there are packages for dyndns although they vary from OS to OS( I know they are available for Ubuntu and Debian, Im sure others)I cant right now remember the name of the package but if you are able to check into this service it may provide you with what your trying to do.

---

### Post by Amjad14 on 2013-01-20
tenx! i'll try to find a solution in this direction.

But you have no idea why the system stop working when i reinitialize the networking :confused:
i'm still confused...

---

### Post by chadk5utc on 2013-01-20
> **Amjad14 said:**
> tenx! i'll try to find a solution in this direction.

But you have no idea why the system stop working when i reinitialize the networking :confused:
i'm still confused...

No unfortunately I do not. that command simply restarts networking and should not have affected anything else.

---

### Post by GordThompson on 2013-01-20
> **Amjad14 said:**
> Maybe the problem comes from the network manager limitations...
If you are in an educational environment, especially in a student context, then chances are good that your network administrators have made special efforts to prevent users from doing exactly what you are trying to do. Technologies like DHCP Snooping and Dynamic ARP Inspection (DAI) can be used to prevent machines from accessing a DHCP-controlled network if they have not received their IP address from the authorized DHCP server.

Before you go to the trouble of setting up Dynamic DNS, check the Terms Of Service (TOS) that cover your Internet connection (as provided by the school, I assume). If the TOS expressly prohibits servers -- and many places do -- then just stop. Even if you do get it working it probably won't be long before the network administrators shut you down anyway.

---

### Post by Cheesemill on 2013-01-20
> **GordThompson said:**
> If you are in an educational environment, especially in a student context, then chances are good that your network administrators have made special efforts to prevent users from doing exactly what you are trying to do. Technologies like DHCP Snooping and Dynamic ARP Inspection (DAI) can be used to prevent machines from accessing a DHCP-controlled network if they have not received their IP address from the authorized DHCP server.

Before you go to the trouble of setting up Dynamic DNS, check the Terms Of Service (TOS) that cover your Internet connection (as provided by the school, I assume). If the TOS expressly prohibits servers -- and many places do -- then just stop. Even if you do get it working it probably won't be long before the network administrators shut you down anyway.
A big +1.

Talk to whoever is in charge of the network.

They will either give you the correct settings needed, or they will tell you that static IP's aren't allowed. Either way you have your answer.

---

### Post by Amjad14 on 2013-01-20
Wise answers! 

I'll try to contact the IT department in my university. 

I already went to this dyndns solution, it's pretty simple but the only problem is that it detects the university DNS ip adress instead of mine  but i think because after all I just have a private ip within the subnet and that i'm connected to internet through my university public dns servers ...

---

