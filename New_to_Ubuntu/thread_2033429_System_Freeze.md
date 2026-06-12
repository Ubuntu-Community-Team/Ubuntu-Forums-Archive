---
title: "System Freeze"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by dj357 on 2012-07-26
Hi all,

For some strange reason the last few weeks I've been noticing some graphical glitches with both Firefox and Chromium while on Facebook, a slight flickering of the screen while scrolling now and then. Tied to this, for some reason every now and then while scrolling all the way to the top of the page, whether it's the main feed or someone's timeline, a large black section will appear on the page and my system will freeze. Rhythmbox keeps playing out whatever tune was still on, but I cannot do anything. The cursor stays frozen in 'clickable link' mode and no amount of key presses or combinations results in any kind of reaction. This has happened on 3 separate occasions, twice in Firefox and one in Chromium, but always only on Facebook. Any suggestions?

My Ubuntu is 12.04 and I only just installed Chromium in the last week so I assume it's the latest version.

---

### Post by Bufeu on 2012-07-26
Does the whole computer freeze or just the mouse + the web browser?

---

### Post by mapes12 on 2012-07-26
A few weeks back an Ubu machine I maintain for my Dad started behaving like what you are experiencing. It turns out he clicked a link in a spam email. The link attempted to break his FF security but it didn't succeed. His machine kept freezing just like yours though.

There were a couple of solutions that worked for me. I'm not sure about Chromium but for FF there is a hidden folder in the users /home called .mozilla, click ctrl+h with /home open to see it. If you delete it then launch FF the folder will be automatically recreated and set up a fresh user profile for the user. All should work OK.

But I'm paranoid so I did a fresh install of 12.04 just to be sure there was nothing else lurking around.

Good luck.

Mark

---

### Post by Bufeu on 2012-07-26
> **mapes12 said:**
> A few weeks back an Ubu machine I maintain for my Dad started behaving like what you are experiencing. It turns out he clicked a link in a spam email. The link attempted to break his FF security but it didn't succeed. 

There were a couple of solutions that worked for me. I'm not sure about your browser but for FF there is a hidden folder in the users /home called .mozilla, click ctrl+h with /home open to see it. If you delete it then launch FF the folder will be automatically recreated and set up a fresh user profile for the user. All should work OK.

But I'm paranoid so I did a fresh install of 12.04 just to be sure there was nothing else lurking around.

Good luck.

MarkOP, just be aware about deleting all Firefox-profiles will result in lost of **ALL** history, bookmarks, download history, settings, addons, etc.

---

### Post by dj357 on 2012-07-26
> **Bufeu said:**
> Does the whole computer freeze or just the mouse + the web browser?

The whole computer. I can move the cursor around but I can't click anything and I get no response from the system at all, but as I mentioned Rhythmbox will keep playing out the current song, though it doesn't move on to the next as it normally should.

---

### Post by mapes12 on 2012-07-26
> OP, just be aware about deleting all Firefox-profiles will result in lost of ALL history, bookmarks, download history, settings, addons, etc.A very valid point. Thanks. 

For bookmarks I have the Xmarks addon so syncing them up again from the Xmarks server is not a problem.

Not sure if you have heard of Remastersys. It's great for making a custom installation of your system. So, if you did do a fresh install, get all the updates, add your favourite packages etc etc. Then create your Remastersys iso. Keep it safe somewhere then when your system breaks all you need to do is burn the iso to a DVD and reinstall your system to the exact same state as what it was before your system broke.

EDIT:- It makes the Remastersys process a whole lot easier if your keep your personal files on a separate data partition i.e. not in /home but just have /home store your package config files.

---

### Post by Bufeu on 2012-07-26
> **dj357 said:**
> The whole computer. I can move the cursor around but I can't click anything and I get no response from the system at all, but as I mentioned Rhythmbox will keep playing out the current song, though it doesn't move on to the next as it normally should.When the computer freezes happens, press CTRL + ALT + F1 and login. Type *unity --reset* and then *exit*. Press CTRL + ALT + F7 to go back to graphic mode. Did it worked?

---

### Post by dj357 on 2012-07-26
> **Bufeu said:**
> OP, just be aware about deleting all Firefox-profiles will result in lost of **ALL** history, bookmarks, download history, settings, addons, etc.

duly noted!

> **Bufeu said:**
> When the computer freezes happens, press CTRL + ALT + F1 and login. Type *unity --reset* and then *exit*. Press CTRL + ALT + F7 to go back to graphic mode. Did it worked?

I will try this and report back, thanks!

---

### Post by DGINSD on 2012-07-26
Whats your set up Computer/graphics and driver used?

---

### Post by Bufeu on 2012-07-26
> **dj357 said:**
> duly noted!



I will try this and report back, thanks!Hmm, my wrong. You shouldn't type *exit*, skip that and press CTRL + ALT + F7 after you have typed *unity --reset*.

---

### Post by dj357 on 2012-07-27
> **DGINSD said:**
> Whats your set up Computer/graphics and driver used?

Ubuntu 12.04, Intel Core 2 Duo 2.66GHz, 3Gb Ram, using propiertary Nvidia graphics driver for my card, can't find what make of card it is though.

---

### Post by dj357 on 2012-07-27
Ok, now I'm seeing the graphical glitch on most pages when scrolling slowly, but facebook hasn't frozen me in the last 2 hours... the glitch is only appearing in firefox now, and the deleting of the firefox folder didn't help

---

### Post by SV44 on 2012-07-27
> **Bufeu said:**
> When the computer freezes happens, press CTRL + ALT + F1 and login. Type *unity --reset* and then *exit*. Press CTRL + ALT + F7 to go back to graphic mode. Did it worked?
At the second day of using Ubuntu I got the same freezing problem and did not know what to do, except pressing power button, like in Windows. This brought new problems - with HD. After reinstalling, all these days I was affraid this would happen again. 

Now I copied your recommendation to my evernote. Hopefully, next time I will act in a more civilized way :grin:. Did not expect Ubuntu community  answers such questions (from novice users).  Thanks!

---

### Post by Bufeu on 2012-07-27
> **SV44 said:**
> At the second day of using Ubuntu I got the same freezing problem and did not know what to do, except pressing power button, like in Windows. This brought new problems - with HD. After reinstalling, all these days I was affraid this would happen again. 

Now I copied your recommendation to my evernote. Hopefully, next time I will act in a more civilized way :grin:. Did not expect Ubuntu community  answers such questions (from novice users).  Thanks!I hope you read this: [http://ubuntuforums.org/showpost.php?p=12131335&postcount=10](http://ubuntuforums.org/showpost.php?p=12131335&postcount=10).

---

### Post by JuhazOne on 2012-07-29
I had Firefox freeze twice today while using Facebook. The first time the screen just went blank and the computer didn't respond to ctrl+alt+1, ctrl+alt+del or [alt+sysrq+reisub]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses"). The second time the display seemed to duplicate itself but slightly shifted to the original and there were some vertical lines visible (alt+sysrq+reisub helped here). The latter problem has occurred before, too, but mostly right after logging in to KDE.

My experience today supports the idea that there's something with Firefox and Facebook... I haven't got ideas on what would help, though.

---

### Post by SV44 on 2012-08-02
> **Bufeu said:**
> I hope you read this: [http://ubuntuforums.org/showpost.php?p=12131335&postcount=10](http://ubuntuforums.org/showpost.php?p=12131335&postcount=10).
Thank you very much. Yes, I read attentively (too important) and copied all magic words into evernote. Hopefully it will work if my Ubuntu will freeze.

---

