---
title: "[SOLVED] Creating a static ip address..."
date: 2008-09-14
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-09-14
Hello all,
I have taken on the task today of opening a port.  I have figured out what to do in deluge, how to cofigure my router, etc etc, but there is one step missing.  How to assign a static IP address??  [www.portfoward.com](www.portfoward.com) only explains how to do this on mac/windows.... anybody have any advice?

---

### Post by Zzl1xndd on 2008-09-14
go to system > Administration > Network, Unlock it, click on the adapter you want to work with, then properties disable roaming and then there is an option for static in the drop down just fill out the info.

---

### Post by rideburton56 on 2008-09-14
So I am working with a wireless router, a linksys wrt54g.  when i go to the routers ip address to set it up, there is an option at the top to auto config or static IP address.  also at the bottom it has an option to put in static DNS numbers.  Now there are 4 or 5 other computers running off this wireless router, and I can assure you that none of the other users are interested in using static IP addresses, so would I have to configure each one independently, or can I just keep it on automatic and select one that I can use on this one all the time by entering it into that DNS address?
I am starting to feel like I am in over my head in regards to port fowarding, but I really would like to figure it out!

---

### Post by Zzl1xndd on 2008-09-14
Not sure if your router supports it but some can grant exclusions to IP address so it doesn't assign your static to another machine. Or just pick something really high in the available list and you should be ok

---

### Post by lovinglinux on 2008-09-14
> **rideburton56 said:**
> So I am working with a wireless router, a linksys wrt54g.  when i go to the routers ip address to set it up, there is an option at the top to auto config or static IP address.  also at the bottom it has an option to put in static DNS numbers.  Now there are 4 or 5 other computers running off this wireless router, and I can assure you that none of the other users are interested in using static IP addresses, so would I have to configure each one independently, or can I just keep it on automatic and select one that I can use on this one all the time by entering it into that DNS address?
I am starting to feel like I am in over my head in regards to port fowarding, but I really would like to figure it out!

[COLOR="Red"]**STOP**[/COLOR] before you mess things badly. I have the same router so let me write a tutorial for you. Just give some time, because my router interface is in Portuguese, so I need to figure out the correct names of all the options in English.

Is not that complicated as you think. You just need to do the proper steps and don't need to mess with static IP's, this is something your ISP determine.

---

### Post by rideburton56 on 2008-09-14
so for example my router says it starts assigning IP addresses at xxx.xxx.x.100, and it says maximum of of dhcp uses is 50, so if i were to go with xxx.xxx.x.149 in my network administration for linux (i.e. admin, network, unlock, wireless pref, turn off roaming, i should be alright, without changing anything on the router?

---

### Post by lovinglinux on 2008-09-14
Read my previous post and wait for instructions.

---

### Post by rideburton56 on 2008-09-14
stopping and waiting :)

---

### Post by lovinglinux on 2008-09-14
> **rideburton56 said:**
> stopping and waiting :)

is it possible for you to join ububtu irc channel so we can talk live and in private?

---

### Post by rideburton56 on 2008-09-14
sligtly embarrassed... but I dont know what IRC is, or how to use it...

---

### Post by lovinglinux on 2008-09-14
OK. I will try to explain here.

---

### Post by rideburton56 on 2008-09-14
well actually i know pigdin has irc protocol, but outside of that, nothing.

---

### Post by mikewhatever on 2008-09-14
> **lovinglinux said:**
> is it possible for you to join ububtu irc channel so we can talk live and in private?

What's the privacy for? Let others benefit from the feedback rather then hide away.

rideburton56, it's really no big deal, those read alerts seem like a wild exadgeration. xxx.xxx.x.149 should be fine as long as there isn't close to 50 computers on that network. You can also go outside that range asking for say xxx.xxx.x.151.:) This will not affect others on the network since they'll still be getting their IPs dynamically, while your computer will be asking for the specific ip. DNS addresses are usually assigned automatically by ISPs. Unless yours has given you a static DNS address, leave those spaces blank.

---

### Post by lovinglinux on 2008-09-14
I assume you are using this network for connecting to the Internet right now and all other computers in the network already have Internet access.

Since your network is working, is not a good idea to change the router configuration, because we don't know how the other computers in the network are configured and if the already rely on static IP.

I'm not sure if internal IP's do change like you think they do. For example, I have my router setup to automatically distribute internal IP's and I always get the same IP. I don't have static DNS.

Let's assume your internal IP does not change. So we need to find out which IP you have. I don't know how to do it via Administration with Ubuntu (I'm a LInux newbie too) but I know a simple way of doing it. Do you have Firestarter?

---

### Post by rideburton56 on 2008-09-14
no but couldnt i pull that up with iptables? if not i have no problem getting firestarter

---

### Post by lovinglinux on 2008-09-14
> **mikewhatever said:**
> What's the privacy for? Let others benefit from the fitback rather then hide away.

rideburton56, it's really no big deal, those read alerts seem like a wild exadgeration. xxx.xxx.x.149 should be fine as long as there isn't close to 50 computers on that network. You can also go outside that range asking for say xxx.xxx.x.151.:) This will not affect others on the network since they'll still be getting their IPs dynamically, while your computer will be asking for the specific ip. DNS addresses are usually assigned automatically by ISPs. Unless yours has given you a DNS address, leave those spaces blank.

I agree, but he doesn't have to change his router configuration.

---

### Post by mikewhatever on 2008-09-14
> **lovinglinux said:**
> I agree, but he doesn't have to change his router configuration.

He does, just a little bit. :) Namely, a TCP port must be forwarded to the chosen static IP. That's all.

