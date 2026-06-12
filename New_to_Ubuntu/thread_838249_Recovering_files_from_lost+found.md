---
title: "Recovering files from lost+found"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by SMA11784 on 2008-06-23
Okay, fcsk just moved the entire contents of my hard drive except for installed packages into lost+found.  I was told to use 'gksudo nautilus' to get into the folder and it looks like everything is intact but I can't copy or move any of it back to where it belongs.

I really have no idea what I'm doing here and Google is useless.  Anybody bored enough to point me in the right direction?

---

### Post by bcom on 2008-06-23
Have you tried to copy or move the files manually form a Terminal command line?

---

### Post by SMA11784 on 2008-06-23
I tried and quickly realized I don't know how.  I don't know how to navigate to the lost+found folder or get root access (hence posting under Absolute Beginner).

I'm serious; I have no idea what I'm doing.  I need any explanations to be thorough and specific.  Assume only that I know what a computer is.

---

### Post by Yuki_Nagato on 2008-06-23
Here is a quick rundown of commands.

When there is a blinking light, type (without quotes) "ls"

This will provide a list of the files that you currently can enter.

Type "cd XXX" with XXX being the EXACT (capitalization counts) name of one of those files to move into it.  "ls" will provide different output now.  Type "cd .." to move back out of the file into the previous area.  Typing "ls" should look familiar.  In this way, you can find your way around.  Perhaps get a pad and pen to write things down.

Typing "cd ~" will bring you back to your "home" folder if you get lost.

Once you can "see" the lost and found folder (but not be inside of it), type "sudo cp (lost and found folder's name) /home/XXX/Desktop"

sudo - asks for root access and administrative abilities.
cp - copy folders
Type the name of the folder, just like in "cd"
/home.... - this is where the folder will be copied to - your desktop.

If any command seems fishy, type "man XXX"  This brings up the manual for the command.  You can read about it then.  Press "q" to quit the manual.

Finally, when cd-ing around, the files will be in the same place they are in Nautilus.

---

