---
title: "Would i be able to make a file that i could open which would run a terminal command?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by g2bandrew on 2008-10-22
Ok, lets get something out the way first which'll become clear as you read the rest of this post anyway - i hate terminal.

I have several codes which are on webpages i've bookmarked so i can remember them. I was wondering if there was a way for me to make some file where i could click to open it and it would run that command like it would in terminal. So, for example, if it was "gksudo nautilus", it would open nautilus with the permissions of root user.

Is this possible? Please walk me through it easily.:)

---

### Post by billgoldberg on 2008-10-22
> **g2bandrew said:**
> Ok, lets get something out the way first which'll become clear as you read the rest of this post anyway - i hate terminal.

I have several codes which are on webpages i've bookmarked so i can remember them. I was wondering if there was a way for me to make some file where i could click to open it and it would run that command like it would in terminal. So, for example, if it was "gksudo nautilus", it would open nautilus with the permissions of root user.

Is this possible? Please walk me through it easily.:)

Sure.

Create a new text document.

Create a little bash script.

A bash script to open sudo nautilus would be:


```

#!/bin/bash          
gksudo nautilus

```


Save the file.

Then right-click it, select properties. In the permission tab, tag the "allow executing ..." box.

Then double click the file to launch nautilus as root.

---

Put that document somewhere in your home directory, go to system -> preferences -> main menu and create a new entry.

In the command box, just link to the script. (something like /home/username/script)

Then you can open nautilus as root from your menu.

---

### Post by The Cog on 2008-10-22
Right-click your desktop and choose Create launcher... In the command, put something like **gksudo nautilus** or **firefox [http://ubuntuforums.org](http://ubuntuforums.org)**

---

### Post by billgoldberg on 2008-10-22
> **The Cog said:**
> Right-click your desktop and choose Create launcher... In the command, put something like **gksudo nautilus** or **firefox [http://ubuntuforums.org](http://ubuntuforums.org)**

You can do that, but I presume you would have to leave it on the desktop then and you can't put it in the menu?

---

### Post by The Cog on 2008-10-22
Ah. Right-click the menu (Ubuntu symbol) and choose edit menu. You can add new menu items there. The command is ths same as a desktop launcher command.

---

### Post by billgoldberg on 2008-10-22
> **The Cog said:**
> Ah. Right-click the menu (Ubuntu symbol) and choose edit menu. You can add new menu items there. The command is ths same as a desktop launcher command.

Duh!

It's late (01:03h).

---

### Post by g2bandrew on 2008-10-22
Thanks guys! I thanks'd 2 posts each of yours (just to make it fair).

---

