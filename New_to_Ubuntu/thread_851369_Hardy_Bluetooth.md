---
title: "Hardy Bluetooth"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by darkworld on 2008-07-06
From another thread I see Hardy Bluez-utils is bust. Ive seen Blueman suggested and ive tried but still the same problem, also bluetooth file sharing app is bust.

Has anybody got a fix that will allow me to up load pics to pc from phone? I can transfer PC to phone but not phone to PC.

---

### Post by Troll_the_Great on 2008-07-06
Turn on bluetooth from both phone and PC, right click on the "Bluetooth Manager" icon from the panel and choose "browse device".It worked for me.Hope this helps.
Cheers!

---

### Post by darkworld on 2008-07-06
Im running blueman now because other peeps are say bluez-utils 3.26 is bust and no fix. Its bust on my machine too.

Blueman fires up fine and connect both ways but will not allow file from phone, it seems to drop the connection when I try to transfer.

---

### Post by Troll_the_Great on 2008-07-06
I have blues-utils and I have the same problem, but I managed to get around it by doing what I suggested in the previous post.Give it a try, I hope it will work for you too.When you click "browse device" your phone will show up on the desktop and you can explore it.
Cheers!

---

### Post by darkworld on 2008-07-06
yes you are right, phone appears on desktop and browse opens a window which is completely empty and I cant browse my nokia N70. No paths just empty window.

Am I being a noob??? I just dont see what im missing? sorry.

---

### Post by Troll_the_Great on 2008-07-06
:( I don't know what to say...Mine is working this way, I have a Nokia N 93.Sorry, I can't offer another solution.Hope you will find something useful and get your bluetooth to work.
Cheers!

---

### Post by darkworld on 2008-07-07
Ok can anybody tell me if they have a nokia N70 that will send via bluetooth to Hardy desktop?

---

### Post by darkworld on 2008-07-07
Ok its a bug!

Found in launchpad and they have a patch. This is the link to patch. How do I apply it???

> [http://bluez.cvs.sourceforge.net/bluez/utils/sdpd/request.c?r1=1.22&r2=1.23&view=patch](http://bluez.cvs.sourceforge.net/bluez/utils/sdpd/request.c?r1=1.22&r2=1.23&view=patch)

---

