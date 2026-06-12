---
title: "[SOLVED] Is there a better search engine than the forums"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Scunnered on 2008-10-11
I have been trying to find information on how I can download photographs without any luck.

I have tried various search phrases but keep having information displayed which is not relevant to my search.

When using Puppy there were at least two search engines which we a lot better than the forums which I used with great success.  

Is there any similar search engines and where may I find them.

Thanking you in  anticipation

---

### Post by jerome1232 on 2008-10-11
I just use google and add the word 'ubuntu' into my search terms, 9 times out of 10 ubuntu forums are the top results. Followed by good how-to's.

---

### Post by Kevbert on 2008-10-11
A better search engine is google (just include linux as one of your search words).
Regarding photos, how are the photos saved (compact flash, secure digital etc) ? Have you tried just connecting the camera to your PC and then tried browsing removable media ? Or using F-Spot to import pictures ?

---

### Post by dasunst3r on 2008-10-11
jerome1232 is on the right track, but I would use this instead: site:ubuntuforums.org {whatever you are looking for}

---

### Post by whitethorn on 2008-10-11
I usually use google with the word ubuntu, but when I'm looking for something specific I use

[www.uboontu.com](www.uboontu.com)

Ubuntu's Search Engine.  :D

---

### Post by cariboo on 2008-10-11
I always use Google with the words ubuntu and howto in the search criteria, unless I know there is a solution in the forum that i'm searching. For instance yesterday I locked myself out of my server, it is in my detached garage and has no monitor or keyboard attached. I remembered seeing a solution to exactly the same problem in a particular forum, did a search on "denyhosts locked me out" and had the solution to my problem is seconds.

Jim

---

### Post by Ryadt on 2008-10-11
[http://www.googlubuntu.com](http://www.googlubuntu.com)

works great
;)

---

### Post by OutOfReach on 2008-10-11
I use google, and when I search I type in this:
```
site:ubuntuforums.org MY_SEARCH_TERM_HERE
```

It has better accuracy than the forum's engine.

---

### Post by ubername on 2008-10-11
[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

### Post by Scunnered on 2008-10-11
Many thanks to you all for your replies.  I will have a close look at things and see how they work.

Kevbert

As you asked about photos what I was attempting to find out was how do I download photos into the pictures folder.  When using Doz I would use a card reader which automatically sent them to the required folder.  When I attempted to try this I got nothing.

This prompted the search which was fruitless and prompted this post.  If you can guide me on this it would be most appreciated.

I have 2 cameras which I work from both Nikon and normally use the card reader for downloading as it saves the batteries.

Hope this is of assistance.

---

### Post by t0p on 2008-10-11
> **Scunnered said:**
> how do I download photos into the pictures folder.  When using Doz I would use a card reader which automatically sent them to the required folder.  When I attempted to try this I got nothing.


Are you talking about SD cards?  I have a fujifilm SD card reader, which plugs into my pc's usb socket and is auto-mounted by ubuntu.  But it doesn't work with SDHC (high capacity) cards. So I use it with 2 GB cards (which is plenty big if you ask me).

---

### Post by jerome1232 on 2008-10-11
I always just copied them myself, I know f-spot does the import type of thing your talking about. 

Those programs have always just annoyed me though.

---

### Post by xeth_delta on 2008-10-11
About the regular search process itself. Try also the advanced search tool. You can then choose how the results should be shown (for instance relevancy can sometimes be better) and to what sections of the forum they should be limited to. I have found the search results are acceptable.

---

### Post by richg on 2008-10-11
I use Scroogle. They do not track you.

[http://www.scroogle.org/](http://www.scroogle.org/)

Rich

---

### Post by Kevbert on 2008-10-12
> **Scunnered said:**
> Many thanks to you all for your replies.  I will have a close look at things and see how they work.

Kevbert

As you asked about photos what I was attempting to find out was how do I download photos into the pictures folder.  When using Doz I would use a card reader which automatically sent them to the required folder.  When I attempted to try this I got nothing.

This prompted the search which was fruitless and prompted this post.  If you can guide me on this it would be most appreciated.

I have 2 cameras which I work from both Nikon and normally use the card reader for downloading as it saves the batteries.

Hope this is of assistance.

What version of Ubuntu are you using ?  In Hardy, with the system running, I'm able to connect a card reader and insert a SD card and F-Spot opens automatically. Then select import and then select the removable card drive via F-Spot.  The card also is displayed under Places-Removable Media so I can get it via Nautilus File Manager.
The second possibility is not ideal but it works. I'm not sure if I installed this as an extra or not but I believe its called Kamera and you can get it via Synaptic Package Manager. Connect the camera to a USB port, turn on the camera and going to Preferences-Digital Camera and see if is shows up there. It will be shown as Mass Storage Camera.

---

### Post by Scunnered on 2008-10-12
**t0p**

I am using SD cards 1 256 MB and a 2GB via a USB 2.0 card reader and would you believe it when I tried this again in response to your and** Kevbert's** replies it worked in part. I am using 8.04 as a Live session user at the moment and liking what I see so far. 

I loaded up the 2GB card and it was immediately registered and f-spot took over. It initially advised that *folder contents could not be displayed* and then downloaded the pictures.  I was able by using CTRL + A copy them all to the photos folder.  

When I loaded up the second card and went through the same system it displayed OK but would not copy the pictures into the photo folder.  I note that when they are initially displayed that they are by date but on saving to the photos folder they display by number.  Would that be the reason why the second card was not read.  Do I have firstly have to prepare a folder to copy each card to in order that both will display as being saved?

Once again my sincere thanks to all who assisted in this post.

---

### Post by Kevbert on 2008-10-12
You'll find the photos are saved in folders based on the date you took them, i.e. 2008 followed by month subdirectory (10) and finally day subdirectory (12).  
Why the second card did not work I don't know.  Can you do a reboot and see if the 256Mb card works. If it does then try the 2Mb drive, if this works it may have been a connection problem.  If not, it may be worth raising a bug report on [[COLOR="Red"]launchpad[/COLOR]]("https://launchpad.net/").  You need to give the following information: your kernel -you can get this via terminal;
```
uname -a
```
what you did and the type and make of card that failed.  You can get additional information by going to Places-Computer, right-click on the card and select properties, select drive tab and volume tab and adding that info to the bug report.
Thanks. Together we can make Ubuntu better!

---

### Post by Scunnered on 2008-10-12
Kevbert

Perhaps it is the fact that I at the moment I am working with a live DVD.  Both SD cards displayed the pictures and as both cameras were used on the same day I would have thought that at the worst they would have ended up in the one folder.

Using doz each card will show up as an individual folder within the my-pictures section so I had anticipated something similar to happen here.

I anticipate that by the weekend I shall be up and running with a full HD install and will see how that goes.  I will meantime follow your suggestion and see how it comes out.

Once again thanks

---

### Post by Kevbert on 2008-10-12
Good luck. If you have a router I'd connect to that when you do a full install as then any initial updates will go a lot smoother.  If you have any problems with display, wireless, please don't hesitate to ask questions on the forum.

---

