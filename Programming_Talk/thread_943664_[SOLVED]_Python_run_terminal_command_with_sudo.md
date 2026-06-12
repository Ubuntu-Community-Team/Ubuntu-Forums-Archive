---
title: "[SOLVED] Python run terminal command with sudo"
date: 2008-10-10
forum: Programming Talk
---

### Post by MaxVK on 2008-10-10
Hi there.

I am *very* new to Python, so new in fact that this is the first thing I have considered doing with it, so be gentle! Anyway:

I would like to write a script that, when executed, would be able to open a terminal window for me to type my password. I want to be able to create a desktop launcher that will point to the correct script (python <script name>)

I need to run the following command:
sudo /home/checkit/fellowsbook

Of course I can do this:
```
import os
os.system("sudo /home/checkit/fellowsbook")
```

but no terminal window opens, so I cant type my password and the script does nothing.

Is there a way around this?

Many thanks

Max

---

### Post by geirha on 2008-10-10
Try with gksudo instead of sudo, it will pop up a graphical password dialog.

---

### Post by LaRoza on 2008-10-10
You are better off running the script with sudo.

---

### Post by MaxVK on 2008-10-10
Thanks for the replies:

geirha:
Surely gksudo is for graphical apps, and this one would normally be started from a terminal with sudo. Is it okay to use gksudo like that? I always thought that sudo and gksudo should be used in different circumstances.

LaRoza:
Do you mean that I should include sudo in the launcher command? Remembering that I want to run this script from an icon on the desktop.

regards

Max

---

### Post by lykwydchykyn on 2008-10-10
```

import os
os.popen("sudo -S somecommand", 'w').write("mypassword")

```

That'd obviate the need for asking a password, but it's not secure.  I just re-read your post, you want a terminal to pop up here.  So why not:

```

os.system("xterm -c \"sudo /home/checkit/fellowsbook\"")

```

---

### Post by Rich78 on 2008-10-10
As Laroza said use sudo for the launcher command.

This will prompt for the password prior to running the script, once the password has entered, the content of the script will run under sudo.

---

### Post by unutbu on 2008-10-10
If this is your python script:
```

#!/usr/bin/env python
import os
os.system("/home/checkit/fellowsbook")
```
Then make the launcher command
```

gksu python_script.py

```
If you use sudo, the launcher will not open a terminal for you to ask for your password, so you have to use gksu.

---

### Post by themusicwave on 2008-10-10
It is also nice to check if the user is root when your script first starts to run.  If they aren't tell them to run it as root and exit.  Like so:

[PHP]import os, sys

# if not root...kick out
if not os.geteuid()==0:
    sys.exit("\nYou must be root to run this application, please    use sudo and try again.\n")
[/PHP]

Please note the getuid function only works on Unix.  I tried running that snippet on my Windows machine at work and it failed.  Then I read the docs...

---

### Post by MaxVK on 2008-10-11
Aha! This is great, many thanks to you all - I now have the answer to another question (check to see if user is root) as well as the original!

Many thanks - Ill get onto this as soon as I'm not working! ;)

Regards

Max

---

