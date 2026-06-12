---
title: "point a subdomain to my Ubuntu PC"
date: 2016-10-25
forum: New to Ubuntu
---

### Post by Sky_Dog on 2016-10-25
Hello,

I bought some weeks ago a domain in host provider which administrate the webpage and email server for that domain.

Now, I want to create a subdomain which points to my Ubuntu PC that I am currently using.

Could you please tell me what should I do to point the subdomain to my PC? I need a general description/steps because I don't know currently where to start :(

Thanks in advance
S.

---

### Post by ian-weisser on 2016-10-25
That's an excellent question for your domain provider's paid technical support staff.
That's what you pay them for.

Generally, a domain provider should refer requests for your domain to your Ubuntu system's IP address.

Obviously, if your Ubuntu system is behind a router, then the provider should refer requests to the router's IP address. It's up to you to forward packets through your router to your PC.
Your router should assign a consistent IP address to your Ubuntu system for this to work properly.
If your router is assigned a dynamic IP address by your ISP, then you need to regularly update the IP address with your hosting provider so packets can find you.

Security: It's generally considered good practice to run internet-facing server applications in a VM or Container. Limits the damage if they get compromised.
That means adding an IPTables rule on your system to forward packets to the VM or container.

---

### Post by TheFu on 2016-10-25
There are 3 things needed for a website to work. It is my best practice to split these services up into 3 different companies/providers/systems, but obviously, most people don't know this is possible and often buy a "package" which includes all of them. They are:
* domain registrar - the name - all the registrar does is say where your official DNS for that TLD is location by IP (never name).
* DNS - the thing that lets everyone use [www.example.com](www.example.com) --> 1.2.3.4 (an IP address)
* hosting - the thing that runs the web server

More details about that: [http://blog.jdpfu.com/2009/08/18/internet-hosting-setup](http://blog.jdpfu.com/2009/08/18/internet-hosting-setup)

So - first of all, do you have full control over the DNS or is it only for 1 location/IP?  If yes, then go into the DNS control panel or config file and create a new record pointing to the static, public IP for your WAN connection at home.  Basically, you can have unlimited subdomains and point those anywhere with a full service DNS provider.  The "package deal" guys might not allow this.  I dunno.   Don't have a static IP at home?  Well, then you have an issue and getting another domain is probably the easiest solution - depending on the DNS provider you are using. Some allow dynamic DNS and let you automatically manage it through a script - no-IP does, for example.

I'll leave the other details about port forwarding in the router and setting static IPs inside your home network to others.

Anyway, hope this all helps.

BTW, THE Sky Dog knows this stuff forwards and backwards. [http://www.skydogcon.com/p/about_5.html](http://www.skydogcon.com/p/about_5.html) ;)

---

