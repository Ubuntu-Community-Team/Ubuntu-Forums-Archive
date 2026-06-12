---
title: "Ubuntu Does Not Load at all!"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by alsamman on 2008-05-03
I installed hardy heron on my friends computer through windows wubi installation. I restarted and got to GRUB and selected Ubuntu but when it tries to boot, the loading bar freezes and does not continue. This has been a problem ever since I tried to install Feisty on his computer so we can only use windows xp since hardy heron does nto boot at all. The computer he has is this: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00280650&lc=en&cc=us&dlc=en&product=445596](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00280650&lc=en&cc=us&dlc=en&product=445596)
except he has a ATI Radeon 9250. I can't seem to find a fix on the forums anywhere and this seems to be a very strange issue. Any help would be greatly appreciated.

---

### Post by acelin on 2008-05-03
> **alsamman said:**
> I installed hardy heron on my friends computer through windows wubi installation. I restarted and got to GRUB and selected Ubuntu but when it tries to boot, the loading bar freezes and does not continue. This has been a problem ever since I tried to install Feisty on his computer so we can only use windows xp since hardy heron does nto boot at all. The computer he has is this: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00280650&lc=en&cc=us&dlc=en&product=445596](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00280650&lc=en&cc=us&dlc=en&product=445596)
except he has a ATI Radeon 9250. I can't seem to find a fix on the forums anywhere and this seems to be a very strange issue. Any help would be greatly appreciated.

Sounds like a write error- try reinstalling Wubi.

---

### Post by alsamman on 2008-05-03
> **acelin said:**
> Sounds like a write error- try reinstalling Wubi.

i installed it from the disk with wubi already on it and this issue isnt new for this computer, i tried to install feisty and gutsy using livecd and got the same problem where the livecd would not load at all either so i thought i could get ubuntu installed now that you can install via windows but it doesnt boot

---

### Post by alsamman on 2008-05-04
bump

---

### Post by alsamman on 2008-05-04
bump

---

### Post by SunnyRabbiera on 2008-05-04
I have seen simular issues pop up here before.
Perhaps Ubuntu is not the distro for you, you may want to try another one.
Mandriva is a good option right now.
but this is unusual, most of those specs I share with your friend yet I am up and running full speed with ubuntu hardy.
My model is not too far off from that.

---

### Post by alsamman on 2008-05-04
> **SunnyRabbiera said:**
> I have seen simular issues pop up here before.
Perhaps Ubuntu is not the distro for you, you may want to try another one.
Mandriva is a good option right now.
but this is unusual, most of those specs I share with your friend yet I am up and running full speed with ubuntu hardy.
My model is not too far off from that.

Yeah, I don't understand why it won't work. Since Feisty it just can't function properly and I'm sure to fix this it would probably take a lot of work, it doesn't seem like something that needs a little tweaking.

---

### Post by fixitdude on 2008-05-04
Always look at the log. Where does it stop? You can read the log even if it isn't booting by booting the live CD and using it to see the log.

You can hit "esc" while it's booting to see the text of the boot process.

Most of the boot process is in the "init.d" areas, it's possible to comment out a line and have it skip that part if it's not critical.

Just some suggestions.

---

### Post by alsamman on 2008-05-04
> **fixitdude said:**
> Always look at the log. Where does it stop? You can read the log even if it isn't booting by booting the live CD and using it to see the log.

You can hit "esc" while it's booting to see the text of the boot process.

Most of the boot process is in the "init.d" areas, it's possible to comment out a line and have it skip that part if it's not critical.

Just some suggestions.

thanks for the info, ill try that as soon as i can since its not my computer that has this problem

---

