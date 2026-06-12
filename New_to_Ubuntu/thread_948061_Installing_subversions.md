---
title: "Installing subversions?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by ninjaaron on 2008-10-14
Ok, I'm trying to get my wireless working on my Macbook. I have a artheros wireless card. One of the tech guys at my workplace told me I should get madwifi, but not the main one; he said the subversion would be better. He's a tech guy, so I listened to him.

Anyway, I managed to stumble my half way through the process. I have just run 'make clean', and that seemed to work.

The instructions on the website said 'now just recompile and install!'

That's all well and good for someone who's been running ubuntu for more than two days, but I'm at a loss.

---

### Post by SuperSonic4 on 2008-10-14
Is there no readme file with instructions? There usually is

In case there is not you might need to check if you have subversion install although it might be part of build-essential in ubunut

---

### Post by GrayMagiker on 2008-10-17
Well I don't know anything about wireless drivers or madwifi, but maybe I can help decode what your tech friend is saying.  

To "recompile and install" generally means to run the following lines
```

make
sudo make install

```

---

