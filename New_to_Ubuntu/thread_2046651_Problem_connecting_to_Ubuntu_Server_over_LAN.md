---
title: "Problem connecting to Ubuntu Server over LAN"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by jsimon123 on 2012-08-23
Hello, I am stuck on a major problem. I recently set up a Ubuntu server (12.04) and connected a USB hard drive to it to share across my LAN. I successfully followed this link [http://www.havetheknowhow.com/](http://www.havetheknowhow.com/) all the way through to the end. I did everything it asked and didn't run into any problems! It was working correctly when I installed putty and all the other software on my Windows 7 computer. I could access my hard drive over the network. My problem came when I tried to connect another computer to the server. I entered the //IP address of the server and it logged on. I went to another to access the server, did the same and it gave me the error; "The specified network name is no longer available." I tried typing in the DNS name, "mediacenter" and that didn't work either. I left it alone for a while, figuring the problem was with that specific Win 7 computer. I came back hours later to find I could not access the server on the original computer that I installed putty on. I typed in the IP and it gave me that error. HOWEVER, I tried typing in the DNS name and it works. I went back to the other computers and they don't work with either the ip or the name. The only computer that can access it now is the original with only the //mediacenter path. I need to be able to connect additional computers to it. Please help!

---

### Post by androssofer on 2012-08-24
> **jsimon123 said:**
> Hello, I am stuck on a major problem. I recently set up a Ubuntu server (12.04) and connected a USB hard drive to it to share across my LAN. I successfully followed this link [http://www.havetheknowhow.com/](http://www.havetheknowhow.com/) all the way through to the end. I did everything it asked and didn't run into any problems! It was working correctly when I installed putty and all the other software on my Windows 7 computer. I could access my hard drive over the network. My problem came when I tried to connect another computer to the server. I entered the //IP address of the server and it logged on. I went to another to access the server, did the same and it gave me the error; "The specified network name is no longer available." I tried typing in the DNS name, "mediacenter" and that didn't work either. I left it alone for a while, figuring the problem was with that specific Win 7 computer. I came back hours later to find I could not access the server on the original computer that I installed putty on. I typed in the IP and it gave me that error. HOWEVER, I tried typing in the DNS name and it works. I went back to the other computers and they don't work with either the ip or the name. The only computer that can access it now is the original with only the //mediacenter path. I need to be able to connect additional computers to it. Please help!

did you turn it off and on again? (its cliché, but works :-) )

could be a firewall or router issue. Are you port forwarding to the server on the router? have you opened up the ports in the firewall to only one computer?

is it a samba share? or NFS? 

where the other computers Windows 7?

---

### Post by jsimon123 on 2012-08-27
> **androssofer said:**
> did you turn it off and on again? (its cliché, but works :-) )

could be a firewall or router issue. Are you port forwarding to the server on the router? have you opened up the ports in the firewall to only one computer?

is it a samba share? or NFS? 

where the other computers Windows 7?

Sorry for the delayed response, I was away for the weekend. 
I did try restarting the server to correct the problem but that did not help, I've done it multiple times. 
As far as port forwarding and the firewall on the server, I'm extremely new to this and don't really know how to configure all that. 
It is a samba share and the other computers are all within the wireless network in the same house. 

Thanks!!!

---

### Post by androssofer on 2012-08-28
> **jsimon123 said:**
> Sorry for the delayed response, I was away for the weekend. 
I did try restarting the server to correct the problem but that did not help, I've done it multiple times. 
As far as port forwarding and the firewall on the server, I'm extremely new to this and don't really know how to configure all that. 
It is a samba share and the other computers are all within the wireless network in the same house. 

Thanks!!!

apparantly you dont need to open ports on ubuntu.. who knew?

on you router you might not need to either if you already got it connecting.. so new approach!


go here [https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba](https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba)

and there is a nice trouble shoot guide at the bottom that should help you check for common errors..

---

