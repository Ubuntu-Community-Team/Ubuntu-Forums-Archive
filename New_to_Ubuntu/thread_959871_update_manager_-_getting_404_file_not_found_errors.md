---
title: "update manager - getting 404 file not found errors"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by dustint83 on 2008-10-26
> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.4~5ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.4~5ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

im getting this error for about 50 new updates on intrepid. i have checked the actual servers and the files arent lsited, so why are they showing up in the update if they arent even avliable?

anyone else have problems with updates this past week??

also all of a sudden i can only do a partial upgrade. some packages cant be updated

---

### Post by SunnyRabbiera on 2008-10-26
well I suspect the ibex repos will be messy as its right around the corner.

---

### Post by Kaseas on 2008-10-26
Post your /etc/apt/sources.list file here.

I had a similar problem, and I solved it by removing a bad line in my sources.list file.

---

### Post by Xiong Chiamiov on 2008-10-26
Try updating the sources.list first?
```

sudo aptitude update && sudo aptitude safe-upgrade

```

---

### Post by Don_Dragon on 2008-10-30
Thanks, that solved my problem as well.  in my case, I'm guessing the sources got messed up somewhere during the release candidate and the final version of Ibex.

---

### Post by TJAB on 2010-06-30
I resolved this issue by selecting a difference software source, not necessarily the "fastest" server.   It seems the fastest servers are sometimes not so reliable.

If anyone else has similar issues, consider simply changing the software sources first, via: system>administration>software sources then chose the select box labeled "download from" and select the generic server for your country.

good luck.

---

