---
title: "HOWTO: Easy fix for out-of-sync audio in OpenAL-based Games"
date: 2008-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Megatog615 on 2008-10-30
If sound is out of sync or other issues for OpenAL-based games(such as ioQuake3), try this.

Create a new file in your home directory called ".alsoftrc":
```
touch .alsoftrc
```
Then put "refresh = 2048" inside:
```
echo "refresh = 2048" >.alsoftrc
```

Your games' sound should now be synced. If not, you can try other values for refresh to fix it.

Note: I have gotten rid of PulseAudio in favor of ALSA. If your sound is still out of sync and you use PulseAudio it is likely due to Pulseaudio.

---

