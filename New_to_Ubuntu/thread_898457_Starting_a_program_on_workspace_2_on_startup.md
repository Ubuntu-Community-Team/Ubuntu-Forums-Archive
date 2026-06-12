---
title: "Starting a program on workspace 2 on startup"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by panther_sn on 2008-08-23
Hi all I was wondering if it is possible to get 1 particular program I have in my sessions settings to start on workspace 2 whilst having the rest start on workspace 1 (default workspace). I belive this would be useful for programs like [Elisa]("http://elisa.fluendo.com/") (great media program by the way try it if you haven't already)

Any help appreciated. Thanks Stu

---

### Post by braddcadd on 2008-08-24
Take a look at this link:
[http://ubuntuforums.org/showthread.php?t=685528&page=2](http://ubuntuforums.org/showthread.php?t=685528&page=2)

I moved Geany (a coding app) to workspace 2 like this:
```

wmctrl -r "Geany" -t1

```

---

### Post by mael on 2010-10-04
Thank you braddcadd!

---

