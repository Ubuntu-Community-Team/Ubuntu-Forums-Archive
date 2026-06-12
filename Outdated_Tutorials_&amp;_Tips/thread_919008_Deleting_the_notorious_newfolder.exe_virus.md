---
title: "Deleting the notorious newfolder.exe virus"
date: 2008-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by dayanandasaraswati on 2008-09-13
Hello friends, 
 Every windows user would have fallen prey to the NewFolder.exe virus some time or the other. If you put your pendrive in some public net cafes and bring it back home, you are sure to bring back your Christmas Gift - NewFolder.exe. In linux we can directly delete these exe files but the problem is they live under each directory. Thus navigating through directories and deleting them is tedious. So this small one line code helps you get rid of this virus.

Instructions:
1. Open terminal (Applications -> Accessories -> Terminal)
2. Change directory to the root of your pen drive
3. Type the following and press enter
```
find -iwholename *\ .exe -delete
```Kudos!!! Your virus has been killed!!

---

### Post by ChongZx14o on 2008-09-14
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by C.S.Cameron on 2008-09-30
So what happens to all the valid *.exe stuff on my flash drive?
Like installers and such?

---

### Post by DrMelon on 2008-09-30
> **dayanandasaraswati said:**
> 

Instructions:
1. Open terminal (Applications -> Accessories -> Terminal)
2. Change directory to the root of your pen drive
3. Type the following and press enter
```
find -iwholename *\ .exe -delete
```Kudos!!! Your virus has been killed!!

Um, it'd probably be better just to do this:


```
find -iwholename *\ NewFolder.exe -delete
```

---

### Post by lisati on 2008-09-30
> **dayanandasaraswati said:**
>  Every windows user would have fallen prey to the NewFolder.exe virus some time or the other.
I don't remember encountering it....I think I'll go off and look it up.

EDIT: looked it up, seems like a real pain in the "wherever"

> If you put your pendrive in some public net cafes and bring it back home, you are sure to bring back your Christmas Gift - NewFolder.exe.
Simple answer: (a) be wary of hooking up your writiable drives to "unknown" computers, and (b) scan your drive a.s.a.p. when you get back to your regular machine.

---

### Post by lian1238 on 2008-09-30
Look at a [howto]("http://ubuntuforums.org/showthread.php?t=924080") I wrote on preventing viruses from spreading through your USB flash/pen/thumb drive. (It was moved to Windows Discussion. :o)

---

