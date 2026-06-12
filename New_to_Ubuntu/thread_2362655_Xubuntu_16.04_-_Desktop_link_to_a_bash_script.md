---
title: "Xubuntu 16.04 - Desktop link to a bash script"
date: 2017-05-31
forum: New to Ubuntu
---

### Post by sprinterdriver on 2017-05-31
Hi forum.
(yeey - my first post here :D )

So I have decided to go with Xubuntu on a laptop computer, so I have just barely touched bash script. Because it has an annoying touchpad, I found a command to disable the touchpad, and I made a bash file to do so (so far in my home folder). The bash file runs just fine when I call it from terminal, seems to be nothing wrong with bash file itself.

So I decided to make a shortcut to the Xubuntu desktop for that bash file. But when I try to run it (double click on the desktop link), nothing happens. Neither any terminal windows appears nor did the command execute (touchpad not deactivated).

So my question is - What does it takes to make the bash file work when running from desktop shortcut?

Thanks

---

### Post by ajgreeny on 2017-05-31
Let us see the contents of the script (all of it not just the command) and we may have more idea what is going on here.

As an example I have a script to stop the "tap to click" of my touchpad on a laptop I use, the contents of which are 
```
#!/bin/bash
synclient MaxTapTime=0
```which I have named as notap.sh which sits in my home folder.  The script is also made executable with command ```
chmod +x notap.sh
```
In my user's startup applications I simply point to that script using the full pathway, ie. /home/*username*/notap.sh and it is executed at each session start.

---

### Post by Dennis N on 2017-05-31
A valid bash script can be run from a symbolic link on the Desktop, so that should not be the problem. Look to the script itself.

---

