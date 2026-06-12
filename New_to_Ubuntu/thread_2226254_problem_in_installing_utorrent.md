---
title: "problem in installing utorrent"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by tusharkoshti on 2014-05-26
Hello Friends ,
1)
I am using Ubuntu 14.04. Ubuntu has given default torrent client as Transmission. 
But I am facing problem with it. 
When I use <removed> site to download torrent , it works perfectly. Means I can download torrent file ( few kb ) and then manually open it from Transmission. 
But when I use <removed> site to download torrent, I face problem. I cant download torrent file ( few kb ). When I hit on Get this Torrent , window of Launch Application open. There is a option 
Choose Application. But I didnt find application transmission in that.
But when I use same site in Win 7 , it works perfectly. 
How to solve this problem ? 

2) 
I am trying to install utorrent with the help of following site.

[http://www.howopensource.com/2011/08/install-utorrent-in-ubuntu-fedora/](http://www.howopensource.com/2011/08/install-utorrent-in-ubuntu-fedora/)

But I can't create symbolic link so that I can run torrent server from terminal. 
How to solve this problem ? 
Thanks in advance.

---

### Post by lotharmat on 2014-05-26
Apologies, this doesn't necessarily answer your question but offers an alternative.
Deluge! It is a very capable client and is in the repos!

```

sudo apt-get install deluge

```

Hope this helps.

---

### Post by mastablasta on 2014-05-26
isn't utorrent in the repositories? if not try to get a .deb file.

you can also set tranmission to use magnet links. though i am not using that one myself. 

deluge (GTK, Gnome -i think) and ktorrent (qt, KDE) are excelent alternatives (both opensource).

---

### Post by Vladlenin5000 on 2014-05-26
Please stop suggesting other clients. It's as much ridiculous as the reason that started this thread.

@[**[COLOR=#000000]tusharkoshti[/COLOR]**]("http://ubuntuforums.org/member.php?u=1136366") - We shouldn't be helping you with that unless you're trying to use that website and the software for legal downloads. That said, the website in question usually gives two options, downloading a **torrent file** (by default associated with Transmission) or a **magnet link** (by default NOT associated with Transmission). So... Whenever available grab the torrent file (green double down arrows) instead of the magnet link (red magnet). You can associate the magnet link with Transmission and you need to do it only once. Transmission is at:
```
 /usr/bin/transmission-gtk
```
But the funny thing is you don't even need to do that because you can simply 1. copy the magnet link from the browser, 2. open Transmission and 3. File > Add URL... (your copied magnet link will be already there).

---

### Post by sandyd on 2014-05-26
Ive removed links to illegal/questionable torrent sites/domains - please dont post them here

thanks

---

