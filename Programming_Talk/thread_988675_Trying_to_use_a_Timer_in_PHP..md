---
title: "Trying to use a Timer in PHP."
date: 2008-11-20
forum: Programming Talk
---

### Post by niccholaspage on 2008-11-20
I am making a bot to go around a online game. I need my bot to move every 5 seconds.
Anyone know a way to make a timer like this in PHP?

---

### Post by Phristen on 2008-11-20
while (1) {
...

sleep(5);
}

?
:)


You can also cron it, I suppose...

---

### Post by niccholaspage on 2008-11-20
Thanks so much!

---

