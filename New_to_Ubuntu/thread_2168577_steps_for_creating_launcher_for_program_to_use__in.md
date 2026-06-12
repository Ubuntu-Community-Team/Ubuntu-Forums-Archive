---
title: "steps for creating launcher for program to use  in 13.04 ubuntu"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by newblank25 on 2013-08-18
can some help explain the steps for creating launcher for program to use  in 13.04 ubuntu. thx

---

### Post by kostkon on 2013-08-18
There are applications in the software centre that allow you to do that easily and without much fuss.

The other way is to make your own custom .desktop file and place it in ~/.local/share/applications (~/ means your home folder).

---

### Post by deadflowr on 2013-08-18
There's the easy way and there's the hard way.

The easy way is to open up the dash and type main menu, then launch said program.
Then in main menu click on add new item.
Then fill out the entries.
Name
Command
Comment(optional)
If you want to personalize the icon click on the icon box in the left corner and select your new icon(wherever is may be).
You should have a new launcher in your applications.

The hard is is to manually make one from scratch.
Open up gedit, or text editor of choice, and fill out these lines
```
[Desktop Entry]
Name = Your Program Name
Exec =  Command used to launch the App
Type = Application
Icon = Whatever you want
Terminal = False
Comment = Whatever you want
Categories = What kind of app it is ie, Games, or Office, or Graphics

```

Then save the document with .desktop as the extension and place it in the ~/.local/share/applications folder.

---

### Post by Morbius1 on 2013-08-18
Does this no longer work with Unity:

Install the following package:
```
sudo apt-get install --no-install-recommends gnome-panel
```
Then run the following command:
```
 gnome-desktop-item-edit ~/Desktop/ --create-new
```
That should launch a GUI that some of you old timers might remember from the golden age of Linux:
[ATTACH=CONFIG]245458[/ATTACH]

---

### Post by deadflowr on 2013-08-18
Yep Morbius1, that will still work with unity.
And that command will still put the launcher on the actual desktop instead of the side launcher if that is your wish.

In fact anything you put in the users Desktop folder will be show on the desktop.(except hidden files, of course)

---

