---
title: "run in terminal help"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by d4ng3r on 2008-06-28
I am using Ubuntu 8.04 and just installed MATLAB, which I need for school.  As of right now, the only way for me to run it, is to use terminal to cd to the folder, and run ./matlab  or I could navigate to the folder and double click matlab and have it 'run in terminal'.
What I would like to do is have it come up in my main menu.  I tried creating a launcher and putting in the menu, unfortunately, the launcher for some reason doesn't 'run in terminal' and when you just run it, for some reason it doesn't work.  I feel as though maybe I need to write a shell script, but I don't really know how, or if that is the correct direction to take.

Any help would be appreciated,
Brian

---

### Post by Troll_the_Great on 2008-06-28
Did you buy Matlab? How much did you pay for it? (I need it for school too).

---

### Post by d4ng3r on 2008-06-28
I did not, my school has a license since I am a TA.

---

### Post by Troll_the_Great on 2008-06-28
OK, I was wondering how much it is.Thx anyway.

---

### Post by dizee on 2008-06-28
> **d4ng3r said:**
> I am using Ubuntu 8.04 and just installed MATLAB, which I need for school.  As of right now, the only way for me to run it, is to use terminal to cd to the folder, and run ./matlab  or I could navigate to the folder and double click matlab and have it 'run in terminal'.
What I would like to do is have it come up in my main menu.  I tried creating a launcher and putting in the menu, unfortunately, the launcher for some reason doesn't 'run in terminal' and when you just run it, for some reason it doesn't work.  I feel as though maybe I need to write a shell script, but I don't really know how, or if that is the correct direction to take.

Any help would be appreciated,
Brian
Try setting up a symbolic link:
```
sudo ln -s /path/to/matlab /usr/local/bin/matlab
```
(replace path/to with the location of the matlab folder of course, e.g. /opt/matlab/matlab)
Then running the "matlab" command should work. If it does create a launcher with that command.

to launch something in a terminal the command is gnome-terminal -e matlab

---

### Post by RomeReactor on 2008-06-28
Hi. When you create the launcher in the menu, fill it out like this:

* Type: Application

* Name: MatLab

* Command: sh -c "cd /path/to/matlab_folder && ./matlab"

* Comments: (Leave empty if you want).

---

### Post by d4ng3r on 2008-06-28
I tried both your suggestions, but to no avail.  When I made the launcher, it seemingly does nothing (usually when you click just 'run' it opens and closes quickly)  and when I type matlab in bash after making the link it says no command found.

---

### Post by karasuman on 2008-06-28
It does work when you CD to the folder and run it, right?  Here's what I do with things like that.

First, make a folder (I call mine shell) that's never going to move, and save shell scripts in it.  Then, in whatever text editor, type what you'd have to type in the terminal to do what you're trying to do.  For instance, here's the one that launches Byakhee for me:

> cd .wine 
cd drive_c 
cd "Program Files" 
cd bykhe30 
./Byakhee.exe

Then, save it.

Now, open your terminal, CD to the folder you just made, and do 

```
chmod +x ./whateveryounamedyourtextfile
```

Now the file can be executed.  Make a custom application launcher with the command 

```
/home/whoeveryouare/path/to/your/textfileyoujustmade
```

That should do it for you.

I hope that helps.  :)

---

### Post by d4ng3r on 2008-06-28
So the executable file works, but i still need to click 'run in terminal' when I run it.  Is  there any way to put this in main menu.

---

### Post by dizee on 2008-06-28
```
gnome-terminal -e /home/whoeveryouare/path/to/your/textfileyoujustmade
```
should do it. (edit the launcher to this in the menu editor)

there might be an easier way in the menu editor, i think you can right click the entry and tick "run in terminal".

---

### Post by DGortze380 on 2008-06-28
you could write a script to run the program and add it to your PATH, then just create a launcher with the command to run the script.... thats what I do anyways. good luck.

---

### Post by RomeReactor on 2008-06-28
> **d4ng3r said:**
> When I made the launcher, it seemingly does nothing (usually when you click just 'run' it opens and closes quickly)  and when I type matlab in bash after making the link it says no command found.

Please post the 'Command' section of the launcher.

---

### Post by karasuman on 2008-06-28
Assuming you wrote the script like I suggested...  You just want this in the applications menu, right?

Right-click on applications.

This should bring up a menu that allows you to add/remove items from the drop-down menu.  Choose "new item", and this should bring up a box to create an application launcher.  Fill it out as described earlier.

---

