---
title: "What is the best Bit Torrent Client for Ubuntu?"
date: 2012-07-26
forum: Recurring Discussions
---

### Post by idonald on 2012-07-26
I used uTorrent in Windows but it seems to be some kind of server for ubuntu which I can't figure out how to use.  There looks to be a fair amount of torrent clients out there, what is the best one in terms of speed and functionality?

Thanks

---

### Post by Cheesemill on 2012-07-26
I use [Deluge]("apt:deluge").

---

### Post by Grenage on 2012-07-26
Deluge is a pretty good client; I'll second that.

---

### Post by errrn on 2012-07-26
I use transmission. simple, but does everything I need.

---

### Post by angry_johnnie on 2012-07-26
it depends on what you're looking for.  deluge is much like utorrent.  transmission is much simpler, but it gets the job done.  i prefer simple, but that's just me.

transmission is included by default with ubuntu.

---

### Post by claracc on 2012-07-26
I use ktorrent. Fully featured.

---

### Post by greenpeace on 2012-07-26
+1 for Transmission... couldn't be simpler or easier to use!

---

### Post by vasilbelarus on 2012-07-26
I use Ktorrent on Kubuntu and Transmission on Ubuntu. Transmission is simple, Ktorrent have much more settings.

---

### Post by philinux on 2012-07-26
Moved to recurring discussions.

---

### Post by idonald on 2012-07-26
Thanks guys I will check Deluge and Transmission

---

### Post by idonald on 2012-07-27
Trying Transmission atm, seems fine although for some reason I am not seeding anything so will need to look into that further.  My chosen port is open so maybe its just my connection sucks :-)

---

### Post by BrokenKingpin on 2012-07-27
qBittorrent. It only brings in a few QT libs and no KDE libs... so don't worry. Deluge is decent, but I found it didn't work after one of the Ubuntu upgrades, and it feels a bit chunky.

Transmission sucks. I try it every new Ubuntu release and it gets horrible speeds. I am not sure why this is because I do not see the issue with qBittorrent or Deluge.

---

### Post by ratcheer on 2012-07-27
I like **Transmission**. It is easy to use and it always works.

Tim

---

### Post by 14quartz on 2012-07-27
Transmission. It's the best for Ubuntu & installed by default.

---

### Post by raja.genupula on 2012-07-27
+1 for Deluge .....

---

### Post by BigSilly on 2012-07-28
I have never used bittorrent before, but would like to give it a try. Is it quicker than a regular download? Is it safe to use, and what other points would you recommend I consider before trying it out? I'm using Kubuntu and I see KTorrent is installed so I would likely use that. I guess I'm a bit behind the times... :D

---

### Post by Version Dependency on 2012-07-29
I've used Transmission, Deluge, and Vuze on Ubuntu.  I liked Transmission the least.

---

### Post by idonald on 2012-08-03
I'm still using transmission.  I like the simplistic approach to it, the speeds seem fine.  The uploads are working too.  It feels very lightweight.

---

### Post by Sandertje on 2012-08-03
> **BigSilly said:**
> I have never used bittorrent before, but would like to give it a try. Is it quicker than a regular download? Is it safe to use, and what other points would you recommend I consider before trying it out? I'm using Kubuntu and I see KTorrent is installed so I would likely use that. I guess I'm a bit behind the times... :D

Torrents are not quicker than regular downloads, unless the server in your regular download is the limiting factor. With torrents, you are left to the whoes of popularity. Torrents are distributed, which means that you download from people that are also downloading (i.e., the peers). There also are people who have finished downloading and only upload (i.e. seeds). So unlike regular downloads - which get slower after more people try to use it - torrents become *quicker* with more users, although you will never go faster than the max your connection is able to do.

This also means that relatively popular files will be easy to obtain, but more obscure stuff will have virtually no peers and hence no-one to download from. 

I therefore personally prefer usenet; lot quicker in many circumstances ;-).

---

### Post by vexorian on 2012-08-05
I never had the need to do anything that transmission cannot do. And it is the one that integrates best with ubuntu.

> 
I have never used bittorrent before, but would like to give it a try. Is it quicker than a regular download? Is it safe to use, and what other points would you recommend I consider before trying it out? I'm using Kubuntu and I see KTorrent is installed so I would likely use that. I guess I'm a bit behind the times... It's very full of factors.

When the thing you are downloading is very popular and your bandwidth is very good, then torrents might be the thing for you. It is distributed so you are not limited to a speed cap on a single server. And when there are plenty of seeds you can get to use all your bandwidth downloading.

Torrents are also good for downloading large files, because they can always be paused and they transmit themselves by packets with verification codes so a failed byte is not going to corrupt the whole archive.

The bad thing is that if the thing you want to download is not so popular, there might be few seeders (or ZERO seeders, in which case you'll download will not happen) and you might take ages to download.

In my case, my bandwidth is very poor. So, even a server that intentionally limits free downloads to 20kbps uses the best download speed I can get :/ So I usually do not use torrents... Unless the file in question only exists as a torrent in the net.

There is a catch, and it is that the download is distributed, which means that you might be uploading some packets to other people while you download other packets. Also, if you care about the file you are downloading not getting lost in the void, you might be interested in leaving the torrent open *after* you finish downloading it. In fact, maybe you might like to wait till you upload at least twice of what you uploaded. Some trackers may actually enforce you to keep a good percentage between upload and download.

---

