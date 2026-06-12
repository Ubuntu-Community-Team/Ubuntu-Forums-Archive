---
title: "bash full screen"
date: 2011-07-15
forum: Programming Talk
---

### Post by Jonny87 on 2011-07-15
Is there a command that can be placed with in a bash script that the script will open in a full screen terminal window each time it is run.

---

### Post by Bachstelze on 2011-07-15
No. What would happen if such a script were run from a virtual console or  hardware TTY? If you know which terminal emulator the script will use, there might be a command to make it full-screen, but it will only work on that particular terminal emulator.

---

### Post by papibe on 2011-07-15
I don't know any bash control the size of the screen (curses maybe?).

But, you can do a trick: create a script that calls the gnome-terminal using full screen mode and run your script on it. Something like this:
```
#!/bin/bash
gnome-terminal --full-screen -e /path/to/your/script.sh
```
I would advice you to put a readline or pause at the end of your script, since the terminal will close as your script exits.

Hope it helps.

---

### Post by Jonny87 on 2011-07-15
> **papibe said:**
> I don't know any bash control the size of the screen (curses maybe?).

But, you can do a trick: create a script that calls the gnome-terminal using full screen mode and run your script on it. Something like this:
```
#!/bin/bash
gnome-terminal --full-screen -e /path/to/your/script.sh
```
I would advice you to put a readline or pause at the end of your script, since the terminal will close as your script exits.

Hope it helps.

Yea I was thinking it might be something like that, I was just looking for another option rather running another script. Thanks for ya help.

---

### Post by mikejonesey on 2011-07-16
not sure if it's what your after but incase your not aware, you can change your bash profile to default to full screen so you don't require the extra peramiters...

---

