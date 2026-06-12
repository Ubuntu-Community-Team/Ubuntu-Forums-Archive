---
title: "[SOLVED] Torrent questions..."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-09-11
For all of you who helped me jump the bridge and take on Ubuntu, Thanks!!! I made the jump, took XP off 100 percent, and I am loving it.

I have decided to try to learn a little about .torrent.  The first thing I did was take off transmission, install azureus, which after reasearching a little more this morning, I think was the wrong choice.  I only have .5gig ram and 1.7 ghtz, and as I understand its a resource hog.  Besides, I dont really know what to do with the client, so all the features would definitely be wasted.

I have pretty much decided that when I get home I am going to go back to transmission.  Now when I open up transmission, what do I do?  The first thing I did was add all my music folder to shared, and it seems that I have to do something about opening up a port.  Is this true?  If so I enjoy the challenege of trying to figure it out myself first, but I also have learned that part of why this OS is so secure is because no ports are open.

Once I get my client set up to actually work, is it as simple as going to google and searching for said file?  As in, lets say I wanted to download a free and approved music file called "The BEst Song Ever!"  Would I search that with torrent??  I tried to search the forums, but sadly, due to it being a touchy licensing situation and me being the only person not knowing what torrent even was until an hour ago, I cant seem to find my answers.  Thanks in advance!!

---

### Post by cb951303 on 2008-09-11
First of all transmission is a good choice. You can try deluge too. These 2 are the best torrent clients that you will find for gnome. Torrent doesn't work like other p2p protocols. You don't need to add anything to shared. All you have to do is to open/forward a port of your choice to your local ip. In order to do that you must go to the admin interface of your router/modem. I can't help you there because everyone's router/modem is different. Google will get you tons of information though.
After opening the port, go to transmission preferences and enter the port that you opened. Thats all. Now go to one of the sites below, search anything, download the *.torrent file, open it with transmission. voila!

