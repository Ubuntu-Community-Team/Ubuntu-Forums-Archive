---
title: "Basic Firewall Understanding"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by held7over on 2011-11-09
Ultimately, I want to utilize Shorewall on a server, but I haven't found much I understand on their site! As they assume I understand the basic elements they are utilizing. I don't.

So, I have been looking to find a basic tutorial(s) on the internet that will start at scratch and walk me through the fundamentals so that I have a grasp upon what is called for in their config files. But I am not having much luck finding what I need. I either find something so general it isn't helpful or something that assumes I know what they are talking about. It just isn't clicking for me.

Can you recommend some Internet based tutorials that will give me the working knowledge I need? Assume I know nothing.

Thanks!

---

### Post by HermanAB on 2011-11-09
Howdy,

Bear in mind that the Linux network stack has changed enormously over the years.  The result is that most of the rules in Shorewall and its ilk are simply not needed anymore.  That is why Ubuntu ships with no iptables rules by default, because nothing special is needed for a desktop system.

For a server, I only use ONE rule, an iptables rate limiting rule, which discourages DOS and brute force attacks.

So, IMHO trying to understand the convoluted Shorewall configuration script is mostly a waste of time.

---

### Post by held7over on 2011-11-09
Hi Herman! As I have been looking for information, it has been very evident things were changing,but the implecations and meaning of those changes was lost on me, so I was trying to find information that is recent....but wasn't finding the kind of basic tutorial that would help me. 

I think my problem is far more basic, as I don't understand how to use many of the terms or how all the elements come together to create routes of the transfer of IP and web traffic within the computer...and that is probably where I need to be pointed to something written for a beginner to form a visualization of how things work between a host and Virtual Environments.

Here is what I have done and what I need to do, and I will leave it to you to tell me what I need to learn and where I can find it in a form I can understand! As I don't understand the elements concerned with routing different forms of communication between the host and the VE's:

On a GUI-less computer, I have created a Debian host system, and then installed OpenVZ which gives me my virtual environments at a very low CPU and RAM overhead.....something I need.

Next, where I am stuck, is, I need to create a what a professional who does this for a living, that I bumped into called, a "rough" firewall in the host that directs all port 80 and 443 traffic to VE 101 (which for some reason isn't actually aimed at protecting the host...something that puzzles me!) However, I don't understand enough about directing the communications flow to do this. I am pretty sure it is actually simple to do, but I lack the understanding and haven't found the basics to give me the handle I need. I must be running the wrong searches...

VE 101 becomes my master firewall (which the professional called a "sophisticated" firewall) which recognizes port numbers and has them mapped to their respective various VE Containers own IP addresses, thus routing IP number traffic directly to the proper VE Containers. I need, probably, the same understanding as above, to do this.

VE 101 also directs all domain name based http traffic to VE 102, which is also setting inside of VE 101's dmz. Another thing I haven't figured out how to do because I lack the basics.

VE 102 contains an Apache Server (which will be another big hurtle for me...but hopefully more easily researched) and it will be running in something called "VIRTUAL HOST MODE" and which then handles all the external incoming and internal outgoing domain name based http(s) traffic (coming from the host firewall I assume) by passing it to the proper VE containers I create, by changing the headers of the incoming communications, by a mapped table of some kind containing the URL domain names to their assigned PORT NUMBERS which are high numbers, like 8800, etc., which the VE's have been assigned, by swapping the new port number of the mapped table for the arriving port 80 number, AND then Apache is set to send it back to the firewall setting in VE 101.

And the VE 101 firewall, which understands port numbers and not domain names, sees the new port number, and knows the correct internal IP of the VE it belongs to, and connects to it.

Of course, the real destination VE's where I am going to build my websites, all have their own firewalls and Apache servers, operating in SINGLE SERVER MODE, listening on their unique respective port numbers.

Herman:  This is a summation of my notes notes on how to lay this out, which I got from the profession linux website guy, who said it is really very elegant, simple and very secure, and will accomplish what I explained to him I wanted to create. 

My two questions really are: what online tutors of the basics will explain to me what I need to understand and will educate me enough to create this flow of information routing through firewalls and Apache? As I have been road blocked here for ten times longer than I want to admit to anyone! (This is why I said assume I don't know anything...because that is how I am pretty sure I feel right now. This will really be my first real use of the command line if that tells you where I am at.

Also, I assumed Shorewall was the "sophisticated" firewall he was talking about, whereas, he named Apache in the case of the server to use. I tried asking in several places if Uncomplicated Firewall would do this. No one answered. I have looked at other firewalls, trying to see if they have what I need, but I can't tell, and many of them, I later discovered don't seem to be active anymore, like FireHOL. I really need a bit of steering here on firewalls, or what will do the job with the easiest approach. I am building this, or rather, setting on this, in my home, but I want to be able to deploy this as a commercial venture someday on the web, holding my own little mini businesses, and blogs, or whatever....so, it has to stand up to traffic and attacks.

Sorry about the length. I know you are a busy guy.

Thanks! :)

---

