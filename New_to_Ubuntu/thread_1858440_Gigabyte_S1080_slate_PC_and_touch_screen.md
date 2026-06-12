---
title: "Gigabyte S1080 slate PC and touch screen"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by inocentpc on 2011-10-12
I've already installed kubuntu on my laptop, and it runs faster than win 7. 

now, I've got this slate PC that runs win 7, and to try kubuntu on it i've already got a new separate HDD. everything is great but the touch screen is not responsive. every time I touch it, the mouse arrow runs to the upper left corner. do you know if there are drivers for the touch screen? I googled and nothing so far. 

another concern I have is the batt life. from what I read, there are some issues with the kernel. any thoughts?

---

### Post by acrazyplayer on 2011-10-12
What version of ubuntu are you using? The battery life can be resolved through some settings being changed. The packages to update would be the xorg ones, thats is what would handle the input you want, however nothing may change at all by doing so. to do so you need to enable "xorg-edgers" but I will warn you that this can potentially mess up your system so please have a back up and also install the program "ppa-purge", you should be able to revert any changes should your system mess up. 

here is how to update xorg...
```

sudo add-apt-repository ppa:xorg-edgers/ppa && sudo apt-get update && sudo apt-get dist-upgrade 
```you must say yes to install everything it wants, do not pick and choose what to install.

after it is finished, restart and see if what you want works if so then good job. If not and there are no problems then you can just leave it as it without worrying. If there are some problems or you can not even get to a desktop and only get a black screen then get to a terminal, easiest way is to start up in "recovery mode" and type in 

```
 sudo ppa-purge xorg-edgers
```to revert any changes and get your system back up and running. Good luck

---

### Post by inocentpc on 2011-10-14
I tried to work your commands last night and it took me too long (lost connectivity several times etc). I'll work on it this weekend.

---

