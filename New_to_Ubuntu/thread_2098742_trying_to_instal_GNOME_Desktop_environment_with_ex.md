---
title: "trying to instal GNOME Desktop environment with extra components getting not found"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by howhy on 2012-12-27
trying to instal GNOME Desktop environment with extra components getting not found message ... what did i do wrong few minutes back it was their but now it is not it does shows 59 in brackets...

how do i get GNOME desktop environment?

---

### Post by superDave972 on 2012-12-27
you can install gnome very easily by searching for it in the Software Center

---

### Post by howhy on 2012-12-27
yes i know thats exactly where i am getting this message.

---

### Post by audiomick on 2012-12-27
Most likely, I think, is an internet problem. Either your connection messing around or the server where the packages are experiencing difficulty (or something in between).

I don't know what the 59 in brackets means, but perhaps if you just try again in an hour or so it might be there again.

Incidentally, the occasional full stop and capital letter would make your post much easier to read, and make life easier for the people who might be willing to try and help you. ;)

---

### Post by howhy on 2012-12-27
i tried it again in the search now i cant even get Gnomoe in the list that says desktop enironment with extra components .

---

### Post by Cheesemill on 2012-12-27
Can you copy the following into a terminal one at a time and post back the results (please put the results in [noparse]```
 
```[/noparse] tags to make it easier to read).
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gnome-shell
```

---

### Post by howhy on 2012-12-27
> **Cheesemill said:**
> Can you copy the following into a terminal one at a time and post back the results (please put the results in [noparse]```
 
```[/noparse] tags to make it easier to read).
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gnome-shell
```
yes you are right sudo apt-get update is the answer

---

