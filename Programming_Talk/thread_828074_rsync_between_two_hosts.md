---
title: "rsync between two hosts"
date: 2008-06-13
forum: Programming Talk
---

### Post by boupartac on 2008-06-13
Hi all,

I currently have two file servers. One has many files on it, and the other is brand new. I would like to synchronize them, in a realtime manner, so as soon as the master has a new file, the slaves will get them.

Those two (and more in the future) servers will be load-balanced with a fully-functional IPVS server.

I know that rsync can be used for that kind of job. I am wondering how to implement this, in order to make rsync "watch" a directory located on server A, and rsync any occurring changes to server B, to the same location, in _real_ time. And this, as long as the two servers are running.

Thus, a user connecting to our load-balanced "media cluster" would have the same results, even if the connection is being load-balanced to server A or B.

Do you guys know how to implement this?

Thanks for your help.

Chris a.k.a. boupartac :)

---

