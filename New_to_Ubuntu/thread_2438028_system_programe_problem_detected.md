---
title: "system programe problem detected"
date: 2020-03-04
forum: New to Ubuntu
---

### Post by hogdigerdy on 2020-03-04
pretty much as above, about 30-45 seconds after i start my pc i get an pop-up which says 

'system program problem detected

do you want to report now

cancel         report problem'

i normally click the report option but nothing seems to happen, if anyone can point me in the right direction, it would be much appreciated.

---

### Post by CatKiller on 2020-03-04
/var/crash is where the crash reports are stored. You can see which particular component is being problematic from that.

There is sometimes a glitch where the report gets generated and prompts you to upload it, but never takes note of the fact that it's done so. So the next time you turn your computer on it notices there's a crash report, doesn't know that it's already asked you, so it asks you if you want to upload it. Simply deleting the crash report stops that happening.

---

