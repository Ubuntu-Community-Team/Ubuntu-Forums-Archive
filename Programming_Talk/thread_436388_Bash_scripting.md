---
title: "Bash scripting"
date: 2007-05-07
forum: Programming Talk
---

### Post by Matthaeus on 2007-05-07
Hi, i have a reasonable knowledge of AHK (auto hot key) for windows, but i can't use these now that im on ubuntu (3rd day) - so at the moment i am making a couple of quick basic scripts.

What command should be used too: open a terminal and run a sh script or a command in that terminal - and also continue on to the next line in the first terminal (while the newly created terminal remains active)?

I've tried gnome-terminal -e "wine "game"" or gnome-terminal -e "sh ....script.sh" and a heap of other ways of writing it but nothing seems to work.

I'm guessing theres no way to implement a timer into a .sh file full of bash commands?

Thanks, Matt.

---

### Post by WW on 2007-05-07
I'm not sure why you would want to run programs this way, but try this script:

**termrun.sh**
```

#
# termrun.sh -- run a bunch of programs in separate terminals.
#
gnome-terminal -e top &
gnome-terminal -e "man bash" &
gnome-terminal -e "nano nothing.txt" &

```
Call it termrun.sh, and then run this in the directory where you saved termrun.sh:
```

$ sh termrun.sh

```

---

### Post by Matthaeus on 2007-05-09
Thank you, That did what i wanted....i needed to run a couple of scripts simultaneously and one in a terminal so i can see its output....it also gives me another way of closing it if it crashes.

Thanks, Matt.

---

