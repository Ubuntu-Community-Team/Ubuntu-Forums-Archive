---
title: "Create desktop shortcut to home"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Stabback on 2008-08-28
Hey all, stupid quick question.  How does one create a desktop shortcut that opens up the home directory?

Thanks all

---

### Post by Ryadt on 2008-08-28
Just click and drag the home directory to your desktop. :)

---

### Post by imagenius on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Stabback on 2008-08-28
I click and drag the home directory to my desktop and receive an error stating that I cannot move a folder into itself.

---

### Post by ajgreeny on 2008-08-28
Open System >> Configuration Editor (command **gconf-editor** if it is not in your menu) and go to apps>>nautilus>>preferences, and check there is no mark in the **desktop_is_home_dir** entry.  If there is remove it and see if you can drag the icon from nautilus to the desktop again.  I don't know if you will need to log out and in again for it to have any effect.

---

### Post by Dougie187 on 2008-08-28
You can always just make a launcher that has the command
```
nautilus
```
It should open up your home folder.

---

### Post by Therion on 2008-08-28
Install [QuickStart](http://quickstart.phpbb.net/index.php?sid=f23e3738e9951a1ce3c87a7d0673cd07).  

One of the options is it affords you is putting such shortcuts on your desktop, "Home" being one of them.

---

### Post by kukibird1 on 2008-08-28
Hit Alt F2 and type in gconf-editor click on  apps expand nautilus and click on desktop and put a check mark in home_icon_visible.

---

### Post by anotherdisciple on 2008-08-28
> **kukibird1 said:**
> Hit Alt F2 and type in gconf-editor click on apps expand nautilus and click on desktop and put a check mark in home_icon_visible.

+1 This will do what you want.

---

### Post by joeelmex on 2009-06-25
> **kukibird1 said:**
> Hit Alt F2 and type in gconf-editor click on  apps expand nautilus and click on desktop and put a check mark in home_icon_visible.


Thank you!  That worked great and learn something new.

---

### Post by Teutorix on 2009-06-25
ubuntu tweak can do it, it also has many other usefull features.

---

### Post by aeiah on 2009-06-25
if you want other folder locations that arent possible with gconf-editor, you can create a launcher and put the command as either: 'nautilus /path/to/folder' or set the target as a file and just put the folder path in. i use it for my incoming and film folders to have them on my desktop.

---

### Post by mark bower on 2012-10-23
To put a launcher for the home directory on both the top tool bar and desktop,12.04LTS and Gnome Classic, I did the following where my home directory is "/home/rocky".

mouse over the top tool bar
Window-Alt-rtclk>Add to Panel> this opens the list of add to panel options
select Custom App Launcher-create new launcher - this opens the Create Launcher box,
fill in as follows:

	Type:  		Application
	Name:		whatever
	Cmd:		nautilus /home/rocky
	Comment:	whatever

after closing the box the Nautilus applet should appear on the tool bar.  Now drag the applet to desktop and you should have the Nautilus applet on both the top tool bar and desktop.

I do not like unity for how I do business and I see postings where others are migrating away from Ubuntu because of Unity.

---

