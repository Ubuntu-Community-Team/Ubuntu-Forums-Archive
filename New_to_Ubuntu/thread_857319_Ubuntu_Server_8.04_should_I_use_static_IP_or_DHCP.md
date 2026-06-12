---
title: "Ubuntu Server 8.04 should I use static IP or DHCP?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by adamgram on 2008-07-12
I'm setting up a home server for remote access of some of my files and as a temporary place to host websites while they are being developed.  I'm following the step by step how-to found here:

[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)

I looked at another one too, and they both tell you to set up a static IP address, but I don't think this is what I want to do. However, I don't know enough about this sort of thing to know for sure, so I'd like a second opinion.  The how-to says:

"Ubuntu installer has configured our system to get its network settings via DHCP, Now we will change that to a static IP address for this you need to edit..." followed by instructions to change to a static IP address.

I'm setting the server up AFTER my router because I want to be able to use the internet at home without having the server on.  Since my router assigns an IP address to computers on its network, this means the server will connect to the internet via DHCP, right?  And therefore I should skip this step?

---

### Post by hyper_ch on 2008-07-12
you want to have a static ip... so that you can forward ports accordingly from your router to your server.

---

### Post by ibutho on 2008-07-12
If you plan to access this server from other computers on the network or from the web, you are better off using a static IP address for the server. This makes it easier for things like port forwarding and access to the server from other systems (if the ip address changes via dhcp, how do other computers know how to access the server).

---

### Post by adamgram on 2008-07-12
So this will set it up so it always gets the same IP from the router?  I think I was confused about what it was doing.  Thanks for the help guys.

---

### Post by carlinuxlearner on 2008-07-12
Yes, this sets it up so the computer will always have the same IP address. (well on your home network that is)

C@RL

---

### Post by fatality_uk on 2008-07-12
> **adamgram said:**
> So this will set it up so it always gets the same IP from the router?  I think I was confused about what it was doing.  Thanks for the help guys.

That's correct. But bear in mind that the IP address you set or is assigned by DHCP is only local to your network. If your friends are not on your network when they try to connect to a share you have on your server, they wont be able to see it. Unless you specified your ISP to give you a static IP address, you will need to allow them remote access to your network. So you will need a VPN they can join and as such be on your network.

---

### Post by adamgram on 2008-07-12
Since I clearly have no idea what I'm doing maybe I should ask this too... do you use the IP address my router assigns to the server or the IP address of the router in place of what they use as an example here:

"Ubuntu installer has configured our system to get its network settings via DHCP, Now we will change that to a static IP address for this you need to edit Edit /etc/network/interfaces and enter your ip address details (in this example setup I will use the IP address 172.19.0.10)"

---

### Post by adamgram on 2008-07-12
> **fatality_uk said:**
> That's correct. But bear in mind that the IP address you set or is assigned by DHCP is only local to your network. If your friends are not on your network when they try to connect to a share you have on your server, they wont be able to see it. Unless you specified your ISP to give you a static IP address, you will need to allow them remote access to your network. So you will need a VPN they can join and as such be on your network.

Oh no, now I'm twice as confused... If the server is after the router and uses the local IP address assigned by the router will I be able to access the server from any internet connection or will it only work from my home network?

---

### Post by jerome1232 on 2008-07-12
> **fatality_uk said:**
> That's correct. But bear in mind that the IP address you set or is assigned by DHCP is only local to your network. If your friends are not on your network when they try to connect to a share you have on your server, they wont be able to see it. Unless you specified your ISP to give you a static IP address, you will need to allow them remote access to your network. So you will need a VPN they can join and as such be on your network.

That's not entirely correct, for example I have a server that hosts teamspeak 2, it get's it's ip addy via dhcp from my router, my router has a specific ip address for that server reserved (192.168.1.2) so it doesn't randomly change, I have a dynamic dns account (joebob.joe.dns for this example) that points to my routers public ip address (55.55.55.55), the router forwards teamspeaks port to my server (8787 udp).

So my friends tell their client to connect to joebob.joe.dns, which points them to my router, 55.55.55.55, it receives traffic on that port (8787 udp), and forwards it to my server.

Just outside the local network they have to connect to you're public ip address, not the local ip, and you're router must forward the correct ports to the server.

edit: Sorry if I'm not very good at explaining just trying to give a working example. Feel free to ask more questions.

---

### Post by movrshakr on 2008-07-12
Whoa, folks, we need to go slow here.  The asker is not highly conversant in IP addressing, so we need to be very specific in answering him.

First, with static addressing, that means you are yourself putting a "fixed" address on the computer.  It IS NOT getting it from the router (that would be DHCP, Dynamic Host Configuration Protocol).

Now, there are some things that some routers do that "look like" static addressing, and it is implemented a bit different in every router.  With this method, you "reserve" the same address for that machine (normally by listing its MAC address in the router) and telling the router to give that address to that machine every time.  This is kind of a mix of DHCP and static.

The addresses on your local network are only seen by other machines on you local network.  They probably will have numbers between like 192.168.1.2 and 192.168.1.254.  192.168.1.1 is usually the LAN side of the router itself. (The .1.  is often .0. depending on router brand.)

The WAN side of the router will have an address it gets by DHCP from your cable modem or whatever.  IF you get a static address from your provider, that will be for his interface device.  You can think of it as the address for "your house" so to speak.

---

### Post by adamgram on 2008-07-12
OK!!  Now we're getting somewhere!  Thanks so much for the help guys...

So do I understand this correctly that my server will have its own IP address, and will send data over the internet through the router, so it will be seen to the outside world through it's own IP address, and will access the rest of the world through the 192.168.1.xx address assigned by the router?