[http://www.mininova.org](http://www.mininova.org)
[http://www.thepiratebay.org](http://www.thepiratebay.org)
[http://www.isohunt.com](http://www.isohunt.com)

Edit: Forgot to tell you that in torrent you upload what you're downloading at the same time. That's called leeching. If you continue to upload after that your download is finished it's called seeding. Now, when you will enter the sites above you'll see some numbers called 'seeds' and 'leechers/peers'. Theoretically your downloads will be faster if the seeds/leechers ratio is greater.

---

### Post by neurostu on 2008-09-11
So to find torrent files you need to search sites like ISOHunt, ThePirateBay.

Also you need to create torrent files for each file you want to share and then upload those torrents to a tracker so others can find them.

---

### Post by amazingtaters on 2008-09-11
for port forwarding try out [www.portforward.com](www.portforward.com)

cb listed 3 very good public torrent sites.

---

### Post by Therion on 2008-09-11
Torrents are a little different, but once you get the hang of it, you'll be rockin'.

In short you search for a .torrent file of "The Best Song Ever" on torrent sites, like Pirate Bay and so forth (see the links in the post above).  

You'll get hits for what you search on, and then download a tiny little file (the .torrent) from one of those hits and then open that with Transmission.  The tiny little .torrent file you download first tells Transmission everything it needs to know to go out and get "The Best Song Ever" and download *that* to your PC.

Now, the thing I like about torrenting is that it works both ways.  What I mean by that is, as soon as you have even a small section of the total file that you're downloading - say you only have 10% of the download of "The Best Song Ever" - you're already sharing that 10% with anyone else who wants to download it.  Furthermore - and this is the cool part - the more you UPLOAD (the more you share) the FASTER you download the stuff you want.  Torrents encourage sharing by increasing how fast you get what you want when you share with the community.  Pretty neat idea in my opinion.  

Sharing your files with the community is called "Seeding".  You automatically start to seed files when you have the whole file... You can share what you have when you have less than 100% of the file, but you're a seed when you have 100% and are sharing it with the community.  Those that have 100% of the file and are NOT sharing it, are called "Leechers".  Don't be a leecher.  You can delete the .torrent file when you're done downloading "The Best Song Ever" but I'm pretty sure that prevents you from being able to seed that particular file.

---

### Post by lovinglinux on 2008-09-11
> **rideburton56 said:**
> I have decided to try to learn a little about .torrent.  The first thing I did was take off transmission, install azureus, which after reasearching a little more this morning, I think was the wrong choice.  I only have .5gig ram and 1.7 ghtz, and as I understand its a resource hog.  Besides, I dont really know what to do with the client, so all the features would definitely be wasted.

Azureus is excellent for a power user. I would recommend Deluge, which is the best Linux client in my opinion. Easy to configure and has everything you need.

You can install Deluge from Add/Remove manager

> **rideburton56 said:**
> 
I have pretty much decided that when I get home I am going to go back to transmission.  Now when I open up transmission, what do I do?  The first thing I did was add all my music folder to shared, and it seems that I have to do something about opening up a port.  Is this true?  If so I enjoy the challenege of trying to figure it out myself first, but I also have learned that part of why this OS is so secure is because no ports are open.

You don't need to share folders like Limewire or other Gnutella applications (deluge doesn't have this option) and if transmission has this I would advice you to not use it. Folder share is much less secure than sharing torrents. When you download/upload with bittorrent you are transferring data of a single file, so the other peers don't have access to your directory and they cannot see what other files you are sharing.

You don't necessarily need a port open to download, but this will slow down your downloads, because your client will connect only to those peers that your machine requests. Let's explain how bittorrent works:

- when you go to a download site you don't download the file you want, you just download a .torrent file, which is a "recipe" containing the name of the actual file you want, how many pieces the file has and at least a tracker

- a tracker is a server that stores information about files being shared and peers sharing them. When you start a .torrent file, your client will scrape the tracker and add your IP and listening port to the list, allowing other peers (users) to connect to you. At the same time, your client will retrieve the lists of peers/ports sharing that file, so you can connect to them. 

- if you do not open a port, you will be able to request connections to other peers, but won't be able to receive requests. You still can download files, but you will connect to less peers than with a port open. This is not necessarily bad, if the swarm is big (popular swarms can has more than 50.000 peers), since you will have a lot of peers to connect. But if you try to download a torrent with only a few peers then you can expect some degradation on your speed and you won't be able to seed.

To properly configure a bitorrent port you need to choose the port number in the torrent client, then create a rule in the firewall to allow inbound connections on that port and if you are connected to a router, you need to forward that port to your machine, so all requests incoming on that port will be redirected to your machine by the router, the firewall will allow them to pass and your torrent client will be listening on that port. BitTorrent protocol has it's own set of ports to be used, but is not advised to use them, because some ISP's cap torrent bandwidth on those ports. So you can choose any port from 49152 to 65535.

I would also advise you to close the port while you are not sharing and to use block lists, to prevent bad peers (hackers, virus sharing people etc) form connecting to you. Deluge has a Blocklist plugin by default and you can download block list from [Bluetack]("http://www.bluetack.co.uk/forums/index.php") or from [IBlocklists]("http://iblocklist.com/lists.php"). I also advise you to use full stream encryption in the Deluge options.

> **rideburton56 said:**
> Once I get my client set up to actually work, is it as simple as going to google and searching for said file?  As in, lets say I wanted to download a free and approved music file called "The BEst Song Ever!"  Would I search that with torrent??  I tried to search the forums, but sadly, due to it being a touchy licensing situation and me being the only person not knowing what torrent even was until an hour ago, I cant seem to find my answers.  Thanks in advance!!

There are several torrent search engines like [[COLOR="DarkRed"]**Torrentz**[/COLOR]]("http://www.torrentz.com/"), which will search all sites already mentioned above. You can also use Google (it has a special search string but I can't recall), but is not a good method. Once you find the .torrent file, simple click over it and an choose to open with your torrent client. You can configure your client to start downloading the actual file as soon as the .torrent file is added to the list. Alternatively, you can save the .torrent files into a designated folder and configure the client to auto load them when it starts or you can open the torrent client and click "open", then browse the torrent file in your machine. Deluge has also a RSS dowloader, which will automatically download torrents from sites that provide RSS support. I personally think they are a little bit complicated, so I use a regular RSS feed reader inside Firefox that download the .torrent files to a designated folder, from where Deluge will automatically load.

I also advise you to learn more about p2p security at [Phoenix Labs]("http://forums.phoenixlabs.org/") forums. They make the Windows ip blocking software called PeerGuardian, but has tons of info about p2p security. The Linux PeerGuardian counterpart is called "[[COLOR="DarkRed"]**Moblock**[/COLOR]]("http://moblock-deb.sourceforge.net/")". Moblock has a thread [[COLOR="DarkRed"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=803183&highlight=moblock") and a forum at [[COLOR="DarkRed"]**Phoenix**[/COLOR]]("http://forums.phoenixlabs.org/forumdisplay.php?f=15").

---

### Post by cb951303 on 2008-09-11
> **Therion said:**
> ...Furthermore - and this is the cool part - the more you UPLOAD (the more you share) the FASTER you download the stuff you want...

AFAIK that's wrong. There isn't a relation between your download and upload speed. Actually if your dsl is asymetrical (adsl), the less you upload the faster you download but that's not just valid for bittorrent but for all protocols. it's the nature of adsl.

---

### Post by rideburton56 on 2008-09-11
Once again you guys have come through huge, thank you so much for all the great advice/info!

---

### Post by billgoldberg on 2008-09-11
I guess someone should tell you about private torrent sites.

You might find some that are still taking members, for most you'll need invites.

No fakes there and always super fast speeds (well 99% of the time).

---

### Post by lovinglinux on 2008-09-11
> **rideburton56 said:**
> Once again you guys have come through huge, thank you so much for all the great advice/info!

You are welcome. I have added and changed some info on my post after you posted this.

> **cb951303 said:**
> AFAIK that's wrong. There isn't a relation between your download and upload speed. Actually if your dsl is asymetrical (adsl), the less you upload the faster you download but that's not just valid for bittorrent but for all protocols. it's the nature of adsl.

This is partially true. While this is indeed the nature of adsl, the torrent protocol itself automatically balance how much you get depending on how much you give. So it advised to not allow unlimited upload bandwidth, which will slow down your overall connection, but to cap you upload speed to something like 85% of your upload speed limit.

---

### Post by cb951303 on 2008-09-11
> **lovinglinux said:**
> This is partially true. While this is indeed the nature of adsl, the torrent protocol itself automatically balance how much you get depending on how much you give. So it advised to not allow unlimited upload bandwidth, which will slow down your overall connection, but to cap you upload speed to something like 85% of your upload speed limit.

thanks for the info but could you explain further. How is it possible to balance upload and download if the protocol is decentralized. I mean it would be really easy to exploit that. Am I wrong?

---

### Post by lovinglinux on 2008-09-11
> **cb951303 said:**
> thanks for the info but could you explain further. How is it possible to balance upload and download if the protocol is decentralized. I mean it would be really easy to exploit that. Am I wrong?

It is a per torrent basis balance, not per user, although private trackers have ways of further balancing the speed based on user upload ratio history.

---

### Post by cb951303 on 2008-09-11
> **lovinglinux said:**
> It is a per torrent basis balance, not per user, although private trackers have ways of further balancing the speed based on user upload ratio history.

sure but, since there is no server, it must be the client who balances the d/u ratio but than it would be really easy to exploit it since its a client side feature thus it would be meaningless to implement such a thing in the first place. Nvm though I think I'll take a look at the protocol ref :lolflag:

---

### Post by lovinglinux on 2008-09-11
> **cb951303 said:**
> sure but, since there is no server, it must be the client who balances the d/u ratio but than it would be really easy to exploit it since its a client side feature thus it would be meaningless to implement such a thing in the first place. Nvm though I think I'll take a look at the protocol ref :lolflag:

I'm not really sure how it works and I'm not sure is just the client. I guess the tracker records the upload speed or ratio and passes to the clients, but I could be wrong. Maybe is just  a widespread belief or a hoax to make people upload more :)

 I know that at least [[COLOR="DarkRed"]**BitTyrant**[/COLOR]]("http://en.wikipedia.org/wiki/BitTyrant") is capable of effectively determining which peers it should prioritize based on upload speed.

---

### Post by Therion on 2008-09-12
> **lovinglinux said:**
>  I know that at least [[COLOR="DarkRed"]**BitTyrant**[/COLOR]]("http://en.wikipedia.org/wiki/BitTyrant") is capable of effectively determining which peers it should prioritize based on upload speed.
I don't know how, exactly, the system enforces or monitors the situation regarding up/down speeds, but allow me to say that my experience very much confirms that this IS, in point of fact, how things work.

---

### Post by cb951303 on 2008-09-12
I stand corrected. bittorrent does have a d/u ratio balancer implemented. However I must say when I reduce my uploads my download rate always gets better.

I'm still confused about the implementation of this thing though. Even though tracker may balance d/u (I don't know if thats the case), since official torrent protocol also supports DHT (which doesn't depend on trackers) it makes the whole thing meaningless. But of course it's better than nothing :)

---

### Post by Clancy_s on 2008-10-29
> **lovinglinux said:**
>  Deluge has also a RSS dowloader, which will automatically download torrents from sites that provide RSS support. I personally think they are a little bit complicated, so I use a regular RSS feed reader inside Firefox that download the .torrent files to a designated folder, from where Deluge will automatically load.

(hoping someone's still watching the thread)

I've been using torrents for years and would like to have another go at using rss feeds with them.  I've tried with azureus with very patchy results.

Which rss feeder?  After a brief look at live feed I can't see how to get it to select and save a particular torrent.

If you have the time I'd appreciate some more details on both setting up the rss feeder and setting deluge up to run certain torrents.

---

### Post by lovinglinux on 2008-10-29
> **Clancy_s said:**
> (hoping someone's still watching the thread)

I've been using torrents for years and would like to have another go at using rss feeds with them.  I've tried with azureus with very patchy results.

Which rss feeder?  After a brief look at live feed I can't see how to get it to select and save a particular torrent.

If you have the time I'd appreciate some more details on both setting up the rss feeder and setting deluge up to run certain torrents.

Have you tried deluge's rss plugin (FlexRSS)?

[http://dev.deluge-torrent.org/wiki/Plugins/FlexRSS](http://dev.deluge-torrent.org/wiki/Plugins/FlexRSS)

---

### Post by Clancy_s on 2008-10-29
> **lovinglinux said:**
> Have you tried deluge's rss plugin (FlexRSS)?

[http://dev.deluge-torrent.org/wiki/Plugins/FlexRSS](http://dev.deluge-torrent.org/wiki/Plugins/FlexRSS)

No.  I've spent a fair bit of time trying to get Azureus' to work, with iffy results when I already have some torrents in a series and only want it to grab the new ones..  I was hoping a dedicated rss reader would have more user friendly filters.

I'll look at the deluge one on the weekend.

eta: I found it fairly easy to set up flexrss with deluge.  Whilst looking into it I found out Azureus has a 'bug' which causes the whole feed to hang if there's some xml it doesn't like in one of the links.  It applies to all the Azureus rss plugins and was probably the cause of my problems with rss in Azureus: I'd thought I had some fundamental problem understanding regular expressions.

---

