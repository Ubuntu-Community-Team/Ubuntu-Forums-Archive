---
title: "Clear in Python"
date: 2011-12-05
forum: Programming Talk
---

### Post by didinium on 2011-12-05
Hello everyone. I'm somewhat new to python and want to create an ASCII animation, how would I do a clear in the code itself to create frames. Thanks in advance, Jonah Lubin.

---

### Post by cgroza on 2011-12-05
You cold print a bunch of lines or you could look into a more advanced library such as ncurses.

---

### Post by didinium on 2011-12-05
Though with an ASCII movie there is already so many lies of code it would be more streamlined if i just used a single line clear command.

---

### Post by DangerOnTheRanger on 2011-12-06
ncurses is probably what you're looking for.

---

### Post by Bodsda on 2011-12-06
or you could use the os module to run the clear command, ncurses is better but this still works

```

import os
os.system('clear')

```

---

### Post by didinium on 2011-12-06
Ya I'm kinda new to python so NCurses is a bit out of my reach but the os clear looks good

---

