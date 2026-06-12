---
title: "awn gone"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by westentertainer on 2008-06-03
hello i managed to get awn working with the dock on screen but when i loged on again it was gone   how can i get it back  where is it installed thanks

---

### Post by useResa on 2008-06-03
Are you sure Compiz is running? AWN requires Compiz to be working properly otherwise it will not show.

Furthermore you could also check out [this thread]("http://ubuntuforums.org/showthread.php?t=762363"), it has quite a lot of information and support.

---

### Post by westentertainer on 2008-06-03
yes compiz is working ive got wobbly folders  flame folders etc  i have found the awn manager but it still wont activate

---

### Post by billgoldberg on 2008-06-03
It should be under "applications -> accessories".

If you want want awn to start at boot up, go to "system - >  preferences - > sessions"

add a new entry, fill this in

- awn
- avant-window-navigator
- dock

---

### Post by useResa on 2008-06-04
> **westentertainer said:**
> yes compiz is working ive got wobbly folders  flame folders etc  i have found the awn manager but it still wont activateHave you tried activating awn from a terminal? This may provide additional information on why it will not start.

You can do this by opening a terminal and issue the command
```
avant-window-navigator
```

---

### Post by westentertainer on 2008-06-04
all ok now many thanks once again

---

### Post by gvartser on 2008-06-04
You may want to check out "cairo-dock". I also used to run "AWN" but changed it into cairo-dock instead after testing it out.

For me it has been running stable and i like the effects and functions much more in cairo-dock then in awn.

Ubuntu Link: 
- [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

Download Link:
- [https://developer.berlios.de/projects/cairo-dock/](https://developer.berlios.de/projects/cairo-dock/)

/g

---

