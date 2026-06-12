---
title: "Making Bit Torrents Run Faster"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by mikemont012 on 2008-05-03
I am sure this has been answered but I can't find it - making bit torrents run faster - I've used various torrents but can't get to run faster than 70kbs on a 1.5MB/256kb service.  My router has all ports open. I've turned off the router firewall.  Any other suggestions - I'd be happy if I can get a torrent to run around 100kbs.  Any suggestions.


thanks Mike M

---

### Post by Joeb454 on 2008-05-03
Try turning encryption on - you may find that your ISP throttles torrents (I know mine does :() So you *should* get faster speeds :)

---

### Post by sstusick on 2008-05-03
Open up your upload to maximum, that should help speed things up. But you're really limited by the seeders' upload speeds. You can only download as fast as the seeder is uploading the file.

---

### Post by Joeb454 on 2008-05-03
> **sstusick said:**
> Open up your upload to maximum, that should help speed things up.

Not necessarily, I've had my uploads limited to 15-20kb/s before now and still got 300-500kb/s download speeds.

I leave it on full other times and never really get any higher than that, usually lower

---

### Post by Glaxed on 2008-05-03
BitTyrant

It's a Java client based on the Azureus 2.5 codebase and it has an enhanced algorithm that targets high capacity peers.
In their paper, they claim to get 30% to 70% faster download rates, and more or less the same on uploads.

Unforunately, if all peers are using BitTyrant, it is thought to harm the overall performance of the swarm.

I'm not positive exactly how it works, but apparently, BitTyrant hits peers and then keeps track of the higher performing peers, and leeches from them...

I've used BitTyrant, and although there's almost no physical way to test torrent speeds using different clients, I'd say that it's a little faster than uTorrent.

BitTyrant encryption may not be as robust as uTorrent's or with clients based on a newer Azureus codebase (> 3) - so if you do torrent illegal media (don't), I wouldn't reccommend it. If you insist (and I'm not saying that you do, this is for all readers) that restricting digital content is practically a crime against humanity, consider using Moblock...

---

### Post by Nythain on 2008-05-03
rtorrent got me and still gets me my fastest speeds ever... but on a 1.5mbps connection i dont know how fast your gonna get anyways... i know when i was on "road runner light" i was capped at 80kb/s period

that being said, with a slow connection like that, i would leave you upload at about 10-15kb/s, make sure you only have no more than 2 torrents goign at the same time, and try encryption, because as already mentioned, your isp could be reshaping your torrent traffic... 

if none of that helps, you might be up the creek without a paddle mate

---

### Post by jpeddicord on 2008-05-03
My guess is the port is not properly opened. If your router supports UPnP (it probably does) make sure it is active and give Transmission a go. It's available in 8.04 from Applications > Internet > Transmission. It automatically configures the port forwarding, and with it I've been able to max out my speed of 60KB/s (sad as it is).

And like others said - it could just be a low seed rate.

---

### Post by CREEPING DEATH on 2008-05-03
I use Deluge (its in the repos), not only is it extremely fast it's also very light.  Just set the ports to random so it uses everything it can!
Java-based clients all suck CPU and RAM then slow down to a crawl!

CD

---

### Post by Glaxed on 2008-05-04
Deluge under Linux doesn't perform as well as uTorrent under WINE for me...
I've always liked Deluge though.

Is there a C port of it with the same UI?
When I'm running firefox or something, the Deluge GUI slows down the computer too much.

---

### Post by NightwishFan on 2008-05-04
Ktorrent is the best client I have ever used. My isp throttles my speed to about 750kb/s, and thats with encryption. If they were aware it was p2p protocol it would be much slower.

Set your upload and download caps to something reasonable to save connection for other things if your firefox is lagging. On my connection, 100kb/s max upload makes no noticeable impact on my browsing.

---

### Post by Jake90 on 2008-05-04
+1 for transmission. I've used it before and didn't like it that much. I had deluge and it was ok, then when transmission came with the installation of hardy I tried it again and it blew me away. I'm getting speeds of close to 300kib/s!! 
After you get it, go to preferences and see if the port is opened, if it's not open it and make sure that it's not firewalled and you should be good to go.

Jake

---

### Post by iSplicer on 2008-05-04
What torrent are you downloading? If it's illegal, get it from a Private tracker (It will max your connection 70% of the time). (Make sure you have the legal version purchased though =) )

---

