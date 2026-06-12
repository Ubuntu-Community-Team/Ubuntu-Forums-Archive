---
title: "Ubuntu 11.10 with Hauppauge PVR-250 problems"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by grnmon97 on 2011-10-25
I am a complete newbie to Linux and have run into issues with installing a PVR-250 tuner card. In my ignorance, I thought the process would be nearly plug and play, but that wasn't necessarily the case. I installed Ubuntu 11.10 and installed the hardware physically ok. lspci shows the card is recognized, but after running cat /dev/video0 > test.mpg the playback shows no sign of any signal and it looks as though it did nothing at all. I have started in MythTV but want to first make sure the tuner card is functioning before I knock my head against the wall with Myth. Can anyone point me in a direction to be able to test that the tuner card works? I have found a wealth of info on drivers, firmware, etc. but I don't know how old or relavent any of it is. I have followed many of the instructions, but end up at the same place. Any help is greatly appreciated.

---

### Post by wolfen69 on 2011-10-25
[My tutorial]("http://ubuntuforums.org/showthread.php?t=1734916")

---

### Post by anewguy on 2011-10-25
This is an old post, but I think it still applies (except for the ivtv-source - it's not in synaptic anymore so it may not be needed now).  I would install the ivtv packages from synaptic package manager, reboot, the start at step 4.  The guide is in the kubuntu forums, but should work equally well with "normal" Ubuntu.


[http://kubuntuforums.net/forums/index.php?topic=3085164.0]("http://kubuntuforums.net/forums/index.php?topic=3085164.0")

Dave ;)

---

### Post by wolfen69 on 2011-10-25
And to add to this, in order to do:
```
cat /dev/video0 > test.mpg 
```
you need **ivtv-utils** first,
then do 
```
ivtv-tune -c25
``` (25 is just a random channel #)

*then* run
```
cat /dev/video0 > test.mpg
```
should yield results.

---

### Post by grnmon97 on 2011-10-26
Thank you all for the feedback and ideas... I finally realized that the card was capturing video all along, it was my playback that was tainted.  In my effort to get MythTv working, I added a source that was corrupting some of the video files in oneiric.  I removed the sources, reinstalled VLC and now I have video.  So I KNOW my tuner card works.  The video is currently scrambled (a movie from svideo plays but is wavey and scrambled.) and needs to be fixed, but at least I know that I am on the right track and the tuner is not a dud.
Thanks again. Looking forward to learning a lot more.

---

### Post by anewguy on 2011-10-27
> **wolfen69 said:**
> And to add to this, in order to do:
```
cat /dev/video0 > test.mpg 
```
you need **ivtv-utils** first,
then do 
```
ivtv-tune -c25
``` (25 is just a random channel #)

*then* run
```
cat /dev/video0 > test.mpg
```
should yield results.


As per the info I provided:  install the ivtv stuff from synaptic package manager, then go to step 4 in the how-to -> notice step 5 as what you have posted is already in the thread.  Just thought I'd mention that so that if someone else sees this thread they know to read the how-to carefully.

BTW - love the avatar, wolfen69!  ;)

---

