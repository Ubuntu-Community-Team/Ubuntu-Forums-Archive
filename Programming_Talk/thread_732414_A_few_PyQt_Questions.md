---
title: "A few PyQt Questions"
date: 2008-03-22
forum: Programming Talk
---

### Post by xelapond on 2008-03-22
Hello everyone, 

I am learning how to write GUI application with PyQt, so for a practice(and kinda useful) I am writing a GUI VNC Server Controller.  So, I have two questions regarding PyQt.  I searched the documentation, but I couldn't find anything quite like what I am trying to do.  So, 

Is there a way to make it run a command on program exit?  Also, is there a way to make the window not show up in the Task Manager?  Finally, is there a way to make it stay on the bottom?

Thanks,

Alex

---

### Post by skullmunky on 2008-05-29
to run another program at the end of your program, you could do this:

```

import os

# at the end ...
os.system('otherprogram')

```

you could also wrap your python script in a bash script and put the other program after it so it executes after the python script is done.

If by "on the bottom" you mean "underneath other windows," in KDE anyway you can just set that as a window property for that application...

---

