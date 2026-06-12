---
title: "Ignoring Inputs at autoatart"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by jwn-2 on 2014-03-10
I have written a script that needs some input and displays some output. It works fine when run from a terminal. However, I want to run it at boot from ~/autostart. The problem is that when run like that it seems that all read commands are simply ignored, and when the script reaches its end the terminal is closed before I can read any output. I have tried ¨gnome-terminal -x scriptname¨, ¨gnome-terminal --command=scriptname¨ and ¨xterm -e scriptname¨, all with the same result. All other commands in the script seems to execute correctly. Please help.

---

