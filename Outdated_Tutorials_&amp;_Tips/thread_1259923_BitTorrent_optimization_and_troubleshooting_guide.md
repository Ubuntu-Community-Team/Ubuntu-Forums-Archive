---
title: "BitTorrent optimization and troubleshooting guide"
date: 2009-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by lovinglinux on 2009-09-06
The objective of this thread is to provide a comprehensive list of BitTorrent optimizations and troubleshooting common issues (this is a work in progress). 

> **[COLOR="Red"]Warning:[/COLOR]** I do not support downloading unauthorized content, so any questions related to copyrighted material will be ignored and I will ask a moderator to delete it. The BitTorrent technology is not designed, as many other Internet technologies, to do illegal activities. That's solely the responsibility of the user. There are many legal uses for the BitTorrent technology, including downloading Ubuntu releases, which helps to distribute the load over Canonical severs, specially the day a new version is released.

**[size="4"][color=#CC0000]Index[/color][/size]**
[color=#CC0000][b][LIST=1]
[*]Introduction
[*]How does it work
[*]Download Speeds
[*]Configurations
[*]Security
[*]FAQ
[*]Troubleshooting
[*]References
[/LIST][/b][/color]

**[size="5"][color=#CC0000]1. Introduction[/color][/size]**

Understanding the technology is essential, in my opinion, to get the best of it. In this  tutorial I try to explain the basics as simply as possible, but this is not easy to do in a few words, specially for someone like me who doesn't have English as native language.  Nevertheless, I hope you will enjoy torrenting even more after reading this tutorial and I expect to be much easier for you to optimize and troubleshoot your download speeds.

For the purpose of simplifying this tutorial, I will be using [Deluge 1.1.9](http://deluge-torrent.org/) as an example when explaining configuration of [clients](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Client). I consider Deluge the best [BitTorrent](http://en.wikipedia.org/wiki/BitTorrent_%28protocol%29) client for Linux and Windows. Nevertheless, most of the contents of this tutorial can be applied to any client, since the concepts are the same and most clients have the same sort of basic features. You can check a list of available clients and their respective features [here]("http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software").

I have included several links throughout the tutorial, most of them to Wikipedia articles, which has a lot of good info on torrents. I wish I could explain everything, but then you probably wouldn't read it. So, I will present only the essential information to let you understand the basic concepts and properly configure your Ubuntu box for torrent download. Nevertheless, further reading is strongly recommended.



**[size="5"][color=#CC0000]2. How does it work[/color][/size]**

[BitTorrent](http://en.wikipedia.org/wiki/BitTorrent_%28protocol%29) is the most popular [peer-to-peer ](http://en.wikipedia.org/wiki/Peer-to-peer) file sharing protocol these days. It is popular not only because of availability of all sorts of files, but because of the high speed downloads. This is possible because you don't download a file from a single source and the file is not transmitted in sequence, but broken into several small [pieces](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Piece). This means you can download pieces of the file from someone who has 100% of the entire file downloaded, but at the same time from someone who has only 1% of it. 

Each user sharing the same file can contribute, by uploading to you or to other [peers](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Peer) in the [swarm](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Swarm), as long as it has a single piece of the file and you don't have the same piece. This method greatly increases the speed, because you can download from several peers at the same time and they don't have to wait for a complete download to upload to others. Even if a peer has a limited bandwidth for uploading, your download speed can be much superior to his bandwidth, because the upload speed of all connected peers are counted to your final download speed.

There are some very interesting differences between BitTorrent protocol and clients, compared to other popular file sharing networks, like [Gnutella](http://en.wikipedia.org/wiki/Gnutella) (Limewire, Forstwire) and [eDonkey](http://en.wikipedia.org/wiki/EDonkey_network) (Shareaza, aMule, Morpheus), although some of these network clients also support BitTorrent recently. For instance, with BitTorrent you don't share folders, only single files and you don't browse/search other peers computers to find what you want. You need to download a special file, with the **[COLOR="DarkRed"].torrent[/COLOR]** extension, for each content you want to download. This file, usually referred as [torrent](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Torrent), has all the information you need to connect to other peers and get pieces of the content form them. That information is embedded as [metadata](http://en.wikipedia.org/wiki/Metadata) and includes the identification of the files included in the download ([hash](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Hash)) and one or more [trackers](http://en.wikipedia.org/wiki/BitTorrent_tracker), which are servers responsible for listing all peers sharing the same content and allowing them to connect to each other.  

So, instead of connecting to a network of peers and then searching among their folders for the files you want, you need to browse a torrent directory to look for the torrent files or get them from a friend by e-mail, from developers web sites or any other method of direct file distribution. Once you have the torrent file loaded into your favorite BitTorrent client, it will connect to the tracker specified in the torrent, to retrieve a list o peers IP addresses sharing the content specified in the torrent. Your client will also [scrape](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Scrape) the tracker in order to add your IP address to the list, so other peers can connect to you. The tracker and the torrent doesn't have the content itself, just information about contents and peers.

Torrent directories or indexers are web sites that allow users to upload and download torrents, but not the content itself, which is always stored in the users computers. They are usually organized into categories and provide some sort of searching feature. The torrent directory does not necessarily provides the tracker, which can be any server on the Internet, although some of them also have their own. A popular torrent directory is [Mininova.org](http://en.wikipedia.org/wiki/Mininova), which also provides a tracker, but only for featured contents. These are contents provided by the site partners, which are creators or distributors, thus being legal and authorized. Torrents uploaded by regular users are not guaranteed to be copyright free, although the site has a system to filter copyrighted material. So use common sense, read the torrent comments or Google the content name for additional info before downloading.

Other kinds of useful torrent sites are just search engines like [Torrentz.com](http://en.wikipedia.org/wiki/Torrentz). They do not allow uploading, so they don't host the  torrent files. Instead, the provide a search engine like Google, that targets only torrent files and popular torrent directories. Nevertheless, they can be much more complex than Google, since they usually provide list of trackers currently active for each torrent, the number of peers, number of [seeders](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Seeder) and even a forum or comment section. They also can allow to search torrents by hash info.

For example, the link below uses the torrent hash to link to an Ubuntu release, which is tracked by the official Canonical tracker. The part of the address in red is the torrent hash number.

[**http://www.torrentz.com/[COLOR="Red"]60d5d82328b4547511fdeac9bf4d0112daa0ce00**[/COLOR]](http://www.torrentz.com/60d5d82328b4547511fdeac9bf4d0112daa0ce00)

Google also indexes torrent files and provide a method for searching them, through the filetype method like below:

[**ubuntu filetype:torrent**](http://www.google.com.br/search?q=ubuntu+filetype%3Atorrent)

Keep in mind that is always a good idea to browse torrent directories for additional info, to avoid fake files, which might contain malware or undesirable content. The torrent protocol is much more secure than other file sharing networks, but is not immune to people with bad intentions. For example, browsing the [Torrentz link](http://www.torrentz.com/60d5d82328b4547511fdeac9bf4d0112daa0ce00) above clearly reveals that the Ubuntu file is tracked by Canonical, due to the presence of tracker address **[COLOR="DarkRed"]torrent.ubuntu.com[/COLOR]**. So you know that file is distributed by a trusted and official source, thus is not a fake, does not contain malicious code and it's a legal file. Nevertheless, is also essential to [check the final download hash](https://help.ubuntu.com/community/UbuntuHashes) against the the one provided by the content distributor, no matter if you download directly from their site via HTTP or using BitTorrent.


**[size="5"][color=#CC0000]3. Download Speeds[/color][/size]**

[color=#CC0000][SIZE="3"]Closed Port[/SIZE][/color]

The first thing most users suggest when questioned about connection issues is that the torrent [port](http://en.wikipedia.org/wiki/Computer_port_%28software%29) is not properly configured in the client or it is closed by the router/firewall. While a closed port will usually result in lower download speeds, it doesn't prevent you from connecting to some peers, downloading and uploading. Nevertheless is not recommended and impolite to join a swarm with closed ports.

The port configured in the BitTorrent client is used only for incoming **[COLOR="DarkRed"]unrequested[/COLOR]** connections. So even if it is closed, your client will still be able to request connections to other peers, but won't get any requests from them. Once the connection is established by your request, the data transfer between your client and the connected peer is always allowed. This means a closed port only reduces the number of connected peers. This happens because each peer has a limited number of possible simultaneous connections, so they will not accept your connection requests all the time, but they might try to connect to you when they have a connection slot available. So, having the port opened and properly configured will increase the number of connected peers.

Please notice that the number of connected peers does not means that they will all be uploading to you at the same time. Your client connects to a large amount of peers and keep sending them requests for content pieces. The peer being requested might not have a free upload slot at the time of request, so the client tries another connected peer. So as general rule, the more peers you can connect, bigger will be your chances of getting more file pieces at the same time and thus your download speed will be higher. 

[color=#CC0000][SIZE="3"]Bandwidth Limit[/SIZE][/color]

One of the most common misconceptions about download speeds is related to the wrong assumption that the connection speed advertised by your ISP is what you should see in the torrent client. For example, my DSL plan has a maximum download speed of 4 Mbps, which is advertised as "4 Mega Plan". Well this speed is not actually what I see in the torrent client, which uses another measurement, named KiB/s. To check my maximum download speed, I need to convert what is advertised from Mbps to KiB/s. So my maximum download speed is actually 488.28 KiB/s.

[LIST]
[*]Test your bandwidth at [http://www.speedtest.net](http://www.speedtest.net)
[*]You can find a bandwidth conversion tool [here](http://web.forret.com/tools/bandwidth.asp).
[/LIST]

Additionally to that limitation, there is the fact that BitTorrent protocol works in a way that the more you give, the more you get. After all, is called file sharing, not file [leeching](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Leech). This means that even considering that I have 488.28 KiB/s maximum download speed, I rarely reach that value when downloading torrents, because my upload limit is only 74 KiB/s, which will also influence my download speed.

[color=#CC0000][SIZE="3"]Tracker Health[/SIZE][/color]

As you already know, if you followed this tutorial from the beginning, that a [tracker](http://en.wikipedia.org/wiki/BitTorrent_tracker) is responsible for listing all peers sharing a particular torrent content. They are almost essential to let you connect to peers for downloading a torrent content.

Sometimes the tracker for a particular torrent file can list just a few peers, while another tracker has hundreds of them. This happens because some trackers are more popular than others and the same torrent file can be uploaded to different sites using different trackers. 

There is also the possibility that you can't even connect to the tracker. In this case, you won't be able to retrieve the list of peers sharing the content and thus won't be able to download. Nevertheless, there is a technology on most modern BitTorrent clients, called [DHT](http://en.wikipedia.org/wiki/Distributed_hash_table), that allows to find peers without a tracker server. This is particularly useful if the tracker is temporarily offline, which has been very common recently due to torrent related legal battles. Torrent trackers also go offline permanently, since it's no cheap to maintain a popular tracker. 

The situations above can be fixed by simply replacing a tracker specified in the torrent file with one that is currently active and listing a decent number of peers. Torrent search engines like [Torrentz.com](http://en.wikipedia.org/wiki/Torrentz), provides a list of active trackers for each torrent and the corresponding number of peers and seeders, so you can easily replace a bad tracker with a new one, full of seeders.

Fortunately, most BitTorrent clients allows to edit the trackers from a torrent file and also add multiple trackers. So if the client can't connect to the first tracker listed, it will try another one from the list until it can connect or the connection request times-out.

Another technology available in modern BitTorrent clients, called "Peer Exchange (PEX), can also help to increase the number of connected peers. It basically allow you to connect to a peer not listed on the tracker you are using, but that is connected to another peer on it through another tracker. PEX basically connects peers from different trackers, as long as the share a peer in common. 

PEX and DHT are the reasons why sometimes your torrent client reports a lot more connected peers than the total number of peers in the swarm.

[color=#CC0000][SIZE="3"]Torrent Health[/SIZE][/color]

One of the most important aspects of a torrent health is the seeder/peer ratio, which is basically the number of peers with 100% of a given torrent content, divided by the number of those with incomplete content. The bigger the ratio, the better can be your download speed, because the seeders are just uploading and not draining resources from the swarm. Let's say I join a swarm with 500 seeders and 100 peers, in which case there will be 5 uploaders for each downloader. This probably means that I will connect to some peers that will be uploading to me at full capacity, since there are enough uploaders to upload to the other 99 peers. A good ratio is at least 1:1, but 2:1 or higher are very desirable. 

A healthy torrent is not just one with a good seeder/peer ratio, but also one with a big swarm (total number of peers + seeders). Some popular torrents can have more than 50.000 peers simultaneously, but as far as I know there is no limit. Anyway, sometimes a torrent becomes virtually dead, even with hundreds of peers in the swarm. This happens when there is no more seeders in the swarm and combining all pieces of the content from all peers in the swarm you still can't complete 100% of the desired content. 

In a situation like that, you will usually see lots of peers with 99% of the file, but none with 100%, because a single piece could be missing from all of them. So unless a seeder joins this swarm, nobody will be able to complete the download. This situation can happen because a lot of people simply download the contents of the torrent and stop after completing the file. They do not keep uploading (seeding) to others that still don't have the entire file. This kind of impolite behavior is called [leeching](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Leech) and it's definitely not good for the torrent community. It is recommended that you seed at least the same amount of pieces you have downloaded, which can be verified in BitTorrent client as "Share Ratio". A desired ratio is above 1. A ratio of 0.5 means you half uploaded half of the amount of pieces you have downloaded.

> **[COLOR="DarkRed"]Note:[/COLOR]** If you are downloading videos, then most of the video players are still able to play incomplete files, so sometimes is better to leave the swarm instead of waiting for that last piece.

Sometimes the torrent simply die because of lack of interest. A dead torrent happens when there are no seeders or peers in the swarm. Unlike a game server or chat room, in which you can join and wait for another peer to join, torrents without peers are pretty much dead. The chances of finding some peers and actually downloading with decent speeds are extremely low. Nevertheless, sometimes you can find a few peers using a different tracker. 

Keep in mind that some torrent directories list the number of peers in each swarm, but they do not update that info very often, so you need to check when this value was updated, before downloading the torrent. Otherwise, you might find out that actually there are no peers sharing it when loading the torrent into the BitTorrent client.

[color=#CC0000][SIZE="3"]Other Factors[/SIZE][/color]

There are several other factors that influence the download speed of BitTorrent content. It's not an exact science, but with time you gain experience and learn how to tweak your torrent client, to identify the best torrents and how to avoid bad swarms. For example, these are some other factors that can influence your download speed:

[list]
[*] the bandwidth upload limit of those peers you are downloading from
[*] the the number of peers also downloading from those you are downloading from
[*] the number of torrents being uploaded by those you are downloading from[/list]

For example, let's say you are downloading from me and 5 other peers. I have an upload limit of 74 KiB/s. But I'm also uploading to other 4 peers. So instead of getting 74 KiB/s from me, you only get about 18.5 KiB/s, if I upload to all peers at the same proportion. Let's say all other 5 peers you are downloading from have the same upload rate, so you will get only 92.5 KiB/s total. That is a scenario considering that I have only one active torrent, but if I'm sharing more than one torrent at the same time, then my upload speed to you will be even smaller. So as a general rule, the less torrents you share at the same time, better will be your upload and download speed for each torrent.

Most BitTorrent clients like Deluge allows to control how many upload slots for each torrent you will use, how many torrents will be active at the same time, how many will be seeding or downloading and also how many peers you can connect at the same time. 



**[size="5"][color=#CC0000]4. Configurations[/color][/size]**

As already explained, we need to open a port so other peers can request connections to your BitTorrent client. If you have a router, then this is the first place to start with. If not, then proceed to the Firewall and Client Configuration topics.

[color=#CC0000][SIZE="4"]**Router Configuration**[/SIZE][/color]

To open a port in the router you will have to forward the port or port range used by the BitTorrent client to your machine. If you don't do that, all connections attempts from remote peers reaching your router won't pass through it, even if you have only one computer in your local network. This happens because all connections to all computers on your local network reach the same router, so it needs to know if the connection on a specific port should pass through and to which machine the connection should be forwarded or they will be ignored. 

Keep in mind that a closed port in the router does not prevent you from downloading, because it only affects incoming **[COLOR="DarkRed"]unrequested[/COLOR]** connections. All torrent file pieces related to connections already established by your client will pass through as expected, even with a closed port, because the router is "clever" enough to know that they belong to a connection requested by the BitTorrent client on your machine.

So, the first step is to decide which port or port range to use. The standard port range for BitTorrent traffic is 6881 to 6889. But that doesn't mean you have to use it. In fact is not even recommended, because some Internet Service Providers throttle the traffic on those ports, exactly because they are used for BitTorrent. 

> **[COLOR="Red"]Warning:[/COLOR]** you should consult your ISP contract to see if there are any restrictions related to BitTorrent usage and incoming ports. If not, then you can safely use a different port or port range, because they do not have the rights to throttle your connection if this not specified in the contract.

It is recommended to use any single port or port range between 49152 and 65535, but it should not be in use by another server in your machine. To check if there are any ports being used, run the following command in a terminal:

```
netstat -plntu
```

Most modern routers and BitTorrent clients offers an automatic method of port-forwarding, called [UPnP](http://en.wikipedia.org/wiki/UPnP). All you have to do is enable UPnP on the router and the BitTorrent client and configure the ports you want to use in the client. There are some security risks involved in this method, like a for example a malicious web site gaining access to your router settings and redirecting web pages you visit to phishing sites. So some people prefer to forward the ports manually as explained below.

To manually forward the port from the router you also will need to know the internal IP address of your machine. To do that, run the following command in a terminal and look for the IP value next to **inet addr:** in the results. It should be something like **192.168.x.x**.

```
ifconfig
```

> **[COLOR="DarkRed"]Note:[/COLOR]** it is recommended to use static internal IP if you have more than one computer on your local network. You can do that from the Network Manager. Basically a static IP means that every time you connect to the router you will get the same IP, even if another computer is already connected to it or not. You need to configure a static IP for each computer in your local network.

Once you have your internal IP address and have chosen a port or port range to forward, then visit your router settings page to proceed with the port forwarding. There are too many router models, so this will not be explained here, but you can get specific instructions for your router model at [http://portforward.com](http://portforward.com)


[color=#CC0000][SIZE="4"]**Firewall Configuration**[/SIZE][/color]

If you have firewall rules enabled, then you also need to open the port in the firewall for incoming connections. You should allow all incoming connections on the port or port range selected to be used by the BitTorrent client. Additionally, you need to allow incoming traffic on the [loopback device](http://en.wikipedia.org/wiki/Loopback#Virtual_network_interface).

Deluge has a [daemon](http://en.wikipedia.org/wiki/Daemon_%28computer_software%29) and a [frontend](http://en.wikipedia.org/wiki/Frontend), that allows you to connect remotely from any client machine. On a default standalone installation, Deluge launches the daemon and connects with the frontend automatically, through the [loopback device](http://en.wikipedia.org/wiki/Loopback#Virtual_network_interface), so you don't even notice the separation. It uses port 58846 by default and another random port, both listening on the default loopback address, 127.0.0.1. If you start Deluge and it shows a blank interface, is probably due to blocked connections on those ports. 

Additionally, if you use UPnP, then you need to allow incoming traffic from the IP address of your router on port 1900.

In regard to outgoing connections, you should allow all traffic, since Deluge will use random ports for requesting connections to other peers. Gufw firewall manager does not even allow you to block outgoing connections, which is perfectly normal. Nevertheless, if you use Firestarter or creates your own iptables rules, then you might have to create a rule to allow all outgoing connections.

If you don't have any firewall rules enabled or don't know if you have, then probably there isn't anything else to do in regard to the firewall. Ubuntu comes with a firewall installed and running by default, but it has no rules, because there is no need to block traffic, since Ubuntu also comes without any server running. This means all traffic will reach your computer on any port, but all ports are virtually closed because there aren't any applications listening to incoming connections (server) on any of them. When you run a BitTorrent client, which is a server, it will use the port or port range as expected, because the firewall won't block them. To decide if you need a firewalled BitTorrent connection or not, read the Security section.


[color=#CC0000][SIZE="4"]**Client Configuration**[/SIZE][/color]

[color=#CC0000][SIZE="3"]Network Settings: incoming ports[/SIZE][/color]

Opening the ports on Deluge is pretty simple, no matter if you have a router or not and if you are using UPnP or not. To do that open Deluge and select "Edit >> Preferences" from the menu. Then select the "Network" category. 

If you do not have a router or are using the UPnP method, then select the option "Use random ports" in the "Incoming Ports" configuration. Enable the UPnP option in the "Network Extras" if you have a router with UPnP enabled. You can also use a port range when enabling UPnP, then you can have more control over which ports will be chosen every time you start Deluge. Please notice that only one port is chosen from the range on every start.

> **[COLOR="DarkRed"]Note:[/COLOR]** if you have firewall rules, then do not use random ports. You need to specify the same port or port range allowed in your firewall.


If you are forwarding the port from your router manually or if you have firewall rules, then you need to specify the port range in the "Incoming Ports" configuration. If you decided to use a single port instead of a range, which I prefer, then put the same value in both fields. Also leave the option "Use random ports" unticked.

To test if the port is properly forwarded and configured in the client, see section [COLOR="DarkRed"]**7.2 Troubleshooting Ports**[/COLOR].


[color=#CC0000][SIZE="3"]Other Network Settings[/SIZE][/color]

Outgoing Ports - although Deluge also offers an option to configure the Outgoing Ports, usually there is no need to do it, unless you have very restrictive outgoing firewall rules and need a specific range. So leave the option "Use random ports" enabled for outgoing connections.

For TOS option visit [this discussion](http://ubuntuforums.org/showthread.php?p=7694210), but you should be fine with the default value. 

NAT-PMP is another method of automatic port-forwarding used with routers that support the NAT port mapping protocol (Apple products, for example). You can leave it unticked if you are using UPnP or manual forwarding.

LSD - can be used to connect to peers on your local network

DHT and PEX - see the Download Speeds section for explanations

Encryption - there are a lot misconceptions about what the encryption options do. Some people believe it helps to hide your identity. That's not true. The encryption simple makes hard for a third-party (aka your ISP) to detect the type of traffic generated by your BitTorrent application, in order to throttle your torrent speed. 

> **[COLOR="Red"]Warning:[/COLOR]** you need to check if there are any restrictions related to BitTorrent traffic in your ISP contract. If not, then is safe to use encryption to avoid [traffic shaping](http://en.wikipedia.org/wiki/Traffic_shaping), because if it is not in the contract, then they don't have the rights to slow you down.

For the encryption options I recommend using **[COLOR="DarkRed"]Forced[/COLOR]** for both "Inbound" and "Outbound" traffic, **[COLOR="DarkRed"]Full Stream[/COLOR]** for the "Level" and tick "Encrypt entire stream". This way you will have the highest level of encryption possible. Keep in mind that if a peer trying to connect to you does not have encryption enabled or his BitTorrent client it's not compatible with encryption, then it's connection requests will be rejected. This could eventually prevent you from connecting to any peers on very small swarms. Nevertheless, most modern clients are indeed compatible and most people use encryption, so you should be fine most of the time. 

[color=#CC0000][SIZE="3"]Bandwidth Settings[/SIZE][/color]

The bandwidth settings allow you to tweak Deluge in order to maximize the download speed. First check your bandwidth limits at [http://www.speedtest.net](http://www.speedtest.net). If you need to convert your speed, than change the settings for the reports or use a conversion tool [from here](http://web.forret.com/tools/bandwidth.asp)

According to Deluge FAQ, you should start with these settings:

> Maximum Connections: **[COLOR="DarkRed"]200[/COLOR]**
Maximum Download Speed (Kib/s): [COLOR="DarkRed"]**-1**[/COLOR]
Maximum Upload Speed (Kib/s):	**[COLOR="DarkRed"]80% of upload speed limit of your bandwidth[/COLOR]**
Maximum Upload Slots: **[COLOR="DarkRed"]4[/COLOR]**
Maximum Half-Open Connections: [COLOR="DarkRed"]**-1**[/COLOR]
Maximum Connection Attempts per Second: **[COLOR="DarkRed"]20[/COLOR]**

**[COLOR="DarkRed"]Maximum Connections[/COLOR]** is the maximum number of peers Deluge will be able to connect at the same time. Please keep in mind that this not represents all peers actively uploading to you, because after the establishment of the connection with another peer, the client still needs to request file pieces. Since everyone  has a limited upload bandwidth, they also limit the number of **[COLOR="DarkRed"]Maximum Upload Slots[/COLOR]**. This means that, if everyone followed the recommendations above, each peer would be capable of uploading to another 4 peers at the same time (4 upload slots). So most of the peers among those 200 connections will be connected to you but not uploading. Most of the time, the peers that are actively uploading to you keeps changing, so having a lot of peers connected will maximize the number of active downloading connections. Nevertheless, you should exaggerate with these settings, otherwise you could end up clogging your network and actually reducing your download speed. Some experimenting is required. I use 150, but I usually do not have more than 2 torrents active at the same time and only increase to 250 when both are being downloaded.

The [COLOR="DarkRed"]**Maximum Download Speed**[/COLOR] set as [COLOR="DarkRed"]**-1**[/COLOR] means no limit. I use that setting and never have  issues, but it could slow down your regular network activity, like web browsing. If you experience this kind of issue, then put a value a little bit lower than the download speed limit of your bandwidth, like 95% of it.

[COLOR="DarkRed"]**Maximum Upload Speed**[/COLOR] should be about 80% of the upload speed limit of your bandwidth, otherwise it will clog you network and reduce your download speed.

[COLOR="DarkRed"]**Maximum Upload Slots**[/COLOR] also depends on the upload speed limit of your bandwidth. There are some formulas to calculate this value like "1 + ( upload speed / 6)" but I prefer to use common sense. Consider a value that will give at least a good fraction of your bandwidth to each peer you upload simultaneously. If you have 50 KiB/s upload limit, then use 5 upload slots, so each peer could get about 10KiB/s (if you upload at the same rate to all of them). If you use 50 slots in this scenario, then the upload speed for each peer will be extremely reduced.

[COLOR="DarkRed"]**Maximum Half-Open Connections**[/COLOR] and [COLOR="DarkRed"]**Maximum Connection Attempts per Second**[/COLOR] determine the outbound concurrent connection attempts. If you use unlimited value (-1) for the first one as suggested, then you should be conservative with the second value, since too many half-open connections could cause your router to restart or even block the network completely. I believe is better to limit the number of connection attempts per second, then reducing the half-open connections. This way, new attempt connections won't be put on hold if there are already too many half-open connections, but will avoid firing too many connections at the same time. The default suggested values should be enough, which in this case means it would take 10 seconds to try to connect to 200 peers.

[color=#CC0000][SIZE="3"]Per Torrent Bandwidth Usage[/SIZE][/color]

These settings allows to distribute the bandwidth between each torrent. If you have limited the number of active torrents to just one or two, then leave this unchanged. Otherwise, change the default values so each torrent gets a decent fraction of your bandwidth. 

Keep in mind that setting these values to lower than the global settings will limit your download/upload speeds, if you have just one active torrent or if you still do not reach your bandwidth limit, after combining the usage of all of them. So if you do not have several torrents active all the time, it might be a good idea to not limit the bandwidth on a per torrent basis.



**[size="5"][color=#CC0000]5. Security[/color][/size]**

Whenever you are connected to the outside world, you are prone to attacks. This is true  even for the most simple web browsing activities and also for peer-to-peer file sharing. Nevertheless, sharing files impose additional security issues. 

As already explained, the BitTorrent protocol is much more secure than other file sharing networks, because you do not grant anyone the rights to browse your folders. But a torrent client is essentially a server and thus will be listening to a port for incoming connections. This means anyone can connect to you without your request, as long as they are using a compatible BitTorrent client and sharing the same file through the same tracker. This is obviously wanted, to maximize the number of potential connections with other peers, since the download speed depends on being connected to several of them, as already explained in the Download Speed section. Nevertheless, some people might try to use this opened pathway to your computer to gain unauthorized access to other resources on your machine.

In a normal situation, the BitTorrent client will not allow any access to your computer other than transferring pieces of the file specified in the torrent metadata, between both connected peers. Nevertheless, security holes exists in any kind of software. So, if your torrent client has a security vulnerability, it could be used to gain access to other resources on your machine. Fortunately, there are lot's of people in the open source community that tries to find those flaws in applications and alert the community about possible risks. To minimize the risks you should always keep your system and torrent client updated with the latest patches.

Having an updated system is essential for any Internet activity, but does not guarantee your immunity, since an attacker could be exploiting a security flaw that hasn't been discovered or fixed by the application developers, which are known as "zero-day exploits". To protect your machine against "[zero-day attacks](http://en.wikipedia.org/wiki/Zero-Day_Attack)", you can use [Apparmor](http://en.wikipedia.org/wiki/Apparmor) to limit what resources and permissions are granted to your BitTorrent client, thus limiting what an attacker could do if he gains full control of your client. More about Apparmor at [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)


[size="3"][color=#CC0000]Firewall[/color][/size]

Do I need a firewall to protect my machine while sharing files? Probably not. Essentially, a firewall just limits the access to your machine from the outside world based on port number or the IP of the remote machine. But since you want to connect to the most number of peers you can, to maximize your download speed, it makes no sense to block access to your BitTorrent port by closing it with a firewall, otherwise other peers won't be able to request connections to your client and the number of peers connected to you will be reduced. Using a firewall to protect other ports not in use by the BitTorrent client or any other server is redundant, because a port without a listening service is essentially a closed port. As far as I know, there is no possibly way to breach your computer through a closed port.

If you have other servers running, like a ssh server for example, then you might want to use firewall rules to block connections from the outside world to the ssh port, while still allowing computers on your local network to connect. Nevertheless, if you have a router, you can do that through the router firewall, instead of your machine.


[size="3"][color=#CC0000]Blocklists[/color][/size]

Most torrent clients like Deluge and Transmission, offers a feature called blocklist plugin. It works like a p2p firewall, by rejecting connections coming from untrusted known IP addresses. These known bad IP addresses are collected by some users and organizations engaged in Internet security and distributed for free, as lists of IP ranges. There are several different types of blocklists, targeting specific threats, since they are not used only for p2p.

Although there is a lot of controversy about blocklists effectiveness, because IP addresses keep changing all the time and some publishers add more ranges than necessary, there are several well known addresses that you probably don't want to connect to you. Besides, you can customize these lists and create your own, which can be very useful.

There are also standalone applications that uses the same blocklists, called ip blockers. There are two of them for Ubuntu that I'm aware of, [moblock](http://moblock-deb.sourceforge.net/) and [iplist](http://iplist.sourceforge.net/). Although I prefer moblock, because it also handles my firewall rules, they both work very well. If you used PeerGuradian on Windows, then you probably will prefer iplist, because it has a very similar interface. Nevertheless, moblock can also be controlled with a [graphical interface](http://en.wikipedia.org/wiki/Graphical_interface) [frontend](http://en.wikipedia.org/wiki/Frontend) called [mobloquer](http://mobloquer.foutrelis.com/).

Standalone ip blockers are better than blocklist plugins, because they protect your entire network, by acting at the firewall level, not only the p2p connections. Nevertheless, there is nothing that could prevent you from using both. Most people consider this redundant, but I like for example to use different lists for p2p activity, so using both gives me more flexibility.

You can get several blocklists from [Bluetack](http://www.bluetack.co.uk) and [I-Blocklist](http://iblocklist.com), although all standalone ip blockers and BitTorrent blocklist plugins offers some sort of automatic download and update from these sources.

Keep in mind that more blocklists is not necessarily better. Some of those lists will block several valid peers and thus could reduce your download speeds considerably.


[size="3"][color=#CC0000]Fake files, malware and other threats[/color][/size]

Ubuntu has it's own trusted repositories of applications, that should be used as the preferred method of installation. Nevertheless, sometimes you want to download Ubuntu itself or other applications like games, that are also distributed via direct download or BitTorrent. No matter which method you use, whenever you are downloading applications from outside the repositories, you should always  [check the final file hash number](https://help.ubuntu.com/community/UbuntuHashes), to verify it's validity. Most publishers will offer hash numbers on their download site, so you can compare them with the one from your downloaded file.

Most torrent directories and search engines offers some sort of validation method, like marking torrents uploaded by trusted users or distributors. They also provide comment sections for each torrent, so you can read other users comments about the downloaded content. Fake files will be usually spotted pretty fast and moderators of some sites are very effective in cleaning up the junk. Some sites also provide a method of identifying copyrighted material and automatically removing them, so these sites are preferred to avoid legal issues. 

Nevertheless, there is always people with bad intentions uploading junk to BitTorrent sites. So use common sense and the site tools before downloading any torrent. For example, browsing [this Torrentz link](http://www.torrentz.com/60d5d82328b4547511fdeac9bf4d0112daa0ce00) clearly reveals that the Ubuntu file is tracked by Canonical, due to the presence of tracker address **[COLOR="DarkRed"]torrent.ubuntu.com[/COLOR]** and thus is an original file. 

[[IMG]http://img198.imageshack.us/img198/7822/ubuntu904desktopi386iso.th.png[/IMG]](http://img198.imageshack.us/i/ubuntu904desktopi386iso.png/)


For more information on security visit the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.



**[size="5"][color=#CC0000]6. FAQ[/color][/size]**


[IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG] [COLOR="DarkRed"]**My logs shows a lot of connection attempts after stopping a torrent or closing the BitTorrent client. Should I be worried?**[/COLOR]

When you close the BitTorrent client, you probably will keep receiving several connection attempts for a while. This is normal and they are called "ghost packets". This happens because trackers and BitTorrent clients do not update the list of peers sharing a particular torrent very often. As already explained in previous sections, your BitTorrent client [scrapes](http://en.wikipedia.org/wiki/BitTorrent_vocabulary#Scrape) the tracker to add your IP address, so other peers can connect to you. This procedure is done in a determined interval, which is the same used to retrieve the list of peers from it, so your client can connect to other peers. When you close your client, your IP number will still be listed in the tracker and other peers clients as sharing the file, therefore they will still try to connect to you, not knowing that your client is already closed.

There is nothing to worry about those connections attempts, because the are just BitTorrent connections and since your client is closed, your port is virtually closed too. So these connections will be ignored. Nevertheless, you can make them stop by simply restarting your router or modem.

Sometimes you get "ghost packets" even when you haven't used a BitTorrent client for a while. This can happen even if you just connected your modem or router and it's due to the way IP addresses are assigned. Most Internet Service Providers assign home users with a dynamic IP, which means you get a "new" IP address every time you connect to them. This IP is not actually "new", but it's part of an IP range available to the ISP, that is shared among all it's costumers. By shared, I don't mean you will be using the same IP as another dude simultaneously, but since most costumers are not connected at the same time, the ISP does not have a single IP for each one of them. Instead, they assign the first available IP when a someone connects. Sometimes you get an IP number that has been just released by someone else and if he was engaged on some Internet activity that rely on accepting incoming requests, like torrenting, then you will probably get his "ghost packets".



**[size="5"][color=#CC0000]7. Troubleshooting[/color][/size]**

Answer the questions below and follow their directions. These questions are designed to eliminate possible issues until only one is left.


[color=#CC0000][SIZE="4"]**7.1 Speed and connection issues**[/SIZE][/color]

[SIZE="3"]**[COLOR="DarkRed"]#1[/COLOR] Are you able to download?**[/SIZE]

[LIST]
[*]If the answer is "YES, I can download, but the speed is slow": proceed to question [COLOR="DarkRed"]**#2**[/COLOR].
[*]If the answer is "NO, I can't download anything": skip to question [COLOR="DarkRed"]**#9**[/COLOR].
[/LIST]

[SIZE="3"]**[COLOR="DarkRed"]#2[/COLOR] Does the torrent has dozens or hundreds peers?**[/SIZE]

[LIST]
[*]If the answer is YES: proceed to question **[COLOR="DarkRed"]#3[/COLOR]**.
[*]If the answer is NO: check the [COLOR="DarkRed"]Torrent Health[/COLOR] topic on the [COLOR="DarkRed"]**Download Speeds**[/COLOR] section.
[/LIST]

[SIZE="3"]**[COLOR="DarkRed"]#3[/COLOR] Does the client connects to dozens or hundreds of peers but the speed is slow?**[/SIZE]

[LIST]
[*]If the answer is "YES, there are lots of connected peers, but the speed is slow": skip to question [COLOR="DarkRed"]**#6**[/COLOR].
[*]If the answer is "NO, the client connects only to a few peers": proceed to question **[COLOR="DarkRed"]#4[/COLOR]**.
[/LIST]

[SIZE="3"]**[COLOR="DarkRed"]#4[/COLOR] Is the incoming port used by the BitTorrent client properly opened?**[/SIZE]

[LIST]
[*]If the answer is "I don't know how to open ports": refer to the [COLOR="DarkRed"]**Configurations**[/COLOR] section to learn how to do it.
[*]If the answer is "I have opened it, but I'm not sure if it is working": check the section [COLOR="DarkRed"]**7.2 Troubleshooting Ports**[/COLOR].
[*]If the answer is "YES, I have already tested it": proceed to question **[COLOR="DarkRed"]#5[/COLOR]**.
[/LIST]

[SIZE="3"]**[COLOR="DarkRed"]#5[/COLOR] Are you using blocklists plugins or standalone ip blockers?**[/SIZE]

[LIST]
[*]If the answer is "YES": check the blocked IP log to see if there are too many entries. You might be blocking too many IP ranges, that could be preventing you to connect to most peers.
[*]If the answer is "NO, I'm not using such a thing": check the [COLOR="DarkRed"]**Bandwidth Settings**[/COLOR] section of the tutorial. Your client settings might be limiting the number of allowed connected peers. Also try to disable encryption, to see if the number of connected peers improve.
[/LIST]

[SIZE="3"]**[COLOR="DarkRed"]#6[/COLOR] Does the torrent has a good seeder/peer ratio?**[/SIZE]

[LIST]
[*]If the answer is "I have no idea": check the [COLOR="DarkRed"]Torrent Health[/COLOR] topic in the [COLOR="DarkRed"]**Download Speeds**[/COLOR] section.
[*]If the answer is "NO, the ratio is lower than 1:1": try another tracker or another torrent with more seeders, or give some time to build up speed. It's normal to experience slower speeds when the number of peers is higher than the number of seeders.
[*]If the answer is "YES, the ratio is 1:1 or higher": proceed to question **[COLOR="DarkRed"]#7[/COLOR]**.
[/LIST]

[SIZE="3"]**[COLOR="DarkRed"]#7[/COLOR] Are you using standard BitTorrent ports (6881-6889)?**[/SIZE]

[LIST]
[*]If the answer is "YES": your ISP might be throttling your connection on the specified port. Try to change the torrent port to any port in the range 49152 to 65535.
[*]If the answer is "NO, I use a different port or port range": proceed to question **[COLOR="DarkRed"]#8[/COLOR]**
[/LIST]

[SIZE="3"]**[COLOR="DarkRed"]#8[/COLOR] Have you checked if your Internet connection speed is normal?**[/SIZE]

[LIST]
[*]If the answer is "I don't know how to do that": visit [http://www.speedtest.net](http://www.speedtest.net)
[*]If the answer is "YES, the connection is fine": try downloading another torrent from a reliable tracker, like [official Ubuntu torrents](http://www.ubuntu.com/getubuntu/downloadmirrors#bt), to see if it behaves the same way. If it does, then your ISP might be slowing you down according to protocol or time of day. You could try to enable full encryption or download another time to see if the speed improves.
[/LIST]

[SIZE="3"]**[COLOR="DarkRed"]#9[/COLOR] Does the client connect to any peers?**[/SIZE]

[LIST]
[*]If the answer is "NO": proceed to question [COLOR="DarkRed"]**#10**[/COLOR] 
[*]If the answer is "YES, but nothing happens": go back to question **[COLOR="DarkRed"]#6[/COLOR]**.
[/LIST]

[SIZE="3"]**[COLOR="DarkRed"]#10[/COLOR] Do you have active firewall rules?**[/SIZE]

[LIST]
[*]If the answer is "NO": it's probably a tracker issue, so check the [COLOR="DarkRed"]Tracker Health[/COLOR] topic in the [COLOR="DarkRed"]**Download Speeds**[/COLOR] section.
[*]If the answer is "YES": check if you have allowed all outgoing connections in the firewall manager. Refer to the **[COLOR="DarkRed"]Firewall Configuration[/COLOR]** section for further instructions.
[/LIST]


**[size="4"][color=#CC0000]7.2 Troubleshooting Ports[/color][/size]**

Deluge and most BitTorrent clients offers a method of checking if the configured incoming port is open or not. But this method relies on sending a request to the developers site and waiting for a remote scan. So if the developer site is not responding, Deluge could tell you the port is closed, when in fact it could be opened. Besides, it doesn't give you any additional info, so it's hard to troubleshoot using this kind of tool.

To test if the port forwarding is working properly and if your client is properly configured follow these steps:

1 - Open Deluge client and check which port it is using for incoming requests. To do that, go to "Edit >> Preferences >> Network" and check the value after "**Active Port:**", in the "Incoming Ports" section. 
2 - Go to [http://canyouseeme.org](http://canyouseeme.org) and put the port number in the form, after "What Port?" and click "Check".

**Possible results, explanations and solutions:**

> Error: I could not see your service on **xxx.xx.xx.xxx** on port (**xxxx**)
Reason: [COLOR="DarkRed"]**Connection timed out**[/COLOR]

The port is stealth. It means the connections are dropped (ignored) before reaching the BitTorrent client. Check your router and firewall settings/log.

[list][*] If the firewall log shows an entry for the test scan, then you need to open the port with a new firewall rule or disable the firewall. 
[*] If the test scan is not logged by the firewall, then the problem is probably in the router port forwarding settings or your ISP is blocking the connection on the selected port. If you use UPnP, don't forget to allow incoming traffic from your router IP address on port 1900, otherwise the automatic port-forwarding might fail.
[*] [/list]

> Error: I could not see your service on **xxx.xx.xx.xxx** on port (**xxxx**)
[COLOR="DarkRed"]**Reason: Connection refused**[/COLOR]

The port is closed. This means the client is not accepting connections on that port or the firewall is rejecting the connection attempts. Check your client port configuration and make sure the firewall has a rule to allow inbound tcp (also udp if you use DHT) connections on the selected port. Temporarily disabled the firewall completely might help to troubleshoot.

> Success: I can see your service on **xxx.xx.xx.xxx** on port (**xxxx**)
Your ISP is not blocking port **xxxx**

The port is open, which means it is properly forwarded by the router, the firewall is not dropping or rejecting connection attempts and the client is properly configured. Additionally, your ISP is not blocking connections on the port. 




**[size="5"][color=#CC0000]8. References[/color][/size]**

[LIST]
[*][BitTorrent vocabulary](http://en.wikipedia.org/wiki/BitTorrent_vocabulary)
[*][Comparison of BitTorrent clients](http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_software)
[*][Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421)
[*][Deluge FAQ](http://dev.deluge-torrent.org/wiki/Faq)
[*][General Moblock Thread](http://ubuntuforums.org/showthread.php?t=803183)
[/LIST]

---

### Post by careertargetph on 2009-09-08
Nice instructions. I'm using this software Bittorrent for downloading some movies and softwares. This is the first I encountered such optimization, but I can do this in the future.

---

### Post by lovinglinux on 2009-09-08
> **careertargetph said:**
> Nice instructions. I'm using this software Bittorrent for downloading some movies and softwares. This is the first I encountered such optimization, but I can do this in the future.

Thanks. Keep in mind that it's not finished yet. I'm still writing it.

---

### Post by lovinglinux on 2009-09-08
Thanks to the moderators for fixing the typo on the title and moving it to the Tutorial & Tips forum.

---

### Post by lovinglinux on 2009-09-13
I think the tutorial is ready. Any feedback will be much appreciated.

If you still have issues after reading the tutorial and following the troubleshooting section, then post a description of your issue, so I can analyze your situation. Please also provide which steps you took to troubleshoot.

---

### Post by brookie on 2009-09-18
Thanks for the explanations. I'm sure this will help lots of users. However, I have one question that was not addressed and can't seem to find any information on it anywhere. 

I use Deluge and have one port dedicated to torrenting. The same port is open on my router and in my gufw/ufw firewall rules. I am also using the Deluge IP block list. 

When I start Deluge the IP block list loads and then I watch /var/log/messages: UFW immediately starts blocking incomming connections to random ports.

I have no torrent loaded, I have deleted all .torrent files, and have restarted cable modem and router before this test. These incomming hits will continue until I restart the computer and/or network. 

I read the information about ghost packettes but there should be no ghost packettes since I had no torrent loaded in my Deluge. Are these ghost packets from the last time I downloaded a torrent? 

I can't figure this one out. 

Cheers, 
brook

ps after more testing the only way to stop the incoming hits is to turn off the cable modem, routers, machine, restart the network, then restart the machine. the hits are coming into ports other than the designated open port in deluge and firewall, thus being blocked by firewall.

---

### Post by lovinglinux on 2009-09-18
> **brookie said:**
> I use Deluge and have one port dedicated to torrenting. The same port is open on my router and in my gufw/ufw firewall rules. I am also using the Deluge IP block list. 

When I start Deluge the IP block list loads and then I watch /var/log/messages: UFW immediately starts blocking incomming connections to random ports.

I have no torrent loaded, I have deleted all .torrent files, and have restarted cable modem and router before this test. These incomming hits will continue until I restart the computer and/or network.

Since your router is only allowing incoming traffic on one port and you don't have any torrent loaded, these connections must be internal traffic on the loopback device. Deluge has a daemon and a frontend, that allows you to connect remotely from any client machine. But on a default standalone installation, Deluge launches the daemon and connects with the frontend automatically, so you don't even notice the separation. Nevertheless, it still uses the local network to do that.

So, After starting Deluge, open a terminal and run this command:

```
netstat -plntu
```

You will see something like this:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:52715         0.0.0.0:*               LISTEN      23142/python    
tcp        0      0 0.0.0.0:54194           0.0.0.0:*               LISTEN      23122/python    
tcp        0      0 127.0.0.1:58846         0.0.0.0:*               LISTEN      23122/python    
tcp6       0      0 :::54194                :::*                    LISTEN      23122/python
udp       0      0 0.0.0.0:1900               0.0.0.0:*            LISTEN      23122/python 
```   

Port #58846 is the default port for connecting the frontend to the daemon. This can be changed in the "Daemon" settings, although I do not recommend. In the example above, port #54194 is the one I choose for incoming torrent connections, so it's the one forwarded in the router. Port #52715 is also used by Deluge internal traffic. This port s random and changes on every start. Port #1900 is used for communication with the router and is related to UPnP. It only shows up if you have UPnP enabled.

So after doing that, check if the firewall blocked connections are incoming on those ports. 

To fix this you will have to enable traffic on the loopback device. If you use UPnP, then you need to allow incoming connections from your router IP address on port 1900.

BTW, I totally forgot about these settings, but I have already edited the Firewall configuration section to include this info. Thanks for reminding me.

---

### Post by brookie on 2009-09-19
Thanks for the reply lovinglinux. :-) 

I got Deluge bandwidth settings tuned in a little better according to your tutorial and will test later. I figured out what the UFW block messages were in my logs as well. 

I upgraded gufw to version 0.20.7 which has an option to add a service or program on the preconfigured tab. It looks for installed programs and it saw deluge. I added it and it only added my deluge port for TCP but not UDP. Therefore, UFW was blocking all UDP attempts for my Deluge opened port. 

Once I added my deluge port for UDP as well as TCP all the blocks stopped. I guess UFW has been blocking the ghost packets on UDP when I opened it with no torrent present. I originally got the UDP/TCP firewall info from the uTorrent forums when I was using windows and uTorrent. By the way, this is not in your tutorial so I don't know if you want to add it or not. :confused:

After adding UDP for my Deluge port the block attempts are gone from my logs, so it seems that these are ghost packets since I have no torrents loaded in Deluge at the moment and I deleted the .torrent files after seeding. 

One more thing, I adjusted my bandwidth settings under Global Bandwidth Usage and just noticed that there are also Per Torrent Bandwidth Usage. More settings to tinker with. 

Also, Speedtest.net has a cool settings in the upper left hand corner where you can select kilobits, kilobytes, megabits, megabytes for measurement so no need to convert. I assume that using kilobytes for the measurement is the same as the deluge setting for KiB/s.


From Speedtest.net: 
Avg. DL Speed = 7.65 Mb/s = 933.84 KiB/s
Avg. UL Speed = 3.03 Mb/s = 378.4 KiB/s

My Deluge bandwidth Settings: 
**Global Bandwidth Usage:**
Maximum Connections:                                    200
Maximum Upload Slots:                                    30
Maximum Download Speed (KiB/s):                 -1
Maximum Upload Speed (KiB/s):                      302, (378.4 KiB/s x 80% = 302.72)
Maximum Half-Open Connections:                    50
Maximum Connection Attempts per Second:    20

Ignore limits on local network, checked
Rate limit IP overhead, checked

**Per Torrent Bandwidth Usage:**
Maximum Connections:                           -1
Maximum Upload Slots:                           -1
Maximum Download Speed (KiB/s):        -1
Maximum Upload Speed (KiB/s):             50

Deluge default settings here:
[http://dev.deluge-torrent.org/wiki/Faq#HowdoIrestoreallsettingstodefault](http://dev.deluge-torrent.org/wiki/Faq#HowdoIrestoreallsettingstodefault) 

Have a great weekend! 
Cheers,
brookie

---

### Post by lovinglinux on 2009-09-19
> **brookie said:**
> Once I added my deluge port for UDP as well as TCP all the blocks stopped. I guess UFW has been blocking the ghost packets on UDP when I opened it with no torrent present. I originally got the UDP/TCP firewall info from the uTorrent forums when I was using windows and uTorrent. By the way, this is not in your tutorial so I don't know if you want to add it or not. :confused:

The UDP connections only appear if you use DHT. In the tutorial I say that you should allow all connections in the incoming port, which means tcp and udp. Perhaps I should be more specific about this.

> **brookie said:**
> Also, Speedtest.net has a cool settings in the upper left hand corner where you can select kilobits, kilobytes, megabits, megabytes for measurement so no need to convert. I assume that using kilobytes for the measurement is the same as the deluge setting for KiB/s.

Yep, you are correct. I guess I wasn't clear enough about the possibility of changing the settings on speedtest.net. Nevertheless, I think it is interesting to provide a converter.


> **brookie said:**
> One more thing, I adjusted my bandwidth settings under Global Bandwidth Usage and just noticed that there are also Per Torrent Bandwidth Usage. More settings to tinker with. 

Yep, there are already instructions about them in the tutorial.

> **brookie said:**
> 

From Speedtest.net: 
Avg. DL Speed = 7.65 Mb/s = 933.84 KiB/s
Avg. UL Speed = 3.03 Mb/s = 378.4 KiB/s

My Deluge bandwidth Settings: 
**Global Bandwidth Usage:**
Maximum Connections:                                    200
Maximum Upload Slots:                                    30
Maximum Download Speed (KiB/s):                 -1
Maximum Upload Speed (KiB/s):                      302, (378.4 KiB/s x 80% = 302.72)
Maximum Half-Open Connections:                    50
Maximum Connection Attempts per Second:    20

Ignore limits on local network, checked
Rate limit IP overhead, checked

**Per Torrent Bandwidth Usage:**
Maximum Connections:                           -1
Maximum Upload Slots:                           -1
Maximum Download Speed (KiB/s):        -1
Maximum Upload Speed (KiB/s):             50

Deluge default settings here:
[http://dev.deluge-torrent.org/wiki/Faq#HowdoIrestoreallsettingstodefault](http://dev.deluge-torrent.org/wiki/Faq#HowdoIrestoreallsettingstodefault) 

Have a great weekend! 
Cheers,
brookie

Your settings look fine to me.

---

### Post by lovinglinux on 2009-10-09
I have decided to give Ktorrent a try and I'm quite impressed. I guess it will be my default BitTorrent client for now.

---

### Post by lovinglinux on 2009-10-09
> **KaranMetha said:**
> Hey man, Thanks for sharing, I was searching for BitTorrent optimizationguide and when I have goolged, I got this page, then I have checked other threads too, it seems the forums is very useful to me, So, I just joined here.. :D Thxs again for this.

You are welcome. I'm glad it's helping.

---

### Post by tommcd on 2009-10-24
Very nice tutorial. It is about as comprehensive as anyone could possibly ask for. Thanks for taking the time to write it.

---

### Post by lovinglinux on 2009-10-24
> **tommcd said:**
> Very nice tutorial. It is about as comprehensive as anyone could possibly ask for. Thanks for taking the time to write it.

Thank you.

---

### Post by Frenzybr on 2009-10-25
thank you very much for the tutorial, it was very helpfull. 
but i got a problem last night that i dont know what to do anymore..
Vuze simply wont open anymore, and when i try to run it thru the terminal i get this..

 > danny@danny-laptop:~$ vuze
file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/swt-gtk-3.4.jar ; file:/home/danny/
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.gudy.azureus2.ui.common.Main.directLaunch(Main.java:229)
    at org.gudy.azureus2.ui.common.Main.main(Main.java:132)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.ClassFormatError: Unknown constant tag 86 in class file org/gudy/azureus2/core3/util/ListenerManagerDispatcher
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:637)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at com.aelitis.azureus.launcher.classloading.PrimaryClassloader.loadClass(PrimaryClassloader.java:103)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
    at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
    at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
    at org.gudy.azureus2.ui.swt.Main.main(Main.java:216)
    ... 12 more
Invoking main failed
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.ClassFormatError: Unknown constant tag 86 in class file org/gudy/azureus2/core3/util/ListenerManagerDispatcher
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:637)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at com.aelitis.azureus.launcher.classloading.PrimaryClassloader.loadClass(PrimaryClassloader.java:103)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
    at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
    at org.gudy.azureus2.ui.common.Main.main(Main.java:160)
    ... 6 more
Exception in thread "MainRunner" java.lang.SecurityException: VM exit operation prohibited
    at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl$2.checkExit(SESecurityManagerImpl.java:269)
    at java.lang.Runtime.exit(Runtime.java:105)
    at java.lang.System.exit(System.java:923)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:42)
    at java.lang.Thread.run(Thread.java:636)i have tried re inst\llign it but it stilwont work/.. any ideas???

thank you in advance.. 
-Danny

---

### Post by lovinglinux on 2009-10-25
> **Frenzybr said:**
> thank you very much for the tutorial, it was very helpfull. 
but i got a problem last night that i dont know what to do anymore..
Vuze simply wont open anymore, and when i try to run it thru the terminal i get this..

 i have tried re inst\llign it but it stilwont work/.. any ideas???

thank you in advance.. 
-Danny

I have seen reports on the net about Vuze crashing or not being able to start. It seems that it is a widespread problem. The solution provided was to update Vuze, but I'm not sure how you would do that on Ubuntu. Perhaps you could try to find a PPA repository for Vuze, meanwhile, I suggest using Ktorrent as a temporary alternative.

---

### Post by Frenzybr on 2009-10-25
> **lovinglinux said:**
> I have seen reports on the net about Vuze crashing or not being able to start. It seems that it is a widespread problem. The solution provided was to update Vuze, but I'm not sure how you would do that on Ubuntu. Perhaps you could try to find a PPA repository for Vuze, meanwhile, I suggest using Ktorrent as a temporary alternative.


after 3 boots its still wouldn't work but now for some reason after the 4th its working.. 
thx for the help anywaiz

---

### Post by vinutux on 2009-10-25
very helpful infos gr8...tutorial

---

### Post by lovinglinux on 2009-10-25
> **vinutux said:**
> very helpful infos gr8...tutorial

Thank you.

---

### Post by ashmew2 on 2009-10-31
.

---

### Post by emigrant on 2009-10-31
[lovinglinux]("http://ubuntuforums.org/member.php?u=649167"), thank you for the wonderful tutorial. its well done.
i have a question.
if i have correctly understood, by default while we download, we do uploading as well for the other peers.
if that is the case, why do we need to reconfigure routers and firewall to accept incoming request?

---

### Post by lovinglinux on 2009-10-31
> **emigrant said:**
> [lovinglinux]("http://ubuntuforums.org/member.php?u=649167"), thank you for the wonderful tutorial. its well done.
i have a question.
if i have correctly understood, by default while we download, we do uploading as well for the other peers.
if that is the case, why do we need to reconfigure routers and firewall to accept incoming request?

Thanks for your comments.

Yes we do download and upload at the same time, until the file is completed, then we only upload (seed). We need to open ports in the router and firewall to accept incoming requests to maximize the chances of connecting to peers. If we don't do that, we will be able to connect only to those peers that accept our connection requests. But they do not accept all the time, because all peers have a limited number of possible connections, so we must accept incoming requests to allow them to try connecting to us when they can. Once the connection is established, either by our request or them, the data transfer flows both ways (download/upload).

---

### Post by emigrant on 2009-10-31
thanks, i understand now.
closed ports means - less generous
opened ports means - more generous

am i right?
anyway both are generous ;)

---

### Post by lovinglinux on 2009-10-31
> **emigrant said:**
> thanks, i understand now.
closed ports means - less generous
opened ports means - more generous

am i right?
anyway both are generous ;)

Is not about generosity, but opportunity of connections.

---

### Post by emigrant on 2009-10-31
thank you for the explanation. i got it now. :)

---

### Post by ashmew2 on 2009-11-01
(This is a re post)
This is one of the most comprehensive tutorials on a topic ive ever seen..I especially liked the Troubleshooting part with " If Yes goto #3 else #4 " and so on , hehe

By the way , for some reason , i cant seem to get a speed of above 50 KiB/s , when downloading torrent files..Its not related to the Torrent health , have tried many torrents including the Karmic ISO.
I have a 512 kbps connection , so should be getting 60~64 KB/s , (I called the ISP , they told me i'd be getting 60-64 KB/s)..
So , when i download files from the repos or using wget , i get a constant 62 KB/s more or less ,But the torrents simply wont go above 50 KB/s...
After trying everything , I switched my router back to the Bridging mode , meaning that i now need to issue "sudo pon dsl-provider" to connect to the internet , and the Router Firewall is turned off now so no need to port forward.What should i do , im Clueless now ( ,.. Thanks man

---

### Post by lovinglinux on 2009-11-01
> **ashmew2 said:**
> (This is a re post)
This is one of the most comprehensive tutorials on a topic ive ever seen..I especially liked the Troubleshooting part with " If Yes goto #3 else #4 " and so on , hehe

By the way , for some reason , i cant seem to get a speed of above 50 KiB/s , when downloading torrent files..Its not related to the Torrent health , have tried many torrents including the Karmic ISO.
I have a 512 kbps connection , so should be getting 60~64 KB/s , (I called the ISP , they told me i'd be getting 60-64 KB/s)..
So , when i download files from the repos or using wget , i get a constant 62 KB/s more or less ,But the torrents simply wont go above 50 KB/s...
After trying everything , I switched my router back to the Bridging mode , meaning that i now need to issue "sudo pon dsl-provider" to connect to the internet , and the Router Firewall is turned off now so no need to port forward.What should i do , im Clueless now ( ,.. Thanks man

Have you limited your torrent UPload speed to 80% of the total UPload bandwidth limit you have? If you use unlimited UPload speeds, the network gets clogged and your download speed is reduced.

---

### Post by ashmew2 on 2009-11-01
Yeah , i set it to 50 KiB/s..

---

### Post by lovinglinux on 2009-11-01
> **ashmew2 said:**
> Yeah , i set it to 50 KiB/s..

If you are not getting extremely slow connections than it could be just a slow torrent. Have you tried to download the latest Ubuntu release? You should get high speeds with it.

---

### Post by ashmew2 on 2009-11-02
> **lovinglinux said:**
> If you are not getting extremely slow connections than it could be just a slow torrent. Have you tried to download the latest Ubuntu release? You should get high speeds with it.

Yeah i tried that. I contacted my ISP , they did some Virtual Pipe Changing thing from their end , so now im getting like 75 KiB/s when downloading via firefox/wget. But even now the torrents are running at 15 KiB/s..Ive switched back to the routing Mode , Setup port forwarding , but still no luck..
I tried the Karmic ISO , no luck with that as well..

---

### Post by lovinglinux on 2009-11-02
> **ashmew2 said:**
> Yeah i tried that. I contacted my ISP , they did some Virtual Pipe Changing thing from their end , so now im getting like 75 KiB/s when downloading via firefox/wget. But even now the torrents are running at 15 KiB/s..Ive switched back to the routing Mode , Setup port forwarding , but still no luck..
I tried the Karmic ISO , no luck with that as well..

Try to reduce the number of connections per second and the number of half-open connections.

---

### Post by H2SO_four on 2009-11-02
Nice write up! Great job :)

---

### Post by bdalzell on 2009-11-08
I am using Transmission Bittorrent for my Ubuntu iso's and I leave my machine running overnight so that I can upload to the torrent. However I made the mistake of downloading the .iso images to Desktop. Some of the older Ubuntu versions  still get quite a bit of requests but they are cluttering up the Desktop. Is there a way to move them into another folder and have the Transmission still find them for upload.

I have upload/download ratios of up to 9 on some of them and I would like to hold onto those ratios.

---

### Post by lovinglinux on 2009-11-08
Right-click on the torrent, select "Set Location", then select the folder you want to save it and tick the option "Move from the current folder".

It will move the ISO to the new folder without loosing share ratio or anything.

---

### Post by bdalzell on 2009-11-08
When I right click on the torrent as it is presented as a line in the main transmission window the only choices I get are:

Properties
Open Folder
Start
Pause
Verify Local Data
Ask Tracker for more peers
Remove
Delete Files and Remove

If I right click on the iso icon I do not get anything other than the normal things the Gnome desktop tells you to do with icons.

---

### Post by lovinglinux on 2009-11-09
> **bdalzell said:**
> When I right click on the torrent as it is presented as a line in the main transmission window the only choices I get are:

Properties
Open Folder
Start
Pause
Verify Local Data
Ask Tracker for more peers
Remove
Delete Files and Remove.

What version of Transmission are you using?

---

### Post by bdalzell on 2009-11-09
The version that came with my upgrade to Jaunty - Transmission 1.51(7963) according to the "Help>About".

---

### Post by lovinglinux on 2009-11-09
> **bdalzell said:**
> The version that came with my upgrade to Jaunty - Transmission 1.51(7963) according to the "Help>About".

Install version 1.76 **[http://www.transmissionbt.com/download.php](http://www.transmissionbt.com/download.php)**

---

### Post by bdalzell on 2009-11-10
I am not quite ready to install Karmic as this is my main work computer.

this is the error I get with gdebi trying to install Transmission 1.75

Error: Dependency is not satisfiable: libevent-1.4-2 (>= 1.4.11-stable)

will finding and installing libevent-1.4-2 mess up anything in jaunty?

---

### Post by lovinglinux on 2009-11-10
> **bdalzell said:**
> I am not quite ready to install Karmic as this is my main work computer.

this is the error I get with gdebi trying to install Transmission 1.75

Error: Dependency is not satisfiable: libevent-1.4-2 (>= 1.4.11-stable)

will finding and installing libevent-1.4-2 mess up anything in jaunty?

I don't really know. Anyway, you could remove the torrents from Transmission, re-download the .torrent files, move the ISO files to the new destination, change the destination directory accordingly in Transmission. then load the .torrents again. Transmission will do a re-check to see how much you have downloaded and then start seeding again. The only issue is that you will loose your share ratio.

---

### Post by bdalzell on 2009-11-10
Thanks for your help. What I ended up doing was to temporarily activate the Karmic repository in my Synaptic and add the 1.75 version of Transmission. It added the needed dependency. Then I deactivated the Karmic repository.

Everything works OK so far and I was able to move my 11 torrent iso files to a subfolder on Desktop.

---

### Post by ckop64 on 2009-11-11
Thanks for the guide, it helped a lot! =)

---

### Post by pw_f100_220 on 2009-11-18
and how exactly do i enable "Karmic" repository in synaptic?

i can't find that option, just the usual multiverse, etc.

---

### Post by Toke on 2009-11-19
That is a very useful guide, now I have at least some idea of what is going on.

One of my problems is that I am on a shared broadband connection with the rest of the building and cannot get one of those static ip-addresses, as I read it it means there is no way to forward a port. 
As soon as I start seeding the number of peers start dropping towards 0. 

I suspect there are some blocking going on too, one torrent site appear to be working fine for others (new torrents keeps appearing) but I get a time out on the tracker status.

I just switched to deluge, ktorrent greyed out too often.

---

### Post by lovinglinux on 2009-11-19
> **pw_f100_220 said:**
> and how exactly do i enable "Karmic" repository in synaptic?

i can't find that option, just the usual multiverse, etc.


Please create a new thread, since this is not related to this tutorial.


> **Toke said:**
> That is a very useful guide, now I have at least some idea of what is going on.

One of my problems is that I am on a shared broadband connection with the rest of the building and cannot get one of those static ip-addresses, as I read it it means there is no way to forward a port. 
As soon as I start seeding the number of peers start dropping towards 0. 

I suspect there are some blocking going on too, one torrent site appear to be working fine for others (new torrents keeps appearing) but I get a time out on the tracker status.

I just switched to deluge, ktorrent greyed out too often.

Yep, that's probably the case. I recommend using UPnP to see if the port is automatically forwarded in  the router. Also enable DHT and PEX, so you can download without the tracker. This will probably work for most popular torrents, but if it has just a few peers, than DHT and PEX might not be enough.

---

### Post by Toke on 2009-11-19
> **lovinglinux said:**
> 

Yep, that's probably the case. I recommend using UPnP to see if the port is automatically forwarded in  the router. Also enable DHT and PEX, so you can download without the tracker. This will probably work for most popular torrents, but if it has just a few peers, than DHT and PEX might not be enough.

I have plugged my computer strait into the cable and bypassed my own router, that makes no noticeable difference.

I think they are already enabled by default, when I check under edit>preferences>network they are checked under network>network extras.

---

### Post by lovinglinux on 2009-11-19
> **Toke said:**
> I think they are already enabled by default, when I check under edit>preferences>network they are checked under network>network extras.

Have you tried to download a popular torrent from a reliable tracker, like the Ubuntu ISO files?

Perhaps in your case would be better to use a different method. Try [BitLet](http://www.bitlet.org/) service. It downloads the torrent to their server, so you can get via http.

---

### Post by Toke on 2009-11-19
> **lovinglinux said:**
> Have you tried to download a popular torrent from a reliable tracker, like the Ubuntu ISO files?

Perhaps in your case would be better to use a different method. Try [BitLet]("http://www.bitlet.org/") service. It downloads the torrent to their server, so you can get via http.

I have no problem getting hold of torrent files, the problem seem to be that one particular tracker is not working for me. 

I am currently downloading at 600Kbit/s and uploading app. 150Kbit/s.

Am trying to figure out bitlet now.

---

### Post by lovinglinux on 2009-11-19
> **Toke said:**
> I have no problem getting hold of torrent files, the problem seem to be that one particular tracker is not working for me. 

I am currently downloading at 600Kbit/s and uploading app. 150Kbit/s.

Am trying to figure out bitlet now.

Ah, that's great. Probably the tracker is down or has been terminated. Check if it is from the pirate bay, since they closed their tracker for good a couple of days ago.

---

### Post by jarmore on 2009-11-22
Thankyou thankyou lovinglinux. For the first time all is well torrentwize here. Deluge (never heard of it before) works great. Your efforts are much appreciated!

Jim

---

### Post by lovinglinux on 2009-11-22
> **jarmore said:**
> Thankyou thankyou lovinglinux. For the first time all is well torrentwize here. Deluge (never heard of it before) works great. Your efforts are much appreciated!

Jim

You are welcome. I'm glad it helped. Happy torrenting.

---

### Post by warfacegod on 2009-12-22
Excellent thread. Cheers to you and all the others that are willing to take the time to write tutorials or reply to help folks in need of it.

In ktorrent, under the peers plugin, what are the definitions for choked, snubbed and score. I assume that score has to do with a peers share ratio. If so, how is that calculated? More specifically, is it 

   .01 That one particular torrent share ratio?

   .02 The overall share ratio of all torrents they are currently sharing?

   .03 The overall share ratio of all torrents they've ever shared?

What do the scores really mean? Hypothetically, if I've only ever downloaded one torrent and let it seed until say 3.5, how would that translate into a score?

Is there a way for me to check my own score?

Thanks.

---

### Post by warfacegod on 2009-12-22
Sorry, one more question. Will the ktorrent's UPnP plugin port forward correctly or is that something I should do manually?

Thanks again.

---

### Post by lovinglinux on 2009-12-22
> **warfacegod said:**
> Excellent thread. Cheers to you and all the others that are willing to take the time to write tutorials or reply to help folks in need of it.

Thanks.

> **warfacegod said:**
> In ktorrent, under the peers plugin, what are the definitions for choked, snubbed and score. 

[http://en.wikipedia.org/wiki/BitTorrent_vocabulary](http://en.wikipedia.org/wiki/BitTorrent_vocabulary)

> **warfacegod said:**
>  I assume that score has to do with a peers share ratio. If so, how is that calculated? More specifically, is it 

   .01 That one particular torrent share ratio?

   .02 The overall share ratio of all torrents they are currently sharing?

   .03 The overall share ratio of all torrents they've ever shared?

What do the scores really mean? Hypothetically, if I've only ever downloaded one torrent and let it seed until say 3.5, how would that translate into a score?

Is there a way for me to check my own score?

KTorrent uses the score to determinewho to upload to. I believe it is calculated based on the share ration for each torrent, because when you start a new torrent they all start with 0 or -50. So it doesn't matter if you seed to 3.5, your next torrent should start from scratch.

I don't know how to check your score, but your share ratio for each torrent should be a good indicative.

> **warfacegod said:**
> Sorry, one more question. Will the ktorrent's UPnP plugin port forward correctly or is that something I should do manually?

It works like a charm. You don't have to set it up manually. When you start Ktorrent it automatically forward the ports. You can check the UPnp plugin at the bottom. If the ports are forwarded, you will see the ports listed. Nevertheless, don't forget to enable UPnP on the router for this to work. You can also interrupt a port forwarding manually, through the UPnP plugin.

---

### Post by matyasfalvi on 2009-12-28
Hi!

I have a problem that occures quite frequently. I would appreciate if anyone could give any advice as to why this is happening and how I can stop this from happening again.

Usually when I resume a torrent download with Transmission on Ubuntu 8.04 after a longer period of time the download process starts from 0% eventhough the file is still there. Then when I hit the verify local data button Transmission quits. After several times of trials Transmission suddenly says: "Destination folder doesn't exist" (I don't mess around with files still in progress.) So to give you an example In this case I've stopped downloading on 2009.12.19 and I wanted to resume the download today 2009.12.28 and the above described happened.

Thanx in advance for any help!

Take care!

---

### Post by lovinglinux on 2009-12-29
> **matyasfalvi said:**
> Hi!

I have a problem that occures quite frequently. I would appreciate if anyone could give any advice as to why this is happening and how I can stop this from happening again.

Usually when I resume a torrent download with Transmission on Ubuntu 8.04 after a longer period of time the download process starts from 0% eventhough the file is still there. Then when I hit the verify local data button Transmission quits. After several times of trials Transmission suddenly says: "Destination folder doesn't exist" (I don't mess around with files still in progress.) So to give you an example In this case I've stopped downloading on 2009.12.19 and I wanted to resume the download today 2009.12.28 and the above described happened.

Thanx in advance for any help!

Take care!

I have seen threads with similar problems in Transmission. I believe it has something to do with permissions to create those folders. Check if the folders really exists and if the permissions are setup correctly. Also try to update your Transmission with the latest release.

---

### Post by warfacegod on 2009-12-29
See, this must be a great post, I'm back for more.

In ktorrent in the settings window under Advanced> Performance is the Network sleep interval 50ms the reason my wireless signal drops and then resumes a second later? If so, can I safely reduce the ms to 0 or at least shorter? Thanks.

---

### Post by lovinglinux on 2009-12-29
> **warfacegod said:**
> In ktorrent in the settings window under Advanced> Performance is the Network sleep interval 50ms the reason my wireless signal drops and then resumes a second later?

I don't think so.  I'm not sure exactly how it would affect your network stability. Nevertheless, it seems to put torrent connections to sleep when the bandwidth limit is reached. It has no effect if you don't have speed limits configured in the client. Put the mouse cursor over the value on that option and you will see a better explanation of what it does.

Perhaps the problem with your wireless is the UPload limit. Set it to 80% of your UPload bandwidth limit to avoid clogging your network. I guess this is why your connection drops. It could be overloaded.

> **warfacegod said:**
>  If so, can I safely reduce the ms to 0 or at least shorter? Thanks.

I don't think is recommended. As far as I know, it will increase CPU usage considerably.

Take a look at [this](http://ktorrent.org/forum/viewtopic.php?t=2540).

---

### Post by warfacegod on 2009-12-29
> Perhaps the problem with your wireless is the UPload limit. Set it to 80% of your UPload bandwidth limit to avoid clogging your network. I guess this is why your connection drops. It could be overloaded.


I keep my upload limit set to 100 K/s (roughly 40% upload bandwidth) any higher and my down speed drops through the floor. Any lower and I get the same thing if only because I'm not not sharing enough.

---

### Post by lovinglinux on 2009-12-29
> **warfacegod said:**
> I keep my upload limit set to 100 K/s (roughly 40% upload bandwidth) any higher and my down speed drops through the floor. Any lower and I get the same thing if only because I'm not not sharing enough.

Try reducing the "Maximum number of connection setups" in the "Network" section. Use something like 50. This will reduce the number of simultaneous outgoing connection attempts and probably help with your connection issue.

---

### Post by warfacegod on 2009-12-29
It's already at 50. 

...I just used ktorrents recommended settings button (something I was leery of doing) and down speeds are lower but seem to be much more consistent.

At least part of the problem is that the two torrents I've got going are about 100GB total.

But none of this explains the connection dropping. I think I'll post a thread in the networking section, if I don't find a workable answer.

...this sad excuse for a body...   ...I want to see gamma rays...

---

### Post by lovinglinux on 2009-12-29
> **warfacegod said:**
> It's already at 50. 

Then put 25 or lower.

---

### Post by mickeyy on 2010-01-07
Has had anyone has any success with optimizing BitTorrent speeds for Vista ?

I'm not sure which approach to take in order to optimize my BitTorrent on my Vista. I've downloaded BitTorrent Accelerator patch to increase speed but not seen any significant difference in speeds.
Pls. advise, Thanks

---

### Post by lovinglinux on 2010-01-07
> **mickeyy said:**
> Has had anyone has any success with optimizing BitTorrent speeds for Vista ?

I'm not sure which approach to take in order to optimize my BitTorrent on my Vista. I've downloaded BitTorrent Accelerator patch to increase speed but not seen any significant difference in speeds.
Pls. advise, Thanks

The principles explained on this tutorial are the same, for any BitTorrent client. Nevertheless, this question would be better placed in a Windows forum. 

Windows has a limitation on the number of half-open connections, so Google for how to bypass half-open limitation on Windows.

---

### Post by TidyBhoy on 2010-01-12
Hey, I've been scratching my head here all day with this, hoping you mig... well you deffo no more about it than me.

I've forwarded ports and all that stuff and can download faster than i even expected, except when I connect to a VPN server to anonymize myself.

I'm running Karmic and don't have firestarter or anything.. infact i removed it cause it was causing me such hardship ha. 
Even if i change the port settings in Deluge to a number i havent forwarded on my router i can still connect to peers and download. When the vpn is connected its completely dead. 
Browsing and all other internet activity is unaffected by the VPN.
I should probably add that I'm working wirelessly from a laptop. 

Thanks for your time to read and hopefully help. :)

---

### Post by lovinglinux on 2010-01-12
> **TidyBhoy said:**
> Hey, I've been scratching my head here all day with this, hoping you mig... well you deffo no more about it than me.

I've forwarded ports and all that stuff and can download faster than i even expected, except when I connect to a VPN server to anonymize myself.

I'm running Karmic and don't have firestarter or anything.. infact i removed it cause it was causing me such hardship ha. 
Even if i change the port settings in Deluge to a number i havent forwarded on my router i can still connect to peers and download. When the vpn is connected its completely dead. 
Browsing and all other internet activity is unaffected by the VPN.
I should probably add that I'm working wirelessly from a laptop. 

Thanks for your time to read and hopefully help. :)

Unfortunately, I never used a VPN service, so I don't know about how to properly configure the client to work with it. Sorry. Nevertheless, it looks like your VPN provider is blocking your connections on the torrent ports. Perhaps it only allows standard ports like HTTP, FTP, SSH, IMAP etc.

BTW, you are able to connect to peers without forwarding the port on the router, because it is your client that is requesting connections. This is normal. Forwarding the port only allow remote peers to request connections to you, but once the connection is established, it doesn't matter if the port is opened or not. The data flow goes freely between connected peers.

---

### Post by TidyBhoy on 2010-01-12
Yea if i pick a Random port in Deluge that isn't forwarded on my router i can still get connections to peers. But if I connect to a VPN.. and I've tried 2.. there's nothing at all.

down in the bottom left corner the connections might get up to 100 (200) but it just goes back to nothing again with no connection being made.

Could there be a setting somewhere or do I have to put the IP of the VPN in somewhere... Are the connections coming into deluge getting confused cause my IP changes?

I really have no idea... any1?

---

### Post by lovinglinux on 2010-01-12
> **TidyBhoy said:**
> Could there be a setting somewhere or do I have to put the IP of the VPN in somewhere... Are the connections coming into deluge getting confused cause my IP changes?

I really have no idea... any1?

I guess so.  Take a look at [this](http://filesharefreak.com/2008/10/16/anonymous-bittorrent-through-a-vpn-the-speed-tests/).

---

### Post by TidyBhoy on 2010-01-12
I knew How to do it in Windows but its there anyway to check if my IP is static in karmic? Could that even be the problem? on my router when open ports ect. it doesn't give me an IP.. just the name of my laptop, so I'm not sure.

---

### Post by lovinglinux on 2010-01-12
> **TidyBhoy said:**
> I knew How to do it in Windows but its there anyway to check if my IP is static in karmic? Could that even be the problem? on my router when open ports ect. it doesn't give me an IP.. just the name of my laptop, so I'm not sure.

For internal IP

```
ifconfig
```

For external - [http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by TidyBhoy on 2010-01-13
Still aint sorted it :(

Just Try'd to send an email in Evolution tho. and It kept Timing out. Despite being able to recieve instantly.

As soon as i disconnected from the vpn.. Woosh, Sent no problem.

Does this give any1 any Ideas? I've my fingers crossed.

---

### Post by lovinglinux on 2010-01-13
> **TidyBhoy said:**
> Still aint sorted it :(

Just Try'd to send an email in Evolution tho. and It kept Timing out. Despite being able to recieve instantly.

As soon as i disconnected from the vpn.. Woosh, Sent no problem.

Does this give any1 any Ideas? I've my fingers crossed.

You should contact your VPN provider and ask for instructions on how to configure your network. It seems it is not a BitTorrent issue.

---

### Post by sandy1 on 2010-01-15
My university uses a squid proxy server 10.10.0.1: 3128, and i cannot download any torrents. however when my friend uses tunneling software like ultrasurf on windows os it is possible. sometimes it is possible even without the tunneling software once the download has begun. i downloaded utorrent and installed ultrasurf both with the help of wine (which works fine with the web browsers etc), yet i still cant get a download so i know its not a ultrasurf related issue. i also tried a dozen other p2p clients...deluge, bitcomet, bitspirit but none of dem see to do the trick. finally i also tried http tunnel client (with wine again..n it works fine wid browsers) but again didnt work wid d p2p clients. i did succeed however  in downloading only those torrents which were available for videos hosted by vuze using its client(note only http tunnel not by ultrasurf), but not any other torrent!!! the weirdest part is that i can see the peers, the seeders but i cant connect to anyone of them!!! i also tried installing tor in ubuntu, but gave up after two failed attempts. its very difficult to configure it whereas in windows u dont have 2 do anything. i have completely switched over from windows (after somehow managing to install ms office 2007 wid wine) but i cant get p2p 2 work at all in ubuntu..except 4 in vuze and that too the videos it hosts. Can some1 help me out here...??? any help would be a big relief.

---

### Post by lovinglinux on 2010-01-15
> **sandy1 said:**
> Can some1 help me out here...??? any help would be a big relief.

Unfortunately, bypassing the network blocking features of your University and using their network for personal p2p is probably not allowed (might be illegal as well). You should contact the University network administrator and request assistance to configure your client appropriately. If you have a legitimate reason to use the university network resources for p2p traffic, then I'm sure they will be kind to help you out or indicate a computer center with such privileges.

---

### Post by matyasfalvi on 2010-01-25
Thank you Lovinglinux for your answer!

Temporarily I solved the problem with starting a new download and before initiating I verified the local data this solved the problem.
I will look into the permissions later too busy these days to do follow up. Thanx again!
Take care!

---

### Post by Pelgar on 2010-02-03
lovinglinux, I just wanted to add my thank you to the growing list. I installed Deluge and tried my first torrent on a Linux box today. The only real problem I had was with the "No incoming connection" message. Your guide helped me clear that up, had to get out of the 6881 to 6889 port range.
I've been using uTorrent on a Win XP box for a good while. I'm far from a torrent expert but feel that I have made a huge step forward by reading this excellent guide.

---

### Post by lovinglinux on 2010-02-04
> **Pelgar said:**
> lovinglinux, I just wanted to add my thank you to the growing list. I installed Deluge and tried my first torrent on a Linux box today. The only real problem I had was with the "No incoming connection" message. Your guide helped me clear that up, had to get out of the 6881 to 6889 port range.
I've been using uTorrent on a Win XP box for a good while. I'm far from a torrent expert but feel that I have made a huge step forward by reading this excellent guide.

Thank you.

---

### Post by MetalMusicAddict on 2010-02-08
These look right to you guys?

Speedtest.net: 
Avg. DL Speed = 10.65 Mb/s
Avg. UL Speed = 0.32 Mb/s

[B][U]My Deluge bandwidth Settings: 
[/U][/B][LIST]
[*]Maximum Connections: 200
[*]Maximum Upload Slots: 4
[*]Maximum Download Speed (KiB/s): -1
[*]Maximum Upload Speed (KiB/s): 25
[*]Maximum Half-Open Connections: 50
[*]Maximum Connection Attempts per Second: 20
[/LIST]

Ignore limits on local network, checked
Rate limit IP overhead, checked

[B][U]Per Torrent Bandwidth Usage:
[/U][/B][LIST]
[*]Maximum Connections: -1
[*]Maximum Upload Slots: -1
[*]Maximum Download Speed (KiB/s): -1
[*]Maximum Upload Speed (KiB/s): 50
[/LIST]

This feels a bit slow lately. Also, I typically connect to largely seeded torrents. Should I change things because of that? And should I change use of the standard ports?

---

### Post by lovinglinux on 2010-02-08
> **MetalMusicAddict said:**
> These look right to you guys?

Speedtest.net: 
Avg. DL Speed = 10.65 Mb/s
Avg. UL Speed = 0.32 Mb/s

[B][U]My Deluge bandwidth Settings: 
[/U][/B][LIST]
[*]Maximum Connections: 200
[*]Maximum Upload Slots: 4
[*]Maximum Download Speed (KiB/s): -1
[*]Maximum Upload Speed (KiB/s): 25
[*]Maximum Half-Open Connections: 50
[*]Maximum Connection Attempts per Second: 20
[/LIST]

Ignore limits on local network, checked
Rate limit IP overhead, checked

[B][U]Per Torrent Bandwidth Usage:
[/U][/B][LIST]
[*]Maximum Connections: -1
[*]Maximum Upload Slots: -1
[*]Maximum Download Speed (KiB/s): -1
[*]Maximum Upload Speed (KiB/s): 50
[/LIST]

This feels a bit slow lately. Also, I typically connect to largely seeded torrents. Should I change things because of that? And should I change use of the standard ports?

Looks OK to me. I would just change the Maximum Upload Speed from 25/50 to 30/30.

Changing the ports is recommended only if your ISP blocks or cap connections on the default ports.

---

### Post by andrew.46 on 2010-03-14
Hi lovinglinux,

I hope this question does not fall outside the scope of your guide.... My ISP allows unlimited downloads between 0200 and 0800 and for my torrents I therefore need scheduled downloading/uploading. I will happily admit to limited BitTorrent experience and I have been using Transmission which in its newest release (1.91) has pretty bulletproof scheduling. In fact I have[ a guide]("http://ubuntuforums.org/showthread.php?t=1391718") on these forums for building this version. Can I ask then, in your experience, are there other bittorrent clients which offer the *reliable* download scheduling I have found with the latest Transmission? 

Thanks for your trouble,

Andrew

---

### Post by lovinglinux on 2010-03-14
> **andrew.46 said:**
> Hi lovinglinux,

I hope this question does not fall outside the scope of your guide.... My ISP allows unlimited downloads between 0200 and 0800 and for my torrents I therefore need scheduled downloading/uploading. I will happily admit to limited BitTorrent experience and I have been using Transmission which in its newest release (1.91) has pretty bulletproof scheduling. In fact I have[ a guide]("http://ubuntuforums.org/showthread.php?t=1391718") on these forums for building this version. Can I ask then, in your experience, are there other bittorrent clients which offer the *reliable* download scheduling I have found with the latest Transmission? 

Thanks for your trouble,

Andrew

Ktorrent has a bandwidth schedule plugin that can control download/upload speeds or stop torrents according to day of the week and time. Nevertheless, I never used it, since I have unlimited bandwidth. It seems reliable tho.

Ktorrent is awesome, so I would give it a try if I was you.

---

### Post by andrew.46 on 2010-03-14
Ji lovinglinux,

> **lovinglinux said:**
> Ktorrent is awesome, so I would give it a try if I was you.

Thanks, I shall install and investigate :).

Andrew

---

### Post by DeadlyOats on 2010-09-09
Hello lovinglinux,

I've been searching in the Deluge forums and wiki, but I can't find a straight answer to this question (deluge forums ignore the words "add" and "peer", so it was kind of hard to do a search on their forum...  I also searched your guide as well, din't find anything (search terms: "add" "manually" "peer"  without the quotes).

When I right click in the "Peers" tab in deluge, ver. 1.2.3, I get a box that says "Add Peer", I click on that, and I get a box that says "hostname:port".  (smileys can be annoying...  "hostname : port" without the spaces.)

What does that do?  What is it for?  Why would I use it?

Thanks.

---

### Post by lovinglinux on 2010-09-09
> **DeadlyOats said:**
> Hello lovinglinux,

I've been searching in the Deluge forums and wiki, but I can't find a straight answer to this question (deluge forums ignore the words "add" and "peer", so it was kind of hard to do a search on their forum...  I also searched your guide as well, din't find anything (search terms: "add" "manually" "peer"  without the quotes).

When I right click in the "Peers" tab in deluge, ver. 1.2.3, I get a box that says "Add Peer", I click on that, and I get a box that says "hostname:port".  (smileys can be annoying...  "hostname : port" without the spaces.)

What does that do?  What is it for?  Why would I use it?

Thanks.

I'm not using Deluge anymore, but I'm almost sure it is for adding local network peers. 

BTW, I'm using qBitTorrent, which is the fastest client I ever used. After Deluge, I used Ktorrent for a while, until the developer changed the UI to something I didn't like and then I tried qBitTorrent and settled with it.

---

### Post by DeadlyOats on 2010-09-10
> **lovinglinux said:**
> I'm not using Deluge anymore, but I'm almost sure it is for adding local network peers. 

BTW, I'm using qBitTorrent, which is the fastest client I ever used. After Deluge, I used Ktorrent for a while, until the developer changed the UI to something I didn't like and then I tried qBitTorrent and settled with it.

Only with open source can you find conversations between end users describing how quickly they'll change applications, because of something they din't like about the last one they tried...

I was using Vuze for a long while, but I got tired of the problems I was having with updates..., so I tried Transmission, then I found that Transmission has a PPA with a much advanced version number than what is found in Ubuntu repos....  ('buntu has lots of repos that are out of date, it seems...  Well, it seems...), and now I'm giving Deluge a try.  I like it's UI.  Lot's of stats, ease of use, multiple torrents listed in one window, and not a resource hog.

Halite looks interesting too, but it's still in it's early development stages for Linux.  I also read that uTorrent is working on a port to Linux...

Thanks for your reply.

---

### Post by lovinglinux on 2010-09-10
> **DeadlyOats said:**
> Only with open source can you find conversations between end users describing how quickly they'll change applications, because of something they din't like about the last one they tried...

I was using Vuze for a long while, but I got tired of the problems I was having with updates..., so I tried Transmission, then I found that Transmission has a PPA with a much advanced version number than what is found in Ubuntu repos....  ('buntu has lots of repos that are out of date, it seems...  Well, it seems...), and now I'm giving Deluge a try.  I like it's UI.  Lot's of stats, ease of use, multiple torrents listed in one window, and not a resource hog.

Halite looks interesting too, but it's still in it's early development stages for Linux.  I also read that uTorrent is working on a port to Linux...

Thanks for your reply.

Yes, there is already a uTorrent daemon and a client will be available soon.

Deluge, Ktorrent, Transmission, qBitTorrent are all excellent. Here is my order of preference:

[LIST=1]
[*]qBitTorrent
[*]KTorrent
[*]Deluge
[*]Transmission
[/LIST]

---

### Post by ozzyprv on 2010-09-10
> **lovinglinux said:**
> Here is my order of preference:

[LIST=1]
[*]qBitTorrent
[*]KTorrent
[*]Deluge
[*]Transmission
[/LIST]

A bit off-topic.

Any comment about rtorrent?
Thanks.

---

### Post by lovinglinux on 2010-09-11
> **ozzyprv said:**
> A bit off-topic.

Any comment about rtorrent?
Thanks.

Never used, but is a popular one, specially among headless server users.

---

### Post by brookie on 2010-09-18
Hello again LL,

Just wanted to let you know that Deluge put up a bandwidth tweaking page  (sometime?) to supplement their settings FAQ. It also has some pretty  good information and I thought it may be of use to some folks who are  using deluge. 

[Deluge UserGuide Bandwidth Tweaking]("http://dev.deluge-torrent.org/wiki/UserGuide/BandwidthTweaking")

Peace,
brook
[]("http://dev.deluge-torrent.org/wiki/UserGuide/BandwidthTweaking")

---

### Post by lovinglinux on 2010-09-18
> **brookie said:**
> Hello again LL,

Just wanted to let you know that Deluge put up a bandwidth tweaking page  (sometime?) to supplement their settings FAQ. It also has some pretty  good information and I thought it may be of use to some folks who are  using deluge. 

[Deluge UserGuide Bandwidth Tweaking]("http://dev.deluge-torrent.org/wiki/UserGuide/BandwidthTweaking")

Peace,
brook
[]("http://dev.deluge-torrent.org/wiki/UserGuide/BandwidthTweaking")

Thanks

---

### Post by sarthorks on 2010-12-25
Hello

I am behind some college filters which has blocked many things, including being able to download from a torrent client.

I use Jondo/JAP to bypass the filters to browse the net. I use the localhost as the proxy and 4001 as the port, as specified in jondo. 

I have tried adding this as the network proxy in deluge/ktorrent, etc, and I can connect to the trackers, but I just dont get any peers.

Am I missing something? 

Btw, my college connection is behind a proxy, which I have to specify in jondo.

---

### Post by lovinglinux on 2010-12-25
> **sarthorks said:**
> Hello

I am behind some college filters which has blocked many things, including being able to download from a torrent client.

I use Jondo/JAP to bypass the filters to browse the net. I use the localhost as the proxy and 4001 as the port, as specified in jondo. 

I have tried adding this as the network proxy in deluge/ktorrent, etc, and I can connect to the trackers, but I just dont get any peers.

Am I missing something? 

Btw, my college connection is behind a proxy, which I have to specify in jondo.

Sorry, but I don't give advice on how to bypass college network restrictions, specially for torrent.

---

### Post by br4nd0nh347 on 2011-02-22
Hello I have a simple question.

I'm trying to understand the information in the first post.

I want to get faster downloads.  I have my router forwarding certain ports to my pcs ip address in the network.  I have a torrent program using the same ports.

My question is I do not need to configure iptables since it automatically forwards the ports to my router from my torrent program, is this correct?

---

### Post by br4nd0nh347 on 2011-02-22
> **br4nd0nh347 said:**
> Hello I have a simple question.

I'm trying to understand the information in the first post.

I want to get faster downloads.  I have my router forwarding certain ports to my pcs ip address in the network.  I have a torrent program using the same ports.

My question is I do not need to configure iptables since it automatically forwards the ports to my router from my torrent program, is this correct?

Sorry for double post, but the edit button doesn't seem to work for me right now.  I just wanted to answer my own question.

I believe the answer is yes.

With my router forwarding the port and my torrent program using the ports, I still need to use iptables to accept connections to those ports for quicker speeds.  As said in the beginning post you can still connect, but it will not be as fast as forwarding the port, because you can get extra peers.

---

### Post by lovinglinux on 2011-02-23
> **br4nd0nh347 said:**
> Hello I have a simple question.

I'm trying to understand the information in the first post.

I want to get faster downloads.  I have my router forwarding certain ports to my pcs ip address in the network.  I have a torrent program using the same ports.

My question is I do not need to configure iptables since it automatically forwards the ports to my router from my torrent program, is this correct?

The torrent client UPnP feature only opens the port in the router. You still need to open the port in the firewall.

---

### Post by InvIsiBlekID on 2011-03-24
i noticed disabling “Rate limit IP overhead” under Bandwidth in preferences made a HUGE difference for me

i was getting at most 300kb/s, and it would drop constantly down to almost nothing. disabled that and im steady at 1.3mb/s :)

disabling dht seemed to help a little bit too

just thought i would pass it along (although im not using ubuntu, i followed this thread for a lot of good ideas and thought the OP may consider adding it)

deluge 1.3.1 here

---

