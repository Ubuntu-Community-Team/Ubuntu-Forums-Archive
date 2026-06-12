---
title: "can't install plugins"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-26
When I try to install pugins I get the message
E:dpkg was interrupted, you must manually run ' dpkg -- configure -a' to correct the problem.
e: cache->open()failed, please report.

I dont know how to either manually run dpkg or report.

---

### Post by sayakb on 2008-04-26
Which plugins are you installing? Try using apt-get.
```
sudo apt-get install packagename
```

---

### Post by saskatchewan on 2008-04-26
I am trying to install flashplayer and a couple of others

---

### Post by billgoldberg on 2008-04-26
> **saskatchewan said:**
> When I try to install pugins I get the message
E:dpkg was interrupted, you must manually run ' dpkg -- configure -a' to correct the problem.
e: cache->open()failed, please report.

I dont know how to either manually run dpkg or report.

open a terminal and enter this

```
sudo dpkg -- configure -a
```

(the error message tells you what to do to fix it)

---

### Post by saskatchewan on 2008-04-26
How do I open a terminal?

---

### Post by SunnyRabbiera on 2008-04-26
its in applications under "accessories"

---

### Post by saskatchewan on 2008-04-26
okay, I have that open

---

### Post by OisinT on 2008-04-26
> **saskatchewan said:**
> okay, I have that open
enter

```
sudo dpkg -- configure -a
```

often the error will tell you what you need to do.

---

### Post by saskatchewan on 2008-04-26
I have a terminal open but I am not sure what to do now.. I have tried entering sudo apt-get install packagename but am still confused...

---

### Post by sdowney717 on 2008-04-26
just type into the terminal screen

dpkg -- configure -a

and hit enter.

---

### Post by saskatchewan on 2008-04-26
i type install and then the deb file name but can not seem to get it right

---

### Post by saskatchewan on 2008-04-26
I tried that and it seems to suggest using the help command.
But I am still a bit clueless of what to enter to, for example, get my skype-debian file to enter

---

### Post by saskatchewan on 2008-04-26
I am not sure what to enter after I type install.
-i|--install       <.deb file name> ... | -R|--recursive <directory> ...

I seem to keep getting the deb file name etc incorrect.

---

