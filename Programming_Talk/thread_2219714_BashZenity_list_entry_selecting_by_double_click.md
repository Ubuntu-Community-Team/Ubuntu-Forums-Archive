---
title: "Bash/Zenity: list entry selecting by double click"
date: 2014-04-25
forum: Programming Talk
---

### Post by DiederikL on 2014-04-25
I have been using a very simple zenity script for some years now to manage SSH connections to several servers. 

After installing Ubuntu 14.04 the double clicking to select one option from the list does not seem to be working anymore, no terminal is opened and the zenity form is closed. If I select a option with a signle click and then click on the "Ok" button the terminal is opened as espected.

Over the year I have developped quite the habbit of double clicking on one server in the list does anyone know how I can change this behaviour?

```

#! /bin/bash

selection=$(zenity --list \
"Server 1" \
"Server 2" \
 --column="" --text="Select a server" --title="SSH connector" --width=400 --height=400)

case "$selection" in
"Server 1")gnome-terminal --hide-menubar --title="Server 1" --geometry=100x32 -e       'ssh server1.com';;
"Server 2")gnome-terminal --hide-menubar --title="Server 2" --geometry=100x32 -e       'ssh server2.com';;
esac

```

---

### Post by Vaphell on 2014-04-25
if you ran zenity without capturing its output, you'd see that for whatever reason doubleclicking returns
```
Server 2|Server 2
```

try *case "${selection%|*}" in ...*

in general it's a good idea to have a *) case for unrecognized input to print something like "error". You'd know where to look.

---

### Post by Habitual on 2014-04-25
[ssh to host using zenity]("http://bournetoraiseshell.com/article.php?story=20110702095228930") is my meager attempt using zenity with ssh targets.
Maybe it will yield a clue.

Good luck!

---

### Post by Vaphell on 2014-04-25
```
me=$(whoami) # I used this so other users of the script won't have to change the --filename parameter on the next line.
key=$(zenity --title "Select key" --file-selection --filename=/home/$me/.ssh/);
```

is there a reason for not using $HOME/.ssh?

---

### Post by Habitual on 2014-04-25
> **Vaphell said:**
> ```
me=$(whoami) # I used this so other users of the script won't have to change the --filename parameter on the next line.
key=$(zenity --title "Select key" --file-selection --filename=/home/$me/.ssh/);
```

is there a reason for not using $HOME/.ssh?

Cause you'd be bored if I did?  :)
Updated with credit. 
You rock!

---

