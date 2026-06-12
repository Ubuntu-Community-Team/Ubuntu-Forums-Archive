---
title: "[SOLVED] How do I get around blocked ports? SSH Tunnel?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by neurostu on 2008-08-21
I'm at a summer course for the next week or so. The only internet provided has a pretty draconian firewall (As far as i can tell only ports 80 and 22 are open).  This normally would be fine except I can no longer connect to IRC(the server I connect to uses port 6667) and I can't use my outgoing mail server... (evolution never connects and can't send mail)

I was wondering what i would have to do to use ssh to get around the blocked ports... I've heard people mention that you can do it but I haven't found a good explanation....

So i have a laptop and desktop... my laptop is behind the firewall and my desktop is plugged into my network back at work (outside the firewall)...

what commands do I need to run on my laptop and what commands do I need to run on my desktop that will allow my local IRC client to connect to the IRC server?

---

### Post by Titan8990 on 2008-08-21
I have a feeling that it is against forum policy in assisting you with getting around administrative rules set by your school/work/etc. If it is not, then it should be.

---

### Post by H3retic on 2008-08-21
Surely a week without email/IRC won't kill you :)

---

### Post by Titan8990 on 2008-08-21
Also, I should add that in a work environment, getting around those types of restrictions and easily result in termination.

---

### Post by forger on 2008-08-21
I think it's pretty good they banned sending emails through the summer course.. then you just **have to** learn :KS Why not ask your administrator to allow you to check your email?
I use gmail as my email client and the web interface at [http://mail.google.com](http://mail.google.com)

hint: [http tunneling]("http://en.wikipedia.org/wiki/HTTP_tunnel_(software)")

You have to install software for it to work though, so you're pretty much stuck with no email/IRC :)

---

### Post by neurostu on 2008-08-21
So I'm fully aware that what I'm trying to do is very much in the grey area. I also fully understand that most networks have ports shutdown to make it easier to monitor their network security and to prevent activities that may be considered illegal (P2P, Bittorrent)...

However I'm doing email and IRC both of which are NOT for personal reasons rather for work related reasons, which are both directly applicable to the course I'm taking.

Frankly though I'm quite suprised that I got 4 "mothering" responses.... I understand the implications of what I'm doing, and obviously I'm accepting the possible consequences by posting this question... 
 However if its agains Ubuntu Forum policies for the instrcutions to be posted then fine don't tell me... but honestly it isn't your job or place to tell me if what I'm doing is either appropriate or inappropriate...

If I had said something like:
"Hey i'm visiting a relative and they have a firewall in their router that I'd like to get around for work... etc." I'm sure I wouldn't have gotten the same response and probably would have gotten the answer the I need....

anyway sorry to flame/rant but anyway...

---

### Post by Catalyst2Death on 2008-08-21
you could set up an ssh server on your home machine and tunnel to it from wherever they have you locked down through one of the open ports... once your in, its essentially as if you were sitting at a terminal on your home machine.

(I'm not too good at this, I tried it once, and emailed my administrator etc, the response I got was "we're not going to help you do this because if your asking the question, you should be knowledgeable enough to set it up on your own"  it wasn't strictly no, but it wasn't yes either, and I was very careful to read the use policies carefully)

---

### Post by Titan8990 on 2008-08-21
> 
However I'm doing email and IRC both of which are NOT for personal reasons rather for work related reasons, which are both directly applicable to the course I'm taking.

And both run the risk of introducing malware onto the network. It's doubtful they will make you th exception. Try to look at this from the network administrators point of view.

---

### Post by forger on 2008-08-21
There could be a million of reasons a network administrator blocked the traffic to all ports except those.
Could be.. cheating to a test? :)
Supposedly your desktop runs linux, preferrably ubuntu, and you have an ssh server on your desktop, I fail to see the reason you haven't tried to install and use applications that run from the ssh/console yet.

---

### Post by neurostu on 2008-08-21
So i do have applications installed on my desktop that I can run over ssh with X forwarding... but have you ever tried that over a slow wifi connection?  It really is terrible as there is a ton of data that needs to get transmitted... When a protocol like IRC uses such low bandwith it really make sense to only transmit the IRC data and not the entire window.

---

### Post by Catalyst2Death on 2008-08-21
then find cli mail-readers and irc clients.. its not that hard.  Every once and a while someone decided that it would be a great learning experience to do everything by the command line.  I'm sure they post what programs they use etc...

---

### Post by pauper on 2008-08-21
[http://www.hackinglinuxexposed.com/articles/20040830.html](http://www.hackinglinuxexposed.com/articles/20040830.html)

---

### Post by neurostu on 2008-08-21
So I actually found the answer to what I was looking for...

Funny enought it was IN the OFFICIAL DEBIAN DOCS! 

So for future reference: [http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall](http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall)

---

### Post by Dr Small on 2008-08-21
As long as they have one open port, you can bypass their entire firewall restrictions, by setting up a system outside the network that accepts incoming connection on the only port opened on the restricted firewall.

Example. If work has port 80 and 443 opened on their firewall and block traffic for all others, you can setup SSH to listen on port 443 at home. At work, you create a SOCKS connection to your home SSH server that is listening on port 443. You now basically bypass their entire firewall.

This sort of stuff is very trivial, and I don't see how it could be considered in the 'grey' zone. You learn alot over time, just by expirimenting with networking.

Dr Small

---

### Post by fahadsadah on 2008-08-23
For IRC, why not setup a port 80 psyBNC on your work machine?
Mail: Webclients are good enough.

---

### Post by neurostu on 2008-08-23
> **fahadsadah said:**
> 
Mail: Webclients are good enough.

I'm not sure you can define "good enough" for other people eh?

---

