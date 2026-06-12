---
title: "Sound in both Rhythmbox and Firefox"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Ameades on 2008-07-30
Hey guys I am trying to get sound to work when both Rhythmbox and Firefox are open and I am trying to following this guide 

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

but I am stuck on step 2 configuring the asound.conf settings.  How do I preform this step?  Is there an easier way to get sound to play on both?

Please remember I am an Linux newbie.  

Thanks a bunch :)

---

### Post by mevets on 2008-07-30
You need to run this in the terminal:
```

sudo gedit /etc/asound.conf

```
It probably worth it to mention my computer has problems with pulse audio too. My fix was to essentially use ALSA instead. You can do this by going to System > Preferences > Sound and change all the comboboxes to ALSA. This doesn't actually fix pulse audio, but for me, it just works and thats what I care about most.

---

### Post by tuxxy on 2008-07-30
Yes try ALSA, this should get them both working together.

---

### Post by Ameades on 2008-07-30
Awesome that worked! Thanks for your help :)

---

