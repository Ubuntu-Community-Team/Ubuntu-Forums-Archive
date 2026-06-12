---
title: "[SOLVED] Panel has disappeared"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Spooky5 on 2008-07-05
I installed xubuntu on my friend's computer a while back. She has done something weird to make the top panel disappear. :roll: How do I get it to display again?

---

### Post by sayakb on 2008-07-05
At at terminal or at the run dialog:
```
xfce4-panel
```

---

### Post by Spooky5 on 2008-07-05
> **LinuxIsInnovation said:**
> At at terminal or at the run dialog:
```
xfce4-panel
```
Okay, it worked until I closed the terminal. Then it disappeared again. How do I get to stay.

I don't have a clue how she got it to disappear in the first place, lol.

---

### Post by gettinoriginal on 2008-07-05
right click the bottom panel and choose new panel

---

### Post by sayakb on 2008-07-05
XFCE Menu->Autostart Applications
Click Add. Enter Name as panel, command as xfce4-panel
Press OK and then Close.
Login again into XFCE

PS: Have you lost all panels or you still have the bottom panel?

---

### Post by sisco311 on 2008-07-05
Alt+F2:
```
xfce4-panel
```
Close all applications. Click on the panel Quit button, 
select the Save session option and log out.

(from the terminal:
```
xfce4-panel&
disown %xfce4-panel
```)

---

### Post by Amanda HazLaPaz on 2008-07-05
It's been a while since I used Xubuntu, but if I recall correctly, click on the desktop and a window should open (panel manager). There are options to indicate where you want the new panel to be, and how many you want.

---

### Post by arashiko28 on 2008-07-05
I have the same problem. Both of my panels disappeared at the same time, my computer only recognizes half of the memory installed, actually I have 768MB of RAM and only recognizes half or less.

---

### Post by sayakb on 2008-07-05
> **arashiko28 said:**
> I have the same problem. Both of my panels disappeared at the same time, my computer only recognizes half of the memory installed, actually I have 768MB of RAM and only recognizes half or less.

For the panel problem, follow post 5 or 6.
Also, post the output of the following command:
```
free -m
```

---

### Post by tjwoosta on 2008-07-05
> Okay, it worked until I closed the terminal. Then it disappeared again. How do I get to stay.

I don't have a clue how she got it to disappear in the first place, lol. 
a terminal is not the place to run commands like this

use alt-f2, then run the command there

---

### Post by Spooky5 on 2008-07-05
> **sisco311 said:**
> Alt+F2:
```
xfce4-panel
```
Close all applications. Click on the panel Quit button, 
select the Save session option and log out.

(from the terminal:
```
xfce4-panel&
disown %xfce4-panel
```)

Okay saving the session and logging out seems to have worked. Thanks ever so much! :KS

---

### Post by sayakb on 2008-07-05
Please mark the thread as solved.

---

### Post by h0bbe on 2008-07-07
It didn't solve it for me though :-(

When I click on the panel Quit button I get the question "Close xfce-panel?" instead of having the possibility to choose "save session".

Please help me!

---

### Post by sisco311 on 2008-07-07
> **h0bbe said:**
> It didn't solve it for me though :-(

When I click on the panel Quit button I get the question "Close xfce-panel?" instead of having the possibility to choose "save session".

Please help me!
Try to restore the default session.

rename the ~/.cache/sessions folder:
```
mv ~/.cache/sessions ~/.cache/sessions-backup
```
restart the x server(Ctrl+Alt+Backspace)

to restore the old one:
```
mv ~/.cache/sessions-backup ~/.cache/sessions
```

---

### Post by maizuddin35 on 2010-04-19
this post save me from not knowing the part where i need my panel back.Thank you guys!

---

