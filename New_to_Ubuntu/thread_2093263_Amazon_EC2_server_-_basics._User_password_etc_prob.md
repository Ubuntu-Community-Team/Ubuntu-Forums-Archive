---
title: "Amazon EC2 server - basics. User password etc problems"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by Dariusz1989 on 2012-12-10
Heya

I'm quite new to linux so I lack a loot of knowledge. I speed last 2 weeks researching and googling day and night internet to get my answers but each answer is different and still don't work so I give up.

Issue 1 : Root password for Ubuntu EC2 user.

Apparently I cant change it so how do I get it to work ? I guess I have to create new user + assign a password for him but then how do I log as this user ? Its one of the most troubling issues  I have currently, I can not break it so far :( Even tho I did manage to do sudo passwd and type in new pws etc etc it don't work at the end... not sure what to do :(

Issue 2 : VPN
I've added a VPN network connection to my network panel and when I go to networks and add VPN connections but all settings are grayed out... I guess modules is missing? How can I fix it...

Issue 3 : vncserver crash
It happens so many times I consider not using Linux instances and paying more for windows... Problem is once it crash I cant reconnect I have to restart instance... I try vncserver -kill :1 but that wont work, I try deleting /tmp/* folder but that did not work either so... 

I guess once I got them solved I should be able to set up a automatic bat file to connect to my home VPN/map HDDS(I hope its not too complicated...) and get my softwares running... so for now its not a problem but I might come back regarding it...

Thanks every1 for patience and time ! I'm off to learn how to make bat files for ubunt and see if I can find a way to fix that damn instance :(

Thanks, bye.

---

### Post by sandyd on 2012-12-10
> **Dariusz1989 said:**
> Heya

I'm quite new to linux so I lack a loot of knowledge. I speed last 2 weeks researching and googling day and night internet to get my answers but each answer is different and still don't work so I give up.

Issue 1 : Root password for Ubuntu EC2 user.

Apparently I cant change it so how do I get it to work ? I guess I have to create new user + assign a password for him but then how do I log as this user ? Its one of the most troubling issues  I have currently, I can not break it so far :( Even tho I did manage to do sudo passwd and type in new pws etc etc it don't work at the end... not sure what to do :(

Issue 2 : VPN
I've added a VPN network connection to my network panel and when I go to networks and add VPN connections but all settings are grayed out... I guess modules is missing? How can I fix it...

Issue 3 : vncserver crash
It happens so many times I consider not using Linux instances and paying more for windows... Problem is once it crash I cant reconnect I have to restart instance... I try vncserver -kill :1 but that wont work, I try deleting /tmp/* folder but that did not work either so... 

I guess once I got them solved I should be able to set up a automatic bat file to connect to my home VPN/map HDDS(I hope its not too complicated...) and get my softwares running... so for now its not a problem but I might come back regarding it...

Thanks every1 for patience and time ! I'm off to learn how to make bat files for ubunt and see if I can find a way to fix that damn instance :(

Thanks, bye.
1. you cant. you have to use the security key that amazon provides (providing that they haven't changed how you log in)
2. What kind of VPN is this?. PPTP? OpenSWAN? OpenVPN? You have to install the corresponding network-manager module. i.e. network-manager-openvpn-gnome/network-manager-openvpn for openvpn

---

### Post by Dariusz1989 on 2012-12-10
Heya

Thanks for fast reply!

Ow... well I'm using amazon key I got generated but past that I have no idea how to get password so I can install apps etc etc...

As to VPN yea its VPN to windows server 2008 PPTP.

I want to connect to my home VPN and map HDD and license addresses as well as find some syncing software to sync my data off FTP to hdd as quickly as possible... but that is for another time to get it working...

For now I mainly want VPN/PW and probably I have to find a way to change ubunt name to IP so I dont have duplicates... is there a startup folder for ubunt I could do it in like I Do with bat and windows?

Thanks, bye.

---

