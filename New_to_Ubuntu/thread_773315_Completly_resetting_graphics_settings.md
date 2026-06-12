---
title: "Completly resetting graphics settings?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Totalchaos02 on 2008-04-28
So I was unable to set up ATI Big Desktop (it really just refused to use any setting that was not two screens of the same resolution) and now I just want to restore my original settings (Single screen at 1440x900). I reset my xorg.conf file and tried to use aticonfig to turn off one of screens but it simply didn't work.

 At one point my system crashed and after that aticonfig just restarted my system and I cant change my resolution at all (it just resets to 2560 x 1024 even though my primary screen looks like 800x600). Is there anyway I can just reset all files that have to do with video settings? When I booted up after installing 8.04 it was 1440x900 with no issues, now I don't even have that option and if I couldn't change it anyway. Anything I could do here short of completely formating and reinstalling because I desperate.

---

### Post by Totalchaos02 on 2008-04-28
I finally managed to separate the two screens however at 1440x900 my primary monitors desktop is actually larger than the screen. When I move the mouse to the side of the screen in pans over. Any ideas on how to fix this?

---

### Post by Totalchaos02 on 2008-04-28
bump

---

### Post by dokdoom on 2008-04-28
I know people who have xinerama enabled with ATI cards, they used xrandr though. Unless you want big desktop. I also think typing aticonfig -h will be your friend also. As far as reseting your xorg.conf the only way I know how to do that is to reconfigure x.

---

### Post by Totalchaos02 on 2008-04-28
I looked through it and didn't see anything that I thought could help me, but I am also wary of making things worse.

---

### Post by Totalchaos02 on 2008-04-29
bump

---

