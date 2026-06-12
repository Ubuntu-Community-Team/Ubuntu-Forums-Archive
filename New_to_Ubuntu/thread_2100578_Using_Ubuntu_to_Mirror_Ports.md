---
title: "Using Ubuntu to Mirror Ports"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by Krowvin on 2013-01-02
Greetings!

As a little bit of background, I took a Linux class a few semesters back and that is the extent of my knowledge with the Ubuntu O.S. I'm decent in C++ and do have a basic understanding of syntax. 

My question is this: "How would I go about setting up a Ubuntu server that would take in a connection through port(s)of my choosing and redirect them to a port(s) that I also would be able to choose?".

I've looked through several proxies and other methods of tunneling, but all of those options seem to have some sort of port that does not change. For example, 1723/22/80/ect... 

Assuming I have a machine running the latest version of the Ubuntu desktop software (It is my understanding that it wouldn't matter whether I use desktop or server software, it's just personal preference in this case). 

An example of what I would be trying to do would be this-
I'm over at my friends and he thinks he's being witty by blocking certain ports on his router. Without going through to much hassle. Would it be possible to use a common port such as 443 to access my Ubuntu server at home and have it redirect me to the ports of whatever it was I may be trying to access? 

I have done a fair amount of research online to try and figure out some solution as to what I might be able to do. From my research I have discovered a draw backing being a ping almost double that of the norm, due to the middle-man(my server at home). 

I could try to figure out whatever his router's password was and just turn off whatever port range he may have assigned, but then that'd be besides the point.

---

### Post by I8NY on 2013-01-04
Hmm.... interesting.  So I'm going to guess that your "friend" is blocking ports so you can't play games or run a server over the internet that require other ports besides 22, 20, 80, and 443.  The proxy method would be the easiest to get past it and there _should be an option to set what port it uses_.  There may be issues with using standard ports, like 80 & 443.  Those are for website traffic and may not allow other types of traffic on those ports.  I'm assuming you know what ports are open so you can test each one until one works.  What I don't know is if you can make out-going connections through the blocked ports or if it is completely blocked.  If you can make out-going connection then you shouldn't have to worry about using the only opened ports to connect and things should work just fine.  Open ports are only needed if someone is trying to connect from the internet to you.  My ports are all blocked except for 80 (HTTP) and 443 (HTTPS) but I can still connect to stuff on the internet using other ports that aren't open my end.  Figure that out and reply back and I will figure out what else can be done.

---

