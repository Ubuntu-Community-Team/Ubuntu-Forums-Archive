---
title: "Add clock to top bar?"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by noahsdev on 2013-10-31
I updated to saucy salamander and the clock is disabled by default. In the menu where you can enable it all of the options are whited out. Any way around it? I tried running settings as root but the menu is not there. Aha what can I do?
Thanks.

---

### Post by noahsdev on 2013-10-31
Solved it. If anyone else comes across this thread who just upgraded to 13.10 just run this command:
```
killall unity-panel-serivce
```
Basically just restarting the unity top panel. It worked for me, apparently it only happens after first boot. :)

---

### Post by mörgæs on 2013-10-31
Good, please mark the thread 'solved' using 'thread tools'.

---

