---
title: "Bash scripting and keyboard shortcuts"
date: 2012-09-17
forum: Programming Talk
---

### Post by Thrashrokz33 on 2012-09-17
Update: Solved. It was as easy as using Gnome-terminal -e /pathtofile as the shortcut command.

I'm trying to ssh into a server with a bash script so I don't have to type "ssh -l user server" into gnome-terminal every time.

My script works on it's own:

```

#!/bin/bash
ssh -l myusername theserver.edu
```

And I'm trying to set a keyboard shortcut, so that I can just hit ctrl+alt+[ and have it open gnome-terminal, and run that script.

I've tried, as a shortcut command:

gnome-terminal && /pathtofile/myscript.sh

and it just opens a blank terminal. Which command should I run so that it opens a blank terminal, and then inside that terminal window, it runs my ssh connect command?

And the reason I can't just make the shortcut to the bash file itself, is that it opens up the wrong program, something called Openssh.

---

### Post by markbl on 2012-09-18
You should learn about ssh client configuration. E.g. to log in to a specific server using a specific username just add the following to your ~/.ssh/config:
```

Host theserver.edu
    User myusername

```

There is **plenty** more you can configure. E.g:
```

Host uni
    Hostname theserver.edu
    User myusername

```

Now you can just type "ssh uni". Then learn about the enormously useful Proxycommand to automatically tunnel through intermediate servers etc.

---

### Post by Bucky Ball on 2012-09-18
*Thread moved to **Programming Talk***

---

