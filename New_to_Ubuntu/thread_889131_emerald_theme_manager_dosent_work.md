---
title: "emerald theme manager dosent work"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-13
i load it up, even made my own tool bar look. and ill sit there clicking on it and it wont change the tool bars. any idea why?

---

### Post by Crafty Kisses on 2008-08-13
> **WinterMadness said:**
> i load it up, even made my own tool bar look. and ill sit there clicking on it and it wont change the tool bars. any idea why?

Try the following in Terminal:
```
emerald --replace
```
That should work.

---

### Post by WinterMadness on 2008-08-13
> **Codename said:**
> Try the following in Terminal:
```
emerald --replace
```
That should work.

awesome thanks
is there any way i can get the gui to work though?

edit:when i close the terminal my borders go away

---

### Post by Crafty Kisses on 2008-08-13
> **WinterMadness said:**
> awesome thanks
is there any way i can get the gui to work though?

Hmmm, try running "emerald" in Terminal, do you get an error?

---

### Post by dje on 2008-08-13
> **WinterMadness said:**
> awesome thanks
is there any way i can get the gui to work though?

that command runs emerald, the gui only changes the theme, it does not run emerald. if emerald is running the gui works ;)

dje

---

### Post by dje on 2008-08-13
press Alt + F2 and type:
```
emerald --replace
```
that will solve the problem of the borders going away when you close the terminal
to get emerald at login add the above command in System >> Preferences >> Sessions

dje

---

### Post by Darkade on 2008-08-13
If you press Alt+F2 and type
```
emerald --replace
```
it should work. You can also add it your startup session in System>preferences>Sessions
that would have the same effect if in the compizconfig settings manager if you enable Windows Decorator and in command you type emerald -- replace

---

### Post by flick on 2008-08-13
A nice GUI app for turning compiz and emerald on and off is the fusion-icon. Puts a nice icon in your system tray, right-clicking on it gives you all sorts of options for selecting window decorator, window manager, some compiz options, and other goodness. Once it is installed you can find it in the Applications >> System Tools menu.

---

### Post by WinterMadness on 2008-08-13
ghost@laptop:~$ emerald
emerald: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
ghost@laptop:~$ 



i get that error when just typing "emerald"

---

### Post by tuxxy on 2008-08-13
goto **system > preferences > session**, add a new session, enter this command **emerald --replace** save it, now it will auto run at boot, so you dont have to type in the command.

---

