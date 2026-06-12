---
title: "How can I downgrade a program?"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by bachtobach on 2013-10-22
I've installed the latest qbittorrent and just realised that it is not supported on the private torrent site I use. Is there a way to downgrade to an earlier version. On Windows this was easy but it can't find a way to do it in ubuntu. 
Using Xubuntu if that makes any difference.

---

### Post by varunendra on 2013-10-24
From repositories, it is possible but only if an older version is available in it. To check which versions are available, run this command in termianl (Ctrl-Alt-T) -
```
apt-cache show qbittorrent | grep Version
```
If there is more than one, then you can try the older one with -
```
sudo apt-get install qbittorrent=*<version no. here>*
```
The <version no..> should be replaced by the version no. you want to install. For example-
```
sudo apt-get install qbittorrent=2.9.7-1
```

---

### Post by bachtobach on 2013-10-24
Thank you [**[COLOR=#DD4814][B]varunendra**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629"), that's very handy to know. Unfortunately it seems only the latest version is available. 
Thanks anyway.

---

### Post by varunendra on 2013-10-25
No problem.

Why don't you try another torrent client that maybe supported? Transmission is default one, but I am using ktorrent and also have deluge installed (didn't test it yet, just installed for windows/linux cross-compatibility of the client).

---

### Post by monkeybrain20122 on 2013-10-25
After downgrading you need to pin the version so it won't get upgraded.
```

sudo apt-mark hold qbittorrent
```

BTW, all these can be done with a gui if you install synaptic

open synaptic, search for the package you want to downgrade, right click and choose properties, it will show the versions available, then choose in the drop down Package > Forced version, after downgrading then choose Package > Pin version to pin it.

---

### Post by bachtobach on 2013-10-25
That's a great idea varunendra, I did try Deluge on Windows and I found it really horrible to use but I've just installed it and it seems to work pretty well. Qbittorrrent seemed the nicest one I looked at with lots of features but I think I'll just stick with Deluge now. 

Thanks monkeybrain20122, that's really useful. I just done that for Deluge so now I don't have to worry about incompatible torrent clients.

---

