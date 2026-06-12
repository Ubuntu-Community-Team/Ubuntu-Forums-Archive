---
title: "An Ubuntu Torrent Box - I need a game plan"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by uberamd on 2008-05-25
I am building a torrent box dedicated to torrent downloading and seeding. Here is the hardware I have (arrives Tuesday):
[LIST]
[*]3.0GHz Core2Duo Processor
[*]2x 750GB SATA Hard Drives
[*]DVD-Burner
[*]4GB RAM (upgrading to 8GB RAM in a few weeks)
[*]Cube Case
[*]Mobo with Onboard Video, 8GB RAM Supported, Micro-ATX
[*]Modular PSU
[/LIST]
I plan to download content for my AppleTV. My idea is to use Ubuntu, however I am feeling out of luck when it comes to getting content from my Torrent Box onto my AppleTV. Are there any ways? I don't want to be forced into using Windows XP as the OS on the torrent box because that would be a step back for me (I am mainly Windows free, Macbook Pro as my main system and I own a few dedicated FreeBSD servers in datacenters).

I intend to control the server in 2 ways, 1) over VNC, and 2) Using torrentFlux which I use on one of my current dedi-boxes. Is that good enough?

I plan to use Azureus as the torrent application. That sound good?

What would be the best way to setup the hard drives? The mobo supports RAID, should I use both drives as 1 physical 1.5TB drive, or are there better ways?

I have a 27" LCD 1080i HDTV that I use as my main TV (as a college student, its the biggest I can afford :( ). Should I just play my content on that and bypass the AppleTV? Are there good remote-control solutions that Ubuntu supports?

Thanks for any feedback to help me on this project.

---

### Post by cozmicharlie on 2008-05-26
Sounds like you have a good start on what you need.  I can give you some info that might help based on my experience.  I have an older laptop I use as a dedicated bittorrent server.  I have a sata raid 5 configuration (on 4 hard drives in A firmtek container) that was very easy to set up on ubuntu. MDADM is the native program in Ubuntu for raid control and it works very good.  You can mount the drives directly or use LVM and create a virtual disk.  The easiest way to set Raid and LVM up is when you do the install.  When you come to the part on partitioning the drives select manual.  Find a good How To and read up on it first (from your post I get the impression you are not a begginer so you should have no problem following a good How To).  

I use Azureus because it has great plug ins for networking - I use Azsmrc plug in as the client (I wrote a How To for installing and configuring Azsmrc in these forums).  I set up azureus on my server and Azsmrc on all the clients.  Azureus also has great plug in's for remote access.  Some will claim azureus uses a lot of memory and recommend other torrent clients but I don't see it.  The plug in's for sharing over a network and the fact that is is based on java make it ideal for sharing over a network with Windows, Linux or Mac.

As per the TV part, I am not as familiar but Myth TV seems to be a good alternative.

Good luck

---

### Post by redactech on 2008-05-26
For the application managing torrent, I highly recommend to use rtorrent, it does everything you need and it is very configurable and does not take much resource (unlike azureus) along with the screen command rtorrent simply rocks.

If the box itself is headless (not to be use as desktop) then use the server base installation disk and configure samba to access the files from remote computer) after you have set it in RAID 1 + LVM

You control your torrents using ssh, to use it outside your network you may have to play with your NAT.

rtorrent is already in the repo but here the home page give few good trick on how to get the most of it [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

rtorrent is ncurse based so even if it's a CLI tool you have some sort of basic interface you just need to learn the keys to manipulate the torrent

---

