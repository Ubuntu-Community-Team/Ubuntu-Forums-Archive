---
title: "LiveCD"
date: 2015-11-16
forum: New to Ubuntu
---

### Post by Kikikikikik on 2015-11-16
I would like to create a Live CD with no terminal access for regular users and which has basic functions like: Browser, Media player and text editor. What would be the easiest way to create one?

---

### Post by mastablasta on 2015-11-16
do you mean Kiosk mode? like webconverger has?

---

### Post by Kikikikikik on 2015-11-16
Yes something like Webconverger Kiosk mode but with media player, DigiDoc digital signature support(recommended).

Chromixium would be ideal for me but is it possible to disable terminal there?

---

### Post by mastablasta on 2015-11-16
I bet you can disable it anywhere. just do not give permission to user to access it/run it. maybe even remove it, prevent switching to console and you are done. they can't install anything without sudo anyway. so if you want Ubuntu I would build from minimal install iso, add what you need, remove what you don't and block some things for normal users. then create a live CD from it (there is a new program to do that, I forgot what it's called but there was a thread about it here on forums).

although usually live CD has root access... hmm.

---

### Post by Bucky Ball on 2015-11-16
> **mastablasta said:**
> I bet you can disable it anywhere. just do not give permission to user to access it/run it. maybe even remove it, prevent switching to console and you are done. they can't install anything without sudo anyway. so if you want Ubuntu I would build from minimal install iso, add what you need, remove what you don't and block some things for normal users.

+1 to this.

> **mastablasta said:**
> ... then create a live CD from it (there is a new program to do that, I forgot what it's called but there was a thread about it here on forums).


... and this. Where's that thread? I'll have a look. :)

PS: Just a thought while I'm having one. I skip tasksel when doing the minimal install as I don't want a default machine profile. I wonder if there is a Kiosk machine profile there as there are a lot to choose from ... :-k

---

