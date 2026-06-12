---
title: "Internet Security From Linux Newbie.  Kinda"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by user9015 on 2008-10-21
Hello,

I've created a Dual Boot System on my Laptop (IBM X31).  I'm running Windows XP Pro, and Ubuntu 8.04.  Where I work, I have access to a wireless network that I'm not really supposed to be accessing.  It's kinda a don't ask, don't tell sort of environment.  You can't see the network when attempting to connect, you need to know the network name and ID.  Both of which I know (insider sources).  My question is: Not that I am doing anything that I shouldn't be doing (which I guess accessing the wireless network could go either way), is there a way that I can surf the net, and do what I've been doing, but do so without anybody knowing it?  I've read things on open Proxies and such.  But that will just hide my computers identity correct? Someone will still know everything that has been accessed and downloaded/uploaded from said wireless network correct?  Is there a way to hide myself, and shield what content is being accessed, kinda like a ssl connection? I'm mostly concerned with my Ubuntu system as opposed to the Windows XP Pro seeing as though I'm trying to get off the Microsoft bandwagon anyway. Thanks for any assistance.

Linux Newbie

---

### Post by DFlame on 2008-10-21
Even if you use proxies, SSL connections etc, It will always be possible to see that you are connected to the network, The IP you were assigned and the MAC of your wireless network device. any kind of encryption you send over the airwaves will only hide the contents of the data you send, not the fact that it exists.

In short: Yes you can browse securely, No you can't hide it all.

DFlame

---

### Post by user9015 on 2008-10-21
So that said, what is the method of choice for secure web browsing for Ubuntu Users? Is it as easy as using open proxies (which I still don't really know about, but trying to learn) or is there a combination of things I need to do.  And will that secure just my web browsing?  Will that secure any downloading/uploading I may do? Aim connections, etc?  Thanks again for the help

Linux Newbie

---

### Post by greg@localhost on 2008-10-21
> **user9015 said:**
> Hello,

I've created a Dual Boot System on my Laptop (IBM X31).  I'm running Windows XP Pro, and Ubuntu 8.04.  Where I work, I have access to a wireless network that I'm not really supposed to be accessing.  It's kinda a don't ask, don't tell sort of environment.  You can't see the network when attempting to connect, you need to know the network name and ID.  Both of which I know (insider sources).  My question is: Not that I am doing anything that I shouldn't be doing (which I guess accessing the wireless network could go either way), is there a way that I can surf the net, and do what I've been doing, but do so without anybody knowing it?  I've read things on open Proxies and such.  But that will just hide my computers identity correct? Someone will still know everything that has been accessed and downloaded/uploaded from said wireless network correct?  Is there a way to hide myself, and shield what content is being accessed, kinda like a ssl connection? I'm mostly concerned with my Ubuntu system as opposed to the Windows XP Pro seeing as though I'm trying to get off the Microsoft bandwagon anyway. Thanks for any assistance.

Linux Newbie

Why don't you just ask to use the wireless network? Nobody can really condone unauthorised access to someone else's network on this forum.

---

### Post by user9015 on 2008-10-21
Things where I work are very political.  I have access to the internet via the network in the building.  I have a user name and password which allows me access, just not in my office. So therefore, I don't really have internet access at all.  My office has permissions restrictions setup so access to the internet is restricted.  The claim is that the internet cannot be connected to the computers because of the sensitivity of the software and information on the computers.  However, there is internet access to all of the computers in said office.  Bottom line is that it is a control issue with management.  I've been using the wireless network on my personal Laptop unobstructed for a few years now. Having the access is both helpful and productive in my job, however managment refuses to make a decision on it's use.  That said, while I am attempting to secure my doings, it's not as if I'm hacking onto someone else's network. I am simply avoiding any issues with management until the time when someone might actually make a decision that would be useful to the population of this office. I would also like to know because I am setting up a home server, and for security purposes there, I want to learn more about networking and security.

Linux Newbie

---

### Post by Ctrl+Alt+Del on 2008-10-21
Back when i was at school i had a similar misery, what i did was my create a script that changed my mac-adress and then dialed into a VPN-Server at home and tunneled all my traffic through it. That way my traffic was encrypted and noone could actually prove it was my computer unless he found my dial home script  :-)

---

### Post by user9015 on 2008-10-21
That sounds awfully difficult.  when you say Dialed In..  I'm hoping your not refering to accessing a server via Dial-up Modem?  I wish i could say I was a pro, but Networking, and certainly Ubuntu is not my area of expertise.   

Linux Newbie

---

### Post by user9015 on 2008-10-21
What if I was to setup a proxy firewall such as ANON PROXY.  Would this achieve the effect I desire?

Linux Newbie

---

### Post by Frenske on 2008-10-21
> **greg@localhost said:**
> Why don't you just ask to use the wireless network? Nobody can really condone unauthorised access to someone else's network on this forum.

Right!!! I don't know how you got the ESSID and login password, but there are laws against riding on somebody else wireless signal, because you are stealing their bandwidth. In some countries there are laws against this: so be warned it might be illegal.
The neat thing to do is to ask permission and maybe partly pay for the signal.

---

### Post by greg@localhost on 2008-10-21
Indeed, i'm surprised this hasn't been locked yet.

---

### Post by user9015 on 2008-10-21
ok...  let's start this again..  I am NOT riding on, piggybacking, or stealing anybody's bandwith or internet connection..  At home, I have and pay for my own.  At work I have access, but due political stuff with management am not given the means to use it.  Therefore, I do it on my own.  My supervisors know all about it, and just ask that I refrain when upper management is around.  That's why it hasn't and won't be locked out. I can't get into what I do, but rest assured, I'm doing NOTHING illegal. What I am doing is for my own piece of mind, which would be why I'm trying to do this.. I know there is a way, and I'm thouroughly interested in finding out, because I'm trying to learn as much as possible about Open Source, to get rid of everything I have that is Microsoft related, and to learn more about networking in anticipation of setting up a "secure" home server.  If you don't want to offer any help, then that is your choice, but please don't act like the internet police, and tell me what I'm doing is illegal, because you don't know the details, and it is certainly not.


Linux Newbie

---

### Post by user9015 on 2008-10-21
How about TOR?  Would that Hide me?

---

### Post by bodhi.zazen on 2008-10-21
> **user9015 said:**
> Where I work, I have access to a wireless network that I'm not really supposed to be accessing.

I understand how you feel, but this sentence sums it up.

You should discuss this issue with your network administrator and obtain permission.

Circumventing private networks is not supported on these forums.

---

