---
title: "BitTorrent question"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by kvorion on 2008-09-23
This question is not related to Ubuntu in any way, but I was hoping someone here could point me to a place where I can get some help.
Basically I am trying to determine how exactly is your download speed using a BitTorrent client determined. I know that there are multiple factors that affect download speed in general, but there would be a theoretical maximum that one can get which is especially dependent on your upload speed.

Could somebody tell me where I could find the answer to my question. I have rummaged through several papers and forums but I was not able to find the answer to this question.

Any help would be appreciated.

---

### Post by willca on 2008-09-23
Most likely not quite the answer you are looking for. But it does give a bit of an idea how the speed settings affect your down/uploads.

[http://torrentfreak.com/optimize-your-bittorrent-download-speed/](http://torrentfreak.com/optimize-your-bittorrent-download-speed/)

---

### Post by TriSwords on 2008-09-23
I dont know much about BitTorrent but you're upload and download speeds should be independent based off what type of internet you have the the connection speed.

I would guess the major factors determining speed would be the number of peers you are connected to, the speed THEY are uploading at and the speed of your internet. 

A 1Mbps cable line would move much slower than a 8Mbps cable line at downloading the data. Also those lines would upload at different speeds (8 much faster than the 1 based off whatever upload speed they had). So you could be connected to 25 uses all who have dial up modems and be getting very little download speed speed, or 25 8Mbps users (which might give you a better speed). My guess would be that the amount of data you could bring in would still be capped by the download speed of your ISP.

---

### Post by kvorion on 2008-09-23
> **TriSwords said:**
> I dont know much about BitTorrent but you're upload and download speeds should be independent based off what type of internet you have the the connection speed.

I would guess the major factors determining speed would be the number of peers you are connected to, the speed THEY are uploading at and the speed of your internet. 

A 1Mbps cable line would move much slower than a 8Mbps cable line at downloading the data. Also those lines would upload at different speeds (8 much faster than the 1 based off whatever upload speed they had). So you could be connected to 25 uses all who have dial up modems and be getting very little download speed speed, or 25 8Mbps users (which might give you a better speed). My guess would be that the amount of data you could bring in would still be capped by the download speed of your ISP.

To make things very simple, I could assume that all the seeds/peers involved in the system (including mine) have identical bandwidths. That would make this argument simpler wouldn't it? I am trying to consider this from a purely theoretical standpoint to determine how the download speed could be affected by the upload speed (my own and that of others).

---

### Post by kvorion on 2008-09-23
> **willca said:**
> Most likely not quite the answer you are looking for. But it does give a bit of an idea how the speed settings affect your down/uploads.

[http://torrentfreak.com/optimize-your-bittorrent-download-speed/](http://torrentfreak.com/optimize-your-bittorrent-download-speed/)

Yes, already read that. Thanks nevertheless.

---

### Post by Greyed on 2008-09-23
> **kvorion said:**
> I am trying to consider this from a purely theoretical standpoint to determine how the download speed could be affected by the upload speed (my own and that of others).

The only place where your upload speed will have an effect on your download speed is in ACKing (acknowledging) packets either at the IP or Application layer.  In short, if you give all your upload bandwidth over to the torrent client and it is using it all to send data then the ACKs are delayed which, in turn, delays the next packet from your peer and thus lowering your download speed.  Save a few k of your upload bandwidth for ACKs and you're golden.

---

