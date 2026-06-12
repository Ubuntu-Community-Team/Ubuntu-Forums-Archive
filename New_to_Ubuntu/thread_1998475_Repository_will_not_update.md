---
title: "Repository will not update"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-06-06
The terminal reports errors when I run "update". Viz.:

W: Failed to fetch [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


This seems to be the problem, but I don't understand what to do to fix it. This is what /etc/apt/sources.list.d shows:

deb [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu) precise main
deb-src [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu) precise main

---

### Post by sammiev on 2012-06-06
> **Mark_in_Hollywood said:**
> The terminal reports errors when I run "update". Viz.:

W: Failed to fetch [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


This seems to be the problem, but I don't understand what to do to fix it. This is what /etc/apt/sources.list.d shows:

deb [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu) precise main
deb-src [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu) precise main

Edir your source list and # out those two line in your source and try to update. Your problems lie there.

---

### Post by fantab on 2012-06-06
> **Mark_in_Hollywood said:**
> This seems to be the problem, but I don't understand what to do to fix it. This is what /etc/apt/sources.list.d shows:

deb [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu) precise main
deb-src [http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu](http://ppa.launchpad.net/thomas-hinkle/gourmet/ubuntu) precise main

This can happen if the ppa in question is no longer available or might not be working temporarily.

Comment out the the above two lines i sources.list and run update.

---

### Post by Gleichsnerd on 2012-06-06
What's happening is that either the links to launchpad are now faulty or the author switched it to private. You can edit your repositories through Update Manager quite easily (Settings -> Other Software -> Either uncheck the box for the link or remove the link if you don't think you'll get around to fixing it or if you really don't need it)

---

### Post by raja.genupula on 2012-06-06
+1 to all posts . But sometimes will appear because of temporarily server down issues .So what i suggest is switch mainserver or best server and then update again . If error still exists then as our friends saying uncheck those PPA from other software TAB in the settings of update manager .

---

