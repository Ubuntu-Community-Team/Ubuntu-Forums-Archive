---
title: "Update and Upgrade 404 errors"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2013-01-28
Hello there. 

When I manually update and upgrade ```
sudo apt-get update && sudo apt-get upgrade
``` the following errors are mixed within the update/upgrade process ```
Err http://ppa.launchpad.net precise/main Sources                       
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages              
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

What does this mean, and how do I fix this? 


Thanks

K.m

Edit: And also when there is software updates, it states that some could not be updated, such and such has to be installed. Then it says, it cannot be installed because ... and them two 404 up above appear.

---

### Post by arpanaut on 2013-01-28
There are no packages for precise in that repository.
[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/)

Go to "Software Sources" > "Other Software" and uncheck those two entries.
Try again with the update and upgrade and if there are additional errors post them here.

---

