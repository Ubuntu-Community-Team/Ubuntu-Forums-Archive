---
title: "HOWTO: Torrent Broadcatching"
date: 2006-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by gasparov on 2006-11-14
**Background**

Broadcatching is the downloading of content that has been made available over the Internet using RSS syndication for listening on mobile devices and personal computers.

The general idea is to use an automated mechanism to aggregate various web feeds and download content for viewing or presentation purposes. (quote from [Wikipedia]("http://en.wikipedia.org/wiki/Broadcatching"))

**Introduction**

This script works with particular torrent clients like azureus and mldonkey. These clients must be able to periodically fetch torrents from a directory and put them in the queue. If you need it and you can't do it yourself I can fix the script for torrentflux .
As for feeds not every feed works,you can use direct torrent link feeds (the feed has a link in it,you click on it and you get the torrent,not the web page about torrent details) or feeds from mininova.

**Requirements**

[LIST]
 
	[*]Some basic ones like bash , wget and sed
	[*]xsltproc (sudo apt-get install xsltproc)
	[*]A torrent client (see "Introduction")
[/LIST]

**Set It Up**

make a directoy and cd into it

```
mkdir scripts
cd scripts

```

get the tarball
```

wget http://www.lucagasperini.com/files/torbcatch.tar.gz
tar -zxvf torbcatch.tar.gz
cd torbcatch
gedit tvrss.sh

```
and modify the easy CONFIGURATION PARAMETER (is just one)

enable cron 

```
gedit /etc/crontab
```

and add this line at the end (change "%USER" with the user you want to run the script , for both instances)
```

02 * * * *   %USER     /home/%USER/scripts/torbcatch/tvrss.sh
```
restart the cron daemon

**How it works**

The file bp.conf is a simple configuration file that contains the urls of the feeds you want to broacatch in this form

```
caseinsensitiveRegExp@http://urltofeed.com/feed.rss
```

You can use RegExp but you don't have to (I don't), if you leave it empty a wildcard (*) match will be performed.(if so remove the "@" too)

```
NonRegExp Example
```

You are interested in a Video Podcast called "UbuntuCast" but the official feed is unreliable, you can make a search on mininova.org for it.You find out that there are two Podcasters whose show have the same title,one is called "TENFE" and the other "VTZE" so you can change your search parameters and look for "UbuntuCast VTZE".Now it should be better and the results should be a better match.Another problem arises,there are two versions of "UbuntuCast VTZE", one is in HDTV and is 350 Megs the other is with 5.1 sound and is 700 Megs,you don't have 5.1 and you want the 350 megs one. Looking for something like "UbuntuCast VTZE -HR" should do the trick.Ok now the results should be the one you are looking for.Look at the RSS icon with orange background ,thats the rss feed of your results,copy its link and put it in bp.conf.Done

**Another example**

For obvious reasons I didn't post this part on ubuntuforums, [have a look here]("http://www.lucagasperini.com/blog/2006-torrent-broadcatching/").It's a small tip for having lots of torrents on a single feed from a releaser.... I'm kinda paranoid.

**Conclusions**

The first time you run the script all the torrents it finds will be downloaded , after that it remembers the one you already downloaded.Be aware that the first time all the torrents will be added to you client's queue,maybe it could be a good idea to change the directory where the script will move the torrent and change it back again after the first run.
Isohunt has tons of trackers but files shows up later than mininova. Best way is to use an official feed from the releaser.

**Credits**

[Me (gas)]("http://www.lucagasperini.com/blog/")
[Linc]("http://linc.homeunix.org:8080/scripts/bashpodder/")
[Mldonkey Community]("http://mldonkey.sourceforge.net/Broadcatch")

Happy Broadcatching ;)

---

### Post by abhiroopb on 2009-09-14
Hi,

I am interested in this program, but it appears that your site is no longer running.

Could you send me the script please!

Thanks

---

### Post by h0me5k1n on 2009-10-01
The original script is here:

[http://mldonkey.sourceforge.net/Broadcatch]("http://mldonkey.sourceforge.net/Broadcatch")

It downloads torrents from rss feeds and automatically submits them to mldonkey...  but could also be customised to download the torrents to a folder (ready to be picked up by a torrent client)

---

### Post by abhiroopb on 2009-10-01
Hi,

Thanks for responding. Actually I posted on another thread and this kind soul wrote a very simple python script that downloads torrents to a folder and transmission watches this folder.

[http://www.uluga.ubuntuforums.org/showpost.php?p=7949235&postcount=19](http://www.uluga.ubuntuforums.org/showpost.php?p=7949235&postcount=19)

---

