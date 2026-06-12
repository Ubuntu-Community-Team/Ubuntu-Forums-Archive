---
title: "Which is the best IDS? for a ubuntu newbie?"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by smokingates on 2014-07-10
Since making the switch to Ubuntu 14.04LTS (from windows 8.1) almost a month ago now, I have encountered several headaches all of which I have managed to fix with either a fresh install or help from the wonderful volunteers on this forum. I have taken several measures to increase the security of my system such as 1.enabling the UFW as explained in the security discussion stickied 'do I need a firewall?' with the strong outbound rules listes in one of the links. 2. created a password that rates as "strong" on the password creation tool upon first install (this time around!) 3. Only retrieving repositries from the ubuntu software centre 4. installing "noscript" for the firefox browser that ships with Ubuntu 14.04LTS (which I recently read also disables adobe flash by defailt). 5. setting updates to download and install automatically in the system configuration. 5. disabling the on board wi-fi that shipped with my machine in favour of a w-fi dongle (many thanks again to those that helped me here :) )

I read on a stickied thread in the security forum that IDS or "intrusion detction system" can play a vital part in keeping ones system secure. So.. my question is, which is the most secure alongside being the most user friendly IDS? I use wine for a MUD client (telnet) that seems to cause some connection issues at times (though much less than before the switch to ubuntu and even less after further securing the system as explained above).

I am also considering installing and getting to grips with the full apparmour package (I read that part of it ships with Ubuntu from v.8.something and upwards) however as I often use telnet I may struggle so that could be for a whole new thread so please bear with me! My goal is to make my system as secure as possible using the open source stuff available to me to create as many security layeers as possible here on Ubuntu.

Many thanks in advance for not just reply's but anyone who made the effort to read and at least have the mindset of wanting to post a useful reply for the above :D ):P

---

### Post by mooreted on 2014-07-10
Seems like overkill for a regular desktop. Sounds like you want to set up a web-facing server.

If you really want to learn to use IDS then I would recommend Snort.

[https://www.snort.org/](https://www.snort.org/)

---

### Post by ubudog on 2014-07-10
Hi smokingates,

You don't really need an IDS on your desktop system, especially if you're sitting behind a router and have already taken all of those other steps.

If you really want one, +1 to Snort like mooreted said.

---

### Post by Vladlenin5000 on 2014-07-10
Although telnet is very risky anywhere - Short version: [http://www.memoryhole.net/~kyle/telnet.html](http://www.memoryhole.net/~kyle/telnet.html) -, and a native Linux MUD client - [http://en.wikipedia.org/wiki/Comparison_of_MUD_clients](http://en.wikipedia.org/wiki/Comparison_of_MUD_clients) - probably would do much better, there's nothing in a home or SOHO environment that requires what is being mentioned in the stickies about Snort or HIDS. It seems you already have the firewall in 'paranoid' mode or close an such is often unnecessary if the computer connects to the world at large trough a proper router (for home/small networks DD-WRT/OpenWRT should do it fine and beyond). 
Unless, of course, the user is really paranoid or intends to use it for criminal activities in which case paranoia is a perfectly understandable behavioral response.

---

### Post by smokingates on 2014-07-10
I absoloutely do not "intend to use it for criminal activities" rather just spend my time unwasted on the internet and on the MUD I play, at least I think it's telnet based but it may be ssh after reading what was in that link, in-fact it wouldn't suprise me, after all it IS voted number 1 MUD on "the mud connector" and has been since I started playing (again) about 5 years ago :) And that leads me onto my next point, the client I use has been adapted specifically for use with this particular MUD and is way ahead of it's league as far us MUD clients go, just for the record the client is MUSHclient and the MUD is Aardwolf.

So.. I will definately check out this 'snort' and see if I can make head and tail from it :) Thank you for the suggestions!

---

