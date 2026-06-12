---
title: "Could someone point me in the right direction?"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by EliteNeophyte on 2013-04-08
Okay so I have been a long time windows user and have a high opinion of myself (hence the username). I recently wiped my harddrive and rather than aquire a copy of windows again I just got Ubuntu.  Now I've used it before and I would consider myself an advanced windows user, good enough with computers to make a smooth transition

oh how wrong I was

After switching to this system I have put myself in an orange hell, I love the interface, the speed is amazing, but my utilities don't work, My games have NO driver support (and those are the ones that are linux compatible) in an attempt to get drivers I have found that my filesystem must be broken somehow, speaking of the filesystem the most jarring transition of them all is going from this **C:/** to this **/ **how do you people deal with **_this thing /,_** when I have a computer problem I do what all respectable IT professionals do, I google it, with windows this was simple, not with Ubuntu (yes I am aware of googlubuntu) the results are calibrated for the windows user leaving me screwed, I have almost no understanding of the filesystem or terminal commands as understood by the Linux Kernel, you guys have gotta help me, I'm practically re-learning how to computer here, I can't even grammar

so could you guys show me a guide that is written for the computer illiterate, better yet written for the windows user, with comparisons like *sudo is like a more powerful version of the run as administrator command*. I need that, that is what I need, this os makes me feel stupid, I DON'T LIKE FEELING STUPID :confused::(

---

### Post by nothingspecial on 2013-04-08
Hi, welcome to the forums :D

So, in trying to get some linux games working, you have encountered some file system problems ?

Please post a link to the instructions you were following, what you did, what you were trying to do, and any errors you got.

---

### Post by oldsoundguy on 2013-04-08
I suspicion that the OP is trying to get Windows based games to work in Ubuntu .. which will not happen as we know.  Not without installing Wine or Play on Linux or something similar.

---

### Post by snowpine on 2013-04-08
Welcome to Linux! There are plenty of wonderful native Linux games. I particularly like Battle for Wesnoth and Dungeon Crawl. For the best of both worlds I recommend a "dual boot" so you can play your Linux games in Linux and your Windows games in Windows.

If you are having video driver problems then I recommend to start a new thread with the brand and model number of your video card in the thread title, you'll get help quicker that way.

Here are a few links I found invaluable when I was getting started in Linux:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://www.catb.org/esr/faqs/smart-questions.html](http://www.catb.org/esr/faqs/smart-questions.html)
[http://help.ubuntu.com](http://help.ubuntu.com)
[http://wiki.ubuntu.com](http://wiki.ubuntu.com)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

If you google and follow random how-to's from some random guy's blog, you **will** get into trouble eventually! Always follow guides and tutorials from trusted sources (such as the Ubuntu wiki), and if you're uncertain, ask for advice on these forums (but remember there is no test for membership here, so don't just blindly follow the first response you get).

Good luck, and welcome to the club! :)

---

### Post by EliteNeophyte on 2013-04-08
Sir, **thank you** those guides were exactly what I was looking for

---

### Post by EliteNeophyte on 2013-04-08
> **nothingspecial said:**
> Hi, welcome to the forums :D

So, in trying to get some linux games working, you have encountered some file system problems ?

Please post a link to the instructions you were following, what you did, what you were trying to do, and any errors you got.

Okay so you asked what I had done, I just spent an hour typing up a reply only for my browser to crash so pardon me if this one is a bit rushed
Counter-Strike: Source (the linux version that was just released) did not run worth a damn, the framerate was terrible and the brightness was far too low for the human eye with gamma settings and graphical configurations doing nothing to help either problem **screenshot** [http://imgur.com/ZBwNINS](http://imgur.com/ZBwNINS) so I get to searching and find **this** [https://support.steampowered.com/kb_article.php?ref=5452-IOSM-1474](https://support.steampowered.com/kb_article.php?ref=5452-IOSM-1474) after following the instructions within I get **this **[http://imgur.com/CXoQTos](http://imgur.com/CXoQTos) so I do some more searching and find **this post **[http://ubuntuforums.org/showthread.php?t=816982](http://ubuntuforums.org/showthread.php?t=816982)** (read the one from ajgreeny) **after following his instructions about synaptic **I did not run the console commands** I made a trip to the software center, installing and running synaptic got me **this **[http://imgur.com/GDo2TJg](http://imgur.com/GDo2TJg) okay so not knowing what to do I click **edit** and **fix broken packages**, I then tried the update again and got **this **[http://imgur.com/PTEAnaq](http://imgur.com/PTEAnaq)** note the inception like similarity**, so thinking **effit **I just went ahead with the **partial upgrade **and I don't know who could have guessed it but **babam **[http://imgur.com/xk8tz0D](http://imgur.com/xk8tz0D) and now I'm writing this after a large amount of frustration, love ubuntu, but I have absolutely no idea what I'm doing
[B]
sorry about the screenshots if it goes against the policy or anything but working in IT I find it immensely more simple when I can see the user's screen

*oh I forgot to mention my processor is an Intel Pentium b940 integrated Codename: Sandy Bridge if that helps*[/B]

---

### Post by EliteNeophyte on 2013-04-08
> **oldsoundguy said:**
> I suspicion that the OP is trying to get Windows based games to work in Ubuntu .. which will not happen as we know.  Not without installing Wine or Play on Linux or something similar.

No sir, I was attempting to run the Linux version of Counter Strike: Source, I may be a Linux n00b but this is not my first time behind a key board, I suspicion that you suspicion that... ow my head hurts

---

### Post by snowpine on 2013-04-08
You are following a tutorial for Ubuntu 12.04; are you using 12.04? 
If you are not using 12.04 then that's why you got those errors. 
If you want to use the x updates PPA, the correct install instructions can be found here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
I don't own any Sandy Bridge, but I've heard there are big improvements in 12.10, so if you are using 12.04 you might consider giving 12.10 a test-drive: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_intel21&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_intel21&num=1)
Also 13.04 is coming out real soon.

