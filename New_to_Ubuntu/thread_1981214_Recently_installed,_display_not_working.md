---
title: "Recently installed, display not working"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by Quevvy on 2012-05-16
Recently, I installed Lubuntu from a flash drive onto my (other) computer, using UNetbootin. The installation seemed to go without a hitch, but the first time I started it up, the monitor would not display anything. However, the monitor showed that it could tell the computer was on (the monitor wasn't in standby).

Should I try reinstalling? Or is there another solution?

---

### Post by Quevvy on 2012-05-16
Edit:

---

### Post by BLewis on 2012-05-16
What graphics card do you have since there are many known bugs with many cards (there has been in the past and most likely there always will be due to XOrg and stuff...)

If I was new to Ubuntu I would just check out these Ubuntu Help pages:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

---

### Post by Quevvy on 2012-05-16
> **BLewis said:**
> What graphics card do you have since there are many known bugs with many cards (there has been in the past and most likely there always will be due to XOrg and stuff...)

If I was new to Ubuntu I would just check out these Ubuntu Help pages:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

Well, that could help if I could actually do anything with Linux on the computer, but I can't see anything…

---

### Post by Rodney9 on 2012-05-16
Use a live cd and try running with
```

nomodeset
```

when the it is starting up, press Esc and then goto more options and press Enter and select nomodeset. That should let you boot.

you can then check what video you are using.

Rodney

---

