---
title: "Newbie trying to make bash file with infinate loop, needing help..."
date: 2007-08-03
forum: Programming Talk
---

### Post by smartboyathome on 2007-08-03
I am a newbie at bash (this is my first script), so I decided to take it slow by trying to make a bash file for listing my theme stuff (using echo) that shows the text but ends when I want it to, but I cannot seem to get the done portion of my infinate loop to work! Here is the code for my bash file:

```

#!/bin/bash
echo "Smartboy's Desktop";

echo "Brought to you by smartboyathome!";
echo "Theme: iBlack Complete (available at gnome-look.org)";
echo "Wallpaper: Picture of Aurora Borialis from nasa";
echo "Apps open:";
echo "Avant Window Navigator (dock)";
echo "Compiz Fusion (Window Manager)";
echo "Ubuntu System Panel (system panel)";

# infinate loop so that the user decides when to stop the file
while [ true ]
do

done

```

When I run this script, however, I get this:

```
Smartboy's Desktop
Brought to you by smartboyathome!
Theme: iBlack Complete (available at gnome-look.org)
Wallpaper: Picture of Aurora Borialis from nasa
Apps open:
Avant Window Navigator (dock)
Compiz Fusion (Window Manager)
Ubuntu System Panel (system panel)
/home/aabbott/desktop-setup: line 15: syntax error near unexpected token `done'
/home/aabbott/desktop-setup: line 15: `done'
```

What is wrong with this? Also, is there an easier way to call upon my theme details without having to edit this file every time something changes? Thanks to anyone who helps!

---

### Post by McNils on 2007-08-03
You need a statement inside your while block. If you realy want it to do nothing put a : (colon) on the empty line.

---

### Post by Mr. C. on 2007-08-03
A standard idiom is:
```

while :
do
   echo ...
done
```

MrC

---

### Post by smartboyathome on 2007-08-03
I still get the same error with what you said Mr C. Again, here is my file:
#!/bin/bash
```
while :
do

echo "Smartboy's Desktop";
echo "Brought to you by smartboyathome!";
echo "Theme: iBlack Complete (available at gnome-look.org)";
echo "Wallpaper: Picture of Aurora Borialis from nasa";
echo "Apps open:";
echo "Avant Window Navigator (dock)";
echo "Compiz Fusion (Window Manager)";
echo "Ubuntu System Panel (system panel)";
done
```

---

### Post by Mr. C. on 2007-08-03
The code is syntactically correct and runs fine.

What editor are you using?
Show exactly how you run the script, and the error message (copy/paste the run and execution output).

By the way, you do not need semicolon's to terminate lines in bash; newlines are sufficient.  And we usually indent the contents of if's, for's, while's, etc.:
```

#!/bin/bash
while :
do
    echo "Smartboy's Desktop"
    echo "Brought to you by smartboyathome!"
    echo "Theme: iBlack Complete (available at gnome-look.org)"
    echo "Wallpaper: Picture of Aurora Borialis from nasa"
    echo "Apps open:"
    echo "Avant Window Navigator (dock)"
    echo "Compiz Fusion (Window Manager)"
    echo "Ubuntu System Panel (system panel)"
done
```

MrC

---

### Post by smartboyathome on 2007-08-03
What you posted worked for me, though it keeps printing that info over and over. If I put a colon inside the do portion, and put the echos before the while script make it print the info and then do nothing? Thanks for your help, btw :)

EDIT: I tried what I said above and it works!

---

### Post by nitro_n2o on 2007-08-03
```
echo "Smartboy's Desktop";
echo "Brought to you by smartboyathome!";
echo "Theme: iBlack Complete (available at gnome-look.org)";
echo "Wallpaper: Picture of Aurora Borialis from nasa";
echo "Apps open:";
echo "Avant Window Navigator (dock)";
echo "Compiz Fusion (Window Manager)";
echo "Ubuntu System Panel (system panel)";

while true; do
  :
done
```

just say while true 
without the brackets [] :)

---

### Post by nitro_n2o on 2007-08-03
dont' worry

---

### Post by smartboyathome on 2007-08-03
Thanks, that works too! ^_^
I am going to learn more bash script now! :D

---

### Post by kpatz on 2007-08-03
What's the purpose of the infinite loop?  To get the window to stay open or something?

A more efficient way is to use the read command, such as:

```
read
```

This will make the shell wait for the user to enter something (hit the enter key) before the script continues.  The advantage of this is the shell is using no CPU while it's waiting for the input.  Then you can hit enter while in the window and it wil close.

Another option is to use the sleep command, if you want the window to auto-close after a period of time:

```
sleep 60
```

will pause for 60 seconds and then continue.

---

### Post by Mr. C. on 2007-08-04
Smartboy - this might be of some use to you:

[http://cis68b1.mikecappella.com](http://cis68b1.mikecappella.com)

Check out the course notes, homework, etc.

MrC

---

### Post by smartboyathome on 2007-08-04
> **kpatz said:**
> What's the purpose of the infinite loop?  To get the window to stay open or something?

A more efficient way is to use the read command, such as:

```
read
```

This will make the shell wait for the user to enter something (hit the enter key) before the script continues.  The advantage of this is the shell is using no CPU while it's waiting for the input.  Then you can hit enter while in the window and it wil close.

Another option is to use the sleep command, if you want the window to auto-close after a period of time:

```
sleep 60
```

will pause for 60 seconds and then continue.

Thanx, the read command also makes the code much cleaner! Thanks for all your help!

---

