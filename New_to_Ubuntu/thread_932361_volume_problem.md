---
title: "volume problem"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by gkraju on 2008-09-28
hi i am having ubuntu 8.04 in my system the sound is too low i checked the master volume  option it is 100% but sound is not audible if play any video file help me ... thanks in advance

---

### Post by Biggy on 2008-09-28
System > Preferences > Sound . and select alsa or autodetect

---

### Post by kansasnoob on 2008-09-28
Try installing gnome-alsamixer. You can either install from synaptic or from terminal:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Applications > Sound & Video. Look at my toggles:

[ATTACH]86649[/ATTACH]

[ATTACH]86650[/ATTACH]

---

### Post by kansasnoob on 2008-09-28
If you should happen to keep having trouble with sound after that this tutorial solved all my pulse audio troubles:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

But that may no longer be necessary, it's been quite a while since I did a fresh install of Ubuntu 8.04 and I should mention that Xubuntu 8.04 doesn't use pulse audio.

If you need more help or a better explanation for following that guide feel free to ask.

---

### Post by gkraju on 2008-09-28
thanks kansasnoob it worked

---

