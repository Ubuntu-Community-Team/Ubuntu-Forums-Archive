---
title: "Opendns Home Network"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by AustenG on 2012-07-18
Hey everyone,
 
I've just signed up with opendns in order to start a home network. Here is my ultimate goal: To set up a *secure* network with the following devices with static ip addresses on it:
1) Desktop running Ubuntu 12.04 LTS (with dual boot Windows 7)
2) 2 MacBook Pro Laptops
3) Potential for other devices to access my network (smartphones, tablets, and maybe a netbook) - this is the least of my concerns, though.

I now have a static ip address via opendns, and I'd like to set up both screensharing and ssh from computers outside my home network (from work for instance). How do I go about doing this, and how can I check to see if things are working the way I expect? One of the difficulties I'm having with setting up a network is the plethora of numbers (mask, dns, ip, etc..), each with their own meaning. Plus, when I throw the ports and the router into the mix I get totally overwhelmed. Can anyone give me a good rundown of how to go about doing this, plus how I can check to see if things work for a little peace of mind?  

Any info is appreciated - I'm new to Ubuntu and networking in general.

Thanks!

---

### Post by papibe on 2012-07-19
Hi AustenG.

If you're unfamiliar with that concepts mention below, take a look at this is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

This would be the main steps:
[LIST]
[*]Set your server with a LAN static IP.
[*]Install openssh-server on your server.
[*]Test LAN ssh access to your server.
[*]Optional: change the standar ssh port (22) to a different, preferable higher value.
[*]Either install and setup the package ddclient, or (better if available) set your DDNS client in your router.
[*]Forward the ssh port in your router to your server.
[/LIST]
Now you are ready to test accessing your server over the internet.

Important: do not try to access your server using its public IP, or OpenDNS name from inside your own LAN. The proper way to test access if from outside your network. For example, an internet café, public library, a friend house, or using your phone or tablet's 3G service (be sure to NOT being connected to your LAN though).

I hope that points you in the right direction, and tell us how it goes.
Regards.

---

### Post by AustenG on 2012-07-21
papibe, thanks for the response. My only confusion now is that I don't have a server. I basically have a desktop which dual boots Windows 7 / Ubuntu 12.04 which I'm using to set up a secure network (with static IP so that I can ssh and screenshare with all devices on my network - laptops, desktop). 
Do your rules regarding servers simply apply to my linux box? I was hoping to get this all done with Ubuntu instead of Windows7.

---

### Post by papibe on 2012-07-21
> **AustenG said:**
> Do your rules regarding servers simply apply to my linux box?

Yes. The steps that I gave you apply for all version of Ubuntu.

The basic steps on the video apply for Ubuntu, but the software selection (http file server) don't. In Linux, ssh can proveide you remote access easily and much more secured.

I'm sorry if I add some confusion with the Windows video. My intention was to introduce the necessary concepts like Public IP, LAN IP, ports, and router forwarding.

I would gladly walk you in every step.

Have you set up an LAN static IP, or DHCP reservation on your router for your machine?

Regards.

---

### Post by AustenG on 2012-08-12
So far I've set up a static IP through opendns.com , so now this means that no matter what ip my router is assigned by my ISP, I will see my router as having the same address. 

I think I'm especially confused because I don't know if I should be doing all of this through the Netwok Manager, or doing it manually.

Let's take this one step at a time. Can you explain how I can get ssh and screensharing ports to work now that I have a static ip? My router is cisco.

---

### Post by Cheesemill on 2012-08-12
As far as I know OpenDNS just provide DNS services and have nothing to do with assigning you an IP address.

Your external IP address is given to you by your ISP, not by OpenDNS.

To get a static external IP address instead of a dynamic external IP address you usually have to pay your ISP for it.

All that OpenDNS does is provide resolution between domain names and IP addresses for external websites with some extra content blocking features, if all that you are after is to set up a home network where each device has a static internal IP (which makes port forwarding easier) I see no need for OpenDNS.

---

### Post by mr-woof on 2012-08-12
Hi,

have you installed ssh-server yet? You'll need to do that first, once installed you need to complete a number of steps before you open up the ssh server to the internet as there are a lot of brute force bots/scripts out there and they will try and get in.

This is what I usually do, ssh config wise. Someone else might come along and say this is wrong, but..

sudo nano /etc/ssh/sshd_config 
change PasswordAuthentication to no and delete #
change port 22 to port XXXX
change loginGraceTime 120 to LoginGraceTime 20
PermitRootLogin to no
change log level from INFO to VERBOSE

I'd recommend installing ubuntu server into a virtual machine, installing ssh and playing around with it before going on the net. This is what i did and i learnt a lot, you'll need to use ssh keys as well instead of passwords, but get ssh installed first and have a play :)

Edit, if you want to put your pc on a static ip, try this with your own network details:

sudo nano /etc/network/interfaces

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

sudo /etc/init.d/networking restart

---

### Post by AustenG on 2012-08-12
Awesome. I'll give this a shot and get back to you. Thanks!

---

### Post by mr-woof on 2012-08-12
no worries, hopefully you'll be able to get something sorted out.

Also, I change my default port of ssh (22) to something else 2068 for example. Its not perfect but should stop the majority of bots knocking on your ssh door :)

---

### Post by AustenG on 2012-08-12
@Cheesemill: I know that the ISP is ultimately the one who provides the address, but I have had the same "public" address for the last month. As far as I know this is all because of my opendns account. I don't really know the details about what it really does, but how is this not a static ip address?

Also, if I don't have a static ip address as you say, how do I get one without paying my ISP such that I can set up a network with ssh and screen-sharing?

---

### Post by Cheesemill on 2012-08-12
> **AustenG said:**
> @Cheesemill: I know that the ISP is ultimately the one who provides the address, but I have had the same "public" address for the last month. As far as I know this is all because of my opendns account. I don't really know the details about what it really does, but how is this not a static ip address?

This has nothing to do with OpenDNS.

Just because your IP doesn't change regularly, there is no guarantee that it won't. It could happen at any time.
I also have a dynamic IP address from my ISP but it's only changed twice in the last year.

To ensure that you can always reach your network from outside you can sign up for a free account with a 'Dynamic DNS' provider. Basically they provide you with a domain name that points to your IP, and then a piece of client software on one of the machines on your network notifies this provider every time your IP changes so that they can update the domain name with your new address (some routers offer this client functionality as well).

This way you can connect to your network from outside using a domain name that always points to your correct external IP address, whether it has changed or not.

There's a section about Dynamic DNS in the official documentation:
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by AustenG on 2012-08-12
That makes a lot of sense. Is it free to sign up with one of these Dynamic DNS providers? Is OpenDNS one of these providers?

Thanks for the info - I'm not sure why I'm having such a hard really understanding computer networks. Do you have a good book or website that explains everything?

---

### Post by Cheesemill on 2012-08-12
> **AustenG said:**
> That makes a lot of sense. Is it free to sign up with one of these Dynamic DNS providers? Is OpenDNS one of these providers?

Thanks for the info - I'm not sure why I'm having such a hard really understanding computer networks. Do you have a good book or website that explains everything?
Just Google for 'free dynamic dns' and take a look at the results, there's also a list on the documentation page that I linked to.

OpenDNS doesn't provide that type of service, they just provide the same DNS service that your ISP provides (translating domain names to IP addresses so that your browser can find websites) but with blacklisting of sites.

I don't know of any good resources off-hand, but I'll have a look around and post back with some (I work as a network admin and learnt all of this stuff many years ago).

---

