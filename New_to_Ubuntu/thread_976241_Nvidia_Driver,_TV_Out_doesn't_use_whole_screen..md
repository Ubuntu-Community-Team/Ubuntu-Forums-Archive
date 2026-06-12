---
title: "Nvidia Driver, TV Out doesn't use whole screen."
date: 2008-11-09
forum: New to Ubuntu
---

### Post by osc1882 on 2008-11-09
Ubuntu 8.10
Nvidia Drivers

I'm using Ubuntu on a standard def TV to watch videos. But the video out, the top of the TV is not being used. There is a black bar on the top of the TV regardless of what rez I run at. The weird thing is, when I used the same PC and tv and I was running XP I would have the same problem untell I told VLC run on full screen. How can I get it to use the whole screen in Ubuntu?

---

### Post by natirips on 2008-11-09
Try configuring it with NVidia X Server Settings (type```
sudo apt-get install nvidia-settings
```in the terminal to install it (it should be in the System->Admin->NVidia X Serv...).

Also, try using a video file with diffrent proportions (i.e. 4:3, 16:9, etc.) and see how it looks. If the black bar at the top changes as video proportions change, than it's a VLC issue (i.e. it's not centering well so you see a black bar only at the top, and not half of it at the top, half at the bottom).

---

### Post by osc1882 on 2008-11-09
nvidia-settings comes installed when you installed the Nvidia drivers. It's what I had to use to turn on the TV out. And Ubuntu it's self is cropped off as well as any video I play.
Is there a setting in nvidia-settings that you guys know I can change to fix this?

---

### Post by natirips on 2008-11-09
> **osc1882 said:**
> nvidia-settings comes installed when you installed the Nvidia drivers. It's what I had to use to turn on the TV out. And Ubuntu it's self is cropped off as well as any video I play.
Is there a setting in nvidia-settings that you guys know I can change to fix this?

It wasn't installed by default for me (Ubuntu 8.04). I don't have another monitor connected to my computer at the time, but anyway, the only thing that comes to my mind right now is to check panning(see attached jpgs).

---

### Post by MasterSander on 2008-11-09
Is there a switch on your keyboard to switch to LCD+ Tv out? Cause I didn't have to use that in xp either but I had too in ubuntu, try to find that. 

If that works, and you get black and white colors, that means you don't have an ntsc tv and need to switch to pal by typing something in the terminal, you should look that up if it occurs.

---

### Post by osc1882 on 2008-11-09
Hum.I didn't try panning because I thought that was for if you wanted to run your desktop at a higher rez then your screen. So you move your mouse around to see more of your desk top.

And no I Don't have a tv out button on my keyboard. It'sa NTSC tv, I think that is all set correctly.

Any other ideas?

---

### Post by natirips on 2008-11-10
Try setting the "position" to "absolute", and adjusting the value from "+0+0" to something like, for example, "+100+50" to try centering the image. Also adjust panning if needed.

---

