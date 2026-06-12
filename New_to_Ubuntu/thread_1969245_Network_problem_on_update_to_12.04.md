---
title: "Network problem on update to 12.04"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by glad62 on 2012-04-29
unable to upgrade 11.10 to 12.o4 because of this error.

W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Where do I start please?  why Karmic?

---

### Post by williejones on 2012-04-29
This appears to be related to Karmic backports.  Try to disable the backports in Synaptic, Update and Upgrade.

---

### Post by glad62 on 2012-04-29
thanks williejones for response

we are in 'absolute beginner' forum so that's me.

I know synaptic but how disable backports, what ever they are?

Help!

---

### Post by plucky on 2012-04-30
> **glad62 said:**
> thanks williejones for response

we are in 'absolute beginner' forum so that's me.

I know synaptic but how disable backports, what ever they are?

Help!


In Update Manager,select "Settings" and your Software Sources will open.

Un-tick any line that has Karmic Backports or you can delete the lines that refer to Karmic as you don't need them.

Good luck

---

### Post by TBABill on 2012-04-30
Once you do that in synaptic, make sure to hit reload. That's the same as apt-get update.

---

