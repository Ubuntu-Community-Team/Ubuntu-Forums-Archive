---
title: "too much disk activity"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by spectrevk on 2008-04-25
All this evening, which is basically the first time I've used this machine since yesterday's update, I've been getting an unusual amount of hard disk activity, even when no programs are running, or when a program is relatively idle. I've tried to figure out what's causing this, but the System Monitor hasn't been much help here. 

On a similar note, sometime about a week or two ago, I started having trouble with shutdowns, where it takes very long to shut down. Again, I'm at a bit of a loss in how to track down the problem.

As a side question, I've been using the beta of Hardy...is there some process I need to go through to upgrade to the "official" release? Or was that what those 98 updates I had yesterday were for?

---

### Post by dasunsrule32 on 2008-04-25
More than likely, it is your indexing that is running. You can change how it works. Go to: System -> Preferences -> Search and Indexing. Go to the 'Performance' tab and adjust accordingly. Let me know if this helps out or not. Good luck!

EDIT: Also, make sure that you are loading 'hdparm', it will drastically improve your i/o performance. Those 98 updates were for the final release, unlike Windows, Ubuntu just labels their releases RC, Beta 6, etc, in essence, it is all the same, just updated packages and kernels.

---

### Post by noynac on 2008-04-25
Was Firefox running at the time? If so, have a look at the following thread:

[http://ubuntuforums.org/showthread.php?t=759673](http://ubuntuforums.org/showthread.php?t=759673)

Firefox can cause a lot of disk activity when fetching updates to the site-forgery and malware lists that are contained in the file, urlclassifier3.sqlite. A suggested fix is to uncheck the following Firefox security preferences:

* Tell me if the site I'm visiting is a suspected attack site

* Tell me if the site I'm visiting is a suspected forgery

Some people also suggest deleting the above-noted sqlite file. I did this and the file was recreated but it now contains 9 KB rather than 35 MB.

---

### Post by spectrevk on 2008-04-25
Actually, Firefox *was* running around that time...I guess that could be it. Though having a warning of when I'm visiting a forged website might be nice as well. I don't suppose there's a compromise?

---

### Post by FuturePilot on 2008-04-25
> **spectrevk said:**
> Actually, Firefox *was* running around that time...I guess that could be it. Though having a warning of when I'm visiting a forged website might be nice as well. I don't suppose there's a compromise?

Not as of yet.
There's a bug report here
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/215728]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/215728")
Upstream also knows about it
[https://bugzilla.mozilla.org/show_bug.cgi?id=430530]("https://bugzilla.mozilla.org/show_bug.cgi?id=430530")
Hopefully they will find a fix soon.

---

### Post by spiderbatdad on 2008-04-25
I would like to suggest SeaMonkey as an alternative to FF3 beta. Seamonkey is a sibling to FF and available in the 8.04 package manager. I installed the iceape packages, as suggested, then the seamonkey packages, then removed the iceape packages...apparently they are dummy packages used to configure seamonkey. 

Anyway the browser works great. Flash and java both worked with no tweaking.
Security patches are the same as those applied to latest FF.

---

### Post by FreewheelinFrank on 2008-04-25
I seem to be having the same problem: HD is veritably berserk at times! The screen greys out and the computer becomes unresponsive.

I noticed Scrollkeeper running one time, so the computer must have been indexing new Hardy files. Other times Scrollkeeper wasn't running, so I suspect the Firefox bug, as Firefox was open.

> Go to: System -> Preferences -> Search and Indexing. Go to the 'Performance' tab and adjust accordingly. Let me know if this helps out or not. Good luck!

I'll look into that and check the Firefox link. 

Thanks.

---

### Post by glantucan on 2008-04-26
Hi all, 

I've been using hardy since 3 weeks ago. Last one I realized HDD activity light i the PC box was always on . I did a search in the forum and got scared when I found all those issues about hardy kiling HDDs on laptops. But mine is  a desktop PC Was I affected?

Fortunately I found this post: [http://ubuntuforums.org/showpost.php?p=4540900&postcount=5](http://ubuntuforums.org/showpost.php?p=4540900&postcount=5)

Did a: ```
ps aux |grep  mythtv
```

found:
```
mythtv    6464  1.2  0.5  84096 18192 ?        Dsl  10:07   0:46 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
```

and tested:
```
sudo killall mythbackend  
```

and... EUREKA!! HDD activity light turned off. :guitar:

I removed all mythtv related packages (since I din't really use them) and problem solved. At least for me.

Hope this can help you too!
Cheers!

---

### Post by spectrevk on 2008-04-27
> **glantucan said:**
> Hi all, 

I've been using hardy since 3 weeks ago. Last one I realized HDD activity light i the PC box was always on . I did a search in the forum and got scared when I found all those issues about hardy kiling HDDs on laptops. But mine is  a desktop PC Was I affected?

Fortunately I found this post: [http://ubuntuforums.org/showpost.php?p=4540900&postcount=5](http://ubuntuforums.org/showpost.php?p=4540900&postcount=5)

Did a: ```
ps aux |grep  mythtv
```


I tried this, and I got:

```
1000      8227  0.0  0.0   3004   764 pts/0    R+   12:35   0:00 grep mythtv
```

Do I need to bother with anything? Synaptic says that all I've got is libgmyth0, which is just a library. I have no other Myth TV related software installed, as far as I can tell.

---

### Post by glantucan on 2008-04-28
No, that 
```
ps aux |grep  mythtv 
```
spitting
```
1000      8227  0.0  0.0   3004   764 pts/0    R+   12:35   0:00 grep mythtv
```
means you have no mythtv running. These entry correspond to the ps command. Sometimes ps catches itself or the command you piped it to. This is the case, it's catching grep.

I guess your problem is different. 

I don't know much about which processes can cause more disk activity. I was just worried because with laptops there's a documented bug in Hardy which has to do with energy management and causes fast aging on laptop hard disks. Though it's only documented for laptops I was afraid it could affect also desktops. After some googling I found about mythtv. I wanted to share this with the ubuntu comunity just to avoid headaches to paranoic freaks like myself. :P

I hope you find a solution for your problem.

Anyway, I would sugest killing processes one at a time and see if your HD activity stops. This only affects the running session, but once you identified the problematic process you can decide if this one is important for your daily use of the computer or you can just remove it from the processes list starting at boot.

Cheers!

---

### Post by socref on 2008-04-28
> **spectrevk said:**
> All this evening, which is basically the first time I've used this machine since yesterday's update, I've been getting an unusual amount of hard disk activity, even when no programs are running, or when a program is relatively idle. I've tried to figure out what's causing this, but the System Monitor hasn't been much help here. 

On a similar note, sometime about a week or two ago, I started having trouble with shutdowns, where it takes very long to shut down. Again, I'm at a bit of a loss in how to track down the problem.

And I've had similar shut-down problems. See this thread I started a few days ago. Unfortunately, still no solution.

[http://ubuntuforums.org/showthread.php?t=763747&highlight=socref](http://ubuntuforums.org/showthread.php?t=763747&highlight=socref)

socref

---

### Post by spectrevk on 2008-04-28
Mine is a Firefox 3 problem. It was doing it again, I turned off that notification, and suddenly it stopped. It's a shame too, because I really like Firefox 3 in general.

---

