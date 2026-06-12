---
title: "HTML5 audio not working in Chromium (found solution, have trouble understanding it)"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by zzllxxllzz on 2013-03-11
I cannot play songs on bandcamp.com through Ubuntu's chromium.

I stumbled upon this thread online that seems to have found the solution: [http://code.google.com/p/chromium/issues/detail?id=158955](http://code.google.com/p/chromium/issues/detail?id=158955)

However, my knowledge of the lingo used is severely limited. 

According to the thread I found, i[COLOR=#000000]nstalling the "chromium-codecs-ffmpeg-extra" package fixes the problem.

Can anyone tell me in layman's how to go about installing these codecs?[/COLOR]

---

### Post by plucky on 2013-03-11
> **zzllxxllzz said:**
> I cannot play songs on bandcamp.com through Ubuntu's chromium.

I stumbled upon this thread online that seems to have found the solution: [http://code.google.com/p/chromium/issues/detail?id=158955](http://code.google.com/p/chromium/issues/detail?id=158955)

However, my knowledge of the lingo used is severely limited. 

According to the thread I found, i[COLOR=#000000]nstalling the "chromium-codecs-ffmpeg-extra" package fixes the problem.

Can anyone tell me in layman's how to go about installing these codecs?[/COLOR]

Open Ubuntu Software centre and search for **chromium-codecs** and install.

Or from a terminal ```
sudo apt-get install chromium-codecs-ffmpeg chromium-codecs-ffmpeg-extra
```

Good Luck

---

