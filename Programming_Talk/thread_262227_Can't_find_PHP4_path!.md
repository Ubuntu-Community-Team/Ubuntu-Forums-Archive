---
title: "Can't find PHP4 path!"
date: 2006-09-21
forum: Programming Talk
---

### Post by dudinatrix on 2006-09-21
I've been trying to find the path to PHP(4) for practically half an hour now. I can't seem to find it! It's running fine on my system, but I set up Trac and want to point it to the php path for its mimeviewer. I looked everywhere, does anyone know how to find the php path and/or where it is by default?

---

### Post by dudinatrix on 2006-09-21
Found the problem. There *was* no path to it! I had to do install php4-cli (the command-line interface), which wasn't included with the initial php4 package. I now have /usr/bin/php and /usr/bin/php4

:)

Hope this may help somebody else..

---

### Post by X.Cyclop on 2006-09-21
```
sudo updatedb
locate php4
```

;)

---

### Post by jemmrich on 2007-04-14
> **dudinatrix said:**
> Found the problem. There *was* no path to it! I had to do install php4-cli (the command-line interface), which wasn't included with the initial php4 package. I now have /usr/bin/php and /usr/bin/php4

:)

Hope this may help somebody else..

Wow, thanks dudinatrix, after exactly 5 hours of trying to figure out why i didnt seem to have the php4 binary even though i did an apt-get install php4 it is finally working!

now if only i could get that 5 hours back and use it for productive work rather than fighting php the entire time :/

---

### Post by jimmal on 2009-01-25
thx helped me too

---

