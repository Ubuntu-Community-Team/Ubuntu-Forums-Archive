---
title: "Is Ctrl+Alt+Backspace the same as &quot;Log out&quot;?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by hanzj on 2008-05-09
Is Ctrl+Alt+Backspace the same as "Log out"? Or is  Ctrl+Alt+Backspace just for restarting x server?

---

### Post by inportb on 2008-05-09
Neither. It stops the X server.
Something else (Upstart?) starts the X server again when it goes down.

---

### Post by nowshining on 2008-05-09
wrongm corrent answer.. Yes it's the same as logging out and re-starting the x-server and reloading the xorg.conf file.

To logout - ctrl + alt + backspace

To re-start the xorg server and and re-load the xorg.conf file - usually a logout will do however sometimes while in the login screen u'll need to use those key combos.

to stop  - start the login screen - ctrl alt + f1-f6

sudo /etc/init.d/gdm (use kdm if using kde or gdm if using ubuntu - u can use gdm in kde tho) stop - to stop the gdm server

sudo /etc/init.d/gdm start - to start the gdm server

sudo /etc/init.d/gdm restart - to restart the gdm server

all items in /etc/init.d/ are services and all use the start, stop and restart commands. :)

also u don't need the gdm/kdm servers running, u can remove them and login via the CLI and to start X use the command startx.

---

### Post by hanzj on 2008-05-09
I don't understand the first 2 "words" of your post.

---

### Post by Anduu on 2008-05-09
It is not the same as logging out...your session will not be saved if you do this.

---

### Post by Dr Small on 2008-05-09
> **hanzj said:**
> I don't understand the first 2 "words" of your post.
I was stuck on that for about 30 seconds myself. I still haven't figured it out :D

---

### Post by Zralou on 2008-05-09
> **Dr Small said:**
> I was stuck on that for about 30 seconds myself. I still haven't figured it out :D

Two statements: "wrong" and "correct answer"

Sara Lou

---

### Post by nowshining on 2008-05-10
yeah sorry - miss-spelled - it was late and I was a bit tired. :D

---

