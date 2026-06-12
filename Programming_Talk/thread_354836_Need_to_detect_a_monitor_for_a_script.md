---
title: "Need to detect a monitor for a script"
date: 2007-02-06
forum: Programming Talk
---

### Post by johng4 on 2007-02-06
I'm writing a shell script for a friend so that when he boots up with his laptop, it can detect whether or not he's using his dual display (nvidia) or if he's using his single display so that it can automatically load in a config file for his games to have them play at the appropriate resolution.

Namely, this is for WoW, since he has his monitor at home at a slightly larger resolution, he has to manually change the WoW config file to update his in-game resolution every time he switches between using both monitors and the single monitor.

I've done some googling, but I'm not sure of which file or command would return this value.

---

### Post by neilp85 on 2007-02-06
There's probably a way to do this by looking for the devices in /dev. I'm not sure how exactly to do this but hopefully this will get you going in the right direction.

---

### Post by johng4 on 2007-02-06
Well, what I'm going to try when I get a chance to sit at his laptop is grab lsdev results, and grep for his monitor.

Gotta wait for that though.  Not sure if that will return anything other than his video card though.

---

### Post by jblebrun on 2007-02-06
The read-edid package might help you.

---