---

### Post by bijeeshvs on 2008-07-12
hello adamgram check this out

[http://portforward.com/guides.htm](http://portforward.com/guides.htm)

actually the site is for helping in forwarding ports, but it has lot of info about everything you should know, including static ip and how to set it...........

---

### Post by movrshakr on 2008-07-12
That's pretty close.  You might want to do a bit of reading on IP ADDRESSING... google [tutorial "IP ADDRESSING"] without the []'s.  

Ignore any stuff about IPv6; it will just confuse you (confuses everybody except the real gurus).

---

### Post by fatality_uk on 2008-07-12
> **jerome1232 said:**
> That's not entirely correct, for example I have a server that hosts teamspeak 2, it get's it's ip addy via dhcp from my router, my router has a specific ip address for that server reserved (192.168.1.2) so it doesn't randomly change, I have a dynamic dns account (joebob.joe.dns for this example) that points to my routers public ip address (55.55.55.55), the router forwards teamspeaks port to my server (8787 udp).

So my friends tell their client to connect to joebob.joe.dns, which points them to my router, 55.55.55.55, it receives traffic on that port (8787 udp), and forwards it to my server.

Just outside the local network they have to connect to you're public ip address, not the local ip, and you're router must forward the correct ports to the server.

What I stated it **IS** entirely correct. Your talking about a something totally different, a dynamic DNS service. That service stores YOUR ISP assigned address and matches that to your DNS assigned address.

---

### Post by carlinuxlearner on 2008-07-12
Just to sum it all up for adamgram.

Well it starts here:

Your ISP (Internet Service Provider) uses DHCP to assign your modem a IP address.

Your modem talks to the router with a static IP address (usually 192.168.0.1).

Your router talks to your computer with either a DHCP assigned IP or a static IP.

With DHCP your router tells your computer what IP address it will use, so it can change it any time it wants to.
With a static IP YOU tell the router what IP address you will use, so unless YOU change it, it will always be the same.

So, you can control any IP address your router gives out, but you CAN NOT control the IP that your ISP gives your Modem (and basically that IP gets forwarded to your router) UNLESS you PAY your ISP to give you a static IP, which is pretty costly. So any computer on your network can have a static IP but if you want to connect to it from somewhere else it's has to talk through your modem, then through your router, and since your modems IP is assigned by DHCP it can change any time. 

So if you want to have a server you without paying your ISP for a static IP, you must use a middle man like [http://www.no-ip.com/]("http://www.no-ip.com/") that gives you a program to run on your server that tells that website what your IP address is whenever it changes so it can forward people to your computer any time any where.

I hope this helps

C@RL

---

### Post by adamgram on 2008-07-13
> **carlinuxlearner said:**
> Just to sum it all up for adamgram.

Well it starts here:

Your ISP (Internet Service Provider) uses DHCP to assign your modem a IP address.

Your modem talks to the router with a static IP address (usually 192.168.0.1).

Your router talks to your computer with either a DHCP assigned IP or a static IP.

With DHCP your router tells your computer what IP address it will use, so it can change it any time it wants to.
With a static IP YOU tell the router what IP address you will use, so unless YOU change it, it will always be the same.

So, you can control any IP address your router gives out, but you CAN NOT control the IP that your ISP gives your Modem (and basically that IP gets forwarded to your router) UNLESS you PAY your ISP to give you a static IP, which is pretty costly. So any computer on your network can have a static IP but if you want to connect to it from somewhere else it's has to talk through your modem, then through your router, and since your modems IP is assigned by DHCP it can change any time. 

So if you want to have a server you without paying your ISP for a static IP, you must use a middle man like [http://www.no-ip.com/]("http://www.no-ip.com/") that gives you a program to run on your server that tells that website what your IP address is whenever it changes so it can forward people to your computer any time any where.

I hope this helps

C@RL


Thanks!

---

### Post by TSS on 2008-07-13
I'll try another way of explaining the process, which I found helpful when it was explained to me. 

Your router sits between your computer and the outside the world.  The router is the one that gets the IP address that the world can see, and the router is basically in change of what happens on your network.

Imagine that you are the router, and you get a request on port 80 (HTTP).  Unless your firewall says it's ok, you are just going to ignore the request.  But what if you don't want your router to ignore the request?  In your case, you are setting up a server, so it might be nice to be able to host a website.  In order to allow requests on port 80, you open up port 80 on your router's firewall.  So far so good.  But your router has no idea where to send the request, so you also have to give it an IP address inside your network to deliver the request to.  Of course you give it the IP address of your server (something like 192.168.1.125).  But what if your server uses DHCP?  When the lease on 192.168.1.125 runs out, the router might give it a totally new IP address!  Then the router would be sending requests on port 80 to an IP address with no machine.  This is why you use static IPs, so you do not run into that problem.

A few more notes.  Some routers have the option of assigning the same IP to a specific MAC address every time.  In my case, my server uses DHCP, but since my router knows the MAC address of the ethernet port of my server, it always gives it the same IP address.  Also, you can imagine how you could have multiple machines inside your home network, with different points going to each one.  For example, I've got my web server which gets requests on port 80, but I've also got a seperate machine that I use for storage.  I forward all requests on port 21 (ftp) to my storage machine.  So 'lynx mydomain.com' and 'ftp mydomain.com' go to two seperate machines, even though I use the same address. 

Ok, so we've covered inside your network.  Now imagine that your router is a computer and the internet is a router.  Example the internet wont give you a static IP unless you pay up.  So you can use a similar tactic like the MAC addressing with DHCP that I talked about before.  Check out free services like no-ip.com so you can always access your router (and therefore your computers).

TSS

---

