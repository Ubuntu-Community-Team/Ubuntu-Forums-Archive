---
title: "[SOLVED] mobloquer only blocking outgoing connections"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by mazrabul on 2008-11-23
hi very one,

hope you can help with this one.

i have mobloquer installed and should be running. i use deluge for my torrents. 

i usually only use mobloquer when i have some torrents to download. my problem is the log panel in mobloquer is only showing blocked outgoing connections even when i am actually downloading a torrent. i have set no exceptions neither for outgoing nor for incoming. does mobloquer only show blocked outgoing connections or there is something wrong with the way my mobloquer is running on my machine?? please help.

i am using a ubuntu intreped on an acer laptop. when downloading i connect my laptop to the wireless router through a network cable rather than using the wireless connection.

thanks

---

### Post by Nepherte on 2008-11-23
Downloading relies on outgoing connections. You connect to someone else's computer to get a file that is on that remote computer. Someone connecting to your computer to access a file that is stored on your computer would be called an incoming connection.

So mobloquer's behavior is completely normal. I believe it also shows blocked incoming connections when there are any. You should be just fine.

---

### Post by mazrabul on 2008-11-23
many thanks nepherte for your reply.

may i ask, for my own understanding, doesn't an incoming connection occur first (maybe to guide the torrent client to where it should connect) before an outgoing connection is established?

also, if i may, do the companies the usually snoop around to see who is downloading what require an outgoing to connection from my computer to establish what ever they are trying to find or is it that they just follow an incoming connection to its destination and require no response from that machine?

thanks

---

### Post by Nepherte on 2008-11-24
I am by no means an expert in the whole torrent thing, so it's possible I might be wrong with what I'm about to tell.

I believe the torrent client already knows where to connect to because of the torrent file you downloaded. It contains the trackers that tell you where you can find the files you want to download. So you only need an outgoing connection (you can verify this with the firewall blocking all incoming connections while you are still able to download). This doesn't mean the remote computer doesn't send information to you. These are control packages that are inherit to the peer to peer protocol.

I don't know how all those companies snoop around. From what I've heard they simply download files that you make available for download to the public. If they are able to, they consider it as evidence. Perhaps they work with ping requests as well. As I told before, I am by no means an expert.

---

### Post by mazrabul on 2008-11-24
many thanks for your insight. it certainly is more info than i used to know.

cheers

---

