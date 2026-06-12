---
title: "Hamster Time Tracker - Where is it saved?"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by Houmie on 2012-07-03
Hi,

I need to reinstall Ubuntu, and need to make sure my Hamster saves are not lost.  Any idea where it is stored?

Many Thanks,

---

### Post by llamabr on 2012-07-03
What's hamster?  This one?

```
brock@vader:~/Desktop$ apt-cache search hamster
hamster-applet - time tracking applet for GNOME
brock@vader:~/Desktop$ 
```

What's a time tracking applet do?  

Anyway, I don't know.  Try looking in ~/.hamster or some variant.

---

### Post by blueshead on 2012-07-03
Open your Home folder, press 'control + h' to show hidden files. Open .local > share, copy the 'hamster-applet' folder and paste it in the .local/share/ folder on your other computer.

---

### Post by Houmie on 2012-07-05
yeah thats it. Thanks :)

---

