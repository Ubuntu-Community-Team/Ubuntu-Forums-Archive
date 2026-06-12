---
title: "Hardy 8.04 based home network"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by geomur on 2008-06-17
I need to set up a wired home network for file sharing.  I have an old PC that I can use as a file server and need to connect 2 PCs and one laptop.  I have very little Linux experience and wonder if anyone can advise (or direct me to a resource) on how I make a start.

Many thanks, Geoff

---

### Post by Nepherte on 2008-06-17
This should help you out: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by fatality_uk on 2008-06-17
Need a little bit more information. Will all the PC's on the network be using Linux?

---

### Post by MockY on 2008-06-17
If all computer will be running Linux, then this site could be a good start, though it covers samba as well as general networking concepts [http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)

---

### Post by geomur on 2008-06-17
Many thanks for your replies, good to know the resources are out there.  To answer one query, the machines on the network will be 1x XP, 1x Xubuntu and 2x Ubuntu (inc. server), ethernet switch and cable mod. to the outside world.

Should I use Ubuntu desktop or server eds. in your opinion?

thank you!

:)

---

### Post by depele on 2008-06-17
It is both the same.

The only difference is that server has no gui by default.
Server is faster as Desktop because it has no gui.

It is up to you?

Do you know how to handle a terminal? ==> server

You don't ==> Desktop

---

### Post by cozmicharlie on 2008-06-17
I have my home network set up for two Ubuntu box's, 1 Xp and 1 Mac (my wifes).  Of course how you set up depends on what you want to do.  I mainly use mine for sharing multimedia.  I have bittorrent set up on a dedicated older laptop.  I have it set up so I can add torrents from any other computer.  You can share files using Samba as someone suggested and since you have an XP box that is a good way to go.  I however, prefer ssh.  It is faster and I always have problems with Samba.  I use Open ssh on all my Ubuntu box's and tunnelier ([http://www.bitvise.com/tunnelier](http://www.bitvise.com/tunnelier)) on my XP.  It works great, very easy to set up and it is secure.  For outside access you can set up Apache web site, Hamachi ([https://secure.logmein.com/home.asp?lang=en](https://secure.logmein.com/home.asp?lang=en)) or HFS ([http://www.rejetto.com/hfs/?f=intro](http://www.rejetto.com/hfs/?f=intro)).  Hamachi works well for most people and is very easy to set up.  I can access any computer over the web (if I am traveling) via tightvnc running through Apache ([http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html](http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html)).  Ubuntu is great for networking and it really is fairly simple to do.

Enjoy!

---

### Post by geomur on 2008-06-17
Many thanks, everyone.  Lots of useful ideas and pointers....now I've got to go and get on with it!

---

### Post by billgoldberg on 2008-06-17
I have three kind of servers running from my destkop.

A samba one, a ssh one and a upnp one.

For ubuntu only network it is extremly easy to get ssh up and running (1 minute).

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

This should also work with xp and osx, but not that easy.

For upnp, it's also pretty easy:

set up server:
[http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/](http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/)

Access server:
[http://linuxowns.wordpress.com/2008/06/05/accessing-upnp-server-from-ubuntu/](http://linuxowns.wordpress.com/2008/06/05/accessing-upnp-server-from-ubuntu/)

Second part is also possible from xp and osx.

---

