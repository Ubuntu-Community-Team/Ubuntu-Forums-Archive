---
title: "How to set launch arguments in an executable or link."
date: 2012-11-10
forum: New to Ubuntu
---

### Post by Firetaffer on 2012-11-10
Such as this in windows: 

[IMG]http://i.imgur.com/Ap8Wd.png[/IMG]

Right clicking and selecting "Properties" doesn't come up with anything remarkably helpful. I've actually worked around this using bash scripts but that seems a bit unnecessary.

I am using **Ubuntu 12.04**. Thanks in advance!

---

### Post by Impavidus on 2012-11-10
It depends a bit on which system you'e using. In xubuntu, which I use, for programs launched from the menu, you first open the properties of the main  menu (it's a bit difficult to reach, you may have to open the properties of the panel and select the menu from there), then navigate to the starter you want to edit and select properties again. If the launcher is on the panel you can select "properties" directly and then choose "edit". I am sure there must be an easier way, but this works.

In other systems it will be different, but in all cases you have to edit the launcher for the program, not the executable itself, nor a symlink to it. It contains a field named "command", which contains the command to launch the program. This is the name followed by its command line arguments.

I think confusion may come from the fact that windoze automatically converts symlinks to executables on the desktop/in menus to launchers, although I'm not sure about that. I haven't used windoze in years.

I've included a screenshot indicating the path through the menus. It's in dutch, but the icons speak for themselves.

---

### Post by Cheesemill on 2012-11-10
For applications that are installed on your system you can edit the appropriate .desktop file which you will find in /usr/share/applications. For example:
```
gksudo gedit /usr/share/applications/firefox.dektop
```Edit the line that begins like this:
```
Exec=
```

If you want a graphical method of achieving the same thing you can also edit this information using the menu editing application called [alacarte]("apt://alacarte").

---

### Post by Firetaffer on 2012-11-10
> **Cheesemill said:**
> For applications that are installed on your system you can edit the appropriate .desktop file which you will find in /usr/share/applications. For example:
```
gksudo gedit /usr/share/applications/firefox.dektop
```Edit the line that begins like this:
```
Exec=
```If you want a graphical method of achieving the same thing you can also edit this information using the menu editing application called [alacarte]("apt://alacarte").

Thanks, what about for executables which are not installed, such as a version of DOSBOX that comes with a game, one which the system cannot see.

I'm trying to make it so that when you double click the DOSBOX link I created (Using Make Link) which was then moved to the desktop, it would use the config that was contained in the game's folder, rather than the DOSBOX link assuming that the working directory is desktop.

Here are some screenshots of what I mean:

[ This screenshot shows what happens when I double click DOSBOX.]("http://i.imgur.com/dMUaF.jpg")

[This screnshot shows what happens when I double click the DOSBOX link on my desktop.]("http://i.imgur.com/aWzWg.jpg")

As you can see the second screenshot shows that DOSBOX does not pick up the config file in the folder, hence it is starting up as if it has no config file. I could fix this by adding some launch arguments, unless there is another way of course.

Thanks in advance!

---

### Post by mcduck on 2012-11-10
What you want is either a launcher, or a script (which you can the link into).

A link is not the same thing as a shortcut on Windows is. Links are filesystem's features that allow the same file to appear in multiple locations, or with different names, while Launchers (like windows Shortcuts) are separate files that contain information about a file or a program, it's location, command used to open it, icon to be shown and so on. (and like you noticed, links don't take you to where the original file or directory is, they behave exactly as if the file or directory was where the link is).

If you want to create a launcher instead of using a shell script, the easiest way is to install Alacarte Menu Editor. After creating a launcher with it, it will appear in the Dash (or any other standards-compliant desktop menu application). If you want, you can the drag & drop it into your desktop.

Alternative way is to create the launcher manually, by creating a text file with the ".desktop" file name extension.If you prefer doing it that way, here's a basic template:
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=
Exec=
Name[en_US]=Application launcher
Comment[en_US]=
Name=
Name[en_US]=Application launcher
Comment=
Icon=
```
(once created, you can right-click the desktop file to access it's properties and edit the settings if you don't want to do it directly from the text editor)

---

### Post by Firetaffer on 2012-11-10
Thanks a lot, I manually created a .desktop file and it works great now!

---

