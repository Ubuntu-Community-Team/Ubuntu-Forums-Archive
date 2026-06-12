---
title: "Compizconfig-setting-manager"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-10-31
So I like to  invert the colors, when reading because it much nicer on my eyes. I always do it though the compiz config settings manager but it is not there in Ubuntu 12.10 is there anyway to get it back to to achieve this functionality through another method?

---

### Post by howefield on 2012-10-31
It is in the repositories, so you can install it. Whether it is advisable to do so or not is a different story.

Your choice.

---

### Post by TheMTtakeover on 2012-11-01
> **howefield said:**
> It is in the repositories, so you can install it. Whether it is advisable to do so or not is a different story.

Your choice.
What is in the repositories exactly?

---

### Post by grahammechanical on 2012-11-01
> What is in the repositories exactly?

Why CompizConfiguration Settings Manager or CCSM, of course. Look for it in the Ubuntu Software Centre. Just search for Compiz. Whereas Compiz compositing manager is installed by default in Ubuntu

[http://www.compiz.org/]("http://www.compiz.org/")

the settings manager has to be installed afterwards. Unless you are talking about gconf Editor, which is now replaced by dconf Editor. I have dconf editor in the Dash. I do not remember deliberately installing it.

Regards.

---

### Post by TheMTtakeover on 2012-11-01
> **grahammechanical said:**
> Why CompizConfiguration Settings Manager or CCSM, of course. Look for it in the Ubuntu Software Centre. Just search for Compiz. Whereas Compiz compositing manager is installed by default in Ubuntu

[http://www.compiz.org/](http://www.compiz.org/)

the settings manager has to be installed afterwards. Unless you are talking about gconf Editor, which is now replaced by dconf Editor. I have dconf editor in the Dash. I do not remember deliberately installing it.

Regards.

Right and I have CCSM installed. My issue is that the option to invert the colors is not there. It was there in 12.04 but now in 12.10 it appears to be gone.

EDIT: I just read my original post and I see now that it makes it seems like I am trying to install CCSM, I apologize for that. I have it installed I am just looking for a feature in there that I used to use that now appears to be gone.

---

### Post by kanikilu on 2012-11-01
Can you not enable the Negative plugin under Accessiblity? Or are you looking for something else...?

---

### Post by TheMTtakeover on 2012-11-01
> **kanikilu said:**
> Can you not enable the Negative plugin under Accessiblity? Or are you looking for something else...?

Yeah I can't find the negative plugin. Its like its gone.

---

### Post by COMECON on 2012-11-01
Have you installed compiz-plugins? Try opening a Terminal and running:
```
 $ sudo apt-get install compiz-plugins
```
Regards.

---

