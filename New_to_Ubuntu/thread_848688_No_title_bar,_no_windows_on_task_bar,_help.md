---
title: "No title bar, no windows on task bar, help"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Hurrz88 on 2008-07-03
I am having some problems with my bars on the top of my windows, the one containing the title and the maximize, minimize, and exit buttons. It isn't showing up. And each time I restart my computer all of the programs I was running when I turned off my computer are all restarted. Also, none of the items at one the task bar at the bottom are showing up, like it isn't showing any of the windows I have opened. Please help.

---

### Post by sayakb on 2008-07-03
1. For the title bar problem, are you using emerald (with compiz?) Then goto System->Preferences->Sessions and press Add. Type the name as *Emerald* and the command as [I]
```
emerald --replace &
```[/I]2. For the programs problem, click on the Session options in the Session preferences window (the same window as in pt 1) and make sure the *Automatically remember...*  option is unchecked. If it is already unchecked, open a terminal and type:
```
rm ~/.gnome2/session
```And restart X (Press Ctrl+Alt+Backspace)

---

