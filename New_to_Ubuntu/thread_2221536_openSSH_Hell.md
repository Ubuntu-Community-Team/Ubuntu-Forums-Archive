---
title: "openSSH Hell"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by jim50 on 2014-05-02
Hi all!

Okay, bare with me - I'm pretty new to this (about a month). 

I want to set up an ubuntu server for files around the house, and I was told to try setting it up in a virtual box machine first. I did thi and it went great. The one thing I can't seem to do is get a hang on this 'openssh' thing. I've used ubuntu desktop before and had no problem connecting a remote desktop from my phone, but this ssh seems to be far more confusing. 

I have installed openssh-server on my guest ubuntu (I changed the open ssh port to 3232)
I have installed openssh-client on an ubuntu host (i installed ubuntu because it was even more confusing trying to do all this from windows)
On the virtual machine settings i have two network adapters - one NAT and one bridged.
The NAT one I have set port forwarding from 3232 to 3022
On the bridged one I havent done anything.

After 2 days of googling I can ssh from the ubuntu host to the ubuntu guest using

"ssh -p 3022 me@127.0.0.1"

I have no idea where that 127.0.0.1 came from I found it in a search and it worked. 

When I try to connect my phone app it asks for a password, my group, the host name, the user name. 
I've tried the 127.0.0.1 ip address and the ip address of the computer I get from googling my IP, and the IP address I get from typing 

"ifconfig"

in the hostname box

I always get 

"connection failed"

I have no idea what a 'group' is, but I figure the user is my username, and password is my user password?

The worst thing is I really don't understand what I'm doing! Please help ubuntu users!

Jim

---

### Post by coldcritter64 on 2014-05-02
> After 2 days of googling I can ssh from the ubuntu host to the ubuntu guest using

"ssh -p 3022 me@127.0.0.1"If you are issuing that from the host, you are ssh'ing into the _*host*_ NOT the guest. 
127.0.0.1 is the IP of "localhost", aka the computer you are issuing that command from. 
An ubuntu guest install will have an IP as issued by the VM network adapter, most likely a "private" networking address but _*not*_ that of localhost (127.0.0.1).

This is why ...
> I've tried the 127.0.0.1 ip address and the ip address of the computer I  get from googling my IP, and the IP address I get from typing 

"ifconfig"

in the hostname box

I always get 

"connection failed"you will get no connection _*to the guest*_ when you ssh _*into the host from the host*_. I hope that at least makes some sense to you, I can't really help much on the setting up of ssh sorry to say, not experienced enough with it.
(Edit: I THINK, not 100 % sure) I just picked a error in command usage/network understanding there, hope it is of some help, cheers.

P.S. worth a shot. Try going into the guest, locate its IP address with ifconfig, and substitute it in that command from the host. Might work.

---

### Post by drink1297 on 2014-05-02
You can ssh from the host with 127.0.0.1 because your on the machine you ssh into...127.0.0.1 is loopback address
I personally use putty....and you should be able to simply putty in to your IP (hopefully it is on the local network, or is a public IP address) port 3022 and login as root

A group is what your username belongs to, like the Admin group, the sales group, etc.  Groups allow assignment of permissions based on the role, not the user.

try logging in locally and type netstat -tapen | grep ":3022" 
it should return an IP address that is listening on that port, that is the IP to use in: ssh username@ipaddress:3022

---

### Post by jim50 on 2014-05-02
Hi,

Thank you so much for getting back to me guys.

That is a bit clearer! So the 127.0.0.1 basically connects from my host to my host, and so when I tell it to query port 3022 with the ssh command, it reaches my port forward from virtualbox and is directed to port 3232 inside the guest? Have I got that right?

Incidentally I know I'm connecting to the guest as 1) I didn't install an open ssh server on the host, and 2) I set a custom welcome banner so I'd know I got into the right one ;)

My problem seems to be the public network access. So I need the public IP? 

(I tried the listening thing - just got a blank IP, I think I messed that part up!

---

### Post by jim50 on 2014-05-02
Ha!

We have a win!

Now that you guys explained to me what is going on, I've sussed it. I've read all this stuf about a bridged network connector - that just simply refused to connect in the guest! :mad: I just used my NAT eth0 and port forwarding.

After my last message, I checked that I could still ssh from host to guest. this was fine. then I tried ssh from my phone to my guest over my wifi network looking at the host's 3022 port - bingo! for the first time I had my ubuntu server guest on my phone. however I dould not sign in over public IP

I figured this had to be something to do with my router, so I created a port forwarding rule using TCP to port 3022 on my host machine, and boom! I can SSH in from the phone app.

Thank you so much for the help guys!

Final question - I'm now going about generating a public key and disabling password sign in as recommended. Do I need to make any other security options to my linux host as it is port forwarding 3022 direct to the router?

Thank you so much,

Jim

---

