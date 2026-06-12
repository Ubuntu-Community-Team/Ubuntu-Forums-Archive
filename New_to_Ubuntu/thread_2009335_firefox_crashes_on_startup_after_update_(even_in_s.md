---
title: "firefox crashes on startup after update (even in safemode)"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by upjeeper on 2012-06-24
i did a mass update the other day, no firefox crashes immediately when i open the program. i've even tried to open in safemode (firefox -safe-mode) and it still crashes.

any ideas?
please and thank you

---

### Post by Enigmapond on 2012-06-24
Try opening in the terminal and post any errors that may occur..
```
like this
```

---

### Post by upjeeper on 2012-06-24
> **Enigmapond said:**
> Try opening in the terminal and post any errors that may occur..
```
like this
```

thanks, i've run "firefox" from a terminal, and immediately it comes up with a GUI style "mozilla crash reporter"
it says "we're sorry, firefox had a problem and crashed. we'll try to restore your tabs and windows when it restarts"
there is a "details" option, but it appears to be nothing helpful, includes the following
- buildid
- crashtime
- installtime
- product id
- version

the terminal doesn't show anything other than my command to run firefox

---

### Post by Enigmapond on 2012-06-24
Then try un-installing it and re-installing from the terminal.

```
sudo apt-get purge firefox && sudo apt-get install firefox
```

---

### Post by upjeeper on 2012-06-24
that did it. thank you enigmapond!

---

### Post by Enigmapond on 2012-06-24
YAY! Glad I could help.
Cheers!

---

