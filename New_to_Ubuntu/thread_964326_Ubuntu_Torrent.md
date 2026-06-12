---
title: "Ubuntu Torrent"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by expatCM on 2008-10-30
My ISP apparently does not like bit torrent too much.   Torrent traffic is restricted to between 0.1 and 0.3 kB/s.  So  they do not ban it but effectively they do.

I am trying to download the 8.10 release by torrent but it looks like a total waste of effort.

Are there any packages to use torrents differently to get round this type of restriction?  Things like podcasts are downloaded at amazing speeds so I know that generally my connection is good.

---

### Post by bsharp on 2008-10-30
You could try enabling encryption.

What is the torrent client you are using?

---

### Post by sayems on 2008-10-30
Just Download it from here: [http://mirrors.cat.pdx.edu/ubuntu-releases/intrepid/ubuntu-8.10-desktop-i386.iso](http://mirrors.cat.pdx.edu/ubuntu-releases/intrepid/ubuntu-8.10-desktop-i386.iso)

---

### Post by aeiah on 2008-10-30
are you sure the ports are open and forwarded correctly for bit torrent use? those speeds seem far too low even for most isp throttling. i think most clients allow you to check if your ports are open properly.

anyway, if you cant use bittorrent then just download from the server i guess. if you're using ubuntu already then use wget
```

wget http://path/to/ubuntu.iso
```

if you have to interrupt the download you can resume with
```

wget -c http://path/to/ubuntu.iso
```

in windows or mac im sure there's several download managers that will let you resume downloads if something goes wrong along the way

---

### Post by ThreeLies on 2008-10-30
Not trying to divert from your question but I have been getting a timeout when announcing to the Ubuntu tracker.

Anyone else getting this?

---

### Post by nynoah on 2008-10-30
Turn on your encryption that helps with fooling your ISP.  I use Deluge which has an option for encryption.  Also I have found that running Mobloquer is a good idea when torrenting.

---

### Post by hyper_ch on 2008-10-31
contact your ISP and ask them :)

---

### Post by Jimmy9pints on 2008-10-31
I had similarly slow torrent downloads. 

To remedy this, I use deluge, enable encryption and I pick a random port between 49152 and 65535. Then enter that port into the Incoming TCP/UDP Listen Port box. 

I make sure that the ports are fowarded according to router and application specific instructions found [on this website]("http://www.portforward.com"). The website is aimed at windows users, but I followed instructions for a router similar to mine and for Azureus (because Deluge isn't listed).

But with a bit of tweaking I was able to download the .iso via bit torrent. 

Alternatively, use a download manager (such as firefox's downthemall (DTA)) and just go to one of the mirrors. That way, you can also enter a MD5 check sum hash into DTA to make sure your .iso is not corrupt.

Cheers,

james

---

### Post by 3rdalbum on 2008-10-31
If your ADSL router has a firewall in it, then set up port forwarding in the ports suggested by your Bittorrent program. Bittorrent downloads only go quickly if you upload, and you can't upload without incoming connections.*

Also, be patient. When you join a torrent, the speeds may be slow. But things will improve, especially as more people get the whole torrent and can start just seeding.

(*You can with UPnP, but it's not the most stable, secure, fast or compatible thing ever).

---

### Post by rzrgenesys187 on 2008-10-31
> **nynoah said:**
> Turn on your encryption that helps with fooling your ISP.  I use Deluge which has an option for encryption.  Also I have found that running Mobloquer is a good idea when torrenting.

You can also try changing the port since if they are trying to block they will usually block the default 6881-6889 if I recall

---

### Post by wardrich on 2008-10-31
Some ISPs, such as Rogers (in Canada) actually throttle all encrypted packets in an effort to thwart torrent users.  I think the best thing you can do is call your ISP and kick up a storm.

---

### Post by expatCM on 2008-10-31
Thank you for your suggestions .......... like everyone :)

I am using Torrentflux 2.4.  I have done this so that I can run it on a server which stays up 24/7.  I think I installed correctly and opened the firewall ports and did the forwarding in the router ... 

Yes, I have encrypted connections set and stealth cypto (to prevent non encrypted attempts).

Yes, I changed the port ranges well away from the defaults.

Some months ago whilst learning about this I tried to use Deluge on a client but I gave up with that deciding that Drip would be a better name given the download speeds achieved.

Talk to the ISP ...  don't think that is the best of ideas.  They are totally clueless at customer support ...  they are almost certain to tell me that I have a virus and come back when I have removed it.  Also it is not like there is a choice ...  it is them or nothing so I want to tread gently.  If I was to find the technicians what do I ask them to check without mentioning bit torrent by name?

Mobloquer - I just looked that up on google.  Sadly I am non the wiser.  In simple terms, what is this and why should I use it?

---