What I would do personally is to start a new thread with a descriptive title such as "improve Counter-Strike performance on Sandy Bridge" and wait 24 hours to let the good advice pile up, rather than following a bunch of random tutorials (one of the pages you linked to is from 2008!) and making a big mess. If you rely on unofficial tutorials for the wrong Ubuntu release, then you are asking for trouble... better to gather trusted information, understand the problem, make a plan to solve it, and **then** start taking actions to fix the problem (copy & pasting terminal commands from trusted sources only). Good luck, now go start that new thread for your Sandy Bridge problem! :)

---

### Post by EliteNeophyte on 2013-04-08
> **nothingspecial said:**
> Hi, welcome to the forums :D

So, in trying to get some linux games working, you have encountered some file system problems ?

Please post a link to the instructions you were following, what you did, what you were trying to do, and any errors you got.

> **snowpine said:**
> You are following a tutorial for Ubuntu 12.04; are you using 12.04? 
If you are not using 12.04 then that's why you got those errors. 
If you want to use the x updates PPA, the correct install instructions can be found here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
I don't own any Sandy Bridge, but I've heard there are big improvements in 12.10, so if you are using 12.04 you might consider giving 12.10 a test-drive: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_intel21&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_intel21&num=1)
Also 13.04 is coming out real soon.

What I would do personally is to start a new thread with a descriptive title such as "improve Counter-Strike performance on Sandy Bridge" and wait 24 hours to let the good advice pile up, rather than following a bunch of random tutorials (one of the pages you linked to is from 2008!) and making a big mess. If you rely on unofficial tutorials for the wrong Ubuntu release, then you are asking for trouble... better to gather trusted information, understand the problem, make a plan to solve it, and **then** start taking actions to fix the problem (copy & pasting terminal commands from trusted sources only). Good luck, now go start that new thread for your Sandy Bridge problem! :)

I understand what you are saying but from what I have been able to accertain, the problem is I am on an integrated card that my os has no working drivers for, now I can update said card's drivers but a corrupted install of the previous ones is in the way, now I will go start that new thread but in the mean time could you explain to me how to get rid of the corrupt install, at the very least how to use synaptic

oh yea I am using 12.04 LTS and I have a good idea where the corrupt drivers came from, you see I have a really ****** satellite connection and downloading the official Ubuntu update package during the installation would have not only gone over my download cap, but once doing so would have slowed down my connection to a point where getting them all would take several days, so to counteract this and get my osless computer running I well... cancelled several during the update, If I had to wager that's where I'd put all me Doubloons... wait what did I just say, sorry old habits die hard, any way can any of you come up with a way to find and destroy these drivers, without Counter Strike work is killing me

---

### Post by ppjdee on 2013-04-08
^ is why i rather stick with my 1mb dls connection then switch to sat connection lol

---

### Post by snowpine on 2013-04-08
This tutorial explains the concept of "repositories," how to manage your software sources, and how you can add/disable/remove third-party sources such as the X Updates PPA:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Zill on 2013-04-09
> **EliteNeophyte said:**
> ...downloading the official Ubuntu update package during the installation would have not only gone over my download cap, but once doing so would have slowed down my connection to a point where getting them all would take several days, so to counteract this and get my osless computer running I well... [COLOR="#FF0000"]cancelled several during the update[/COLOR]...
This *really* is not a good idea!  The problems you have experienced may well be due to a installation that is now incomplete and/or corrupted.

Following the installation of a new OS, such as Ubuntu, from a DVD, it is *essential* to install *all* the updates that have been issued since the DVD was released.  In order to then maintain and, preferably, improve the security of the new OS it is then necessary to install updates on a regular basis.

