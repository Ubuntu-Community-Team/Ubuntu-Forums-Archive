---
title: "Editing touchegg .conf file. File not found? 12.04"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by arumiat on 2013-06-12
Dear Ubuntu users

I have
1) installed Touchegg on Ubuntu 12.04 using software centre
2) installed uTouch on Ubuntu 12.04 using software centre
3) opened up the touchegg.conf file [FONT=Ubuntu Mono]gedit ~/.config/touchegg/touchegg.conf
[/FONT]4) when I try insert text such as (or any text for that matter) into the .conf file in the gedit window

[THREE_FINGERS_DRAG_UP]action=MAXIMIZE_RESTORE_WINDOWsettings=
if I try and save the file an error comes up saying
[COLOR=#0000ff]Could not find the file /home/xxxxxxx/.config/touchegg/touchegg.conf. Please check that you typed the location correctly and try again[/COLOR].

How can his be possible? What am I doing wrong here? 
Thanks in advance

---

### Post by Cheesemill on 2013-06-12
Does the ~/.config/touchegg directory exist yet? If it doesn't then you won't be able to save a file in it.

Either create the directory by doing...
```
mkdir ~/.config/touchegg
```

Or by opening gedit normally (without specifying a file path) and using the 'Create folder' button in the 'Save as...' dialog box when you save your file.

---

### Post by arumiat on 2013-06-13
> **Cheesemill said:**
> Does the ~/.config/touchegg directory exist yet? .

Thanks Cheesemill.

I have not created the file manually. Surely this is created when the program is installed?

---

### Post by Cheesemill on 2013-06-13
No. It will probably be created the first time you run the program, or then again maybe not. It's up to the developers whether or not a config file is created when the program is first run.

---

### Post by arumiat on 2013-06-13
Okay thanks for clarifying that.

Do I need to create just the directory ~/.config/touchegg or the actual .config file ie. 

mkdir ~/.config/touchegg

OR

mkdir ~/.config/touchegg/touchegg.conf

Thanks again

---

### Post by Cheesemill on 2013-06-13
First create the directory...
```
mkdir ~/.config/touchegg
```

Then create a new file for editing...
```
gedit ~/.config/touchegg/touchegg.conf
```

---

