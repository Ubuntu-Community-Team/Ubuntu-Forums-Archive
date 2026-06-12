---
title: "Script help"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-06-02
I need to know what I'm doing wrong with this script.  I want to be able to stop gnome and nautilus and execte World of Warcraft, launch firefox, and then launch ventrilo.  Then upon closing World of Warcraft, relaunch gnome and nautilus.

```

#!/bin/bash

metacity --replace &
wine "C:\Program Files\World of Warcraft\wow.exe"     
gnome-panel nautilus --replace &

sleep 5

firefox

sleep 5

wine "C:\Program Files\Ventrilo\ventrilo.exe"

```[/QUOTE]

---

### Post by dracayr on 2008-06-02
well you're not "stopping" anything

```
metacity --replace &
```
Sets the window manager to metacity

```
wine "C:\Program Files\World of Warcraft\wow.exe"
```  
should indeed execute wow.exe (are you sure that world of warcraft works with wine?)  

```
gnome-panel nautilus --replace &
```
starts gnome-panel and nautilus (you can leave out the --replace)

```
sleep 5
```
the comp. sleeps for 5 seconds

```
firefox
```
opens firefox (though you might want to append an '&')

```
sleep 5
```
the comp. sleeps for 5 seconds

```
wine "C:\Program Files\Ventrilo\ventrilo.exe"
```
executes ventrilo.exe


dracayr

---

### Post by Mauler5858 on 2008-06-02
> **dracayr said:**
> well you're not "stopping" anything

```
metacity --replace &
```
Sets the window manager to metacity

```
wine "C:\Program Files\World of Warcraft\wow.exe"
```  
should indeed execute wow.exe (are you sure that world of warcraft works with wine?)  

```
gnome-panel nautilus --replace &
```
starts gnome-panel and nautilus (you can leave out the --replace)



Ive used replace command before and it seems to work ok by replacing a one process with another, and restarting the original process when the second one stops.

---

