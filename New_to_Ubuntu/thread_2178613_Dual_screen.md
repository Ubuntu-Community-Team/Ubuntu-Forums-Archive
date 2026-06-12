---
title: "Dual screen"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by NotCras on 2013-10-04
I was giving a presentation and I went to hookup my laptop to the projector. My laptop recognized it as a seperate monitor and treated it as such. After some minor problems I got it working fine. The only real problem was that there was an awkward period right before the presentation as I trie to get everything working.

So... to ensure that doesn't happen again, does anyone know where I can set second monitor settings beforehand to mirror the main screen by default? I looked in the displays section in the system settings and could find nothing. I don't want to have to reconfigure my settings every time.

I'm using 12.04. Also, I don't have an nvidia card, I'm using a lowly acer c7. So I can't use: 
```
sudo nvidia-settings
```


Anyone have anything? I feel like I'm missing something obvious.

---

### Post by rsgangr on 2013-10-04
I do not have access to an Acer C7 but I see that it has an integrated Intel Graphics Processor.  Doing a quick test on a borrowed Compaq (also with Intel GPU) running LMDE an external monitor was immediately visible. It was possible to set it either to display the same image on both monitors or to use the external monitor as an extension.  My laptop is running Xubuntu and selecting "Preferences / Monitor Settings" allows me to set up a second monitor or a Data Projector.  If you have a monitor available I suggest using it to test your setup - it is less stressful to do this at home rather than in front of an audience waiting for your presentation! Good luck.

---

### Post by NotCras on 2013-10-05
Thanks but you didn't fully answer my question. Is there a way to set the mirroring on default, rather than as a second window? I can't find any settings for that at all...

---

### Post by heir4c on 2013-10-05
I think there is a conflict with Compiz. A while ago I was on a Ubuntu-Party and they used a beamer and they have problems with. I read something about conflicts with compiz and a beamer. When they switch off Compiz the problem was gone. 
But here is the problem: You can switch to Metacity but in the future Canonical stop using Metacity (already in 13.04) So, you can't switch to it (or you must install it)
So, if there is still a problem on this moment with Compiz: I don't know.
And I don't know where and how you can set the mirror as the main screen. (I have no second screen at the moment so I can't figure it out).
But what you can do (try it some day out when you have the opportunity) is: Install on your laptop a distro without compiz, like Lubuntu or LMDE (see post by 
rsgangr) And use that for your presentations.

---

### Post by NotCras on 2013-10-08
Alright thanks! I'll look into Metacity because I don't know that much about it. 

I would love to figure it out myself, but I also don't have access to a second screen. It's not a huge deal, so I'll just deal with it for now.

---

### Post by Donut50 on 2013-10-08
[COLOR=#000000][COLOR=#DD4814][COLOR=#000000]as [heir4c]("http://ubuntuforums.org/member.php?u=739011")[/COLOR][/COLOR]  said i think its a problem with compiz too, if you have solved it i would love to hear the fix you have found or used :)[/COLOR]

---

