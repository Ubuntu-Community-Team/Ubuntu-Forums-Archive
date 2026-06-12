---
title: "[SOLVED] Are Repositories for End-Of-Life releases still available?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by k3lt01 on 2008-10-13
I have been a regular reader/user of [BobSongs fine thread of how to create your own repository DVDs]("http://ubuntuforums.org/showthread.php?t=352460")and have used it for the versions of Ubuntu I have personally used (7.04 i386, 7.10 i386, 8.04.1 i386). In one of his last updates to his tutorial BobSongs removed Edgy Eft as it had reached End-Of-Life status. 

Today I went looking for the repos of the End-Of-Life releases thinking that they would at least be kept in archive. I did this to see if I could start downloading them because I would like a copy of each version
1: for prosperity (yeah I know I really need to get out into the sunlight more), 
2: to be able to show students how Ubuntu has progressed, and 
3: to be able to help people with older PCs and Laptops who aren't worried at the moment about having the latest and greatest versions but would like to try it out to see what it is like so they can make an informed choice about updating later on.
4: To create an Ubuntu Library of the Repos.

My questions here are:
1. Are these repos still available somewhere online?
2. If yes, where are they?
3. If no, is there a way to make them available again?

It wont be the end of the world if I cant get them but it would be good if I can. I still have all of Windows 3.1, 95c, 98SE, 2000, and even though  am not personally using XP or Vista anymore I have all the Service Packs for them to, this allows me to help keep friends archaic PCs going. I think it would be good to show Ubuntu the same, more actually because it is better, loyalty that I showed Windows over the years.

---

### Post by kostkon on 2008-10-13
> **k3lt01 said:**
> I have been a regular reader/user of [BobSongs fine thread of how to create your own repository DVDs]("http://ubuntuforums.org/showthread.php?t=352460")and have used it for the versions of Ubuntu I have personally used (7.04 i386, 7.10 i386, 8.04.1 i386). In one of his last updates to his tutorial BobSongs removed Edgy Eft as it had reached End-Of-Life status. 

Today I went looking for the repos of the End-Of-Life releases thinking that they would at least be kept in archive. I did this to see if I could start downloading them because I would like a copy of each version
1: for prosperity (yeah I know I really need to get out into the sunlight more), 
2: to be able to show students how Ubuntu has progressed, and 
3: to be able to help people with older PCs and Laptops who aren't worried at the moment about having the latest and greatest versions but would like to try it out to see what it is like so they can make an informed choice about updating later on.
4: To create an Ubuntu Library of the Repos.

My questions here are:
1. Are these repos still available somewhere online?
2. If yes, where are they?
3. If no, is there a way to make them available again?

It wont be the end of the world if I cant get them but it would be good if I can. I still have all of Windows 3.1, 95c, 98SE, 2000, and even though  am not personally using XP or Vista anymore I have all the Service Packs for them to, this allows me to help keep friends archaic PCs going. I think it would be good to show Ubuntu the same, more actually because it is better, loyalty that I showed Windows over the years.
Officially down, but the repos are still available at [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

Thus, for example, the sources list for *Edgy* can be like that:
```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted

deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted

deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted

deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted

deb http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse

deb-src http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse

deb http://old-releases.ubuntu.com/ubuntu edgy-security main restricted

deb-src http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
```

---

### Post by k3lt01 on 2008-10-13
Thanks Kostkon thats what I was looking for.

---

