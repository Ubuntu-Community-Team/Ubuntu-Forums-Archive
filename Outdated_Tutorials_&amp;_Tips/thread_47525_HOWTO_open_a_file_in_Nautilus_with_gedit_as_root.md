---
title: "HOWTO: open a file in Nautilus with gedit as root"
date: 2005-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-07-08
we often need to edit files as root in a text editor. Now we can do this with a right click in Nautilus (no big deal about opening in terminal but what the heck!)

```
gedit ~/.gnome2/nautilus-scripts/gedit-root
```

Copy the following lines into the file and save it and close it.
**Edited**
```
#created by Arnav Ghosh (United States)
foo=`gksudo -u root -k -m "enter your password for gedit root access" /bin/echo "Do you have root access?"`
sudo gedit $NAUTILUS_SCRIPT_SELECTED_URIS

```
Then make it executable with```

chmod +x ~/.gnome2/nautilus-scripts/gedit-root
```
thats it you are all set. Now right click on any file in nautilus and under "scripts" u will find "gedit-root" 
click and enjoy!
U can even select multiple files and open them in gedit as root in tabbed windows just by right clicking and using this script. The possibilities are endless.

---

### Post by manicka on 2005-07-08
[QUOTE=arnieboy]

```
gedit ~/.gnome2/nautilus-scripts/Open\ in\ gedit\ as\ root
```

[/QUOTE]

when I issue this command 3 different gedit files open

'open in', 'gedit' and 'as root'

Edit: Forget this, something went wrong with my copy/paste into the terminal. all is well now

---

### Post by arnieboy on 2005-07-08
cool. enjoy :)

---

### Post by manicka on 2005-07-08
[QUOTE=arnieboy]cool. enjoy :)[/QUOTE]
 installed okay and context menu appears.

Nothing happens though when chosen... sigh

---

### Post by arnieboy on 2005-07-08
[QUOTE=manicka]installed okay and context menu appears.

Nothing happens though when chosen... sigh[/QUOTE]
I have edited the script. try it now. U will get a warning abt "this is not a regular file.. blah blah". just ignore it. if it can be opened by gedit, it will be opened.

---

### Post by manicka on 2005-07-08
not on my ubuntu box at the moment. I'll give it a go later

thanks :)

---

### Post by manicka on 2005-07-09
this works okay but I wasn't happy about the error messages

did a bit of searching and this script works for me without any errors

```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done
```

This will open any folder or file with it's associated program as root.

If it's a  text based file it opens in gedit :)

---

### Post by arnieboy on 2005-07-09
i know abt that script but it wont open a .desktop file for editing in gedit.. for example.. my script helps open any text based file.. even executables.

---

### Post by manicka on 2005-07-09
Thanks for the explanation. 

I think I'll keep both and use as necessary :D

---

### Post by willis on 2005-07-09
[QUOTE=manicka]this works okay but I wasn't happy about the error messages

did a bit of searching and this script works for me without any errors

```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done
```

This will open any folder or file with it's associated program as root.

If it's a  text based file it opens in gedit :)[/QUOTE]


that seems a bit dangerous doesn't it?  opening anything as root, it harks back to easily installable windows virsus.

---

### Post by MikeyXX on 2005-07-09
[QUOTE=arnieboy]we often need to edit files as root in a text editor. Now we can do this with a right click in Nautilus (no big deal about opening in terminal but what the heck!)

```
gedit ~/.gnome2/nautilus-scripts/Open\ in\ gedit\ as\ root
```

Copy the following lines into the file and save it and close it.

```
#!/bin/sh
sudo gedit $@ $NAUTILUS_SCRIPT_CURRENT_URI

```
Then make it executable with```

chmod +x ~/.gnome2/nautilus-scripts/Open\ in\ gedit\ as\ root
```
thats it you are all set. Now right click on any file in nautilus and under "scripts" u will find "open in gedit as root" 
click and enjoy!
U can even select multiple files and open them in gedit as root in tabbed windows just by right clicking and using this script. The possibilities are endless.[/QUOTE]
 I copied and pasted the first line into a command line and it opened Gedit. Then I pasted the second entry into gedit and saved and closed. Then I ran the third line (chmod) and didn't get any complaints. Now I went through nautilus and found a file (menu.lst) for grub. Right clicked...and nothing but the usual properties, open with etc. What could I have done wrong?

---

### Post by arnieboy on 2005-07-09
[QUOTE=MikeyXX]I copied and pasted the first line into a command line and it opened Gedit. Then I pasted the second entry into gedit and saved and closed. Then I ran the third line (chmod) and didn't get any complaints. Now I went through nautilus and found a file (menu.lst) for grub. Right clicked...and nothing but the usual properties, open with etc. What could I have done wrong?[/QUOTE]
right click and look under "scripts". u will find "open in gedit as root"

---

### Post by manicka on 2005-07-09
[QUOTE=willis]that seems a bit dangerous doesn't it?  opening anything as root, it harks back to easily installable windows virsus.[/QUOTE]
 No, you're still asked for a password (in a popup window) to complete the task. 
It's just a graphical way to run sudo

---

### Post by willis on 2005-07-10
but isn't the default mode for sudo in ubuntu, to not ask for a password once one is given for the session?

(i'm no better i have sudo set not to ask for a password at all for my primary user account)

---

### Post by manicka on 2005-07-10
[QUOTE=willis]but isn't the default mode for sudo in ubuntu, to not ask for a password once one is given for the session?

(i'm no better i have sudo set not to ask for a password at all for my primary user account)[/QUOTE]
 I thought it was maintained for 15 mins only

---

### Post by arnieboy on 2005-07-11
[QUOTE=manicka]this works okay but I wasn't happy about the error messages[/QUOTE]

I have edited my script and made it perfect now: no more error messages!
Try it out.

---

### Post by manicka on 2005-07-11
Very nice.... great work :D

---