---

### Post by skippuff54 on 2008-09-14
lovinglinux can explain how to do it for your router, but once you have it set up you might need to edit the hosts files on your other computers so you can connect to your static machine using hostname.

in ubuntu the file is /etc/hosts and win xp it's c:\windows\system32\drivers\etc\hosts (open with notepad)

this file will allow you to map the static IP 192.168.x.x to a hostname.

other than that you will need to use samba for file sharing.

if you're wantin to serve web pages from your home to the outside world, you'll most likely need to get a dynamic dns service, which also involves router configuration, in order to cope with the random IPs your ISP will reassign to you frequently.

---

### Post by mikewhatever on 2008-09-14
> **skippuff54 said:**
> lovinglinux can explain how to do it for your router, but once you have it set up you might need to edit the hosts files on your other computers so you can connect to your static machine using hostname.

in ubuntu the file is /etc/hosts and win xp it's c:\windows\system32\drivers\etc\hosts (open with notepad)

this file will allow you to map the static IP 192.168.x.x to a hostname.

other than that you will need to use samba for file sharing.

if you're wantin to serve web pages from your home to the outside world, you'll most likely need to get a dynamic dns service, which also involves router configuration, in order to cope with the random IPs your ISP will reassign to you frequently.

OMG, the OP is already confused, why complicate things even more! All he wants is to use Deluge.

---

### Post by lovinglinux on 2008-09-14
> **rideburton56 said:**
> no but couldnt i pull that up with iptables? if not i have no problem getting firestarter

As long as you discover your internal IP it doesn't matter. I was thinking about Firestarter, because you can monitor your internal IP from it. Since is not a good idea to forward a port all the time, you will have to forward it to your internal IP every time you want to use the p2p application. This is the way I do, because I think is more secure.

Once you discover your internal IP, go to the router configuration and go to the "Application & Games" section. You should see a list with port intervals.

You should configure the fields like this:

Application:  Torrent or whatever you want to name it
Start: the initial port you want to forward (a value between 49152 to 65535)
End: the ending port you want to forward ( a value between 49152 to 65535)
Protocol: TCP (Deluge does not support UDP)
IP address: put the internal IP of your machine (you just have to put the last number)
Activate: select to activate

If you doesn't like this method and want to leave a port constantly open, then you have to configure your machine to request the same internal IP every time, but you don't need to mess with the router DNS or DHCP configurations. I guess you can do this in Administration > Network. You will need to know the ISP DNS's 

In the router "State" section you will find this information as follows:

...session:  	PPPoE  - this is the most common type of connection	   	 
IP Adress:  XXX.XXX.XXX.XXX - this is your external IP, provided by the ISP. It will change every time you turn on the modem if you have a dynamic IP
Subnet mask: 255.255.255.255
Gateway: this I guess is automatically provided by the ISP	 
DNS 1: 	XXX.XXX.XXX.XXX  	this is the DNS of your ISP 
DNS 2: 	XXX.XXX.XXX.XXX	this is the DNS of your ISP   	 
DNS 3: 		  	 

As I said, my Ubuntu Network is configured as "roaming", which I guess is the dynamic IP. Nevertheless, I always get the same internal IP, without messing with the router configuration. So I guess you don't even have to assign a static IP to your machine.

---

### Post by rideburton56 on 2008-09-14
Its ok, anything I am not interested in doing I just read right over (ie file sharing, samba etc) :).  Let my rephrase my question.  I want to make sure that I am keeping my torrent ratio at around 1.0, and it seems that to do so I should open and foward a port.  It seems that to do so, I need to assign my machine to a static IP address.  I have found where to put in the port forwarding information on my routers page.  If making this work means screwing around on my family's other machines, then it is simply not worth it.

---

### Post by mikewhatever on 2008-09-14
Nothing will happen to the other computers, unless you clog the bandwidth trying to keep the ratio up. Even in the latter case, all they get will be slow browsing.

---

### Post by lovinglinux on 2008-09-14
> **rideburton56 said:**
> Its ok, anything I am not interested in doing I just read right over (ie file sharing, samba etc) :).  Let my rephrase my question.  I want to make sure that I am keeping my torrent ratio at around 1.0, and it seems that to do so I should open and foward a port.  It seems that to do so, I need to assign my machine to a static IP address.  I have found where to put in the port forwarding information on my routers page.  If making this work means screwing around on my family's other machines, then it is simply not worth it.

As I said, you don't have to use a static IP or mess with the router configuration, you just have to make sure you forward the port to right address when using Deluge.

This is the way I do when I want to use Deluge:

1 - I open [http://192.168.x.x/Forward.htm](http://192.168.x.x/Forward.htm) and activate the port forwarding to the port used by Deluge (if your internal IP changes frequently you just have to get it before this step.

2 - I open Deluge and configure the port number accordingly to the port forwarding

3 - I download my torrents 

4 - I turn off Deluge

5 - I open [http://192.168.x.x/Forward.htm](http://192.168.x.x/Forward.htm) and deactivate the port forwarding

That is all you need to get proper port forwarding. This will not mess with your network and will not leave any port open all the time.

Since I' a little bit more paranoid, I have an additional step between 1 and 2, which is opening the port in the Firewall. Then when I finish the download I also close this port in the Firewall.

There is nothing complicated about this method.

---

### Post by rideburton56 on 2008-09-14
Thanks for all the troubles!

---

### Post by lovinglinux on 2008-09-14
> **rideburton56 said:**
> Thanks for all the troubles!

No worries. I hope it didn't sound more complicated than it really is.

---

