---
title: "Whats up will Deluge? 90% completed download is now at 50% after auto hash check."
date: 2008-05-09
forum: New to Ubuntu
---

### Post by kpkeerthi on 2008-05-09
OK... I was downloading a 4GB torrent with deluge. This morning when I shutdown my PC, deluge was at 90% complete. Now when I launched deluge again, it performed a hash check on the torrent (I don't know why?) and it reset the progress to 50%. Where did the remaining 40% go? And with a 4GB content I have lost a substantial portion of my download? It is now at 55% progress. Damn.

---

### Post by TheLions on 2008-05-09
> **kpkeerthi said:**
> OK... I was downloading a 4GB torrent with deluge. This morning when I shutdown my PC, deluge was at 90% complete. Now when I launched deluge again, it performed a hash check on the torrent (I don't know why?) and it reset the progress to 50%. Where did the remaining 40% go? And with a 4GB content I have lost a substantial portion of my download? It is now at 55% progress. Damn.

hash check probably detected damaged files/wrong pieces.anyway after completed download hash check would reset your progres...

---

### Post by kpkeerthi on 2008-05-09
Thats what I've been thinking of (googled a bit too). Thanks for the insight.

---

### Post by kpkeerthi on 2008-05-09
I've been a long time rTorrent user. I find deluge as fast as rTorrent (I compared the speed using the same torrent in both the client). And I can set max number of active torrents that I've been missing in rTorrent. Sweet!

Now who says deluge is slow? :)

---

### Post by TheLions on 2008-05-09
why rTorrent???

what Azureus don't have???

---

### Post by prshah on 2008-05-09
> **kpkeerthi said:**
> OK... I was downloading a 4GB torrent with deluge. This morning when I shutdown my PC, deluge was at 90% complete. Now when I launched deluge again, it performed a hash check on the torrent (I don't know why?) and it reset the progress to 50%. Where did the remaining 40% go? And with a 4GB content I have lost a substantial portion of my download? It is now at 55% progress. Damn.

I often loose progress (80%->0%, 75%->40$, 100%->20%, etc) in deluge; but a quick force-recheck (right-click torrent) immediately brings back the missing stuff.

ymmv.

---

### Post by kpkeerthi on 2008-05-10
I'm getting really sick of it now. 

I let it continue from 50% to 82%. It was at 82% when I closed deluge this morning. Now starting it again, the progress went back to 67%. What the heck is going on. Never faced such issues before (with rTorrent).

---

### Post by kpkeerthi on 2008-05-10
Thanks Prshah. I forced hash recheck but it keeps winding back to 67%. My torrents usually run unattended during off-hours so manually forcing recheck is not an option for me, unfortunately.

---

### Post by kpkeerthi on 2008-05-10
> **TheLions said:**
> why rTorrent???

what Azureus don't have???
Azureus is good. But it has too many bells & whistles that make it too heavy for my liking. Neither will I be using them nor will I sit in front of azureus all the time and admire those useless fancy stuffs. It is simply not for me. I need something simple and functional along the lines of rTorrent.

rTorrent doesn't seem to support queues and the ability to set maximum active torrents, natively. I'm currently evaluating deluge but I've been having this  annoyance with it - it seems to forget its download progress and keeps winding back to some arbitrary state.

---

### Post by shifty_powers on 2008-05-10
> **kpkeerthi said:**
> Azureus is good. But it has too many bells & whistles that make it too heavy for my liking. Neither will I be using them nor will I sit in front of azureus all the time and admire those useless fancy stuffs. It is simply not for me. I need something simple and functional along the lines of rTorrent.

rTorrent doesn't seem to support queues and the ability to set maximum active torrents, natively. I'm currently evaluating deluge but I've been having this  annoyance with it - it seems to forget its download progress and keeps winding back to some arbitrary state.

have you ever thought of utorrent? a great fully featured, but very lightweight package. you do have to run it through wine but it works brilliantly.

Won't touch aby other torrent client, even on linux ;)

---

### Post by kpkeerthi on 2008-05-10
I would  use utorrent if there is a native linux version of it. 

Sorry no wine. I don't like running windows applications in linux using wine. I would rather use windows but I don't want to. Thanks for the suggestion.

---

### Post by monolux on 2008-05-10
Got the same Problem 80% went to 20%! Thats terrible!! But I noticed that when there are few files in the torrent the problem doesn't occur.

---

### Post by phoenix_abhi on 2008-05-29
The same problem in Transmission also, it loses 3-5 % every time log back to the Ubuntu

---

### Post by kpkeerthi on 2008-05-29
> **monolux said:**
> Got the same Problem 80% went to 20%! Thats terrible!! But I noticed that when there are few files in the torrent the problem doesn't occur.

Yeah. That doesn't happen with fewer files. 

There were around 450 files totaling 2.9 GB in the torrent it occurred.

---

### Post by monolux on 2008-06-01
> **kpkeerthi said:**
> Yeah. That doesn't happen with fewer files. 

There were around 450 files totaling 2.9 GB in the torrent it occurred.

Really that weird with me it doesn't happen!!

---

### Post by stanz on 2008-06-02
I've recently got deluge and had no prob @ ....lets say, pirate ...bay,...
It's a more con'figging apt to work with...that I can deal with.
Will post more if anything turns freaky.

---

### Post by dmm1285 on 2008-06-02
I had the same problem with deluge. I eventually gave up on it and switched to ktorrent.

---

### Post by imasickboy on 2008-06-02
It may be a couple of things. First, the data may be coming in faster than it can be written to the disc, and cached as it attempts to catch up. If you shut down before it is able to write that data from the cache, it gets lost. Possible, but unlikely, since you are talking about roughly a 1.6 gig loss.

The other thought I had was that it probably isn't completely aware of the total size of the to-be-downloaded files. If you go to the Deluge preferences, then on the first tab, "Downloads", do you have "Use Full Allocation" or "Use Compact Allocation" checked? If you are using compact, the progress bar may be based upon what it sees allocated, not what is actually supposed to be incoming. I don't know the inner workings of Deluge to confirm how it reads progress, but it is a possibility. 

Also, one additional thing to try, also in the preferences, under the "Other" tab, try checking, (or unchecking), the detailed progress bar.

---

### Post by kpkeerthi on 2008-06-02
> **imasickboy said:**
> 
The other thought I had was that it probably isn't completely aware of the total size of the to-be-downloaded files. If you go to the Deluge preferences, then on the first tab, "Downloads", do you have "Use Full Allocation" or "Use Compact Allocation" checked? If you are using compact, the progress bar may be based upon what it sees allocated, not what is actually supposed to be incoming. I don't know the inner workings of Deluge to confirm how it reads progress, but it is a possibility. 

Also, one additional thing to try, also in the preferences, under the "Other" tab, try checking, (or unchecking), the detailed progress bar.

Thanks imasickboy for the insight. I have full allocation checked (I read somewhere that compact allocation might incorrectly display the progress). Also, I have unchecked detailed progress bar.

Ever since I faced this problem, I have not tried downloading large torrents with deluge again. I'm gonna try downloading the torrent again with version 0.5.9.1 and see how it handles.

---

