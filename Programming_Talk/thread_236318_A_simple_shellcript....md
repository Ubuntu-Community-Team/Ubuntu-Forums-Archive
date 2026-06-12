---
title: "A simple shellcript..."
date: 2006-08-14
forum: Programming Talk
---

### Post by StalfoS on 2006-08-14
Can someone please write me a shellcript that kills a given process after a given number of minutes?

eg.

>> ./timedKill amarok 30
 "amarok" will exit in 30 minuits...

I'm sure that it would require only a few lines, but I am not very familier with bash syntax.

I want to use it as a sleep timer for a music player.

Cheers.

---

### Post by string on 2006-08-14
```

echo $1 will quit in $2 minutes
sleep $(($2 * 60))
pkill -9 $1

```

That should do the trick.

---

