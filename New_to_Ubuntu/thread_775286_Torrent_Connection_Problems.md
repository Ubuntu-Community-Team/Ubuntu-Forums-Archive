---
title: "Torrent Connection Problems"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by jjdarling on 2008-04-30
I'm trying to download the Ubuntu 8.04 iso, and I am unable to connect to peers with most torrent clients. I have had no luck with Deluge, Bittorent, and Bittornado. With Transmission I can connect to peers it seems, but only to 1 at a time, and only for a tiny amount of time. I've been trying to download this torrent for about an hour and i've only gotten 120 kB.

I've tried a bunch of other torrent files, and I've tried two different trackers, all with the same problem.

I'm using the standard settings, and Transmission says that the port I'm using is open. I'm using 8.04 with Gnome, I just want an iso copy to (1) test torrent downloading and (2) install ubuntu on my friends' computers.

I've been using Ubuntu for about a year, but I never dig too deep (because it just works, for the most part), so treat me as a n00b.

---

### Post by T-Virus on 2008-04-30
Is the port you are using for BitTorrent really open? It can be blacklisted by the tracker. I suggest using port like 14545 or something like that. Now if you are downloading from a private tracker it requires you to log in at their site before you can connect to peers.

Does tracker status says - OK or any other message?

---

### Post by Ek0nomik on 2008-04-30
You can also test ports here:  [http://www.whatsmyip.org/ports/](http://www.whatsmyip.org/ports/)

---

### Post by jjdarling on 2008-04-30
I tried port 14545 and it seems to work marginally better (4kB/s) but obviously not the performance I should be getting. I tested that port on the link posted by Ek0nomik, and it said it timed out, as it did with every designated p2p port it tested.

I can't find any info about the tracker status.

---

### Post by Ek0nomik on 2008-04-30
> **jjdarling said:**
> I tried port 14545 and it seems to work marginally better (4kB/s) but obviously not the performance I should be getting. I tested that port on the link posted by Ek0nomik, and it said it timed out, as it did with every designated p2p port it tested.

I can't find any info about the tracker status.

Are you behind a firewall?  Do you have a router with a built in firewall?

The tracker status should be displayed in the bittorrent client.  All torrent clients display it.  Perhaps taking a picture and uploading it somewhere so we can see it would help.

---

### Post by sujoy on 2008-04-30
if you are behind a router then get the router to forward the port

---

### Post by T-Virus on 2008-04-30
Ktorrent has UPnP plugin for port forwarding you can try that one.

---

### Post by hyper_ch on 2008-04-30
could it be your ISP blocks bittorrent traffic?

---

### Post by fusionisthefuture on 2008-04-30
since you would know if you had a firewall installed on your ubuntu machine, im betting its your routers firewall thats causing the issues.  if the router is actually yours, you should log into its config page and figure out how to set up port forwarding.  if you dont know how, just search for port forwarding for your specific router, since they all vary a bit.  if you got that set up and its still slow, ive seen (although never played with) settings in the router that restrict the amount of connections that can be active at once, maybe those are set really low.  
-fitf

---

### Post by iSplicer on 2008-04-30
As a last ditch attempt, I suggest you try azureus, it works perfectly for me always

---

