---
title: "RCXTerm - a wrapper over XTerm that makes it change colors"
date: 2011-05-11
forum: Programming Talk
---

### Post by yanom on 2011-05-11
Here is a short Python program I wrote. To run it, copy the source code below into a file, name it rcxterm, and make it executable ($   **chmod +x rcxterm**    works for this), and run it. You can edit the second and third lines of text to change the available colors and the font size.

```

#!/usr/bin/python


available_colors = ["magenta","yellow", "white", "green", "cyan", "orange", "purple"]
fontsize = 20

import random
import os

color = random.choice(available_colors)
font = "-*-courier 10 pitch-*-r-*-*-" + str(fontsize) + "-*-*-*-*-*-*-*"

command = 'xterm -font \"' + font + '\" -bg black' + ' -fg ' + color

os.system(command)


```

It's called RCXTerm, short for Random Colored X Terminal. It arose out of my inability to choose a text color for my terminal. I then wrote this to randomly choose a color for me each time I open it.

---

### Post by yanom on 2011-05-11
bump

---

