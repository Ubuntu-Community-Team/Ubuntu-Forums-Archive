---
title: "remove software completely"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by hnf a on 2012-09-25
i want to remove my game completely from my computer and reinstall it but when i remove it from the software and reinstall it the software center just download 3 mb of it but the game size is around 30 mb i've try sudo apt-get purge packagename and its still in there ,btw my game is openbve crash when opening map can anybody fix the openbve or remove it completely i will apreciate it

---

### Post by GreatDanton on 2012-09-25
After purging you can try:
```
sudo apt-get autoremove
```
This will remove all things that are no longer necessary.

Hope this helps.

Regards.

---

### Post by hnf a on 2012-09-25
what do you mean "all things" should i add openbve in the last line or just paste it in the terminal?

---

### Post by GreatDanton on 2012-09-25
All things= unnecessary things that you no longer need. 

After purging, software sometimes leaves some things, but since you purge the software, those things are no longer needed. I assume this happened in your case.

After you have purged your software, just copy and paste that command in terminal.
Unfortunately I don't know anything about openbve, so you will have to wait for some expert =).
Regards.

---

### Post by hnf a on 2012-09-25
ok thanks for the advice now i download full size

---

### Post by GreatDanton on 2012-09-25
I am glad it worked.

If you think your problem is solved, then please mark thread as solved, so it will help others which maybe has similar problems like you. To mark thread as solved click on thread tools/ Mark thread as solved.

Regards.

---

