---
title: "HELP Unetbootin crashed my system"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by Durin01 on 2012-02-23
hi,

 I am fairly new to Ubuntu, and I tried unetbootin, but now it prevents my system to boot.

Due to the fact that my mainboards SATA ports are fried and dont detect any harddrives I was froced to install my system on a external USB-Drive.

Now i wanted to create a install from stick using unetbootin. the thing is it created it wrongly on my USB-Harddrive (my main system), so when I boot normally grub doesn't start up but unetbootin and leaves me with the choices "Install Ubuntu" or "Test without Install". (There are a few others but they don't work properly (do nothing))

If I "Test" Ubuntu the normal system folders are not shown, although they are still there (checked it by plugging the harddrive into my laptops usb-port).

Pleeeease anybody who reads this help a noob out and tell me how to repair the damage unetbootin has done to my system!

Durin01

P.s: If a German reads this and replys to me, plz write in german since I am german.

---

### Post by Durin01 on 2012-02-23
Nothing? Not even a "Sucks to be you" , "Maybe you should look there and there..." or "This post is in the wrong Sub-Forum" or anything?

---

### Post by Durin01 on 2012-02-24
ok if nobody can help me removing Unetbootin perhaps somebody can answer me this:

What is to be expected when i install Ubuntu again (not formating first)?

Is the System afterwards mint?
Do the previous installed programs still work (Java, Javascript, Wine...)?
Or is the System buggy and corrupted?

And will it remove the Unetbootin bug i have?


Please somebody, ANYBODY answer me, I am at wits end here!

---

### Post by mastablasta on 2012-02-24
you can restore grub.

---

### Post by HeroOfCanton on 2012-02-24
As mastablasta said try to recover grub: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you install without formatting things could be very buggy. If recovery doesn't work then it may be worth a shot, but recovering GRUB (or just booting to a live cd and doing a proper backup and reinstall) would be better.

---

### Post by Durin01 on 2012-02-24
Thanks your link to the Post helped. Boot-Repair did its magic and i got my system back.

Really thanks a lot you two.

---

### Post by HeroOfCanton on 2012-02-24
> **Durin01 said:**
> Thanks your link to the Post helped. Boot-Repair did its magic and i got my system back.

Really thanks a lot you two.

Sweet! Glad we could help. Be sure to mark the thread solved in Thread Tools.

---

