---
title: "Sound only works through headphones..."
date: 2008-05-17
forum: New to Ubuntu
---

### Post by DMzda on 2008-05-17
I noticed that no sound was playing from th speakers whilst watching a video on Youtube. I started looking around for solutions, but I haven't found any.

When I play a video on VLC or any other media player, no sound is heard at all, not even on the headphones.:(

I have a Dell Dimension 5150, with a Sigmatel STAC9221 A1.

Unfortunately, i am unable to download anything through the terminal or through Synaptic, due to [this unsolved problem.]("http://ubuntuforums.org/showthread.php?p=4979069")I can download packages from [here]("http://packages.ubuntu.com/hardy/i386/allpackages"), however. So if i need to download any extras, please tell me the name of the package.

Any help will be appreciated.:)

---

### Post by DMzda on 2008-05-17
Any help???

---

### Post by nowin4me on 2008-05-17
Try getting an update with the update manager.
Then try getting a driver for your sound card.

---

### Post by DMzda on 2008-05-17
Unfortunately, I cannot use the update manager. Could you give me a link to the driver? Thanks

---

### Post by nowin4me on 2008-05-17
> **DMzda said:**
> Could you give me a link to the driver? Thanks

What's your sound card name?

---

### Post by DMzda on 2008-05-17
> **DMzda said:**
> 
I have a Dell Dimension 5150, with a Sigmatel STAC9221 A1.


There you go.

---

### Post by nowin4me on 2008-05-17
I thought I heard someone once said that the drivers are on the CD.
Go and have a check.

---

### Post by ugm6hr on 2008-05-17
Maybe the spakers are muted?

Try this:
```
alsamixer
```

Then use arrow keys to move between channels and increase, and press M to mute/unmute all channels.  Maximize everything, then try again.

---

### Post by DMzda on 2008-05-18
> **ugm6hr said:**
> 
Try this:
```
alsamixer
```


Thanks.

I tried this before, but it doesn't work. The speakers still don't work.

---

### Post by markbuntu on 2008-05-18
Go to System/Preferences/Sound and fool around with those settings. You will most likely find one of them that will work.

---

### Post by logx on 2008-05-18
Have you check under "volume control" settings the status of the switches?

---

### Post by LambdaCalculus379 on 2009-03-18
Got sound working after reading through this thread...

And also noticing that the speakers I had hooked up to my PC weren't working in the first place. :)

---

