---
title: "Menu Bars disappeared"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by guidolo86 on 2008-07-07
i cant see none of my menu bar's how can i do to restore them??
Plase help....i'm really new and i don't have any experiencies
Regards!
Guido Olomudzski

---

### Post by billgoldberg on 2008-07-07
Haven't had that one,

I don't know if this will work, but try hitting "alt + f2" and enter

gnome-panel

---

### Post by guidolo86 on 2008-07-07
it dosent work but thanks for you interest

---

### Post by wolfen69 on 2008-07-07
```
 sudo apt-get install gnome-menus
```
or, right click taskbar and choose "add to panel", then "main menu"

---

### Post by billgoldberg on 2008-07-07
Ok, I did some googling, looks like this should do the trick.

In a terminal (alt+f2 and then "gnome-terminal) copy paste this:

```
gconftool-2 --shutdown
```

press enter

```
rm -rf ~/.gconf/apps/panel
```

press enter (if it shouldn't work, put "sudo" in front of the code)

```
pkill gnome-panel
```

press enter

---

### Post by guidolo86 on 2008-07-07
I'm really thanks your help and i'm sorry of my insistence and my error in the explanation of the error i cant open the task bar thats my problem:S so I cant add nothing becuase isnt there
sorry and thanks

---

### Post by bliffle on 2008-07-07
Can you get the terminal with alt-f2?

---

### Post by bikerdave on 2008-07-08
Your problem sounds exactly like the one I recently had. I browsed around while waiting for  help and found something that solved my problem. I hope this helps!

[http://ubuntuforums.org/showthread.php?t=851611](http://ubuntuforums.org/showthread.php?t=851611)

---

### Post by wolfen69 on 2008-07-08
are you married to this installation? if not, just re-install. plus you'll know more about the installation process. life is learning . i just don't get why people become emotionally attached to their OS. have a good backup plan, and it's ez.

---

### Post by guidolo86 on 2008-07-09
> **bikerdave said:**
> Your problem sounds exactly like the one I recently had. I browsed around while waiting for  help and found something that solved my problem. I hope this helps!

[http://ubuntuforums.org/showthread.php?t=851611](http://ubuntuforums.org/showthread.php?t=851611)

This really helps!!! PROBLEM SOLVED THANKS!

---

### Post by mdsmedia on 2008-07-09
> **wolfen69 said:**
> are you married to this installation? if not, just re-install. plus you'll know more about the installation process. life is learning . i just don't get why people become emotionally attached to their OS. have a good backup plan, and it's ez.This sounds like a Windows-ish answer LOL.

I remember my ISP giving me Windows re-installation as a solution to one of their numbers not working on dial-up. I spent half a day reinstalling and getting setup again, only to find the number still didn't work. The solution? The number wasn't in use anymore....change the number!! Was I P15SED???

---

