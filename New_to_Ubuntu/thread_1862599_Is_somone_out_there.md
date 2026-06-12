---
title: "Is somone out there???"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by Calerid on 2011-10-16
Hello, Everyone

Umm, I don't know what is going on, my network records don't show any odd IP's or network intrusion. So here is my problem...

I was using the terminal a minute ago to install some drivers for Nvidia, all of the sudden text started displaying a conversation... It said "Hi, like you I am new at using Ubuntu. I just wanted to show you some of my skills. I started using Ubuntu about a year ago. I"

And then it was lost in the code from the driver install. There was more in large chunks but I freakd and as soon as the driver install ended I shut it off.

Has anyone had this happen? any ideas?  It freaked me out, I have had experience as an Ethical Hacker and in return it's not a good feeling. Any trace of a visitor is gone, I don't have a firewall because I was not worried about loss or theft of information on this system. Though I don't like the feeling of being watched back. Any help necessary?

---

### Post by Diametric on 2011-10-16
Daaaaaaaaamn.  Never heard of that happening.  

Anyone know what log(s) to checck to see what's going on?

---

### Post by Calerid on 2011-10-16
> **Diametric said:**
> Daaaaaaaaamn.  Never heard of that happening.  

Anyone know what log(s) to checck to see what's going on?

Well first I checked my inbound, outbound traffic on my Router. Then I checked pings on my computer. The only thing I can think of is ARP poisoning, though no one in my neighborhood is that intelligent... It seemed like they where mimicking my forum use? The website history matched other pings in the network traffic. It seemed like a RAT, though as I stated earlier today on someones thread. I have heard of linux/ubuntu RAT's I have never seen or heard the names of an official one. It's a scary though to me.

---

### Post by Joreus on 2011-10-16
That would give me the hee bee gee bees. >.>
 Never heard of that happening before either.

---

### Post by -kg- on 2011-10-16
> **Calerid said:**
> Hello, Everyone

Umm, I don't know what is going on, my network records don't show any odd IP's or network intrusion. So here is my problem...

I was using the terminal a minute ago to install some drivers for Nvidia, all of the sudden text started displaying a conversation... It said "Hi, like you I am new at using Ubuntu. I just wanted to show you some of my skills. I started using Ubuntu about a year ago. I"

And then it was lost in the code from the driver install. There was more in large chunks but I freakd and as soon as the driver install ended I shut it off.

Has anyone had this happen? any ideas?  It freaked me out, I have had experience as an Ethical Hacker and in return it's not a good feeling. Any trace of a visitor is gone, I don't have a firewall because I was not worried about loss or theft of information on this system. Though I don't like the feeling of being watched back. Any help necessary?

This is the first time I've heard of this, myself.  All I can think to ask is, what NVIDIA driver were you trying to install, and where did you get it?  There is something wrong here, and I doubt someone hacked into your system from the outside...sounds like you were trying to install a "hacked" driver.

Really, you don't want to install anything except from known and trusted sources.  It's hard to hack a Linux system, but it's easy if you allow it in.  But as an "ethical hacker," I would assume you already know that.

Oh, and BTW...unless you've disabled or otherwise altered it, Ubuntu has a Firewall built in and set to block by default.  It's called IPTables.

---

### Post by Calerid on 2011-10-16
> **-kg- said:**
> This is the first time I've heard of this, myself.  All I can think to ask is, what NVIDIA driver were you trying to install, and where did you get it?  There is something wrong here, and I doubt someone hacked into your system from the outside...sounds like you were trying to install a "hacked" driver.

Really, you don't want to install anything except from known and trusted sources.  It's hard to hack a Linux system, but it's easy if you allow it in.  But as an "ethical hacker," I would assume you already know that.

Oh, and BTW...unless you've disabled or otherwise altered it, Ubuntu has a Firewall built in and set to block by default.  It's called IPTables.

Well I just meant that I did not have my own firewall running, most OS's have built in firewalls however light or heavy they may be I generally trust Linux on it's own. As for the driver I dl'd it from the Nvidia source using > sudo apt-get install nvidia-current.So unless all of the Nvidia drivers are exploited I don't think they are the cause at this point. though if someone on the way to me was messing the updates what purpose to go through that kind of trouble?

---

### Post by gsmanners on 2011-10-17
Do you have a wireless keyboard?

---

### Post by Calerid on 2011-10-17
> **gsmanners said:**
> Do you have a wireless keyboard?

Nope, Im using an old Dell I own. Stock Dell XPS Gen 2 desktop, USB keyboard and laser mouse.

---

### Post by gsmanners on 2011-10-17
Anything unusual in the /var/logs/dpkg.log?

---

### Post by Calerid on 2011-10-17
> **gsmanners said:**
> Anything unusual in the /var/logs/dpkg.log?

Nope, it shows the Nvidia Driver install went as planned and the rest of the log was accounted for. This is a fresh install from the day before yesterday. No personal info on it yet, just browsing the web so far.

---

### Post by gsmanners on 2011-10-17
My first impression of that was some weird advert or educational text, but it might be something more sinister. I guess the next thing to do is to boot a live CD and check for rootkits and stuff like that.

---

### Post by HermanAB on 2011-10-17
Hmm, I bet you Dollars for doughnuts that you were playing with VNC recently and have a really kewl 4 character password...

---

### Post by Calerid on 2011-10-17
> **gsmanners said:**
> My first impression of that was some weird advert or educational text, but it might be something more sinister. I guess the next thing to do is to boot a live CD and check for rootkits and stuff like that.

Yeah, I guess you are right. One of those things everyone dreads doing. I guess I will close this thread down for now.

---

### Post by Calerid on 2011-10-17
> **HermanAB said:**
> Hmm, I bet you Dollars for doughnuts that you were playing with VNC recently and have a really kewl 4 character password...

Yeah totally, It's still alpine!!! Lol, no I have not used any Remote Access tools on this PC yet. That would be a funny scenario though...

---

