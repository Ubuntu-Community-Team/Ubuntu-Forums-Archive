---
title: "Do the nvidia drivers work now?"
date: 2018-07-22
forum: New to Ubuntu
---

### Post by robpitt on 2018-07-22
Hello,

Do the nvidia drivers work properly? I read that the nvidia driver is freezing peoples systems and I can't be installing Ubuntu if it's going to freeze on me.

I have an NVIDIA GeForce GTX 970 in a desktop system.

---

### Post by oldos2er on 2018-07-22
I use Xubuntu with an Nvidia 1050ti, using the v390 drivers. No problems.

---

### Post by Bashing-om on 2018-07-22
2 -

xubuntu cosmic (18.10) GeForce GT 710B: nvidia-driver-390   - 390.67-0ubuntu1 

[INDENT][INDENT]no issues
[/INDENT][/INDENT]

---

### Post by NM5TF on 2018-07-22
according to the nvidia driver webpage, your GeForce 970 should be using 375.39

[https://www.geforce.com/drivers/results/114708]("https://www.geforce.com/drivers/results/114708")

---

### Post by oldfred on 2018-07-22
[https://www.geforce.com/drivers](https://www.geforce.com/drivers)
This seems to be more current. The 375 may have been current when card was released.
And 390 or 396 should both be current.
Not sure what version is in Ubuntu repository, but ppa will add all the current versions if you want that.

The 17.10 release using wayland had issues. But 18.04 which does not use wayland by default should be ok.

---

### Post by Autodave on 2018-07-23
No problem here with 3 machines running 18.04 and all 3 different Nvidia cards.

---

