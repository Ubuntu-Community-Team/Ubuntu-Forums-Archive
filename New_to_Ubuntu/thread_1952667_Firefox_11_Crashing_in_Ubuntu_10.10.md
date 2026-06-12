---
title: "Firefox 11 Crashing in Ubuntu 10.10"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2012-04-04
Pretty straight-forward. Ever since updating Firefox to the new version, it randomly crashes. Sometimes after a few minutes, but typically after only a few seconds. Has anyone else experienced this? I either need a fix or to simply downgrade to 10

---

### Post by Tamlynmac on 2012-04-04
You might try looking for information [here]("http://forums.mozillazine.org/viewforum.php?f=38"). After a quick review, there appears to be a number of issues that could cause Firefox 11.0 to crash. Including: incompatible extensions, video drivers (NVIDA management), Java, defective RAM, etc.

I'd suggest you post a assistance request there and also review the existing crash complaints. There seems to be quite a few users who are experiencing similar issues.

Good Luck & hope this helps.

---

### Post by acimi66 on 2012-04-04
I don't think Flash and FF are working very well either...I have had FF crash a couple of times when trying to load Flash videos.

---

### Post by Tamlynmac on 2012-04-04
> acimi66
I don't think Flash and FF are working very well either...I have had FF  crash a couple of times when trying to load Flash videos. 	

Which is why I suggested Captainflowers91 go to the [mozillaZine forum]("http://forums.mozillazine.org/viewforum.php?f=38") and post there. We should keep in mind that Firefox (FF) is a stand alone application running in Ubuntu.

I generally don't suggest other sites to requesters, but in this case it just makes sense. The FF app is one of the fundamental apps that has been a part of the Ubuntu/Linux install for quite some time. When put in perspective it should have it's own forum & support group (which it does) considering it's popularity with users. Users should benefit significantly by going there with Firefox issues - versus posting in other forums.

---

### Post by RJARRRPCGP on 2012-04-04
Flash sucks, because folks at Adobe assume everybody has an Intel processor or a real late AMD processor. Thus, Flash tends to bog down easily. 

With Adobe's thinking, 2 year old processors may be as slow as 15 year old processors!

And because it's proprietary, it can be impossible to solve Flash-related crashes. :(

---

### Post by sguerin on 2012-04-05
Hi my Firefox was doing this too, but now it's also Clementine and VLC. :\

---

### Post by lovinglinux on 2012-04-05
> **Captainflowers91 said:**
> Pretty straight-forward. Ever since updating Firefox to the new version, it randomly crashes. Sometimes after a few minutes, but typically after only a few seconds. Has anyone else experienced this? I either need a fix or to simply downgrade to 10

First try Firefox ion safe mode and check if the problem persists. Close Firefox, open a terminal and run this:

```
firefox -safe-mode
```

If it still crashes, post an error produced in the terminal output.

Then try a clean new profile. The following command will open the profile manager, from where you can create and launch the new profile:

```
firefox -P
```

Report if the problem persists.

---

### Post by 0011235813 on 2012-04-05
Download Chrome or some other browser, and tell us if the issue is present within those as well. That way, we can tell whether it is a system problem or is Firefox related.

---

### Post by Captainflowers91 on 2012-04-07
Well starting Firefox in safe-mode seems to keep it from crashing. Thats a plus at least

---

### Post by lovinglinux on 2012-04-07
> **Captainflowers91 said:**
> Well starting Firefox in safe-mode seems to keep it from crashing. Thats a plus at least

So, the culprit is some extension or theme. Disable all of them, then enable one by one until you find the on e that crashes Firefox.

For instance, the bindwood extension should be removed if you have it, since is no longer used and causes serious problems like preventing Firefox from starting.

---

### Post by Captainflowers91 on 2012-04-07
> **lovinglinux said:**
> So, the culprit is some extension or theme. Disable all of them, then enable one by one until you find the on e that crashes Firefox.

For instance, the bindwood extension should be removed if you have it, since is no longer used and causes serious problems like preventing Firefox from starting.

Interestingly, since running it in safe-mode, even after restarting my computer it hasn't been crashing. Its strange. But its a gift horse and I'm not looking for teeth. Thank you all for the help (Sorry it took so long for me to reply. For some reason, my University's Internet will never let me post a reply, claiming server issues)

---

### Post by lovinglinux on 2012-04-07
> **Captainflowers91 said:**
> Interestingly, since running it in safe-mode, even after restarting my computer it hasn't been crashing. Its strange. But its a gift horse and I'm not looking for teeth. Thank you all for the help (Sorry it took so long for me to reply. For some reason, my University's Internet will never let me post a reply, claiming server issues)

Keep in mind that safe-mode is just a troubleshooting tool. I don't expect you to run in safe mode all the time. You need to find the extension causing the crashes.

---

