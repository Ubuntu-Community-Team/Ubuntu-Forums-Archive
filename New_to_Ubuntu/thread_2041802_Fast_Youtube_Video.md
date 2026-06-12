---
title: "Fast Youtube Video"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by mcimafonte on 2012-08-13
Hello,

I've encountered the problem several times, where I pause a Youtube video and then resume it and the video is played in fast forward speed. I'll try another video and I'll have the same problem. I shut down Google Chrome and go back on Youtube and all videos are playing at that speed. Thanks for the help!

---

### Post by underdog512 on 2012-08-13
Have you observed this behavior in Firefox, or is it isolated to Chrome?

---

### Post by d4m1r on 2012-08-13
I am using the latest Firefox and don't have this issue. I'd recommend switching browsers if you are still seeing this.

---

### Post by PaulW2U on 2012-08-13
> **mcimafonte said:**
> Hello,

I've encountered the problem several times, where I pause a Youtube video and then resume it and the video is played in fast forward speed. I'll try another video and I'll have the same problem. I shut down Google Chrome and go back on Youtube and all videos are playing at that speed. Thanks for the help!

This is a known problem that has nothing to do with the browser you are using. A quick Google and a search of these forums reveals dozens of users experiencing fast playing flash videos. I too had this problem on my laptop and fixed it by changing video/audio card settings in Kubuntu.

One possible fix can be found at [http://forums.fedoraforum.org/showthread.php?t=256584](http://forums.fedoraforum.org/showthread.php?t=256584).

---

### Post by deadflowr on 2012-08-13
Have you installed Flash in Ubuntu? If yes, while in chrome, in the address bar type:

```
chrome;//plugins
```

Expand it by clicking on the details in the upper right corner.
If you've installed flash, you'll see two versions in chrome. The first version is Pepperflash, the one installed in Chrome, and the second is the one installed on your system. Click on the disable link in the Pepperflash version, and see if that helps(try watching something on Youtube.
If it does help, go to the wrench tab in Chrome, dropdown to About Chrome and open, inside this you'll find report a problem button, click it to report your problem and give a rundown of the problem you've had. (I don't know how well this helps but everytime I've had problems and used this, those problems cleared up on later versions.)

Also look in here

[http://productforums.google.com/forum/#!categories/chrome/linux]("http://productforums.google.com/forum/#!categories/chrome/linux")

IF, you haven't installed Flash, go to the software center and install Flashplugin-installer, which will download and install flash onto Ubuntu.

---

### Post by marlow59 on 2012-08-13
when your video is acting oddly try this. 
```
 kill -9 pulseaudio
pulseaudio
```
 Tell me if it works.

---

### Post by drmrgd on 2012-08-13
I'm not sure about if the problem is persistent (i.e. the whole video fast forwards).  If it just fast forwards for a brief period of time when you first load it up, then I do think it's due to Pepper Flash in Google Chrome.  I experienced the same exact thing, and tonight started using Firefox again for comparison.  I've watched about 10 videos now, and none of them fast forwarded at all for me.  

Ever since Pepper Flash, Google Chrome (for me at least) has really not been an ideal browser.  You could certainly try the other suggestions.  But, I do think it's browser related (if you're experiencing the same thing I am that is!).  

Oh, one other thing I forgot - the nice part about it is that I don't have to watch ads anymore.  Since the fast forward only happens at the beginning for me and it only lasts for a few seconds, I find that usually the ads are fast forwarded through and I can basically just skip watching them.  So, that's the plus :)

---

### Post by yorgasor on 2012-08-21
> **marlow59 said:**
> when your video is acting oddly try this. 
```
 kill -9 pulseaudio
pulseaudio
```
 Tell me if it works.

Ugh.  I tried switching back and forth between different flash versions, disabled and enabled flash HW decoding, I installed the latest AMD radeon drivers... Everything I tried either kept the same problem or created new ones.  This is the thing that got it working.  Thanks man, my favorite new activity will be killing pulseaudio.

---

### Post by greasegum on 2012-08-22
This worked great for me. Thanks! Wonder why this works.

---

### Post by Futant on 2012-08-23
This is a strange problem, has happened to me a couple of times using latest firefox (not for ages though), I didn't change anything to fix it, it just sorted itself out... I like it when that happens.

---

