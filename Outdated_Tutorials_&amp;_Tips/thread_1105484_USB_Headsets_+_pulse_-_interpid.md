---
title: "USB Headsets + pulse - interpid"
date: 2009-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by KillerKiwi on 2009-03-24
I just brought my self a new USB headset, which is all good, it appears as a USB sound card.. pulse audio sees it when I plug-in but the sound all stays on the machine card not the headset!

You can then move the streams using pulse utils but if you unplug the headset and plug it back in again you get the same issue.

I've added an option to earcandy to deal with this, so I'm looking for a few people to give a try it works very well for me.. but I only have one headset ;)

```

sudo apt-get install bzr
cd ~
mkdir earcandy
bzr branch lp:~killerkiwi2005/earcandy/0.4
cd 0.4
./ear_candy

```

---

