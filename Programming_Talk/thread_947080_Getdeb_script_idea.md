---
title: "Getdeb script idea"
date: 2008-10-13
forum: Programming Talk
---

### Post by goodrench on 2008-10-13
I have been thinking about making a bash script that will use the rss feed from getdeb.net and when there is a new item posted the script will give either a tray notification or a dialog box that will give the options to 'download/view(the webpage)/ignore' the new item in the feed. I hope this is clear what I want it to do.
I do subscribe to the rss feed in my feed reader but I thought it wold be cool to add a few options to the notifications.
The feed itself does not supply a direct download to the .deb files, so I am not sure how to make the script find the download link.
Is anyone interested in helping with this?
I am also not sure if it would be better written in python or bash. I know nothing about writing python scripts but it seems to be a popular alternative to bash.

BTW - I have added the getdeb repos to my sources.list file but I want to be notified of NEW items in the feed.
I know this may not sound usefull but I just want to play around and see what can be done with this idea.

---

### Post by goodrench on 2008-10-13
I have some commands that I have been playing with.

wget [http://www.getdeb.net/rss.php?distro_id=9](http://www.getdeb.net/rss.php?distro_id=9)

cat rss.php\?distro_id\=9 | head -n 12 | grep release

Output is 

            <link>http://www.getdeb.net/release.php?id=3269</link>

The link is what links to the newest item.
If you add a '0' to the end of the link it will be the link to the actual .deb download.

[http://www.getdeb.net/release.php?id=3269/0](http://www.getdeb.net/release.php?id=3269/0)

I don't know how to grab that link from the output so that I can pass that along to wget or firefox or whatever I want the script to do.

---

### Post by goodrench on 2008-10-14
Correction
The 4 digit number is the pattern I want to extract from the link.
I was not paying attention in my last post.
If I can extract that number in that link I can finish the rest of the script. does anyone know how to do this?

---

### Post by goodrench on 2008-10-14
Update...

I found a script to extract the link from this site

[HTML]http://www.comp.eonworks.com/scripts/scripts.html
[/HTML]
called urlext
I have used it in the following context.

```
cat rss.php\?distro_id\=9 | head -n 12 | grep release  > getdeb.txt
urlext getdeb.txt | tail -c 5 > download.txt

```
The end result is the 4 digit number in the download.txt file.
How can I extract that number from the txt file and use it in the script?
if i 'cat' the file I get '3269'
I want to be able to add that number to a wget line.

```
wget http://www.getdeb.net/download/"$4digitnumber"/0

```
or something similar.

The actual wget line will be

```
wget http://www.getdeb.net/download/3269/0

```

---

### Post by loell on 2008-10-14
hey, you seem lonely up here :)

if you are planning to parse an html to get the download link then python might be more suitable.

---

### Post by goodrench on 2008-10-14
Are you fluent in python?
I am hoping someone reads this and has some input or at least some criticism to offer.

---

### Post by loell on 2008-10-15
> **goodrench said:**
> Are you fluent in python?
I am hoping someone reads this and has some input or at least some criticism to offer.

honestly, i only know a tad about python.. but i could try later ;) not if some python whiz saves the day first. :D

---

### Post by goodrench on 2008-10-15
Cool. Thanks loell.
In the mean time, I will keep at it.

---

### Post by loell on 2008-10-15
> **goodrench said:**
> Cool. Thanks loell.
In the mean time, I will keep at it.

a very simple python script, for getting getdeb's new packages and its respective links. [python-feedparser]("apt:python-feedparser") is a preriquisite for this script. 

```

#!/usr/bin/env python
import feedparser

feed = feedparser.parse( "http://www.getdeb.net/rss.php?distro_id=9" )
for item in feed[ "items" ]:
    print item['title'] ,"  ",  item['link'] 

```

now these are the links for the pages only, if we are going to get the download links then we'll have to parse each page with an htmlparser which in python should be enclosed in a class.

i'd imagine to make a full blown app like this, is you will mostly need pygtk for the UI and the status icon tray and also libnotify for notifying the user. and also architecture detection for interchanging the proper rss feed for the particular architecture.

it is still a long way to go, but i guess very doable provided with enough time.

---

