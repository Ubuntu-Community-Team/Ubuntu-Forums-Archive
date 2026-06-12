---
title: "when I hold a key in, my mouse stops working"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-04-27
I was trying to play alien arena. but It was impossible to do, when I couldn't move and shoot at the same time.

I have been having this problem since gutsy, and I don't have a clue what to do about it. If anyone can tell me how to get my computer receiving input from both keyboard, and mouse at the same time, it would be much appreciated.

specs are lenovo 3000 n200, nvidia GeForce Go 7300 graphics, intel centrino duo proc. it works when I use the touch pad. (I can hold a button and move the mouse at the same time) but anyone who has aver played a FPS knows that using a touch pad is next to impossible.

thanks in advanced.

---

### Post by happyhamster on 2008-04-27
Perhaps your problem is related to:
[https://answers.launchpad.net/ubuntu/+source/xorg/+question/30254](https://answers.launchpad.net/ubuntu/+source/xorg/+question/30254)

---

### Post by Viperlin on 2008-05-19
just in case you never found this, its a bug in mouseemu that thinks your using a laptop, disables mouse/touchpad when using keyboard, removing mouseemu and blocking it fixed this for me

---