I suggest that you do whatever is necessary to connect your computer to a reliable internet connection and then allow it to download *all* available updates.

---

### Post by Sandertje on 2013-04-09
> **EliteNeophyte said:**
>  so to counteract this and get my osless computer running I well... ***cancelled several during the update***

This sounds like very probably the main reason why you have been seeing so many package errors. Cancelling updates is.. well... simply dangerous, and almost 100% guaranteed to lead to a gazillion errors.

---

### Post by EliteNeophyte on 2013-04-09
> **Sandertje said:**
> This sounds like very probably the main reason why you have been seeing so many package errors. Cancelling updates is.. well... simply dangerous, and almost 100% guaranteed to lead to a gazillion errors.

Well I have completed an update since and figured that that would have corrected the problem but I still have the same issue, anything I can do?  I don't want to re-install unless I [COLOR=#ff0000]absolutely have to[/COLOR]

---

### Post by snowpine on 2013-04-09
> **EliteNeophyte said:**
> anything I can do?

You could start a thread in the Gaming sub-forum with a descriptive title.

Imagine that you are a Counter-Strike expert with a Sandy Bridge computer, and you are surfing Ubuntu Forums in your spare time, looking for people to help. Which thread are you more likely to click: "Could someone point me in the right direction?" or "Could someone help me improve Counter-Strike performance on Sandy Bridge"???

If you had done this yesterday, I'm sure you'd have lots of good answers by now. :)

---

### Post by Bashing-om on 2013-04-09
EliteNeophyte; Hi !

I have followed this thread with an interest in alleviating your trials and tribulations ( Hang in there you will get the hang of it ).

May I at this time suggest to get an idea of what condition the package manager is in ?
running the terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
``` will give some direction on where to proceed.
Lots of errors and/or LOTS of updates ->
Might be the better course to go to a high speed access and download the latest .iso file (torrent files often are fastest) and as bad as you do not want to, (re-)install from scratch. Count all this up to the learning experience and carry on !

Alternately; IF you know what you want from your operating system, might consider downloading the "minimal install" CD and installing ONLY the packages that you want on your system. This greatly reduces the on-line time . However, this does take familiarity with the ubuntu operating system at large.[INDENT=3]
just my thoughts

[/INDENT]

---

### Post by EliteNeophyte on 2013-04-09
> **snowpine said:**
> You could start a thread in the Gaming sub-forum with a descriptive title.

Imagine that you are a Counter-Strike expert with a Sandy Bridge computer, and you are surfing Ubuntu Forums in your spare time, looking for people to help. Which thread are you more likely to click: "Could someone point me in the right direction?" or "Could someone help me improve Counter-Strike performance on Sandy Bridge"???

If you had done this yesterday, I'm sure you'd have lots of good answers by now. :)

This thread was initially just asking for a guide to Ubuntu for a beginner, I had never meant for the Counter Strike thing to be more than a mention of the trouble I've been having, people asked what I had done so I told them and I truly appreciate the help, would have used a better title, that just wasn't what I had come here for at the time

---

### Post by Sandertje on 2013-04-10
> **EliteNeophyte said:**
> Well I have completed an update since and figured that that would have corrected the problem but I still have the same issue, anything I can do?  I don't want to re-install unless I [COLOR=#ff0000]absolutely have to[/COLOR]

Unfortunately, ubuntu is quite sensitive to unfinished/cancelled updates - as I've experienced myself. 

Could you perhaps go into the update manager and click 'settings'. Then go to tab 'updates', and UNCHECK the boxes that say "pre-release updates" and "Unsupported updates". You might be asked for your password here btw. Then go to tab "Other software". Do you have any third-party repositories there, and if so, how many? In general, uncheck the ones you don't think are absolutely necessary.

Close the update manager (and synaptic, if open) and open a terminal (sorry, but terminals still give more exact output; any error message produced there is more informative).
Then type 
```
 sudo apt-get update
```
This will NOT actually install anything, but will merely check the repositories for new updates. This shouldn't take too long, even on a satellite connection. If you get ANY* errors there, then there's something wrong in your repositories. Post any errors you get back here.

*note: if you get something along the lines of "could not access /var/lock/blah. is another program using it?", then you have not closed down the package manager and/or synaptic. To be able to run apt-get update in terminal you should really close those two programs.

---

### Post by solarghost on 2013-04-10
Hi EliteNeophyte

Welcome and good luck, I would highly recommend: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Free, very good and best of all available for download.

Have fun, I'm sure you will.

---

### Post by EliteNeophyte on 2013-04-10
On a related note, If I do have to reinstall my os it's going out in style, I'm gonna play lose/lose [http://stfj.net/art/2009/loselose/](http://stfj.net/art/2009/loselose/) till this thing won't boot

---

