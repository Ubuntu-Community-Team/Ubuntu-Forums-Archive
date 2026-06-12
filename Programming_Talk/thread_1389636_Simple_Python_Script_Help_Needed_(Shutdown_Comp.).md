---
title: "Simple Python Script Help Needed (Shutdown Comp.)"
date: 2010-01-24
forum: Programming Talk
---

### Post by Eremis on 2010-01-24
Hi everybody!

I am  new to python, and I am trying to figure out how would I make a script that would shutdown my computer after X seconds...
For example when I am downloading something that takes about 2 hours, I could set the script to shutdown PC after 3 hours, and leave home...

So far this is what I have:

```

#!/usr/bin/python
import os
import time

time.sleep(3600)                        # after 1 hour shutdown computer
os.system("sudo shutdown now -h -k")    # shutdown command

```

My problem is that ubuntu needs a password to do such tasks, so after 1 hour it will ask me for one (the point being I will not be home to type it...) If I leave out the "sudo" it just gives me an error saying that I dont have permission..  :confused:

Is there a way to become admin, then start the timer, then shut-down (with admin privileges...)? Or is there any other way to acomplish this?


Thanks for the help...

---

### Post by Senesence on 2010-01-24
I think you need to run the python program with root privileges.

---

### Post by Can+~ on 2010-01-24
The shutdown command has a [TIME parameter]("http://www.dsl.org/cookbook/cookbook_41.html#SEC566"), so you don't even need a script, check the manpages.

```
NAME
       shutdown - bring the system down

SYNOPSIS
       shutdown [OPTION]...  TIME [MESSAGE]
```

And I think you can run as root indefenitely (aside from su) doing [FONT="Courier New"]sudo -s command[/FONT]. Although, I'm not sure about this.

---

### Post by jpkotta on 2010-01-24
If you use KDM, you don't need root privileges.  
```
kdmctl shutdown halt trynow
```
You can use KDM without using KDE.

Edit: It appears that the GDM equivalent is gdm-signal, in the powermanagement-interface package.  I have not tested it.

---

### Post by wmcbrine on 2010-01-25
Yes, that "now" in the shutdown command actually means something -- just change it to the time you want.

But also, even if you were going to script it, this is one of those tasks where bash would make more sense than Python.

While you're looking at man pages, check out the "at" command.

---

