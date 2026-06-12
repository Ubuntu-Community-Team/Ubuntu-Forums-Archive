---
title: "Ubuntu Torrent Configuration"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by aprilmot on 2008-08-30
Hi all,
I have ubuntu Hardy 8.04. I am new to Ubuntu, just switched from xp few weeks before.  I am trying to setup a torrent client in my machine but always failing.  I am not able to setup the incoming TCPIP port settings correctly.  When I test the port it says port is closed.  I dont know how to open the port.  Is there any other setting I have to modify.

I hope I have explained my problem.  Please let me know if you require somemore details.

Thank you in Advance

Aprilmot.

---

### Post by gmxgeek on 2008-08-30
Which client are you using?

A recommend Azureus Vuze, as it has advanced features, but you can set it up for basic mode if you don't feel like a 1337 h4x0r. It is very easy to configure and has a nice interface. Not too heavy either

---

### Post by swoll1980 on 2008-08-30
> **gmxgeek said:**
> Which client are you using?

A recommend Azureus Vuze, as it has advanced features, but you can set it up for basic mode if you don't feel like a 1337 h4x0r. It is very easy to configure and has a nice interface. Not too heavy either

Have you tried deluge? I just found it yesterday. It's real nice also.

---

### Post by TenPlus1 on 2008-08-30
Deluge is the fastest/easiest torrent client I have found for Ubuntu, and here are my settings for a 2mb line:

Max simultaneous active torrents: 4
Network Extras: UPnP  NAT-PMP  Peer Exchange
Encryption: Enabled
Seeding: 1st 3 options ticked only
Max Connections: 200
Max Download Speed: -1.0
Max Upload Speed: (your choice really) 20
Max Upload Slots: 4
Max Half-Open Connections: 20
Max Connections Attempts Per Sec: 8
Per Torrent- Max Connections:200  /  Max Upload Slots:4 (same as above really)
Other: Everything is unticked (personal preference)
Plugins: Torrent Files / Blocklist Importer

with these settings I can achieve 260kbps on my 2mb line and am still able to surf the web without a problem...

---

### Post by sstusick on 2008-08-30
I second the Deluge suggestion.

---

### Post by TenPlus1 on 2008-08-30
Oops, almost forgot, get the latest Deluge at [www.getdeb.net](www.getdeb.net)

...and I've disabled IPV6 to help with network problems...

---

### Post by aprilmot on 2008-08-30
I am using BitTorrent client.  Ok. I will try deluge
Info:I am connected to internet via wifi.

Thanks

---

### Post by kosmiciatakuja on 2008-08-30
1. First of all deluge is nice, I can second that, although myself I use Transmission, which is rather simple but enough for my needs, and it's light too. 

2. I think we're missing the original point here - the closed port. About that: Unless you installed any special firewall software on your ubuntu box, I don't think there are any ports closed in the default installation. But the port must be open on your router. Since you say you're connected via wifi, there must be some kind of router or access point between you and the internet. If you know it's IP address, and know how to get into its configuration, look for 'port forwarding' and forward the torrent port (or ports) to your machine. 

Let me know if you got problems with the second point, we'll work something out :)

cheers!

---

### Post by eru777 on 2008-08-30
Deluge is my choice. It works , and is simple.
Try it, it has a built in port-forwarding check
Edit> Preferences> Network > Test Port
You have to set a static IP first (actually put ifconfig on console and you 'll see that ubuntu automatically puts a static IP, at least it did for me, correct me if I'm wrong)
THen perform port forwarding through your modem's interface , and finally check the ports through deluge. Don't forget to put the right IP in the modem , where you port forward, if not the ports will be forwarded in vain.

---

### Post by Loaded.len on 2008-08-30
The Azureus Wiki has some good info on NAT. 

Regardless of your choice of client, I recommend reading the following wiki pages...

