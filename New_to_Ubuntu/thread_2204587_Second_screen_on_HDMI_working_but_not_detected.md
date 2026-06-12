---
title: "Second screen on HDMI working but not detected"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by SchrodingerCat on 2014-02-09
Hi,
i am using this new screen but is not detected. Hence i can't really use it as i would. I would like to actually have
two screens, my laptop and the second screen. Right now i can see on both screens what i am doing, i would like to use two screens for different things.
any help?

Thank you

---

### Post by Vladlenin5000 on 2014-02-09
Just disable mirroring.

---

### Post by SchrodingerCat on 2014-02-09
Can't to that...is not checked and i can t change it..cause the screen is not detected

---

### Post by Vladlenin5000 on 2014-02-09
And you graphics card is...?

---

### Post by SchrodingerCat on 2014-02-09
i have both Intel and nvidia...but got to remove the nvidia cause i was having troubles..
so the one running now is Intel

---

### Post by Vladlenin5000 on 2014-02-09
You removed a card from your laptop???  :o:confused:

---

### Post by SchrodingerCat on 2014-02-09
no no i just removed the drivers

---

### Post by Vladlenin5000 on 2014-02-09
So you have a hybrid nvidia+intel graphics system. In order to be able to switch between them - the cards, not monitors - you need to install Bumblebee (plus special drivers) as instructed here: [https://wiki.ubuntu.com/Bumblebee#Installation](https://wiki.ubuntu.com/Bumblebee#Installation)
I don't know much about it but I suspect that having the Intel drivers are somehow limited in what they can support regarding multiple monitors. Hopefully someone can provide more accurate details.

---

