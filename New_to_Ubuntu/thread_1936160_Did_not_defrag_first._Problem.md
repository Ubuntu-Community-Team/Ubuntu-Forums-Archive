---
title: "Did not defrag first. Problem?"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Jridley on 2012-03-05
[SIZE=2]Hello, I'm duel booting with Win7 and just installed Ubuntu and I was reading some beginners guilds, and came across many places where it is recommended that I defrag my drive before installing. How important is this? I gave ubuntu half my drive (150 GB) during the install process and am wondering if I just defrag windows and reinstall?
[/SIZE]

 Thanks; 

Jridley

---

### Post by MG&amp;TL on 2012-03-05
If nothing's broken; don't. It's just a recommendation to aid partitioning, particularly if you have problems.

---

### Post by Jridley on 2012-03-05
Awesome, thank you much.

Jridley

---

### Post by idoitprone on 2012-03-05
You see gparted or the window's partition manager will shrink a paritition that has data in it. Only when the part is empty will it be resized

If you have a 1gb partition and 100 mb used space. In windows the filesystem becomes stupid at time and randomly spread some of the used chuncks to the end of the filesystem. You end up in a scenerio where you were able to decrease the size up to 900 mb, but now is force to use resize and free only 10mb.

That is why you defrag windows before you install. No problem

---

