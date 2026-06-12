---
title: "Flash for Chrome?"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-07
Which flash player should I install for G Chrome & Chrome based browsers from this site [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect) & how, using what command to be typed in terminal?

Thanks.

---

### Post by will1982 on 2012-10-07
Doesn't chrome come with flash?

---

### Post by Yezinki on 2012-10-07
It does but since am having issues checked, probably a new version of Chrome is out?

---

### Post by deadflowr on 2012-10-07
Your best bet, if pepperflash in chrome is causing you trouble is to install flash on your system. I think the program in the software center will give you something like flashplugin-installer, which will download the latest and last version available for non-chrome linux(which is 11.2.xxx).
Then when you have flash installed, in the address bar type:

```
chrome://plugins
```

then click details, and click disable of the version which will either be something like 11.3, or 11.4(depending on which chrome you're using: stable, or unstable). It will be easy to tell as it will say Pepperflash in the location area.

For what I know, there is no way to downgrade the version of flash built into chrome without downgrading chrome.

---

### Post by pqwoerituytrueiwoq on 2012-10-07
Google chrome does not use adobe flash anymore, it uses pepper
if you want to use adobe flash in chrome i suggest [chromium-browser](apt:chromium-browser)

---

