---
title: "How to show PHP errors, local server"
date: 2011-11-03
forum: Programming Talk
---

### Post by Mezzoforte on 2011-11-03
I've just started up doing some PHP/MySQL coding. I've got local Apache and MySQL servers.

A bit of a problem when trying to run some new code is that if it's not correct, my browser will just spit out a "Server error" ("HTTP Error 500 (Internal Server Error)") page that doesn't really me what's wrong.

Could anybody give me a hint as to how I can see more detailed errors? Since my servers are local there is probably some setting I can change somewhere, but I'm pretty new to this and would prefer not dabbling around too much on my own at this stage.

---

### Post by Lars Noodén on 2011-11-03
Open up a terminal and then use [tail](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tail.1posix.html) to track the error log:

```

tail -f /var/log/apache2/error.log

```

---

### Post by Mezzoforte on 2011-11-03
Thanks, exactly what I needed!

---

### Post by DarkAmbient on 2011-11-04
First thing that came to my mind was:
```
error_reporting(E_ALL);
```

For what it's worth, I recall that would be sufficient for showing errors directly on the page. Guess you shouldn't use it on a live-server though. ;)

---

