---
title: "Open with Gnome Text Editor"
date: 2007-01-30
forum: Outdated Tutorials &amp; Tips
---

### Post by pride_chang on 2007-01-30
**Hi All !**
I am very new to linux, this is my first post here, though I am posting a How-To here :D 
It's because I am a quick learner.
Here's a small How-To for those who want to view files in Gnome Text Editor or gedit.
**I will tell you step-by-step, how to add "Open With Gnome Text Editor" function on right clicking any file.**

First copy this and paste into Gnome Text Editor/gedit
You can run gedit by typing gedit in terminal.

```

#!/bin/sh

# Opens files with gedit

gedit $1

```

Then save it to /home/username/.gnome2/nautilus-scripts/ as OpenWithGedit
**NOTE : Replace username with your username** :) 
Then navigate to /home/username/.gnome2/nautilus-scripts/
**NOTE : Replace username with your username** :) 
Then right on OpenWithGedit and click Properties, in Permissions tab, check "Allow executing file as program" and then click "Close"

That's it ! 
Right click any file, you will see, "Scripts" menu, move your mouse onto this, you will see "OpenWithGedit". Congrats ! :D 

**UnInstalling is easy, just delete this file.**

:guitar: 

Remember, I am newbie :)


**TESTED on UBUNTU 6.10 EDGY**

---

### Post by pride_chang on 2007-01-31
Did I miss something ? :(

---

### Post by stalefries on 2007-01-31
Um, this isn't much of a howto. You show how to open files by making a Nautilus script. Technically, gedit should already be in the right-click menu. I'm not trying to be mean or anything, but this is not really much of a howto. 

Also, if you want to open any file with the default program, you can do gnome-open $file in the commandline, and it will just work.

---

### Post by pride_chang on 2007-01-31
:D
No doubt, you are right, I thought maybe this poor guy can help beginners :D
As Linux is FREE, I should help everything I know, for FREE :D

---

