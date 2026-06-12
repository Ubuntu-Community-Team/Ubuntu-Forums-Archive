---
title: "Question about dual booting Windows and Ubuntu"
date: 2014-06-25
forum: New to Ubuntu
---

### Post by Barock_Obama on 2014-06-25
Hello,
I will be doing a major computer upgrade soonish and decided a week ago while cleaning out some malware from windows 7 (I have antivirus and malwarebytes and all that jazz, malware just gonna happen on windows no matter what you do), and thought that I really needed an OS where malware is not such a huge problem. Obviously ubuntu came to mind. HOWEVER; I need windows 7 still because I want to use my comp as a gaming pc, and game devs lean towards windows. So I'm going to figure out how to dual boot windows 7 and ubuntu 14.04 on my new comp (wish me luck I guess).

SO I have one question: if I do this dual boot, could I set it up so windows 7 is always offline and any game downloads or whatever software is downloaded on the ubuntu side, such that windows 7 is never online and never in contact with potential malware? I would do all browsing on ubuntu, and since 99.99% of malware is made for windows, not really have to watch what sites I go on. Is this viable?

Also, is there an av that would check a download for windows malware on ubuntu's end before moving it over to windows? I think that'd be convenient, if no such thing exists then I'll just stick with mbam on windows 7 to double check files before I run them.

My end goal is to do all web browsing and general/practical stuff on ubuntu, and use windows to play games and software that dont support linux, staying offline on windows just to make it safer.

Sorry for the long, possibly newby question. Would greatly appreciate info on this, having been a windows xp/7 user my whole life. Thanks!

---

### Post by lotharmat on 2014-06-25
Hiya.

Piece of cake! When installing Ubuntu - Just tick the 'side by side with the detected (Win 7) OS.

It will work fine!

---

### Post by LastDino on 2014-06-25
First tell us about your system config. What kind of BIOS? (Legacy/UEFI) Is probably Legacy, but you never know.

Then tell us about what kinds of partitioning are you looking for? How much space are you willing to offer to Linux? Does drive contains any data/partitions you would like to preserve? Please post your current partition scheme.  Needless to say please take backups and clone/make recovery disks of W7 installation.

I don't use anything else other than ''something else'' so I can't vouch for ''install along side'', so be careful. 

After this we can get started with what you need to do next.

As far as answering your questions go:
Yes, you can completely cut off Windows internet access. And quite easily too.

However, you're wrong if you think you're free to visit whatever site you want and you wont be putting your security at risk just because you installed Ubuntu or any Linux for that matter, it is just more unlikely to receive heat, the biggest risk to Computer is the person using it, so you need to get into better habits if you want to be more secure.

Yes, you can use Ubuntu for scanning files you wish to use under Windows.

---

### Post by stalkingwolf on 2014-06-25
I could be wrong but most of the windows packages ive seen of late all require some kind of internet connection to install. Granted most of the installs i have done are basic things like av,firewall ,browser, and email client.
So even downloading it in ubuntu it will still need the inet to install.

---

### Post by LastDino on 2014-06-25
> **stalkingwolf said:**
> I could be wrong but most of the windows packages ive seen of late all require some kind of internet connection to install. Granted most of the installs i have done are basic things like av,firewall ,browser, and email client.
So even downloading it in ubuntu it will still need the inet to install.

OP is going to disconnect the Windows from net so I doubt he is going to need them, and he/she probably has them installed already in existing W7 install. My understanding was that he/she was referring to other files like pictures/videos/documents and maybe executables which don't require net, like games. I've one W7 box disconnected from net as the owner only needs it to run 3DMAX and Photo-shop and doesn't own a net connection, I do install driver updates manually on it after downloading them on my Linux box, which is rare, but it can be done.

---

