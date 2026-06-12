---
title: "Video and Music Not Working"
date: 2017-11-15
forum: New to Ubuntu
---

### Post by troubled15 on 2017-11-15
Hi everybody, I turned my computer on today and all videos and music wont work anymore. They just freeze and don't play, though for videos I can look at each frame by moving the selector around, but they never actually play. It doesn't matter if I try something I already downloaded, or try and watch videos on other websites, anything with sound won't play.

I had this problem for several moths before I upgraded to 17.10, but just recently out of nowhere these problems have come up again. I don't know what caused them in the first place, and used a different user account that didn't have them for the months when I had the problems before. I thought the upgrade would fix whatever it was, but now they seem to be back and I don't know what to do

Thanks for any help you guys could give me on this problem.

---

### Post by Quarkrad on 2017-11-15
I can't help specifically but having played/tried 17.10 myself there are a number of areas/things that are not working properly, as with a lot of X.10 releases. So ... in a way not surprising things are not 100% with 17.10.  This is why you see 'stick with LTR or x.04' releases on this forum. I have gone back to 16.04 - 18.04 is not that far away

---

### Post by troubled15 on 2017-11-15
I know the release may have some problems, but when I upgraded the problem was temporarily gone so I don't think it is something specific to 17.10, as I had the problem long before I had 17.10.

---

### Post by Yellow Pasque on 2017-11-15
What specific programs have you tried to play the videos and music? Just to be clear, the alternate user account currently works as intended, correct?

---

### Post by troubled15 on 2017-11-16
Rythembox, Spotify, videos, VLC media player and then Youtube on Chrome and Firefox. Yes, the alternate account hasn't had any issues at all, and plays everything fine.

---

### Post by Yellow Pasque on 2017-11-16
On your problematic account, try to reset the user pulse config (and then restart pulseaudio):
```
rm -r ~/.config/pulse; pulseaudio -k
```

---

### Post by troubled15 on 2017-11-16
Tried that, and the problem is still here. :(

---

