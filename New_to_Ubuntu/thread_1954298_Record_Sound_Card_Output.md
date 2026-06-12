---
title: "Record Sound Card Output"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by Harry084 on 2012-04-07
I can't seem to record output from my sound card. I'm running ubuntu 11.10 on an HP pavilion dv6. In 10.10 I'd been using audacity and alsamixer, but that doesn't appear to work now. 
I'd be really appreciative if someone could point me in the right direction!

Thanks

PS- is there some sort of driver i could use? I'm quite new at this, but the problem is that the correct entry is not appearing in either alsamixer or audacity.

---

### Post by drs305 on 2012-04-07
When I had trouble with audio recording in 11.10 I found *pavumeter* and *pavucontrol* helpful. I could experiment with pavucontrol's 'output devices' tab to change audio outputs until I got it to show the audio levels. If you think you already have the correct drivers installed this may be all that is necessary.

```
sudo apt-get install pavumeter pavucontrol
pavucontrol &
pavumeter &
```

---

