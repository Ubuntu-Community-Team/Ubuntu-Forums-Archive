---
title: "Avant Window Nav. Updating Error"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Mishan on 2008-05-05
I installed Avant Window Navigator on my computer and have since uninstalled it, but when I try to update my computer it downloads the updates then gives me an error message. 

"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

It does not allow me to then install the updates and it tells me that my computer is out-of-date. I am running Ubuntu 8.04 (hardy) as well as Windows XP. I don't know what other information you might need, but thank you very much for your time.

---

### Post by Sparkalo on 2008-05-05
Hi Mishan!

It sounds to me like when you installed Avant Window Navigator, you edited your sources.list to include a couple of new repositories which have since gone offline.  What you're going to want to do is edit your sources.list file and remove the lines:
```

deb http://download.tuxfamily.org/syzygy42 (your version here) avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 (your version here) avant-window-navigator 
```

Just as a reminder to other people who may be unfamiliar with editing sources.list, the quickest way to edit the sources.list file is just to enter the following into the terminal.
```
 sudo nano /etc/apt/sources.list 
```

Delete your offending lines, and then ctrl+o to save the file before ctrl+x to exit

Hope this helps!

---

