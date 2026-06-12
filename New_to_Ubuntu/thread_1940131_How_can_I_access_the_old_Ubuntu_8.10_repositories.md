---
title: "How can I access the old Ubuntu 8.10 repositories?"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by annadaprasad on 2012-03-13
Hi everyone,

I am new to Linux and I just made a switch from Windows xp to Ubuntu 8.10 just 2 days ago. So please go easy on me. Not too much of technical stuffs.

As soon as I installed Ubuntu 8.10, I found out that Ubuntu doesn't natively support mp3, aac, wma, mkv and many other audio/video format because of copyright reasons. (Damn SOPA/PIPA). So I have to download install plugin/codec. I start the installer but it fails to fetch those files. Why? 404 Not found.

I searched the forum and found out that Ubuntu 8.10 reached its EOL or something and something happened and something can be done. So they had advised him (the one who made that thared) get a LTS version or get the latest version.

But I got a problem. I live in a rural area in India and the internet is very slow here. And it is almost impossible to download a 700 MB iso file even via a BitTorrent client. And I pay for every MB of data I use. As ShipIt has closed, so all I've got is a Ubuntu 8.10 Live CD that I got 2 years ago with my Dell laptop.

How can I get the old Ubuntu 8.10 repositories? So please advice me.

---

### Post by howefield on 2012-03-13
Hi,

I think if you change your /etc/apt/sources.list to reflect the below you will be able to download the needed codecs, 

## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

PS. If you PM me an address, I'll be happy to send you whatever Ubuntu CD you want.

---

### Post by mörgæs on 2012-03-13
If limited bandwidth is a problem, you could also try this:

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

Using this approach you will download only the packages you need (unlike a default Ubuntu).

---

### Post by annadaprasad on 2012-03-14
> **howefield said:**
> Hi, I think if you change your /etc/apt/sources.list to reflect the below you will be able to download the needed codecs,  ## EOL upgrade sources.list# Requireddeb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiversedeb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiversedeb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse # Optional#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) PS. If you PM me an address, I'll be happy to send you whatever Ubuntu CD you want. Thanks a ton. Its working like a magic! You're a wonderful guy. Once again, thanks a lot. Hey, can you please send me a UBUNTU long-term-support (which one you think will be the best) CD because I can't download a fresh copy every 6 months. Please give me you're e-mail address so I can PM you.

---

### Post by Zill on 2012-03-14
> **annadaprasad said:**
> ...But I got a problem. I live in a rural area in India and the internet is very slow here. And it is almost impossible to download a 700 MB iso file even via a BitTorrent client. And I pay for every MB of data I use. As ShipIt has closed, so all I've got is a Ubuntu 8.10 Live CD that I got 2 years ago with my Dell laptop...
You *should* be able to buy the latest Ubuntu CDs/DVDs in India.  For example, I had a quick look on [www.google.co.in]("www.google.co.in") and found [LinuxFlavour]("http://linuxflavour.co.in/store/catalog/33") offering Ubuntu v11.10 Oneiric Ocelot Full Install/ Live DVD for Rs. 100.00

---

### Post by howefield on 2012-03-15
> **annadaprasad said:**
> Its working like a magic!

Good to know :-)

You have a PM, go to top right corner of this page and you should find a link to Private Messages, click on it to review and manage your PM's.

---