[http://www.azureuswiki.com/index.php/NAT_problem](http://www.azureuswiki.com/index.php/NAT_problem)
[http://www.azureuswiki.com/index.php/PortIsBlacklisted](http://www.azureuswiki.com/index.php/PortIsBlacklisted)
[http://www.azureuswiki.com/index.php/PortForwarding](http://www.azureuswiki.com/index.php/PortForwarding)

Good luck.

---

### Post by aprilmot on 2008-08-30
> **kosmiciatakuja said:**
> 1. First of all deluge is nice, I can second that, although myself I use Transmission, which is rather simple but enough for my needs, and it's light too. 

2. I think we're missing the original point here - the closed port. About that: Unless you installed any special firewall software on your ubuntu box, I don't think there are any ports closed in the default installation. But the port must be open on your router. Since you say you're connected via wifi, there must be some kind of router or access point between you and the internet. If you know it's IP address, and know how to get into its configuration, look for 'port forwarding' and forward the torrent port (or ports) to your machine. 

Let me know if you got problems with the second point, we'll work something out :)

cheers!

Ya I think my problem is the point 2 you mentioned.  When I test the port I got the message "TCP port 49152 closed on 84.161.194.254 ".  When I try to get into router configuration page it is asking for a password which 
I dont know.  But my friends connected to the same router are able to download torrent files.

---

### Post by lovinglinux on 2008-08-30
Deluge is my choice too. It has Blocklist plugin, UPnP, NAT, PEX, DHT, full encryption and much more. It is a full-featured torrent client, but very simple to configure and is not bloated like Vuze.

You can see a client comparison at [http://en.wikipedia.org/wiki/BitTorrent_client](http://en.wikipedia.org/wiki/BitTorrent_client)

A new version is coming soon. You can download and test the [Release Candidate]("http://deluge-torrent.org/") but I do recommend waiting a little bit, because some things are still not working.

---

### Post by kosmiciatakuja on 2008-08-30
> **aprilmot said:**
> Ya I think my problem is the point 2 you mentioned.  When I test the port I got the message "TCP port 49152 closed on 84.161.194.254 ".  When I try to get into router configuration page it is asking for a password which 
I dont know.  But my friends connected to the same router are able to download torrent files.

Let's distinguish two things here: without the port open on the router you *are* able to download torrent files. It's just much faster with the port open. 
If the torrent file has like hundreds of seeds and peers, it's probably just the same - you should be downloading with your max bandwidth, port open or not. But if it's got like ten seeds, you probably never finish it with the port closed.

If you decide to open the port, you got two choices:
1. somebody (like your friends) logged into the router to configure it in the past, and they know the password
2. nobody logged in and therefore the password is default for the factory settings. 

1 -> ask your friends
2 -> google the exact router model number together with something like 'default password' or 'factory password'. Or find the booklet that came with the thing and 'read the friendly manual' as they say

---

### Post by lovinglinux on 2008-08-30
> **kosmiciatakuja said:**
> Let's distinguish two things here: without the port open on the router you *are* able to download torrent files. It's just much faster with the port open. 
If the torrent file has like hundreds of seeds and peers, it's probably just the same - you should be downloading with your max bandwidth, port open or not. But if it's got like ten seeds, you probably never finish it with the port closed.

This is CORRECT!

Without the port open you will only get pieces of the files from the peers that your client requests connection. When you start the torrent you have only outgoing connections, since the client retrieve the peer list from the tracker and initiate the requests. The port doesn't matter here, since the client will chose any available port to send each outgoing request. At the same time, the client scrape the tracker adding your IP to the list, so other peers clients can find you. If they try to connect to you they will receive a timeout message, because your port is closed for inbound connections.

---

### Post by airtonix on 2008-08-30
> I don't think there are any ports closed in the default installation

yes they are...before transmission would peform as expected...(with my port of choice : 5345) I had to  : 
1 - Allow incoming traffic from all hosts on port 5345 with firestarter.
2 - Forward packets from the internet arriving at port 5345 on the router to my computers port 5345

make sure you have universe repositories enabled.
```
sudo apt-get install firestarter transmission
```

---

### Post by erudite on 2008-08-30
I have both deluge and rtorrent installed.  Both work great.  I use rTorrent more but it's a little more complicated that deluge as it's got no GUI.

---

### Post by airtonix on 2008-08-30
> **erudite said:**
> I have both deluge and rtorrent installed.  Both work great.  I use rTorrent more but it's a little more complicated that deluge as it's got no GUI.

Technically rTorrent is a gui base app. It uses a library called nCurses to render the interface.

It's just that since it uses ascii characters to present it you can be mistaken in thinking that it isnt a graphical user interface.

For the record, I prefer to start up "screen" (sudo apt-get install screen), then start rTorrent from within a session in there. 

Advantages of using screen are that you do not need to keep a terminal window open for any sessions to continue operating, really is one of those tools remote sysadmins love to use.

I have rTorrent on my (now dormant due to power costs) server set up to automatically start torrents found in one folder and save the resulting files on another. Additionally it also saves itself to a session in yet another folder. 

Lastley i found a perl script to run on the server providing my webserver on the same machine with a read only view of the torrents being qued, dowloaded and completed.

Only thing that may deter earnest torrent users from rTorrent is the lack of DHT, well at least the last version i used (feisty) lacked this feature...you may find that it has this included now.

---

### Post by Vivaldi Gloria on 2008-08-30
The default ubuntu comes with all ports open. No need to make any changes in ubuntu to use p2p programs. It's all about router port and router firewall settings.

Open a terminal (Apps. > Access. > Term.) and give the command

```
sudo ufw status
```

If it comes back as

```
Firewall not loaded
```

then all ports are already open. See

```
man ufw
```

and especially the examples section for more info on it.

But I repeat again, in the default ubuntu install, firewall is NOT working and all ports are open. It's all about router port and router firewall settings.

If anyone needs a port forwarding guide then see my post here:

[http://ubuntuforums.org/showthread.php?t=891514](http://ubuntuforums.org/showthread.php?t=891514)

---

### Post by erudite on 2008-08-30
@airtonix Thanks for the explanation.

rTorrent does now support DHT to just let you know.

---