### Post by Glaxed on 2008-05-04
my connection is crap (and so's my PC - its a P3 :sob:, such a terrible fate).
the max my upload has ever been is 48 kbps, so I cap it at 30 or 35 if im not seeding.

Anyone else have any thoughts on BitTyrant?

---

### Post by stinger30au on 2008-05-04
> **mikemont012 said:**
> I am sure this has been answered but I can't find it - making bit torrents run faster - I've used various torrents but can't get to run faster than 70kbs on a 1.5MB/256kb service.  My router has all ports open. I've turned off the router firewall.  Any other suggestions - I'd be happy if I can get a torrent to run around 100kbs.  Any suggestions.


thanks Mike M

firstly buy a high quality router in the first place that will handle torrents.there is a mind blowing amount of data getting pumped thru the router when using torrents and not all routers are build the same.
my first adsl router was a netcom nb 1300+4 . it will let you surf the wen and send/recieve email.... thats it. done expect any more.
i then bought a Billion 7402LM [www.billion.com.au](www.billion.com.au)

best thing i ever did.
i the changed the maximum allowable connections to 700 and can now prividing there is enough seeds download at 140Kb/sec no problems on my 1.5 meg adsl connection

---

### Post by Efros on 2008-05-04
Transmission is blowing away utorrent, identical torrents going much faster on transmission. Weird.

---

### Post by Glaxed on 2008-05-04
Does transmission have encryption that's as robust as uTorrent's?

The last thing I want is my ISP choking my torrents (which are actually all legal, them da** B*******!!!) * .

I asked my dad to change ISP's to <companyname> that costs pretty much the same as <companyname> but doesn't randomly crap out and can get 1.5 mbps... but nooooooo.
So he's definately not gonna buy us a new router :(.

*: Seriously, they're legal; Ubuntu DVD, Kubuntu iso, openarena, and the andLinux beta.

---

### Post by Joeb454 on 2008-05-04
We're not bothered if they're legal or not - it's your choice.

We (we being the forums) Don't really condone illegal pirating though :)

---

### Post by MeTylerDurden on 2008-05-14
just watch what you set upload speed at.. too much and it will slow down torrent and slow you down when surfing..  when you are not download or surfing leave your upload as high as you can..   i leave mine under 50  and when i am downloading and want it fast I set at 30 or 25 upload speed.. also set at 30 to 25 when surfing.. .. also get a good share ratio   , that is when you download share it with others  and try and keep at least a 1:1 ratio   my speed test right now with a few things running is 1500 kpbs down and 240 kpbs up.. there is a little insight for ya- check out "who killed the electric car"  and some "art bell"   for good entertainment

 the liberator who destroyed my property has realigned my perception

---

### Post by nintendorulz55 on 2008-05-20
im sort of new to torrents... i would say im an intermediate person when it comes to them. so, judging on what i know about torrents and internet speed and such, my torrents should download much faster if i use a wired network, right? at the moment, im using deluge, have down speed at unlimited,up speed at 25 kb/s wireless connection, connection speed is 54 mb/s and im using a Linksys WRT54G router and im only getting about 45 kb/s! im not really sure how to encrypt anything like mentioned before, could someone explain? thanks in advance!

---

### Post by NightwishFan on 2008-05-20
From my experience 1mb/s is fast. Your ethernet may possibly be able to do 100mb/s but the internet is not that fast. My torrents max out at around 750kb/s but tend to go around 100 or so. Try using protocal encryption if you are on a more full featured client.

---

### Post by KevinD_Atl on 2008-05-20
I was hitting 1.2 MB/S last weekend on Ktorrent and it was great speeds. These were on Comcast cable.  I had VERY SLOW speeds until I tunred off DHT or whatever that is called.  Also depends on the seeders, the more you have, the faster your download will complete.

---

### Post by stchman on 2008-05-20
> **mikemont012 said:**
> I am sure this has been answered but I can't find it - making bit torrents run faster - I've used various torrents but can't get to run faster than 70kbs on a 1.5MB/256kb service.  My router has all ports open. I've turned off the router firewall.  Any other suggestions - I'd be happy if I can get a torrent to run around 100kbs.  Any suggestions.


thanks Mike M

Is that 70kbits or kbytes?

If your are getting 70kbytes that is pretty good.

Torrents are completely dependent on how many seeders there are.  If there are few seeders and many leechers then the transfer rates are going to be really slow.

What torrent client do you use?

---

### Post by aktiwers on 2008-05-20
I have had same problem.. - or my ISP shape my connection.

Deluge with full encryption works great. Pick a torrent with lots of seeders (5000-8000 seeds maybe) to test it. I have had speeds up to 3000kb/s and more this way.

---

### Post by nintendorulz55 on 2008-05-20
ok, i tried the wired connection and i started getting speeds around 150 kb/s which is great considering i only have about 30 seeders! the problem is, i can't use the wired connection for too long or someone else in the family will want to use the desktop computer and it will have no internet. So i did my research, disable DHT, disabled my router's firewall, fully encypted deluge, and brought my laptop as close to the router as possible and im still getting the same speed! i suppose it's ok, i can make the connection wired for the night or something.. i don't want to have to do that for all my torrents, though! this is by far the biggest torrent ive ever downloaded, 8.6 G. i wouldve been waiting a month if i tried to do the whole thing wirelessly. i just wanted faster speed for future torrents, i dont want to have to bring my laptop in the computer room everytime i want to download a torrent. if anyone has anymore suggestions on what i should do, throw them at me! please!!!

---

### Post by bengoza on 2008-05-31
Is Deluge Java based? Because It was working great until I did this: ```
sudo update-java-alternatives -s java-6-sun

``` to get Frostwire to work in Hardy. Could this affect Deluge at all? If so, can I undo what I did? I'd rather have Deluge than Frostwire.

---

### Post by Joeb454 on 2008-05-31
I don't think so, I know Azureus is Java based but I don't think Deluge is.

From what I head it's Python & GTK

---

### Post by CREEPING DEATH on 2008-05-31
Deluge is strictly GTK, no Java.  I don't have Java on my machine and try not to use it because it sucks to much RAM and CPU.  I'm still very happy with Deluge, uploads are capped at 25k to keep my web browsing and such going full speed, but it downloads pretty fast.  I've downloaded complete movies (from [public domain torrents]("http://www.publicdomaintorrents.com/")) in less time than it takes to watch them!

CD

---

### Post by LebSoLjah on 2009-11-20
THIS IS NOT A MYTH

I just installed 9.10 and had extreme lag on firefox/deluge. To fix this I disabled IPV6 and it works perfectly now. I download at full speed while surfing without problems.

---

