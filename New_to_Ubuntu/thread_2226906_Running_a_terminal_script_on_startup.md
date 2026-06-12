---
title: "Running a terminal script on startup?"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by gijs2 on 2014-05-29
Hi,

Is it possible to run a terminal script on startup?
I want
```
[COLOR=#3E454C][FONT=Helvetica]xmodmap -e "keycode 48 = apostrophe quotedbl"[/FONT][/COLOR]
```
to be permanent since it goes away after restart, thanks :)

---

### Post by deadflowr on 2014-05-29
Put it in "Startup Applications".
Simply put the command where it says command.

---

### Post by gijs2 on 2014-05-29
> **deadflowr said:**
> Put it in "Startup Applications".
Simply put the command where it says command.

Apperantly I dont have startup applications 0.o

---

### Post by sudodus on 2014-05-29
Which version (12.04 or 14.04) and which flavour (standard Ubuntu, Xubuntu, Lubuntu, Kubuntu, Ubuntu Gnome) are you running?

---

### Post by gijs2 on 2014-05-29
> **sudodus said:**
> Which version (12.04 or 14.04) and which flavour (standard Ubuntu, Xubuntu, Lubuntu, Kubuntu, Ubuntu Gnome) are you running?

Ubuntu 14.04 LTS

---

### Post by grumblebum2 on 2014-05-29
In terminal...
```
gnome-session-properties
```

---

### Post by hyperreal on 2014-05-29
gijs2:  Startup applications can be accessed from the Applications lens on the Unity dashboard.  Click on the Ubuntu icon in the top left of the Unity panel, then search for 'startup applications'.

---

### Post by vasa1 on 2014-05-29
> **gijs2 said:**
> Hi,

Is it possible to run a terminal script on startup?
I want
```
xmodmap -e "keycode 48 = apostrophe quotedbl"
```
to be permanent since it goes away after restart, thanks :)
Could you please explain why you want to make this change? Does this change make the single quote key into double quotes? If so, how will you deal with single quotes which are needed in scripting (and possibly elsewhere)?

---

