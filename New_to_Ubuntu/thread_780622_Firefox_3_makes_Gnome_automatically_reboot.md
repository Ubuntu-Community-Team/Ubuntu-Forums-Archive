---
title: "Firefox 3 makes Gnome automatically reboot"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by MockY on 2008-05-03
Since installing Hardy Heron, my computer has suffered from random restarts and Gnome crashes. I am going back to Feisty (not Gutsy who worked poorly as well) who did not crash a single time. However, there is a bizarre problem I have encountered that I would like others to test.

When I go to [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy) with Firefox 3 Beta 5, Gnome crashes and throws me out to the log-in window. I have tried with Visual Effects set on None, Normal, and Extra but with no difference. Could someone try it out? My guess is that it is Flash related (though this site does not use flash), but flash has always work extremely poorly on Ubuntu and just having it installed probably causes issues. Have yet to uninstall it though but don't see the point since that would make half of the website unusable.

---

### Post by SunnyRabbiera on 2008-05-03
remove firefox 3, its probably the most logical answer.

---

### Post by unbuntued on 2008-05-03
> **MockY said:**
> Since installing Hardy Heron, my computer has suffered from random restarts and Gnome crashes. I am going back to Feisty (not Gutsy who worked poorly as well) who did not crash a single time. However, there is a bizarre problem I have encountered that I would like others to test.

When I go to [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy) with Firefox 3 Beta 5, Gnome crashes and throws me out to the log-in window. I have tried with Visual Effects set on None, Normal, and Extra but with no difference. Could someone try it out? My guess is that it is Flash related (though this site does not use flash), but flash has always work extremely poorly on Ubuntu and just having it installed probably causes issues. Have yet to uninstall it though but don't see the point since that would make half of the website unusable.
Firefox 3 Beta 5 is really buggy. My desktop suffered of similar symptoms when streaming video or navigating in Google Maps, using Firefox 3. I suggest you use Firefox 2 instead, proceed as follows if u need to:
```
sudo apt-get remove firefox-3.0
sudo apt-get install firefox-2
```

---

### Post by MockY on 2008-05-03
Again, why even bother adding FF3 to the final release? We have had this discussion in another thread before, but this is just stupid to add a beta (of any kind) in a supposedly stable release. Whats wrong with automatically upgrading it once it is released...

---

### Post by SunnyRabbiera on 2008-05-03
> **MockY said:**
> Again, why even bother adding FF3 to the final release? We have had this discussion in another thread before, but this is just stupid to add a beta (of any kind) in a supposedly stable release. Whats wrong with automatically upgrading it once it is released...

well the reason was for easy transition from firefox 3 beta to firefox 3 final, plus the developers did not want to be left behind like what happened with firefox 1.

---

### Post by MockY on 2008-05-03
I downgraded and going to the website does not crash Gnome anymore. However, it did crash when holding down CTRL and scrolling to zoom in. I am not doing this often so that does not matter. The reason why I did that now was because since downgrading, the font is very small. How do I go about to fix that?

And now nothing on the panel can be moved using left+right mouse button, even though the items are not locked to it. 
It's like the installation is deteriorating little by little without any reason what so ever. Since Feisty it has just gone downhill and I fear the future of this excellent distro that I have been exclusively been using since 6.06, is just going to get worse.

I just realized that no links open up automatically when clicked on in Thunderbird. Again, I have never had this much issues with Ubuntu before and irritation prevailed. It's time for distro-hunting. I will most likely end up with Feisty, but it's a great opportunity to test new waters for a while. Hopefully Intrepid Ibex turns this around.

---

### Post by unbuntued on 2008-05-04
> **MockY said:**
> I downgraded and going to the website does not crash Gnome anymore. However, it did crash when holding down CTRL and scrolling to zoom in. I am not doing this often so that does not matter. The reason why I did that now was because since downgrading, the font is very small. How do I go about to fix that?

And now nothing on the panel can be moved using left+right mouse button, even though the items are not locked to it. 
It's like the installation is deteriorating little by little without any reason what so ever. Since Feisty it has just gone downhill and I fear the future of this excellent distro that I have been exclusively been using since 6.06, is just going to get worse.

I just realized that no links open up automatically when clicked on in Thunderbird. Again, I have never had this much issues with Ubuntu before and irritation prevailed. It's time for distro-hunting. I will most likely end up with Feisty, but it's a great opportunity to test new waters for a while. Hopefully Intrepid Ibex turns this around.
Maybe your computer is sick :)

Regarding the firefox fonts, check here [http://ubuntuforums.org/showthread.php?t=774458&highlight=firefox+fonts](http://ubuntuforums.org/showthread.php?t=774458&highlight=firefox+fonts)

For the link problem, it's probably occuring everywhere not just in Thunderbird. You need to modify your default browser. Execute the following to do so:
```
sudo update-alternatives &#8211;config x-www-browser
```

---

### Post by squidmaster on 2008-05-09
I know that it was firefox causing the problem, just glad to see that others think the same way.

I haven't had nearly as many random freezes (though they still happen) now that I downgraded to Firefox 2.

---

### Post by rlogan on 2008-05-11
Had the same issue but it appears it is mostly related to Flash, I saw a link the other day about this and modified the system accordingly and all has been fine since.

Just wish I could remember where I saw the posting to help out !!!

---

### Post by dtrot55 on 2008-05-11
You don't really have to remove FF3 Beta...just go to add and remove and install FF2 or you can go and get Opera and or Seamonkey.  Though there isn't a flash player for Opera yet :(....FF2 prob your best bet.

---

### Post by yaztromo on 2008-05-11
Not using the screensavers are you by any chance? I had a lot of gnome crashes until I changed screensaver to blank instead of random.

---

### Post by KIAaze on 2008-05-11
It doesn't crash for me and I'm using FF3 beta5 in gnome.
But my system isn't very clean either, so I might have different packages.

However, I recently experienced a similar bug while using Xubuntu Hardy:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/114124](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/114124)
Using xfce-terminal crashes X and puts you back at the login screen.
I have no idea how those bugs could be related, but the effect is the same.

edit: Maybe you should install [NoScript]("http://noscript.net/") to see if it's a script that causes the crash.
I have NoScript installed, that's why I noticed the use of scripts.
However, even with all scripts accepted, the site still worked for me.

---

