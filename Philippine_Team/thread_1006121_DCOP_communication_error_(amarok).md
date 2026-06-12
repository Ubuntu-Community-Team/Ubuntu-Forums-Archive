---
title: "DCOP communication error (amarok)"
date: 2008-12-09
forum: Philippine Team
---

### Post by Lord Kaiaphas on 2008-12-09
It's already been a month since I switch from Hardy to Intrepid and I have installed/add Amarok as my media player and ever since I have installed/add it on Intrepid I have been encountering this error (attached) everytime I would open Amarok. I thought an update would fix it and it's almost a month since and still I am reading this error message. But even though amarok is working fine. I can play my audio files with it. With Hardy it's working just fine. I don't see any error message.

I have have search Ubuntu forums regarding it and I have found some topic regarding it. [[**[COLOR="Red"]Link 1[/COLOR]**]](http://ubuntuforums.org/showthread.php?t=956933&highlight=dcop+communication+error) and [[**[COLOR="Red"]Link 2[/COLOR]**]](http://ubuntuforums.org/showthread.php?t=511300&highlight=DCOP). On the second Link the only thing I did was to delete the folder(hidden) **.kde** and still I am seeing that error message. Any idea on how I could get rid of it. I am really new with Linux. So please be gentle :lolflag: ... apir..

And one more thing, instead of having it displayed on the system tray it would appear on the upper left corner under Applications. Kinda weird.

---

### Post by loell on 2008-12-09
seem to point to a permission issue of **.kde** directory.

---

### Post by Lord Kaiaphas on 2008-12-09
> **loell said:**
> seem to point to a permission issue of **.kde** directory.

hmmm, is there anything that can fix it.

---

### Post by adredz on 2008-12-09
sorry, i know nothing about it..
use the new Songbird instead :)

---

### Post by Script Warlock on 2008-12-09
oi dong kaiphas istoryan man ka sa?

---

### Post by Lord Kaiaphas on 2008-12-09
> **adredz said:**
> sorry, i know nothing about it..
**use the new Songbird instead** :)

*hmmm, noted.*


> **boyet said:**
> oi dong kaiphas istoryan man ka sa?


*huh :confused: pasensya na po. Tagalog at kunting Bikol at Ilocano lang alam ko. :lolflag: apir.. *

---

### Post by Script Warlock on 2008-12-09
> **Lord Kaiaphas said:**
> *hmmm, noted.*





*huh :confused: pasensya na po. Tagalog at kunting Bikol at Ilocano lang alam ko. :lolflag: apir.. *

awtz mistaken identity...](*,)

---

### Post by loell on 2008-12-09
> **Lord Kaiaphas said:**
> hmmm, is there anything that can fix it.

could be

```
sudo chown -R username:groupname .kde/
```

where groupname and username is your user name..

---

### Post by Lord Kaiaphas on 2008-12-09
> **loell said:**
> could be

```
sudo chown -R username:groupname .kde/
```

where groupname and username is your user name..


*Still no luck. Still having the same error message.*

---

### Post by wersdaluv on 2008-12-11
I'm using Amarok 2.0. I suppose, you have the older version. 

If so, add this repo-> **deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main** then **sudo apt-get install amarok-kde4**

:D

[http://www.kubuntu.org/news/amarok-2.0](http://www.kubuntu.org/news/amarok-2.0)

---

### Post by angarato on 2008-12-12
>  	
Re: DCOP communication error (amarok)
I'm using Amarok 2.0. I suppose, you have the older version.

If so, add this repo-> deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main then sudo apt-get install amarok-kde4



[http://www.kubuntu.org/news/amarok-2.0](http://www.kubuntu.org/news/amarok-2.0)

Thank a lot for that info, I had that very annoying dcop problem as well, but taking the 2 minutes of upgrading to Amarok 2.0 solved it easily!

---

