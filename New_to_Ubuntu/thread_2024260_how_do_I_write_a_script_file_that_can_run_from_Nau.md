---
title: "how do I write a script file that can run from Nautilus?"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by s1baker on 2012-07-13
Hi,

How can I write a script file that can be run from Nautilus file manager where all you have to do is mouse click on it for it to run?

Otherwords, I have wrote a script, but I have to run the terminal and manually type in the path to the script to get it to run,
I just want to be able to click on the file with nautilus file manager to run it. 
The script has some commands in it that will only work in a terminal, so I guess the script would have to call up the terminal
first then run it in the terminal, I don't know.

For instance, I want to have in the script something like this:

```

echo "Enter a number [ENTER]:"
read number

at ( set the at command to do something here )

EDITOR=nano crontab -e


```


Thanks for any help.

---

### Post by OM55 on 2012-07-13
Hello s1baker,

Edit the file and write it this way:

```

#!/bin/bash
echo "Enter a number [ENTER]:"
read number

at ( set the at command to do something here )

EDITOR=nano crontab -e
```then change its permissions to be executable. You can do that either from within Nautilus but right-click on the file, select "Properties" tab and check the "Allow executing as a file" checkbox. Or you can do so in the command line:

```
chmod 766 <filename>
```Now when you click on the file name from within Nautilus, it will suggest to you four options:
- Run in terminal
- Display
- Cancel
- Run

Run in terminal - will do just that (identical to open a terminal and type in the file name)
Display - will open the file in editor
Cancel - cancel and close the option window
Run - run the script without opening a terminal

Chose one of the 'Run' options and you have what you wanted.

Hope that helps!

---

### Post by s1baker on 2012-07-13
thanks, I think that is what i need.

---

### Post by s1baker on 2012-07-13
~Also, when the terminal pops up, It runs Gnome 3.4.1.1, which has a solid white background screen. I would like for my terminal that has xfce 0.4.8 to run that has a solid black background screen. How could I pick which terminal to run? ( or change Gnome terminal to solid black background either way, don't matter)

( I am using 12.04 with DE of xfe 4.08 )

Thanks

---

### Post by OM55 on 2012-07-13
First, you can change the colors of the terminal to your liking. Just open the terminal, and in its menu go to:

 Edit -> Profile Preferences

and select the "Colors" tab. All there is left to do is to select the colors you like for each area of the terminal, and you are good to go. You can also change the size of the terminal (number of character per line, number of lines) and the size/type of the font.

But if you really want to change the default terminal (which is gnome-terminal) to another, type:

```
gconftool --type string --set /desktop/gnome/applications/terminal/exec <YOUR-TERMINAL>
```

---

