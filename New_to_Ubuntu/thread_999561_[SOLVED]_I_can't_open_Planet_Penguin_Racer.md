---
title: "[SOLVED] I can't open Planet Penguin Racer"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-02
I turned all the max settings on Planet Penguin Racer on my Dell mini 9. and now it wont open anymore.

I even used the Add/Remove app. removed it and reinstalled it, restarted and still no go.

anyone have a solution to get it running again?

---

### Post by wilbbe01 on 2008-12-02
I am not sure on where it stores its settings.  You might try firing up a terminal and running a

```
ls -lha
```

look and see if there are any directories resembling something to do with the game, such as .ppracer or something (no idea what it might be called).  mv that to something else and try running the game.

```
mv nameofdirectory nameofdirectory_backup
```

---

### Post by shiningkenmonster on 2008-12-02
ah thanks it works now.

but i am not sure if the sound sounds a little too slow than usually. I even turned up the volume on mine. 

maybe i'll run it on a quiet environment.

---

### Post by shiningkenmonster on 2008-12-08
hey, the game works great.

but the problem is that I start on level 3 (which is the level I was on before I did all the commands above.) , I cant access level 1 and 2. When I beat level 3, it doesn't save the levels that i've beated. So I have to   endurer starting at level 3 each time when i start the game.

is there a solution to fix this?

---

