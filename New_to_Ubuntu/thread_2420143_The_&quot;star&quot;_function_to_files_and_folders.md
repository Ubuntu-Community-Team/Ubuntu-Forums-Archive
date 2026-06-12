---
title: "The &quot;star&quot; function to files and folders does not work"
date: 2019-05-30
forum: New to Ubuntu
---

### Post by josleo on 2019-05-30
Well, I have this simple problem. From the videos I've seen, in Ubuntu 19.04, there is an option to highlight a folder or file using a "star" system. What's more, I even have a folder called "starred", which was created automatically. However, on my computer, right-clicking on a file or folder does not give me the option to star it. Do any of you know why I can't highlight the files as I should?

---

### Post by TheFu on 2019-05-30
This is not a normal Linux capability, so it must be specific to 1 program.
Is this a file manager or some other program?
You can use **top** to figure out the real name of the program.

---

### Post by kpatz on 2019-05-30
Are you on Ubuntu 19.04 (with Gnome, not something else like Xfce), and in the Nautilus file manager?  I think this is where the starring option is.

I'm downloading 19.04 to install in a VM now, so I'll see if I get the starring option.

EDIT: I get it on 19.04 live CD... right click a folder and it should appear 2nd from the bottom on the file menu... right above Properties.  Note that you have to create your own folder or file... it won't let you star a default folder like Documents or Home.

EDIT 2:  Files and folders in Home don't give me the star option, even if I create a folder in Home, go to it and create another within, but if I create files or folders in Documents, then the star option appears.  Not sure why.  But try creating a folder or file under Documents and see if the Star option appears.

EDIT 3: Starring has some issues.  [https://gitlab.gnome.org/GNOME/nautilus/issues/243](https://gitlab.gnome.org/GNOME/nautilus/issues/243)

EDIT 4: I'd just skip this, create your own starred folder and symlink your favorite files there.

---

### Post by josleo on 2019-05-30
Thanks for the support! I was able to star some folders, but some others don't. So I just starred the folders that I could, and then I could access the archives I wanted

---

