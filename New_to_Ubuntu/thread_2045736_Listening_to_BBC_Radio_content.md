---
title: "Listening to BBC Radio content"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Raphicerus on 2012-08-21
Hello all, this is my first post here. I have been using a piece of free Windows software called "Radio Downloader" to get MP3 snapshots of BBC programs. It lets me catch up with programs on a music player.

While I can still go and use this option, on my little netbook (which is still Windows 7), my main computer is now Ubuntu 12.04.  After just 2 weeks, I'm far happier with Ubuntu and would prefer to make my BBC snapshots there.

Can anyone advise on how to do the same thing in Ubuntu? Technically complicated answers are OK. I've worked as a programmer;  just woefully ignorant around Linux.

---

### Post by ron999 on 2012-08-21
> **Raphicerus said:**
> 
Can anyone advise on how to do the same thing in Ubuntu? Technically complicated answers are OK. I've worked as a programmer;  just woefully ignorant around Linux.

Hi
**get_iplayer** is OK. ;)
Website is here ---> [http://www.infradead.org/get_iplayer/html/get_iplayer.html]("http://www.infradead.org/get_iplayer/html/get_iplayer.html")

This is how to install latest version of get_iplayer from PPA ---> [https://launchpad.net/~jon-hedgerows/+archive/get-iplayer]("https://launchpad.net/~jon-hedgerows/+archive/get-iplayer")
(The version in Ubuntu repository is out of date)

```
sudo add-apt-repository ppa:jon-hedgerows/get-iplayer
```
```
sudo apt-get update
```
```
sudo apt-get install get-iplayer
```


To download the radio programmes, use commands like this...
(The pid number is part of the URL at iPlayer website)

For aac/m4a:-
```
get_iplayer --get --type=radio --pid=b01m0kj6
```

For mp3:-
```
get_iplayer --get --type=radio --pid=b01m44z6 --aactomp3
```


Also use 
```
get_iplayer --help
```

And more help is at mailing list ---> [http://lists.infradead.org/mailman/listinfo/get_iplayer]("http://lists.infradead.org/mailman/listinfo/get_iplayer")

:p

---

### Post by BDNiner on 2012-08-21
I have been looking for this as well. Thank you.

---

### Post by Raphicerus on 2012-08-22
Thanks for the detailed reply, ron999.

I installed that, and it worked like a charm. I'd recommended it to anyone who's missing Radio Downloader.

---

