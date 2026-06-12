---
title: "How do I run partial code from a new terminal?"
date: 2007-01-18
forum: Programming Talk
---

### Post by kapetanski on 2007-01-18
I'm not used with shell scripting... The thing I want to do is really simple, just start gxine and then change the contrast value, something like this;
```
#!/usr/bin/bash
# Name: movie.sh 

gxine &

xvattr -a XV_CONTRAST -v 64
```

The reason I want to do this is due to a bug with the intel 855gm graphics card, the value changes from 64 to 128 for som reason when gxine or totems is started. 
The problem with script is that the xvattr command runs before gxine changes the value to 128. So, maybe a pause command or something is suitable, or a new terminal with the other command.

---

### Post by -Rick- on 2007-01-18
How about this?

```

#!/bin/sh
# Name: movie.sh 

gxine &

[color="red"]sleep 5[/color]

xvattr -a XV_CONTRAST -v 64

```

---

### Post by kapetanski on 2007-01-18
works great! thanx ;)

---

