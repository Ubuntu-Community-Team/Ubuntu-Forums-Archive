---
title: "WINE Issues with Nvidia"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-05-10
I installed Ubuntu because I wanted to try it out and also heard in some cases that the game ran better than windows...well i got steam installed and get into a game just fine..but...I GET LIKE 9-20 FPS....I have a Nvidia 8600 GT ... yeah its not the best but its way better than this game can show and works flawlessly on Windows....anyone know what is going on...if i cant play the game on Ubuntu then I will have to resort to windows and im trying to find a means to get away from it.

System:
Amd64 x2 4200+
1.5g DDR1 3200 Ram
Biostar T-Force 6100-939
Nvidia 8600 GTXXX 256mb PCIe
Ubuntu 8.04 x64

Thanks!

---

### Post by warbread on 2008-05-10
What game are you trying to run?

I should point out that I do not game on Linux.  I recognize that it's possible, but I don't like it, unless it's native.  I will point out to you that there is no guarantee at all that any Windows game will work in Wine.

---

### Post by dtrot55 on 2008-05-10
Counter Strike Source...it is in the WINE Database as one of the best workign games in WINE...so figured I would give it a try.

---

### Post by warbread on 2008-05-10
Sure, there's no harm in trying.  The only solution I could think of those is to make sure you have the right drivers installed.

[Edit:It looks like you can force Wine back to version 46 ]("http://ubuntuforums.org/showthread.php?t=672818")and it works.

---

### Post by dtrot55 on 2008-05-10
went to the hardware manager in 8.04 and enabled the nvidia drivers.

---

### Post by dtrot55 on 2008-05-11
Wine still acting up....reformatted to Ubuntu 8.04 x32...enabled my nvidia drivers and still only getting 9-20fps....PLEASE HELP....I do play in windows but i want to get Ubuntu working correctly to. 

Thanks!

---

### Post by warbread on 2008-05-11
Go into Synaptic Package manager, search for Wine and under tools, select "Force Version".  Select version 46.

---

### Post by dtrot55 on 2008-05-11
I went to the package manager and found wine and went package>force version but the force version option is not available...any idea???

---

