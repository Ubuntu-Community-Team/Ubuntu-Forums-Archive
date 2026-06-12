---
title: "A good P2P client...Please"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by sillyboy on 2008-08-30
I am looking for a good P2P client such as Ares Ultra, And the best method to acquire it.

Thanks

---

### Post by nicedude on 2008-08-30
Use torrents, and for that I like azureus

---

### Post by boglio on 2008-08-30
Well for torrent i prefer deluge
```
sudo apt-get install deluge-torrent
```

Then there is Limewire, over the Gnutella network.
[http://www.limewire.com/download/download.php?version=linux_deb](http://www.limewire.com/download/download.php?version=linux_deb)

Finally aMule, eMule alternative.
```
sudo apt-get install amule
```


That's everything I use for my p2p needs.

---

### Post by lovinglinux on 2008-08-30
BitTorrent is much more secure than Gnutella applets. You can see a torrent client comparison at [http://en.wikipedia.org/wiki/BitTorrent_client](http://en.wikipedia.org/wiki/BitTorrent_client)

Deluge is one of the most complete, but extremely easy to configure.

---

### Post by swoll1980 on 2008-08-30
Limewire [www.limewire.com](www.limewire.com)

---

### Post by Jheffrey on 2008-08-30
Torrents. Transmission or KTorrent

---

### Post by gmxgeek on 2008-08-30
+1 for azureus vuze

---

### Post by GepettoBR on 2008-08-30
BitTorrent is the most efficient form of p2p networking, so I second the motions to use Deluge, Azureus/Vuze and Transmission. I use Transmission myself, but not the version in the repositories. I compiled the latest version from the official website.

In case you don't want that, Frostwire is a good one, and aMule, as previously stated by other posters.

---

### Post by nicedude on 2008-08-30
limewire & frostwire are full of junk. 

PS Although this is just my joke I think its funny - isn't transmission a part to change gears in my car?

Azureus or Utorrent are #1 in the whole world but you will need to use wine to use Utorrent and with azureus you don't so that is why I say azureus is tops.


Nothing even comes close to torrents in amount of stuff available and amount of files downloaded etc. Join a few private sites if you have to but in general you can just use the following ones that are public and easily found via a google search

pirate bay

mininova

iso hunt

new torrents

---

### Post by misswham on 2008-08-30
Is there something like Peer Guardian for ubuntu or is it not needed?

---

### Post by nicedude on 2008-08-30
Yes it is needed and it is available. You need to install iplist and it contains ipblock which is comparable to peerguardian.

command to install

sudo apt-get install iplist

command to run

sudo ipblock

---

### Post by doas777 on 2008-08-30
> **misswham said:**
> Is there something like Peer Guardian for ubuntu or is it not needed?

that is a topic of some debate. MoBlock is the one they recomend, but unfourunatly it is incompatible with IPTables, the kernel based firewall built into ubuntu. I haven't bothered since i have no good reason to, but look at this thread:
[Moblock (peerguardian linux alternative)]("http://ubuntuforums.org/showthread.php?t=192559")

---

### Post by VitaminBB on 2008-08-30
I downloaded Deluge and its the best ive seen for Ubuntu so far ...

Transmission was slower and doesnt have nearly the same functionality.

Deluge should be the default P2P for Ubuntu really ...

---

### Post by GepettoBR on 2008-08-30
> **nicedude said:**
> PS Although this is just my joke I think its funny - isn't transmission a part to change gears in my car?

Gee, I wonder if that has anything at all to do with Transmission's logo... :)

---

### Post by starcannon on 2008-08-31
> **misswham said:**
> Is there something like Peer Guardian for ubuntu or is it not needed?

Mobloquer is excellent, and intelligent to use whilst torrenting.

---

### Post by picpak on 2008-08-31
Frostwire: [http://frostwire.com](http://frostwire.com)
and Nicotine.

---

### Post by lovinglinux on 2008-08-31
> **misswham said:**
> Is there something like Peer Guardian for ubuntu or is it not needed?

Yes. There is [IPBlock]("http://iplist.sourceforge.net/download.html") an [Moblock]("http://moblock-deb.sourceforge.net/"). The last one also needs Mobloquer if you want a GUI.

IPBlock GUI is very similar to PeerGuardian and I think is easier than Mobloquer. Both provide pretty much the same functions. Be aware that if you use them with a Firewall like Firestarter, you need to load the ip blocklist after the firewall, otherwise it won't work, since all these programs are just an easy way to edit the same iptables.

If you change any firewall rules after IPBlock/Moblock is running you also need to restart the ip blocklist.

[Gufw]("http://gufw.tuxfamily.org/index.html"), is a firewall interface that also allow to import ip blocklists, so you get both functionalities with one single interface, but depending on the size of the list it can take hours to import the ip ranges. Additionally, Gufw doesn't have the "active" and "blocked" connections feature like the other programs.

---

### Post by mellowd on 2008-08-31
rtorrent + moblock = heaven

---

### Post by lovinglinux on 2008-08-31
I forgot a few things...

since you are already familiar with PeerGuardian I guess you will download Bluetack's lists. If you want more lists you can grab them at [http://iblocklist.com/lists.php](http://iblocklist.com/lists.php) 

They have links to all Bluetack's lists plus a few others.

It is a good idea to merge all the lists you want and load a single blocklist into IPBlock or Moblock. There are bug reports about Moblock not being able to block all IP's if you have more than one list loaded with mixed ranges. To merge lists you can use [TinyBLM]("http://www.bluetack.co.uk/forums/index.php?showtopic=11022&hl=TinyBLM"), which runs pretty fine with Wine.

Deluge also has a Blocklist ip filter plugin included. Some people would say that you don't need it, beause with IPBlock or Moblock you have full spectrum protection and not only for the torrent application. While the protection part of this assessment is true, you should load the same blocklist into Deluge's plugin because this will prevent the client from trying to connect to blocked peers. If you don't use the client ip filter, it will try to connect to every peer on the tracker. Obviously that IPBlock or Moblock will block unwanted connection attempts, both from your client or from outside, but this will slow down your download. That's because your client will try to connect to several blocked peers before finding one that is whitelisted. With the client ip filter activated and loaded with the same blocklist of your iptables, the torrent client will discard all IP numbers that are blacklisted before trying to make any connections to peers. So he will only try to connect to IP's that your iptables will not block, an thus reducing the time needed to get a decent number of successful connections.

---

### Post by sillyboy on 2008-08-31
> **boglio said:**
> Well for torrent i prefer deluge
```
sudo apt-get install deluge-torrent
```

Then there is Limewire, over the Gnutella network.
[http://www.limewire.com/download/download.php?version=linux_deb](http://www.limewire.com/download/download.php?version=linux_deb)

Finally aMule, eMule alternative.
```
sudo apt-get install amule
```


That's everything I use for my p2p needs.

Thanks...So all I do is copy the code in the Termimal and go from there?

---

### Post by sillyboy on 2008-08-31
> **lovinglinux said:**
> BitTorrent is much more secure than Gnutella applets. You can see a torrent client comparison at [http://en.wikipedia.org/wiki/BitTorrent_client](http://en.wikipedia.org/wiki/BitTorrent_client)

Deluge is one of the most complete, but extremely easy to configure.

I have installed DeLuge.  Is this client for movies, software and music?  If so is there a tutorial for DeLuge?:confused:

Thanks

---

### Post by wolfie2x on 2008-08-31
+1 for Deluge. Powerful, yet very easy to use.

---

### Post by GepettoBR on 2008-08-31
> **sillyboy said:**
> Thanks...So all I do is copy the code in the Termimal and go from there?
Yes.
> **sillyboy said:**
> I have installed DeLuge.  Is this client for movies, software and music?  If so is there a tutorial for DeLuge?:confused:

Thanks
Deluge is a bittorrent client. That means you simply go to a tracker website (like [www.piratebay.org](www.piratebay.org)), search for the file you want and click "Download torrent". That'll download a very small file (a few KB) which you open in Deluge. When you open the file in Deluge, the real p2p begins. Very simple.

---

### Post by GrandpaLeaman on 2008-08-31
> **VitaminBB said:**
> I downloaded Deluge and its the best ive seen for Ubuntu so far ...

Transmission was slower and doesnt have nearly the same functionality.

Deluge should be the default P2P for Ubuntu really ...

I would agree with this statement. I have tried Azureus and really like the interface, but didn't find it to be any faster than Deluge. When I upgraded to Hardy I gave Transmission a try. In this case I didn't like the interface as much as I like Deluge. It also wasn't any faster than Deluge.

Of course one of the things I really like about Deluge is the plugins. It allows you to customize the program to your particular needs. There is even an IPBlocklist importer.

---

### Post by GepettoBR on 2008-08-31
> **GrandpaLeaman said:**
> I would agree with this statement. I have tried Azureus and really like the interface, but didn't find it to be any faster than Deluge. When I upgraded to Hardy I gave Transmission a try. In this case I didn't like the interface as much as I like Deluge. It also wasn't any faster than Deluge.

Of course one of the things I really like about Deluge is the plugins. It allows you to customize the program to your particular needs. There is even an IPBlocklist importer.

I've used Deluge and I still prefer Transmission and Azureus. I use the former because it has a much cleaner interface. Most bittorrent clients fill your screen with an endless list of options that do absolutely nothing (or very, very close to nothing) for your speeds. The five clients I've used in Ubuntu (Deluge, Transmission, Azureus - before it was rebranded - the default up to Gutsy that was just called bittorrent and uTorrent under WINE) have all provided me with the same speeds and have all been stable. For me, the only things a BT client has to do are encryption, the ability to choose which files you download from a multi-file torrent, the ability to choose the listen port, pausing torrents and controlling speed limits. Transmission does all that, has a very low memory footprint and can even autoload torrents from a designated folder, which allows me to use it together with uTorrent on my Windows install to keep a unified torrenting experience on my dual-boot machine. :guitar:

But Deluge is nice for tweakfreaks, I guess. IIRC Azureus is much more customizable, though.

---

### Post by jre on 2008-09-01
> **doas777 said:**
> MoBlock is the one they recomend, but unfourunatly it is incompatible with IPTables, the kernel based firewall built into ubuntu.
This has been fixed in MoBlock 0.9rc2, the version that I currently have in the repository. Generally you will be fine, if
[LIST]
[*]MoBlock *marks* non-matched (IP is not in the blocklist) packets (this is the default).
[*]Other firewalls do not *mark* packets.
[*]MoBlock is started after other firewalls.
[/LIST]
With other (technical) words: The iptables rule which sends traffic to MoBlock (target NFQUEUE) and (if MoBlock marks matched packets) the iptables rule which decides what happens to matched packets have to stand before all other iptables rules which ACCEPT traffic.

For iplist basically the same is valid.

> **doas777 said:**
> I haven't bothered since i have no good reason to, but look at this thread:
[Moblock (peerguardian linux alternative)]("http://ubuntuforums.org/showthread.php?t=192559")
That thread has been closed, have a look at the new general MoBlock thread: [http://ubuntuforums.org/showthread.php?t=803183&highlight=moblock](http://ubuntuforums.org/showthread.php?t=803183&highlight=moblock)

> **lovinglinux said:**
> There are bug reports about Moblock not being able to block all IP's if you have more than one list loaded with mixed ranges.
This has also been fixed in MoBlock 0.9rc2.

> **lovinglinux said:**
> Deluge also has a Blocklist ip filter plugin included. Some people would say that you don't need it, beause with IPBlock or Moblock you have full spectrum protection and not only for the torrent application. While the protection part of this assessment is true, you should load the same blocklist into Deluge's plugin because this will prevent the client from trying to connect to blocked peers. [...]
Since MoBlock 0.9rc2 matched packets (IP is in the blocklist) first get MARKed and then REJECTED (instead of DROPped). This means that the sending application (e.g. Deluge) gets notified that its request was blocked and so can stop immediately its connection attempts. Anyway feel free to use the blocklist in Deluge, too :-)

Greetings
jre

---

### Post by doas777 on 2008-09-01
jre -- good to know. thanks for the update

---

### Post by lovinglinux on 2008-09-01
Thanks for the update and the Moblock thread link. I finally discovered why Moblock wasn't working properly on my machine and posted the explanation in the [Moblock thread](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5710286#post5710286). So I'm switching to Moblock.

> **jre said:**
> Since MoBlock 0.9rc2 matched packets (IP is in the blocklist) first get MARKed and then REJECTED (instead of DROPped). This means that the sending application (e.g. Deluge) gets notified that its request was blocked and so can stop immediately its connection attempts. Anyway feel free to use the blocklist in Deluge, too :-)

Does this means that an application trying to connect from outside your local network will also receive a rejection packet? If yes, wouldn't be better to just drop it, in case for example someone is scanning your ports?.

---

### Post by Swenghk on 2008-09-01
+ 1 for Frost Wire
+ 1 for eMule

---

### Post by jre on 2008-09-02
> **lovinglinux said:**
> Does this means that an application trying to connect from outside your local network will also receive a rejection packet? If yes, wouldn't be better to just drop it, in case for example someone is scanning your ports?.
No ;-)
Per default incoming and forwarded packets get DROPped, only outgoing packets are REJECTed.
See these settings in moblock.conf:
REJECT_IN="DROP"
REJECT_OUT="REJECT"
REJECT_FW="DROP"
Please note that in the original unpatched MoBlock source incoming packets will always get DROPped directly. In the Debian packages I changed this behaviour to MARK+DROP.

---

### Post by lovinglinux on 2008-09-02
Nice. Thanks for the explanation.

---

