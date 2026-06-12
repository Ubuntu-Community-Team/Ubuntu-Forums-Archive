---
title: "Chaining two commands"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by vasa1 on 2012-05-09
Ctrl+Alt+T opens a terminal. The command appeard to be ```
x-terminal-emulator
```
But if I make a custom keyboard shortcut, Ctrl+Alt+F, in System Settings, Keyboard Shortcuts, and have ```
x-terminal-emulator && nohup firefox
``` as the command, it only opens the terminal just like Ctrl+Alt+T does but it doesn't launch Firefox. What am I doing wrong? Or am I trying something that is just not possible?


Okay! I was just complicating things. There's no need for the **x-terminal-emulator nohup** bit!

---

### Post by sudodus on 2012-05-09
I don't know what is possible in linux, it tends to be much more than I think ;-) but I can do something similar like this
```
xterm -e nohup firefox
``` and it works with the -e option also with ```
gnome-terminal
``` that is activated in my computer by the command
```
x-terminal-emulator
```

---

### Post by Cheesemill on 2012-05-09
> **vasa1 said:**
> Ctrl+Alt+T opens a terminal. The command appeard to be ```
x-terminal-emulator
```But if I make a custom keyboard shortcut, Ctrl+Alt+F, in System Settings, Keyboard Shortcuts, and have ```
x-terminal-emulator && nohup firefox
``` as the command, it only opens the terminal just like Ctrl+Alt+T does but it doesn't launch Firefox. What am I doing wrong? Or am I trying something that is just not possible?


Okay! I was just complicating things. There's no need for the **x-terminal-emulator nohup** bit!
Using && means that the second command will execute after the first command has completed successfully. As an example:
```
aptitude update && aptitude full-upgrade
```
'aptitude update' runs first and if it completes successfuly then 'aptitude full-upgrade' will run.
If for some reason 'aptitude update' doesn't run successfully (no network connection for example) then the second command won't get executed.

---

