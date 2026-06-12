---
title: "torrents"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-27
i use ubuntu hardy........and i want to use something as http client on windows,to bypass the local network firewall,and i don't know as to which program does that.also tell me the way to install it and use it.which torent programs would work with it,and how can i install them?

---

### Post by freak42 on 2008-08-27
-do want a program for windows or linux?
-do you want a program that downloads torrents or a http client?
-you probably can't bypass a firewall on your local network, but you can configure it to let traffic you want through?

---

### Post by pyromanic123boom on 2008-08-28
Ok...gui for your firewall is FireStarter

sudo apt-get install firestarter

Then you can enable/disable your firewall for torrent connections. What client do you use?

---

### Post by OutOfReach on 2008-08-28
For a bittorent client I would recommend Deluge ([http://deluge-torrent.org/](http://deluge-torrent.org/)).

---

### Post by Crafty Kisses on 2008-08-28
I'd say Firestarter, very reliable from personal experience.

---

### Post by stonecoldjha on 2008-08-28
i want the local firewall to allow me to download and use torrents,which it blocks.also,how do i configure some torrent client(please suggest a good one that has support for SOCKS v5)to access the internet through the program that allows me to bypass the torrent ban?i am familiar with setting up the things on windows,which i have totally discarded.and i don't know about something of help in linux in this direction.

---

### Post by stonecoldjha on 2008-08-28
http client is a program that allows one to use the local proxy server to let in banned traffic,like restricted sites,torrents,etc.i want something similar for ubuntu,and also a bit torrent client that can be configured to make use of it,it should have support for SOCKS v5

---

### Post by hyper_ch on 2008-08-28
by default Ubuntu does not block anything (or rather the firewall "iptables" does not block anything).

If you install firestarter, then everything will be blocked and you have to unblock it.

Besdies, in most cases you don't even need to bother about a firewall or the settings.

---

### Post by stonecoldjha on 2008-08-29
its not about ubuntu blocking something,but the network that i am connected to ,that blocks torrents to prevent waste of bandwidth.how do i make it let me use torrents.in windows,there is something called http client,its a program that bypasses this ban.what is there in linux to do that?

---

### Post by t0p on 2008-08-29
> **stonecoldjha said:**
> its not about ubuntu blocking something,but the network that i am connected to ,that blocks torrents to prevent waste of bandwidth.how do i make it let me use torrents.in windows,there is something called http client,its a program that bypasses this ban.what is there in linux to do that?

There's a program I sometimes use, that allows a user to get past the kind of network restrictions you mean.  It's called **Your Freedom**.  It's a java app, so you'll need Sun Java or whatever, and also OpenVPN, which is in the repos.

Unfortunately, Your Freedom is *not* in any repos, so you can't do an install via apt-get or synaptic.  It's available for download from [www.your-freedom.net]("http://www.your-freedom.net").  And, being a java app, it's a real simple install - full instructions also at that site, and also a very good User Guide in pdf form.

This app is used by journalists and bloggers in China who want to access sites banned by their government.  And it lets me use pidgin, even though my ISP doesn't let customers use IM apps for some unfathomable reason.  It acts as a proxy in both HTTP and SOCKS4/5.

---

### Post by Vadi on 2008-09-02
> **Codename said:**
> I'd say Firestarter, very reliable from personal experience.

Nothing against firestarer, but the last release was four years ago ;). Gufw is a good maintained program to try: [http://gufw.tuxfamily.org](http://gufw.tuxfamily.org)

---

