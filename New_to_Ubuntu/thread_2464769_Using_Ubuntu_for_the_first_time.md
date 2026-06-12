---
title: "Using Ubuntu for the first time"
date: 2021-07-11
forum: New to Ubuntu
---

### Post by namekulero on 2021-07-11
Hi, I installed VirtualBox with the latest version of Ubuntu to get an SSL certificate for my Minecraft server plugin (I'm using Dynmap btw).

I followed the steps seen on [this tutorial]("https://docs.phoenixnodes.com/advanced-guides/install-nginx-reverse-proxy-on-ubuntu-18.04-for-dynmap"), but when I try to use the command on step 5 I get this error:
Domain: map.vecindadpayaso.com
Type: connection
Detail: fetching
[http://map.vecindadpayaso.com/.well-known/acme-challenge/vsMvf88DwGDfUpWdb0VTXzh8E5ASw-cBVFWY0MMO9Gs:](http://map.vecindadpayaso.com/.well-known/acme-challenge/vsMvf88DwGDfUpWdb0VTXzh8E5ASw-cBVFWY0MMO9Gs:)
Timeout during connect (likely firewall problem)

PD: Sorry in advance if this isn't the correct place to post this, if there's any way I can move this post to another location, please tell me.

---

### Post by TheFu on 2021-07-11
Did you buy a domain?
Are the DNS settings all setup and correct?
Step 5 seems awfully dangerous to me.  It is a terrible idea to grab a script off the internet, then run it blindly.
I didn't look any further, since I wouldn't use virtualbox to run a server on the internet.  virtualbox is for running desktops on a desktop.  Those instructions are for using a VPS, which would never use virtualbox.  All sorts of networking things are different between running virtualbox at home and running on an enterprise VPS.

I've never heard of Dnymap and suspect few people here have.  We tend to download the ISO from Canonical, install it ourselves, configure the networking, firewalls, and load any servers we desire.  Things that pre-build stuff aren't something I'm comfortable in trusting.  They could have put anything into the OS - it could be scanning your entire network and performing attacks on your LAN or using your internet connection to launch attacks around the world.  We don't know.  I like to stick with companies and people with good reputations and much to lose if they screw up.  
Pages that talk about how to accomplish things, but not why or anything about trust concern me.  They could be extremely reputable and I'm just not in that industry to know.  Almost all places that provide these types of downloads have ulterior motives, IME.

Be careful out there.

That proxy script has to run as root, btw. It won't work otherwise.  LE Certs validate that the system can be accessed by at least 3 different locations around the world before an SSL cert will be provided.  Making that possible from a home VM isn't hard, but it does require opening ports on the WAN router, setting the VM to have a static IP and forwarding port 80 and 443 to that static IP on the VM.  In the virtualbox network configuration, you cannot use NAT or host-only or the other choice for networking. Only bridged will work and the IP address must be static, so you can put that into the WAN router port-forward rules.

---

### Post by namekulero on 2021-07-12
Yes, the domain is mine, and I made all the configurations necessary for it to forward the *map.vecindadpayaso.com* subdomain to my IP, and I also have the necessary ports open on my router. 

I completely agree with you on not to run unknown scripts on my computer, but as this is what its been recommended in tutorials to port forward the subdomain to my IP, I just follow this steps to do this easily.

I'm just looking to port forward the subdomain as I've said various times here lol, if there's any safer way to do it without using others scripts, I would be glad to know, as well as how to get an SSL certificate for that subdomain, because as I've also said before, I haven't ever used Ubuntu, nor any Linux distribution.

---

### Post by TheFu on 2021-07-12
The router has to be configured to forward port 80 and 443 to the static IP on the LAN for the VM. That's it. There's no "subdomain" forwarding if your DNS for the subdomain points to the WAN-side static IP. It is handled in the router configuration.

Any OS would need the same to run a web server on a home network. There's nothing Unix/Linux related in port forwarding.

As for setting up LE certs, I use **acme.sh** for all LE Cert management, so cannot help with whatever tool the how-to says. The most popular tool never worked for me.  Plus, I've been renewing certs for years. Haven't created any new certs in about 3 yrs, so it isn't fresh in my mind. Sorry.

BTW, many ISPs block inbound ports to prevent people from doing what is being attempted here. They want us to buy "business" connectivity.  Check that is working before doing anything else.  
Go to a cafe and see if you can connect to your system from the internet using **telnet {ip-address} 80**.  
If that works, then the connectivity chain is correct.  
If it doesn't, then the connectivity chain is broken.  You'll have to figure out where that chain is broke. I would start with the router logs, then check the nginx logs to see where the connection request makes it. 

In a forum like this, it is next to impossible for you to understand me and for me to understand which things are tripping you up.  That's where having a mentor for a few years comes in - to fill in the knowledge that isn't in any book and help to build habits to avoid most issues.

Little things like hostnames, groups, and usernames should always be lower-case, never mixed case,
config files should always end with 1 blank line, 
never allow spaces in filenames or directory names,
things like that.  Sure, they shouldn't matter, but every once in a while, they do and things break if we don't follow those ideas.  Following the rules means not spending 20 hours figuring out that a parser for 1 command we use once every 3 yrs is broken.  OTOH, if we follow those rules, we avoid all sorts of dumb issues across 20 platforms.

Check the logs, trace how far the connection is getting on each system along the way.

---

### Post by ActionParsnip on 2021-07-13
You need to permit port 80 for validation, then the certificate will be given

---

