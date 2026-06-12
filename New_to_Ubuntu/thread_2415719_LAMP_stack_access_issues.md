---
title: "LAMP stack access issues"
date: 2019-03-30
forum: New to Ubuntu
---

### Post by killgorack on 2019-03-30
As the subject of this area suggests, I'm new.

I have 2 machines that were windows, and now have installs of Ubuntu 18.04 (one with plasma)

Enjoying them so far. I however have a couple questions.

Question #1 I have a LAMP stack on the HTPC machine serving a webpage, it can be seen throughout the local network **_*with the exception of the other Ubuntu machine*_**. I have NO idea where to start looking to resolve this. Even on my phone I can see it..
The use of the web server is to maintain a website offline for a project I'm working on. I want to connect and maintain with GIT from the other machine directly maintaining the repository on the web server.

Question #2 I can access files from the web server with the exception of /var/www/html. I've shared documents music, and photos just fine, the web root however I have no luck. I get access denied messages even when checking all the boxes for sharing. (right clicking in files)

<edit>
I _***can***_ access the server's served pages via the IP address in the local network.
</edit>

---

### Post by TheFu on 2019-03-30
Does ssh not work after you set it up?  

You've lost me on "LAMP stack access" - what does that mean?  Please specify the protocols you expect to work, firewall settings on both sides and whether you've configured /etc/hosts or DNS so that both machines can resolve names correctly.  

ssh is how Unix people manage Unix machines. Using an ssh-tunel is how I access MariaDB from remove systems, to prevent security issues by allowing any other IPs access.  That way all mariaDB access appears to come from localhost. 

If you haven't setup name resolution between the systems, then you'll need to use IP addresses. Name resolution can be DNS, NIS, NIS+, /etc/hosts, and a few others, but none are automatic. In tcp/ip networking, servers don't announce "here I am" to the entire network, since that would never scale to 4Billion addresses.  

Which "P" are you using?  Perl, Python, Php?

---

### Post by scottbomb on 2019-03-30
Do you mean that on the other Ubuntu machine, you to go [http://machine_hostname](http://machine_hostname) and get a page not found 404 error?

---

### Post by killgorack on 2019-03-30
> **scottbomb said:**
> Do you mean that on the other Ubuntu machine, you to go [http://machine_hostname](http://machine_hostname) and get a page not found 404 error?

Yes sorry that's exactly it it's a DNS thing I gather. Just have no idea why it works on other devices, must be stuck in a cache somewhere.

---

### Post by killgorack on 2019-03-30
protocols? Not sure, but I have a Linux/Apache/MY-SQL/_***PHP***_ webserver set up on one machine for developing. I can use the [http://webpage-name/](http://webpage-name/) on all other devices with the exception of another ubuntu box.

Understood about the IP's of course. It does work by name on other devices. 

its a minor annoyance but the IP addresses should be good for now.

---

### Post by TheFu on 2019-03-30
Try hostname.local/path/to/page
That's what avahil might support.  avahil is the Linux implementation of zeroconf - which can seem like DNS.

Also, don't forget that web hostnames aren't case sensitive, but everything after that *is* case sensitive.  index.php **is NOT** the same as INDEX.php.
N
Or you can just fix DNS for your network in the proper way.  That would require choosing which device you want to run DNS on and setting it up there.  Some routers can be DNS servers for the LAN.

Also, do all your PCs have static IP?  Servers need static IPs for many reasons.

---

