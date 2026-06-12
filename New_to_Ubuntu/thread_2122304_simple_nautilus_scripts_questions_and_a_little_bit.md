---
title: "simple nautilus scripts questions and a little bit of zenity questions"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by Froylan on 2013-03-04
most of us use nautilus scripts and therefore I decided that this is a likely forum where I can get answers
questions:[CENTER]***1) what command incerts a selected file in the command?***
[/CENTER]
EXAMPLE
I want to extract selected files, I do ```
unrar x PATH/TO/FILE
```
how to replace 
```
PATH/TO/FILE
```
to the selected files location?[CENTER]***2)how to list multiple files in a drop down menu on zenity?***
[/CENTER]
for example if I have a folder and want to list all the files inside to select to open one or two or all of them

Thanks for reading.
sincerely Froylan.

---

### Post by Froylan on 2013-03-04
bump

---

### Post by sully101 on 2013-03-06
1/ [https://help.ubuntu.com/community/NautilusScriptsHowto]("https://help.ubuntu.com/community/NautilusScriptsHowto").

```
$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
```

2/ type man zenity in a terminal
```
zenity --file-selection
```

The rest is writing a script to handle it all :)

---

