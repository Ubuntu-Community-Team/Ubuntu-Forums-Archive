---
title: "How Do I remove the mail sign from the top?"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by SidNoob on 2012-05-19
I've removed Thunderbird as it was heavily lagging.Can someone help me to remove the mail symbol from the top right? Yep I'm new to Ubuntu :KS
Thanks in advance.

---

### Post by zombifier25 on 2012-05-19
Put this into the terminal:
```
sudo apt-get remove indicator-messages
```

---

### Post by SidNoob on 2012-05-19
Done.Still it persists.Maybe requires a boot? :) neways thanks!

---

### Post by zombifier25 on 2012-05-19
After doing so, log out and log in.

---

### Post by SidNoob on 2012-05-19
Thank You very much it worked! :)

---

### Post by woxuxow on 2012-05-19
In addition any stuff that is located at top of gnome is an indicator and by searching in indicator word you can find it to remove or install

---

### Post by SidNoob on 2012-05-19
Oh! Thanks for that piece of information.BTW is it possible to move the launchpad to the bottom of the screen? It'd be great!

---

### Post by woxuxow on 2012-05-19
> **SidNoob said:**
> Oh! Thanks for that piece of information.BTW is it possible to move the launchpad to the bottom of the screen? It'd be great!

I don`t think so

---

