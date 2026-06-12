---
title: "[SOLVED] Google--Chili's Website &amp;quot;May harm your computer&amp;quot;??"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by seagullplayer77 on 2008-07-27
Just a quick preface: I know this isn't remotely a Linux question, much less a Ubuntu one, but this is the only computer forum I'm a member of so I figured I'd ask here.

My mom was going to search for Chili's (as in the restaurant chain) locations this afternoon on a Windows machine, and when she Googled "Chili's," the first result it returned was clearly the Chili's Website, but Google pegged it with a "This site may harm your computer." Doesn't it strike anyone as just a little bit odd that a Website of a respectable, nationwide restaurant chain would have content that Google would deem harmful? Or am I just being naive? 

In any case, I'm not particularly concerned with whatever harmful content may (or may not, as the case may be) exists, 'cause I've got Hardy on my laptop and I don't think I'll have to worry about any malicious code. That being said, if anyone has an explanation, I'm curious :-)!

---

### Post by halitech on 2008-07-27
only thing I can think of off the top of my head is there is some kind of script they have running that may grab the IP address to select the best location for the person

here is what it comes up with
[http://safebrowsing.clients.google.com/safebrowsing/diagnostic?client=Firefox&hl=en-US&site=http://www.chilis.com/](http://safebrowsing.clients.google.com/safebrowsing/diagnostic?client=Firefox&hl=en-US&site=http://www.chilis.com/)

---

### Post by Melindrea on 2008-07-27
By the looks of it, I'd guess they've been hacked. This is part of the diagnostics page: [http://www.google.com/safebrowsing/diagnostic?site=http://www.chilis.com/](http://www.google.com/safebrowsing/diagnostic?site=http://www.chilis.com/)

> Of the 10 pages we tested on the site over the past 90 days, 2 page(s) resulted in malicious software being downloaded and installed without user consent. The last time Google visited this site was on 07/27/2008, and the last time suspicious content was found on this site was on 07/26/2008.

    Malicious software is hosted on 3 domain(s), including bce8.ru, iroe.ru, kpo3.ru.

    1 domain(s) appear to be functioning as intermediaries for distributing malware to visitors of this site, including bce8.ru.

---

### Post by seagullplayer77 on 2008-07-27
Interesting...Looking at the diagnostic page, it would appear as though someone tried getting some malware on their Website at one point or another. In any case, it wouldn't affect a Linux machine, would it?

---

### Post by Melindrea on 2008-07-27
I... don't know. =) My instinct says "no, it wouldn't", but I'm not quite sure I want to bet my computer on it.

Other people who know Linux better?

---

### Post by halitech on 2008-07-27
reading the info a little more, it may not have actually been chili's website but any site that was hosted on the same servers as chili's is.

me, being the adventurous fool I am at times went to the site and other then getting a popup saying dangerous site, nothign else happened, don't think I'll try it on a windows machine though :D

---

### Post by seagullplayer77 on 2008-07-27
I wouldn't try it on a Windows machine either, but I think I'll give it a whirl with Ubuntu. After all, life is either a dangerous adventure or nothing at all :-). In any case, if something goes screwy, well...that's why God made forums! Thanks for quelling my curiosity fellas.

---

### Post by Melindrea on 2008-07-27
I tried to go there, but it was blocked due to my security settings, which then scared me to not continue. =)

---

### Post by y-lee on 2008-07-27
No I doubt it would hurt a linux machine, but without knowing more about what malicious software was installed and how it was installed it is hard to be sure. Most of the time malicious software is installed by viewing a web page it is by active X or a browser exploit. Avtive x would only effect IE or browsers based on IE so it wouldn't harm linux unless you were viewing in in IE using wine or something. Even then the damage would be minimal. 

Since there are so many browsers for linux probably the only one people would try to exploit is Firefox (or FF like browsers) and there is some nasty javascript which might affect FF so it is safest to disable javascript. But that makes the net hard to use so it is a personal issue and up to the user to make that call.

But anyway that kind of exploit can do little damage in linux UNLESS you are browsing as root or superuser. At worst it can damage yur home directory. I don't worry about it and click on anything and never had any problems othern seeing somethings maybe I wish i hadn't or having FF crash or freeze up.

---

### Post by seagullplayer77 on 2008-07-27
I went there and I didn't even get a pop-up, so I don't know. I haven't had any problems yet, and I don't anticipate any either. Just thought I'd add that little tidbit of info.

I don't use Wine for much of anything, so the IE thing isn't an issue, and while I have Firefox installed and I'll use it every once in a while, Opera is my browser of choice and I use it for nearly everything. Anyway, thanks for all the help.

---

