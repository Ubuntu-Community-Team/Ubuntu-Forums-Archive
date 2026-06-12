---
title: "NextCloud &amp; Rocket.chat hosted on the same server"
date: 2018-09-27
forum: New to Ubuntu
---

### Post by jsbtdx on 2018-09-27
Hi all!,

So as my first post i'm trying to find out the best way to install Rocket.Chat & NextCloud on the same server. I was thinking I could use Apache to run them as Application servers? 

I'm also wanting to run them securely SSL. And I plan on purchasing a couple domains to allow them to be accessed through a URL. With those criteria, i'm having trouble finding a good post or article with clear explanations on this.

I'm currently running Ubuntu 18.04.1

---

### Post by TheFu on 2018-09-27
SSL doesn't provide security for anything except the communications between point A and point B. Often, one side of those isn't who we think it is, since many corporate environments have started MiTM techniques for all HTTPS connections.

18.04 is relatively new, so there aren't well-tested guides available for lesser-known systems.  I've never heard of "Rocket.Chat" before.  Looked it up. They have a "snap" for installation, so you'd just need a reverse proxy to handle the SSL termination and redirect the requests to the correct back-end.  The default port is 3000 according to their docs.
$ sudo snap install rocketchat-server

Nextcloud has a video and voice chat server built-in, called "Talk", BTW.  I remember the install being trivial compared to other video conference solutions I've deployed.  The downside is that it uses webRTC, which has poor security.  The protocol, not any specific implementation.

---

### Post by jsbtdx on 2018-09-27
So if I understand correctly, Can’t I use Apache2 on my tower as a virtual proxy server? Then have it redirect traffic from one port to NextCloud & one to Rocket.Chat? 
If I buy a domain, “[www.example.com/cloud](www.example.com/cloud) & point it to my IP & port (80 in this example) “IPIP.IP.IP:80”
And then do the same with Rocket.chat
“Example.com/chat” & set it to resolve as “IP.IP.IP.IP:3000”
Can Apache redirect in such a way?

---

### Post by TheFu on 2018-09-27
I guess apache can be a reverse proxy and host a few different webapps.  I just don't use it that way.

Domains don't include ports or subdirectories.

It is easiest to use virtual domains and use different domains to point to different back end services.

chat.ex.com:443 --->   192.168.55.45:3000
cloud.ex.com:443 --->   192.168.55.96:5000

You'd probably want to redirect port 80 public traffic to port 443 on the public interface for each specific domain. You'll need 2 different SSL certs  - 1 for each domain.  LE certs are pretty easy to get and use.
The internal "back-end" server IP can be the same or different.
I prefer to use back-end ports that don't require root for security reasons.  Those have to be higher than port 1024.  8008,9090,8181,9191 are my go-to ports for web services.

Setting up virtual hosts in apache like that is trivial.

Just use the VirtualHost stanza and ServerName setting for each domain.  If you DNS provider supports wild cards, you can redirect all subdomains to a single IP.  This is the easiest.  If you have multiple IPs, then you can specifically set subdomains to resolve to those other IPs in the DNS.  

At least that's how it works on 16.04 and earlier.  I don't haven't any 18.04 systems here. Too new.

I pay for a public DNS. Got hacked in 2002 via DNS and learned my lesson.  I still run an internal DNS but that is very different from a security standpoint.

---

### Post by jsbtdx on 2018-09-28
Just to clarify:
For each domain, I should port from 80 to 443 in my router settings?

Purchase a domain to point traffic to my (router Public IP or my server local IP?) using specific ports for certain domain name traffic. And route all port 80 traffic to 443 (https) if they’re trying to access that service?

Can I use something like CertBot to get the SSL certs? Are you referring to let’sencrypt certs?

I get why we would want to not use root for security, but what do you mean by using the back end ports?

 I’ve been using Putty to SSH into it for a bit, I plan on setting up an SSH key soon. Do you recommend that?

Would you mind explaining the VirtualHost stanza & ServerName settings you mentioned?

Additionally,
Can I make it where a user would type in “Chat.ex.com” & it would send them to the same place “Chat.ex.com:443” would? I mean, is it possible to make it resolve where a user doesn’t have to type in the port numbers?


I know this is a lot, but other than trying to find a mentor, this seems to be the best place to get good information.
Your time is greatly appreciated.

---

### Post by TheFu on 2018-09-29
Nothing teaches more than trying something, working through issues, and solving them.

> **jsbtdx said:**
> Just to clarify:
For each domain, I should port from 80 to 443 in my router settings?
No. That isn't what you want. In apache configs redirect 80 (http) --> 443 (https)  There are reasons that will become clear later.

> **jsbtdx said:**
> Purchase a domain to point traffic to my (router Public IP or my server local IP?) using specific ports for certain domain name traffic. And route all port 80 traffic to 443 (https) if they&#8217;re trying to access that service? Domains go on servers, not routers.  Routers don't do the protocol change, just the port number redirection, but you shouldn't use that for 80-->443.  But only the router knows your public IP, so DNS needs to point at the public IP.

> **jsbtdx said:**
> Can I use something like CertBot to get the SSL certs? Are you referring to let&#8217;sencrypt certs? Yes.  LE = Let's Encrypt.  But I don't use them with apache so cannot help with that.

> **jsbtdx said:**
> I get why we would want to not use root for security, but what do you mean by using the back end ports?  The reverse-proxy is the front-end.  The webapp(s) are the back ends.  The front-ends listen on 80 and 443, the back-ends on any port above 1024 that isn't already used. The back ends should run using an unprivileged account. A different account for each webapp, IMHO.  When you are hacked, and you will be, best not to give them total access immediately.

> **jsbtdx said:**
>  I&#8217;ve been using Putty to SSH into it for a bit, I plan on setting up an SSH key soon. Do you recommend that? ssh keys are good.  Windows is bad.  I would never recommend someone use Windows.  I have no idea whether putty security is good or not. My ssh client made by the same team that makes the ssh server was updated in January 2018.  If your version of putty is later than that, it is probably fine.  Anytime you use a password, assume that is a poor security setup.  If you use passwords, you've failed security 101, IMHO.

> **jsbtdx said:**
> Would you mind explaining the VirtualHost stanza & ServerName settings you mentioned?Yes.  Use google with apache and each keyword to learn more.

> **jsbtdx said:**
> Additionally,
Can I make it where a user would type in &#8220;Chat.ex.com&#8221; & it would send them to the same place &#8220;Chat.ex.com:443&#8221; would? I mean, is it possible to make it resolve where a user doesn&#8217;t have to type in the port numbers? Yes. yes.  domainnames aren't case-sensitive, but the directory parts ARE case-sensitive.
 
I don't use apache much, but I have used it a few times over the last 25+ yrs.  I know what it can do, which is the only reason I answered. There are docs at apache.org which are expansive and have always seemed clear to me.  The hard part for someone new is to learn the correct search terms, which are provided above.  
* help.ubuntu.com has guides. Check the release version.
* wiki.ubuntu.com has guides. Check the release version.

---

