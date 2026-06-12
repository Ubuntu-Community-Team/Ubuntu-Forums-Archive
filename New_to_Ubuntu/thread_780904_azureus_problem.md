---
title: "azureus problem"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by shayvasa on 2008-05-03
hey all
i downloaded azureus and i noticed that i get a yellow face next to my downloads and it says because i have a NAT problem, any1 knows how to fix this? it makes my downloads go really slow.

---

### Post by acelin on 2008-05-03
> **shayvasa said:**
> hey all
i downloaded azureus and i noticed that i get a yellow face next to my downloads and it says because i have a NAT problem, any1 knows how to fix this? it makes my downloads go really slow.

1) Get rid of Azureus.
2)Repeat step 1.
3) Find a new BitTorrent Client.

---

### Post by shayvasa on 2008-05-03
can u advise me of a good one for linux?

---

### Post by DeathAxe on 2008-05-03
> **shayvasa said:**
> can u advise me of a good one for linux?

[Transmission]("http://transmissionbt.com") (the default client of Hardy) is working perfectly, and is really easy to use.
Download from here [http://getdeb.net/app/Transmission](http://getdeb.net/app/Transmission) and install transmission-common before transmission-gtk


Another good one is [Deluge]("http://deluge-torrent.org/").

---

### Post by tacutu on 2008-05-03
[http://azureuswiki.com/index.php/PortForwarding](http://azureuswiki.com/index.php/PortForwarding)

---

### Post by phread59 on 2008-05-03
I really like BitTornado myself.

Mark Shuman

---

### Post by NightwishFan on 2008-05-03
Ktorrent (kde but will run on gnome without a problem)
Transmission (light and works right away)
Deluge (good configuration)

---

### Post by Can+~ on 2008-05-03
Deluge.

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot2.png[/IMG]

```
sudo apt-get install deluge-torrent
```

Also, if you have Hardy, it comes preloaded with transmission.

Why people are so loyal to Azureus? It's powerful, but it's quite slow to load up, meanwhile µTorrent on windows, or deluge/transmission on linux/MacOS load instantly.

---

### Post by NightwishFan on 2008-05-03
I used to use azureus. It was hell. :lolflag:

---

### Post by shayvasa on 2008-05-04
ok thanx all i downloaded deluge and its wworking much better but still quite slow, i dont understand why, i have adsl and from what i recall a speed of 700kb and its downloading max at 20kbs no matter which torrent, any ideas how to make it go faster?

---

### Post by nynoah on 2008-05-04
DUMP azeurious.........get rid of it, it is a system HOG!!!  

I found Deluge to have all the same features that Azeur has.  It works far better and does not bog your system down.

---

### Post by NightwishFan on 2008-05-04
Use protocal encryption and, limit your speeds to something fair.

---

### Post by shayvasa on 2008-05-04
ok i did but how will that help it to go faster?

---

### Post by shayvasa on 2008-05-04
whats protocal encryption?

---

### Post by DeathAxe on 2008-05-04
> **shayvasa said:**
> whats protocal encryption?

From [WikiPedia]("http://en.wikipedia.org/wiki/BitTorrent_protocol_encryption") :)
Peer-to-peer file-sharing traffic makes up more than a third of total internet traffic.[2] Some ISPs deal with this traffic by increasing their capacity whilst others use specialised systems to throttle (i.e. slow down) BitTorrent traffic. Obfuscation and encryption make traffic harder to detect and therefore harder to throttle. These systems are not designed to provide anonymity or confidentiality.

---

### Post by NightwishFan on 2008-05-04
If you limit your speeds relative to your connection you will make sure you do not over use download or upload. I always have a max download of 750kb/s and upload of 100kb/s. Protocal encryption will allow you to fool your ip into thinking that the the protocal is not p2p, which will bypass any throttling (slowing) they would put on it. I am not sure if that is 100% correct, but that is what I gathered so far. Also you can try enabling dht to gain extra peers, if deluge supports that, Ktorrent does. The last thing I noticed is that if you have a firewall like firestarter you might have to configure it or you will have slow download speeds. Default iptables shows no slowdowns for me though.

---

### Post by Can+~ on 2008-05-05
Open deluge:

-Edit / Preferences
-Go to Network, enable encrypt on everything (Inbound, outbound)
-Go to Bandwidth, increase the maximum of connections.

If you're behind a router, you'll have to redirect some ports to your PC. You must set your router for that. For example, opening port 60000, redirect to your pc, and in Network, set the port to 6000, better if you can set a whole range. Linksys routers are usually on the [192.168.1.1](http://192.168.1.1/)

---

### Post by shayvasa on 2008-05-05
ok thanx every1, can+ can u explain the last part better plz?

---

