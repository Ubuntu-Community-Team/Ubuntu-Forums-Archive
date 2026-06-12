---
title: "[SOLVED] downloaded videos"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by _sphinx_ on 2008-10-17
Just for curiosity, where are downloaded videos kept in the file system, if we are just viewing them from the firefox. I mean if have just watched a video on youtube on firefox, then according to trivial sense it should reside in the cache folder of the firefox. But after taking a close look to cache folder in firefox I was not able to locate a any file that was even modified after last week. Can anybody explain this thing and also the place where I can find the video.
TIA

---

### Post by HittingSmoke on 2008-10-17
> **_sphinx_ said:**
> Just for curiosity, where are downloaded videos kept in the file system, if we are just viewing them from the firefox. I mean if have just watched a video on youtube on firefox, then according to trivial sense it should reside in the cache folder of the firefox. But after taking a close look to cache folder in firefox I was not able to locate a any file that was even modified after last week. Can anybody explain this thing and also the place where I can find the video.
TIA

Add VideoDownloadHelper from the firefox add ons page. It will let you download video from most flash based sites.

---

### Post by AnonymousFan9 on 2008-10-17
hmm well on my computer it's in ~/.mozilla/firefox/[some weird number].default/cache

---

### Post by _sphinx_ on 2008-10-17
I know a lot of software that do the same but I don't want that, I mean just after viewing a video, the video should be somewhere on your computer. I just want to know the place where they keep this thing. In Gutsy I was able to find a "recently" viewed video on firefox in the cache folder of the firefox. But now I am on the Intrepid(beta) and now I am not able to find any file in the cache folder that is even modified before one week with all having size in KBs. Can anybody explain that?

---

### Post by _sphinx_ on 2008-10-17
> **AnonymousFan9 said:**
> hmm well on my computer it's in ~/.mozilla/firefox/[some weird number].default/cache

Not able to find video in this on Intrepid(beta). This thing used to work on Gutsy. :(

---

### Post by HittingSmoke on 2008-10-17
> **_sphinx_ said:**
> I know a lot of software that do the same but I don't want that, I mean just after viewing a video, the video should be somewhere on your computer. I just want to know the place where they keep this thing. In Gutsy I was able to find a "recently" viewed video on firefox in the cache folder of the firefox. But now I am on the Intrepid(beta) and now I am not able to find any file in the cache folder that is even modified before one week with all having size in KBs. Can anybody explain that?

You tried checking your Firefox settings to make sure it isnt clearing cache on close?

---

### Post by _sphinx_ on 2008-10-17
> **HittingSmoke said:**
> You tried checking your Firefox settings to make sure it isnt clearing cache on close?

Yes, I checked it before. It was off. 
But I just noticed that my Cache folder was owned by root with no permission given to me. I don't know how it happened. But even after changing the ownership and the permissions also, the Cache folder was not able to store the cache. 
Also when I hit clear cache in firefox, then it is not able to clear the content of that folder. How??

---

### Post by _sphinx_ on 2008-10-17
OK Its' solved. I changed the permission and ownership. After that I "restarted" the firefox and now its working. Thanks to all.

---

### Post by handydan918 on 2008-10-17
> **_sphinx_ said:**
> Just for curiosity, where are downloaded videos kept in the file system, if we are just viewing them from the firefox. I mean if have just watched a video on youtube on firefox, then according to trivial sense it should reside in the cache folder of the firefox. But after taking a close look to cache folder in firefox I was not able to locate a any file that was even modified after last week. Can anybody explain this thing and also the place where I can find the video.
TIA

Try /tmp

---

