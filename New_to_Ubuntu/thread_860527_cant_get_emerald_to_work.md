---
title: "cant get emerald to work"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-07-15
i have emerald theme manager installed but im not sure how to use it.i have themes installed throught it but when i chick on them they wont start. i do have compiz fusion installed and am currently using a theme from the ubuntu theme manager but i dont think this matters. thanks in advanced for all help given!

---

### Post by mevets on 2008-07-15
You should run:
```

emerald --replace

```

---

### Post by ibuclaw on 2008-07-15
In your CompizConfig Settings Manager, scroll down to "**Window Decoration**" in the "Effects" section, and click on it.

You'll see a text box with the title "Command".

Change the text box to say this:
```
emerald --replace
```
Then close the app, press **Alt+F2** and run the following command:
```
compiz --replace &
```

Regards
Iain

---

