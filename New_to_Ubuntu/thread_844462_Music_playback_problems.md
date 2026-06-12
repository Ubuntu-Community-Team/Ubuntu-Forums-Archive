---
title: "Music playback problems"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Tachions on 2008-06-29
Hey guys, I have been having some recent problems with music playback on my Ubuntu box, sometimes when I start to listen to a track on Amarok it freezes up and I need to force quit with no audio playback at all, but then there is times where it will work flawlessly and then I pause/stop and leave my computer for a while and come back and try to play and it freezes again immediately...

Any ideas? thanks for your help...

---

### Post by sayakb on 2008-06-29
I don't use Amarok, but afaik, it is related to the database you use. If you are using SQLite, switch to MySQL.

---

### Post by Tachions on 2008-06-29
hey Linux is Innovation, thanks for the input, how would I change my database, and why would I want to do that? thanks again

---

### Post by Tachions on 2008-07-14
bump

---

### Post by Demon012 on 2008-07-14
> **Tachions said:**
> hey Linux is Innovation, thanks for the input, how would I change my database, and why would I want to do that? thanks again

Go into AmaroK and then Click Settings at the top of the window. Then from the menu select Configure Amarok then down the left click Collection.

Now you will see a section in the window called collection database. Select SQLite or Mysql from there.

However I do not think this will help with your lockup issue maybe you should try run Amarok from the terminal using

```
amarokapp > amaroklog.txt
```

And keep the terminal window open while using amarok for the day and see if the problem reoccurs while you are logging its output. Then hopefully we shall see the error in the log and be able to help further.

---

