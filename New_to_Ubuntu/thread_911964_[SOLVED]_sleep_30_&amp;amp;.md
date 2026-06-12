---
title: "[SOLVED] sleep 30 &amp;amp;"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Bölvaður on 2008-09-06
I was fiddling with conky and discovered that sleep doesn't work as I am using it.
```

$ cat /home/gummi/conky/startconky
#!/bin/bash
sleep 30 &
conky -c ~/conky/conkymain &
#sleep 1 &
#conky -c ~/.conkyscripts/conkyb &
```


I even tried sleep 1000, but it starts up instantly.

What I am trying to gain from this is to start up conky as the last program, so it will not be drawn over by (probably) nautilus (probably not gnome).

---

### Post by Lusse on 2008-09-06
Maybe this:

```
sleep 30
conky -c ~/conky/conkymain
```

would do it. You don't need to use & at the end of each line. BTW. sleep 30 makes it sleep for a half minute, is that what you want?

//Linus

---

### Post by freak42 on 2008-09-06
sleep 30 &
will make the sleep program spawn in a new separate thread, meaning the main program (your script) will continue while sleep sleeps somewhere else, that is probably not what you want.. if you ommit the & your script should sleep for the intended timespan.

---

### Post by Bölvaður on 2008-09-06
> **Lusse said:**
> Maybe this:

```
sleep 30
conky -c ~/conky/conkymain
```

would do it. You don't need to use & at the end of each line. BTW. sleep 30 makes it sleep for a half minute, is that what you want?

//Linus

hmm you are true, I dont need &, I should stop mindlessly follow tutorials.

But I might be correct on the integer being seconds but not minutes, I have it on 20 now.

Thank you very much for answering, both of you that is.

---

### Post by bhadotia on 2008-09-06
I use sleep like this :
```
(sleep 3; conky &) &
```
and that works for me without problem.

---

