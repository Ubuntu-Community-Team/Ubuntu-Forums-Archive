---
title: "Shortcuts on Desktop"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by arriflex6 on 2014-05-01
Hello folks, I'm new to Ubuntu and have only been using it for a few days but I love the interface.  I can't seem to get shortcut icons onto the desktop by dragging them from the DASH.  I get an error message saying it can't be done.  I'm using Version 14.04 64 bit.  Also I know I need to do a lot of studying into this OS as it is quite different from MS Windows, but how do you change the theme from one of the 3 default ones to one that I can get off the interweb?  I daresay I'll be back with more questions as I get into it more.  I've gone the Linux route because I don't like the look of Windows 8.

---

### Post by ajgreeny on 2014-05-01
The whole idea of the launchbar and dash is that it avoids the need for a desktop cluttered with icons for launchers.
However it is possible to add them if you really want to.

You will need to copy the correct **application.desktop** file from **/usr/share/applications **either with nautilus or using the cli
But why not just open the application you want to add which will put its icon on the launchbar, and with the application still open, right click on the icon and choose "Lock to launchbar"

---

### Post by arriflex6 on 2014-05-01
Yes thanks I see your point.  I guess it's migrating from Windows that is making me want icons on the desktop.  I'm not up to speed with all this Nautilus or CLI (what is that?)

---

### Post by pfeiffep on 2014-05-01
> **arriflex6 said:**
> Yes thanks I see your point.  I guess it's migrating from Windows that is making me want icons on the desktop.  I'm not up to speed with all this Nautilus or CLI (what is that?)
[Nautilus]("https://help.ubuntu.com/community/NautilusScriptsHowto") is a file explorer providing functionality similar to Windows Explorer
[CLI]("https://help.ubuntu.com/community/UsingTheTerminal") = command line interface which can be accesses by these keys simultaneously ```
Crtl-Alt-t
```Nautilus is a GUI - graphical user interface

---

### Post by joeblow9104 on 2014-05-05
When I  right-click on what's open in my "taskbar" I only see the following options:
Raise
Restore
Maximize
Iconify
Move to workspace ( what does this mean anyway?)
Close Window

and therefore, I'm still stuck without knowing how to make desktop shortcuts or "taskbar" (what it's called in windows) shortcuts...

Sorry for the n00b-ness of this, but I've been using linux for only a few hours now.

---

### Post by Paulgirardin on 2014-05-05
Hi and welcome to Ubuntu.

By "taskbar" are you refering to the laucher on the left side of the desktop?
If so,when you click on one of the icons there you should get a quicklist showing various options such as 'open a window','quit' or 'lock to launcher',depending on the application.On 'Files' the file browser you will also get the current bookmarked directories as well,for instance.

I've never seen the options you list.
In the Unity Desktop,as explained by a previous reply,the default action is to lock a desired application to the Launcher and to open and close it from there,not to place icons all over the desktop as in more primitive OS's.
This allows you to open an application with the mouse or by tapping the Super Key ( the one with the windows graphic on most keyboards) and typing a description (usually only three letters are needed) and hitting <enter>.Or by holding the Super Key down for 2 seconds an overlay appears on the launcher icons,numbering them.By hitting the relevant number (still holding the Superkey) then <enter> ,the application will open.

Applications can be dragged from the dash to the launcher to fix them there or they can be opened from the dash
and once an application is open a temporary icon will appear in the dash.This can be made to stay permanently in the laucher by right clicking the launcher and selecting 'lock to launcher'.

Workspaces are different desktops that you can open other applications on and switch back and forth to,rather than having everthing squeezed into a single desktop.With an application such as Unity Tweak you can set that number of workspaces to as many as you want.It used to be 36 but I just tried a 20 x 20 grid and it worked.You enable workspaces by typing 'appearance' in the dash and opening the appearance application,selecting the behaviour tab and checking the enable workspaces box.You access the workspaces by clicking the workspace switcher in the launcher or by ctrl-alt-arrow shortcuts.The default number of workspaces is 4.

Here are some tutorials explaining Unity:
[http://www.howtogeek.com/113330/how-to-master-ubuntus-unity-desktop-8-things-you-need-to-know/](http://www.howtogeek.com/113330/how-to-master-ubuntus-unity-desktop-8-things-you-need-to-know/)
[URL="http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial"]http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial



[/URL]

---

### Post by joeblow9104 on 2014-05-05
ok, I'm sorry - I forgot to mention that I'm using lubuntu...
once again, sorry for newbness - please bear with me!

---

### Post by deadflowr on 2014-05-05
For the record, anything in the user's Desktop folder will show up on the desktop.
Just open the file manager "Files" and look for the folder Desktop.
application launchers are normally placed in the system folder /usr/share/applications.
To get to the usr folder, click on "Computer" in the left pane of the file manager.
You can't move the launchers, but you can copy/paste them.
Since it basically makes a file, it loses the apps quicklist functions(that's the right click on the launcher icon and see extra thing it does) and instead only lists what a normal file would.

It's not an intended design, but rather a quick workaround, so far.
Unity's design, as stated, is to keep apps and other functions to the sides, giving you no need to keep jumping around/ opening /closing windows to access something.

The launcher bar acts like a pseudo-task manager.
You can click on an open app and give it focus, and move back and forth between different apps as well.

A few interesting functions are listed in a help screen, to get that press and hold the super key (AKA the Windows button on Keyboard).

Edit: I see I've pretty much posted a re-hash of what ajgreeny posted.:lolflag:

---

### Post by deadflowr on 2014-05-05
> **joeblow9104 said:**
> ok, I'm sorry - I forgot to mention that I'm using lubuntu...
once again, sorry for newbness - please bear with me!

Please start your own thread, make sure to mention you're on Lubuntu.

---

