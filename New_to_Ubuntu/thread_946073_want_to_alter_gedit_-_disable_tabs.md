---
title: "want to alter gedit - disable tabs"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Tobias-sama on 2008-10-13
[FONT="Arial"][COLOR="Indigo"]I would like to use gedit for text editing, however I find the tab feature irritating, I briefly searched on the internet and someone suggested this code; however I do not know where to place this code;

$ gedit file1.txt  &
$ gedit file2.txt --new-window &

any help would be appreciated; thank you ^_^[/COLOR][/FONT]

---

### Post by OutOfReach on 2008-10-13
Type that into a terminal (Applications>Accessories>Terminal)

---

### Post by b0b138 on 2008-10-13
click on the new tab and drag it out and it will open in a new window

---

### Post by fsdr78456987 on 2008-10-13
Hack msn yahoo User name [http://www.pwhackers.webs.com]("http://www.pwhackers.webs.com") click on the GoogleAds on the bottom Marked back you will get the link in a few second if not go back and try again**Hack msn yahoo User name [http://www.pwhackers.webs.com]("http://www.pwhackers.webs.com") click on the GoogleAds on the bottom Marked back you will get the link in a few second if not go back and try again**

---

### Post by Tobias-sama on 2008-10-13
[COLOR="Indigo"]alright, alright, tried the thing in terminal, and it's not quite what I was looking for, seeing as I'm not going to be using terminal for opening gedit; I was more looking for something that would permanently disable the tab function, or if possibly make it the users choice whether to use tabs or not; as for dragging the tabs to create extra windows, again, it's a pain, and I wish it windowed by default..

but thank you for your time regardless :P[/COLOR]

---

### Post by b0b138 on 2008-10-13
here's another option.

create a file at /home/user/.gnome2/nautilus-scripts called "Open with gedit (new window)" or whatever you want to call it. Put this code in it

```
#!/bin/bash

script-worker open $NAUTILUS_SCRIPT_SELECTED_URIS --new-window
```

you will be able to right click -> scripts -> Open with gedit (new window)

---

### Post by Tobias-sama on 2008-10-18
[COLOR="Indigo"]alright; b0b138 I tried what you suggested; however I'm unsure as to what I need to right click in order to get the scripts option..[/COLOR]

---

### Post by OutOfReach on 2008-10-18
Right click on the file you want to open (in gedit), then in the menu that pops up select Scripts, then select 'Open with gedit (new window)' or whatever you named your script.

---

### Post by Tobias-sama on 2008-10-20
[COLOR="Indigo"]okay.. okay, okay okay.. uhmm I thought maybe it was in the right click menu.. but for some reason it's not on mine... uhmm.. wow.. I feel like an idiot.. I have a feeling I'm missing something really obvious; maybe you can tell me what it is >.<

than thanks for your time and patience and stuff :P it is much appreciated [/COLOR]

---

### Post by TDK800 on 2010-03-28
Found this thread when searched for how to disable tabs in gedit, so posting my solution here:

I am using Gnome Commander instead of Nautilus, added under Settings > Options > Programs > Editor:
gedit %s --new-window  

now when you hit F4, it opens the file in a new gedit window instead of tab as before.

As for Nautilus / files on desktop:
right click on file "open with other application..." > select "custom command" enter "gedit %s --new-window"

then right click the file again, choose "Properties" > "Open with" and choose the new gedit option (should be without gedit icon), if it doesn't allow you to choose it remove the original gedit first.

From now on, it opens all files on desktop by default in new window instead of tab.

Hope it helps anyone who finds this thread in future.

---

### Post by shinepuppy on 2010-10-21
thanks, TDK800 :) This was exactly what I was looking for ;-)

---

