---
title: "Adobe Flash not working"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by Malt Frisky on 2011-11-25
Hi

I've posted this before and I pretty sure I'm not the only one having problems but I'm honestly thinking on giving up on Ubuntu if this continues.

So I'll explain from the start.

Adobe flash is not working for any of my videos, it's completely random, inconsistent and have me at my wits ends.

Every time I think I've cracked it, it goes to the previous problem.

At the the present moment when I run a youtube video I stop and select another video and now and again my entire computer will crash, it's not just youtube, it's other videos via blip.tv, dailymotion, etc.

If I try to skip the video at a certain point, it will crash.

I try to enlarge it, it will crash.

I have two videos running it will crash.

I have tried it both in firefox and Chromium and have exactly the same problem

Yes, I have tried using flash aid and it doesn't make any difference.

I've tried uni stalling and uploading from the site physically and from the Ubuntu store.

My last case of action will be to wipe my entire computer and make a fresh install with Ubuntu or Mint.

And I'm pretty sure I'm not the only one from installing 11.10 were things have gone wrong with this, I've read people complaining about this same issue.

I'm just trying to find out what it is.

Thanks

Jonny

---

### Post by cariboo on 2011-11-25
Because you have tried so many different things, I'd suggest you just make sure that libflashplayer.so is installed in the correct place. Open a terminal and type:

```
locate libflashplayer.so
```

If you have the file in any other location but /usr/lib/mozilla/plugins, remove them.

---

### Post by beew on 2011-11-25
Install flash-aid addon for Firefox, then run the script in Wizard mode. It will clean up conflicting versions, install the latest version (you can choose either the stable version in the repo or the beta from Adobe lab, which sometimes work better) and do some optimization

If that doesn't work try the flashvideoreplacer addon so you don't need flash at all for Youtube and a few other supported sites. Flash doesn't seem to work very well with Windows either. At work I have a 64 bit Windows 7 machine and Youtube also freezes or goes into slow motion quite a bit.

---

### Post by the.phantom on 2011-11-25
next time can you post your other two links so we can see what has been tried?

what are the specks on your system?

memory/processor/video card

and have you disabled graphic acceleration in flash control?

---

### Post by Malt Frisky on 2011-11-26
Okay so I've typed locate libflashplayer.so in the terminal and these are my results.

/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

So I'm guessing I would remove the top two.

How do I go about wiping these completely off, is there a command in terminal to do this?

Jonny

---

### Post by beew on 2011-11-26
If you don't know which one to remove just run flash-aid in wizard mode and choose to install the stable version of flash from repo. It will remove the wrong ones.

I don't know for sure either. If you know for sure just run>  sudo rm pathtoflashversiontoremove

---

### Post by Malt Frisky on 2011-11-26
Okay I've tried removing the top two

/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so

with the following command line after

sudo rm

and I'm still getting the exact same problem.

Though this time it's loading them a little while then refusing to do so.

I've got a few pics in what I keep getting.

I press play and then I get the following.

---

