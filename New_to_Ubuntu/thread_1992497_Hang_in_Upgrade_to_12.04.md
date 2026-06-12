---
title: "Hang in Upgrade to 12.04"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by JMcCYoung on 2012-05-31
A couple of weeks ago I successfully upgraded my ThinkPad T43 from 11.04 to 11.10 to 12.04 and decided to do the same today with my Acer Aspire 1810TZ that I use at work. The 11.10 upgrade went fine, but several hours into 12.04 it's been stuck for about an hour on "Configuring ubuntu-wallpapers" (under the progress bar, which has been at "About 57 minutes remaining" for that hour plus and in Terminal it's stuck on "ttf-mscorefonts-installer: donwnloading http://downloads.sourceforge.net/corefonts/arial32.exe".

I found [this advice]("http://askubuntu.com/questions/125938/upgrade-hangs-on-ttf-mscorefonts-installer") to use htop - which I don't seem to have - or ps -ejHf, but I wasn't able to figure out which process I was supposed to kill to skip this particular download.

Any advice? Thanks very much!

---

### Post by matt_symes on 2012-05-31
Hi

Open another terminal and type

```
ps -ejHf | grep [p]ackage-data-downloader
```

That should return the pid of the process to kill.

You can then pass that to

```
kill <pid>
```

If in doubt, post back the output of the ps line above.

Kind regards

---

### Post by JMcCYoung on 2012-05-31
Oh, hooray! Thank you *so * much, Matt! I had to use [FONT="Courier New"]sudo[/FONT] to kill it successfully, but now it's scrolling along happily. 

Thanks again, I enormously appreciate the quick advice.

<sigh of relief>

> **matt_symes said:**
> Hi

Open another terminal and type

```
ps -ejHf | grep [p]ackage-data-downloader
```

...


---

### Post by matt_symes on 2012-05-31
Hi

Don't thank me, thank the poster in askubuntu :)

Kind regards

---

