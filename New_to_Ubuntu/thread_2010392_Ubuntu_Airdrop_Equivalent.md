---
title: "Ubuntu Airdrop Equivalent?"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by mapes12 on 2012-06-25
Is there an Ubuntu equivalent to the Mac Lion Airdrop facility? I'm aware of Dropbox and SSH stuff but I just want a simple one click solution to access files from my other laptops. I've Googled this and come across Aircrack but I don't want to "crack" wifi encryption.

Mark

---

### Post by Paqman on 2012-06-25
What OSes do your other machines run? All Ubuntu machines come with Ubuntu One, which will sync files between Ubuntu machines. There's also a client for Windows, but the Mac one hasn't been released yet.

The best solution for completely cross-platform sync is still Dropbox.

---

### Post by mapes12 on 2012-06-25
Thanks Paqman. The problem I have in the UK is very slow upload broadband speed for cloud services. A 1GB video file will take most of the night to upload to Dropbox, where to my Mac via Airdrop takes no time at all across my home Wifi LAN.

---

### Post by Paqman on 2012-06-25
Right, you can share folders across your own network. Right click on any folder and hit "sharing options". This will allow you to set up that folder as a Windows network share, which should be accessible by pretty much anything. It's not quite an automated sync, but if both machines are on then that folder would be accessible to both. Not quite what you're after, I know.

Ubuntu One is supposed to sync across local networks [eventually]("https://blueprints.launchpad.net/ubuntuone-client/+spec/desktop-o-ubuntuone-lan-sync"), but right now it always uses the internet, which sucks for the reason you point out.

Personally I use network attached storage at home, which needn't be a massive effort to set up. A lot of routers can take a USB stick these days and use that as a share that any machine on the network can access.

---

### Post by sandyd on 2012-06-25
dropbox syncs accross the network.
I personally have an amazon s3 bucket mounted via s3fs on all my computers, but that is just me.

---

### Post by mapes12 on 2012-06-26
> 
dropbox syncs accross the networkI'll give it a try.

Thanks everyone ):P

---

### Post by IWantFroyo on 2012-06-26
Another thing you could do is to set up a file server and use ftp.

Dropbox works well, however.

---

### Post by inashdeen on 2012-06-26
IMHO ,
ubuntuone works well for me, though i cant really guarantee on the speed though.

by the way, take a look here [http://alternativeto.net/software/airdrop/]("http://alternativeto.net/software/airdrop/")

---

### Post by sandwormblues on 2012-12-22
Airdrop is unlike Dropbox or FTP in that it creates an ad-hoc wireless network for direct point to point transfer.  A router / access point / dhcp server is not necessary.

There's an open airdrop knockoff for Linux called [Giver]("http://code.google.com/p/giver/").  It works pretty good! :D

---

