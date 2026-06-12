---
title: "It started with a Steam video card update..."
date: 2013-06-27
forum: New to Ubuntu
---

### Post by Hytaerix on 2013-06-27
I ended up getting tired of the Steam telling me to upgrade my graphics drivers. I had the newest drivers from AMD's site, but I decided to listen to it. It told me to erase the old update, but I decided to not. Ubuntu also had an update, which I installed. (Anything after this may not be in the correct order) I restarted my computer, and when it was booting back up, the screen was shifted off to the side. Though not a big problem, I tried to find how to erase my old update. Somehow, the side bar ended up only being able to roll, I tried to revert my kernel back to a previous one, and now I get this screen after the short "Push f11 to get to bios" msi screen. How do I fix this?
[ATTACH=CONFIG]244214[/ATTACH][ATTACH=CONFIG]244215[/ATTACH]

---

### Post by dino99 on 2013-06-27
as its a graphic driver issue, the easiest way is to purge the installed one(s) then reinstall it in a raw. To do that:
- boot in recovery mode (hold "shift" key down at bios end process to get the grub menu) and select: a) activate the network , b)root console
- there do the driver removal, then reinstall it (sudo apt-get purge xxxxx  / sudo apt-get install xxxxx)
- when done, select "resume" to continue booting

---

### Post by zero2xiii on 2013-06-27
Hay,

See my thread here:
[http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446](http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446)

Under boot problems, also my signature has a link to the grub2 manual-ish thing. Start there and try to get back into the ubuntu, even if only a root shell. After that, you can tackle the graphics issues.

Cheers and good luck

---

