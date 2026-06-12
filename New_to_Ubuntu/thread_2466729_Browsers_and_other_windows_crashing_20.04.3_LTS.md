---
title: "Browsers and other windows crashing 20.04.3 LTS"
date: 2021-09-04
forum: New to Ubuntu
---

### Post by obontoe on 2021-09-04
I use a Dell Precision M4800 with Ubuntu 20.04.3 LTS


And I am having an issue where any browser I use (Chromium, Firefox) constantly crashes. Typically it just goes to the screen on Chromium, 


" Aw Snap! Something went wrong while displaying this webpage."


and similar messages. Occasionally I'll have all of my windows crash (close completely). I have ran a memory test and it appeared to be fine (not an expert). This has been happening ever since I installed Ubuntu on this system, so the issue was present on previous releases as well.




[Output of free -m]("https://i.stack.imgur.com/8tWn4.png")




[ Written to /var/log/syslog around the time of the crash (5:04:52 may have been the time)]("https://i.stack.imgur.com/YbO8R.png")

---

### Post by mikewhatever on 2021-09-04
Please don't post screenshots of windows with text outputs. Give us the outputs as copy/paste in [noparse]```
 
```[/noparse] tags.

There isn't any usefull info to work with, so you might want to rectify that, and post the outputs of the following:
```
lspci -nnk
env | grep XDG_SESSION_TYPE
```

---

### Post by tea for one on 2021-09-04
> **obontoe said:**
> This has been happening ever since I installed Ubuntu on this system, so the issue was present on previous releases as well.

When did you install Ubuntu for the first time?

Couple of suggestions:-

Temporarily disable/remove all browser add-ons.
Try a live session with Firefox for a few hours.

---

### Post by monkeybrain20122 on 2021-09-04
Have you modified your .profile or .bashrc say setting LD_LIBRARY_PATH or LD_PRELOAD?

---

