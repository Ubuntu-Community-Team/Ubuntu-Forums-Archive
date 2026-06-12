---
title: "Installed nvidia... ubuntu loads in 2d not 3d..."
date: 2012-05-06
forum: New to Ubuntu
---

### Post by steviematt on 2012-05-06
My graphics card is a Nvidia GeForce 310 and this is apparently not affected by the bugs reported, it is much newer than the series 7 and 8 nvidia cards that have had problems.

I installed the current nvidia drivers from the software centre, but now when i log on to 12.04 64-bit my screen turns grey for about 3 seconds and then my desktop pops up in 2d, it was working fine in 3d before...

I felt the need to inatll the nvidia drivers because i need to be able to project to an OHP for teaching, withoutthe drivers it wasn't working.

So my problem is: **ubuntu loads in 2d only since i installed the nvidia driver, also related, my web browsers (ff and chromium) always load in full screen mode when i click them from the launcher**

what should i do?

---

### Post by Paqman on 2012-05-06
Which Nvidia driver did you install from Software Centre? Try opening Additional Drivers and if the driver you're using isn't the one it recommends try switching to that. Have you got the Nvidia settings tool installed?

---

### Post by steviematt on 2012-05-06
I did a bit of frantic searching and found a fix. I installed something called bumblebee 3.0 by following the guide here [https://wiki.ubuntu.com/Bumblebee ]("https://wiki.ubuntu.com/Bumblebee")

Everything seems to be working fine now... thanks for replying though... in response to your question, i installed the nvidia-current from the software centre (if i remember correctly it is 290.40)

Anyone with the same problem i had, go to the link in my second sentence :)
[]("https://wiki.ubuntu.com/Bumblebee")

---

### Post by Paqman on 2012-05-06
Ah, so you've got a laptop with hybrid graphics? Glad Bumblebee seems to have sorted you out. Hybrid graphics are a bit of a stumbling block on Linux.

---

