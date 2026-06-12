---
title: "how to associate a file type with an application?"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by mzimmers on 2012-03-24
This isn't so much an ubuntu-specific question, but...in Mac OS X and Windows, there's the capability of associating a particular file extension with an application. When you click on a .pro file, for example, it will open it with Qt Creator (assuming you have that installed). How do I do the equivalent thing in UNIX/ubuntu?

---

### Post by ajgreeny on 2012-03-24
> **mzimmers said:**
> This isn't so much an ubuntu-specific question, but...in Mac OS X and Windows, there's the capability of associating a particular file extension with an application. When you click on a .pro file, for example, it will open it with Qt Creator (assuming you have that installed). How do I do the equivalent thing in UNIX/ubuntu?
Right click on a file of that type in the file manager (nautilus) and choose **Properties ->Open with-** tab.  There you can set it to open with whatever you choose.

---

### Post by mzimmers on 2012-03-24
OK, but Qt Creator doesn't show up in the list of applications.

---

### Post by evilsoup on 2012-03-24
Right-click on one of the files in question (say, an MP3), click 'properties'; in the properties window, go to the 'Open With' tab and... well, the rest is pretty self-explanatory.

If you, for example, set one MP3 to be opened by the program VLC; then all MP3s would be opened by VLC when double-clicked.

This opens according to filetype, however, *not* extension (if anyone knows how to do that, it would be nifty to share).

> OK, but Qt Creator doesn't show up in the list of applications.     Click on the button labelled 'Add'; this will bring up a long list of programs. If you know the terminal command to launch QT Creator, then you can use the 'Use a Custom Command' option.

EDIT: A quick [google search]("http://dev.man-online.org/man1/qtcreator/") tells me that the command should be 
[B]qtcreator

[/B]So you should be able to type 'qtcreator' (without the quotes) into the 'custom command' box.

---

### Post by mzimmers on 2012-03-24
> **evilsoup said:**
> This opens according to filetype, however, *not* extension (if anyone knows how to do that, it would be nifty to share).

Oh...in that case, I probably don't want this after all, as the .pro file is of type "plain text document."

And...where is this "custom command" box? I don't find that in the properties window(s).

---

### Post by evilsoup on 2012-03-24
Here, I made a screenshot that should help:

[IMG]http://i.imgur.com/JqTE1.jpg[/IMG]

EDIT: I know that what you are looking for is possible, because adding .cbr to the end of the filename for a RAR archive makes the system treat it differently (without the extension it is opened with the archive mounter, with the extension it is opened with evince)... but unfortunately I don't know how to replicate this.

---

### Post by forrestcupp on 2012-03-24
There is no more Custom Command in Ubuntu 11.10 and later. Now if you want to add a custom command you have to go through the hassle of manually creating a .desktop file and putting it in ~/.local/share/applications. 

I have no idea why they would make an upgrade be harder to do.

---

### Post by mzimmers on 2012-03-24
Ahh...that explains why my properties window wasn't looking/acting like evilsoup's.

I hesitate to ask, but...what is involved in making this .desktop file?

---

### Post by JKyleOKC on 2012-03-25
You create desktop files with a text editor such as gedit or nano, save them with an extension of ".desktop", and make them executable. 

Here's a sample from my own system for a special script that I wrote. The key items are "Name=" which specifies how the program is shown in menus or on the desktop, "Exec=" which is the CLI command to launch the program (with full pathname, not just the program name itself), and "Icon=" which specifies the icon to associate with it. You can simply copy the other lines, except for "Terminal=" which should be true if it's a CLI program and false if it runs in the desktop.```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=Watcher
Comment=Notify when FTPed file arrives
Categories=Application;
Exec=/home/jk/bin/watcher
Icon=gnome-fs-network
Terminal=true
StartupNotify=false

```It's important NOT to leave spaces on either side of the "=" character of each line.

Someone else will have to tell you exactly where the file should be saved; I'm on an older version and use Xubuntu rather than Ubuntu, but the spec for desktop files themselves hasn't changed.

---

### Post by ajgreeny on 2012-03-25
I had absolutely no idea that ubuntu/gnome-3/unity had "progressed" so far that a simple thing like a custom command box has now gone from this option in file properties.

How on earth can gnome devs remove this sort of thing; or is it simply a case of not quite being there yet, like a lot of other configuration options?

I am so glad I still run 10.04!!

---

### Post by forrestcupp on 2012-03-25
> **JKyleOKC said:**
> 
Someone else will have to tell you exactly where the file should be saved; I'm on an older version and use Xubuntu rather than Ubuntu, but the spec for desktop files themselves hasn't changed..desktop files go in ~/.local/share/applications in your /home folder.

And remember, when you name the scripts to name them with the .desktop extension.

> **ajgreeny said:**
> I had absolutely no idea that ubuntu/gnome-3/unity had "progressed" so far that a simple thing like a custom command box has now gone from this option in file properties.

How on earth can gnome devs remove this sort of thing; or is it simply a case of not quite being there yet, like a lot of other configuration options?

I am so glad I still run 10.04!!Hopefully, they just haven't gotten Gnome3 there yet, and they will. That's a pretty stupid thing to intentionally remove.

---

### Post by Morbius1 on 2012-03-25
I will be the first to admit that this is a goofy thing to do if all you want to do is create one custom association but if you do this sort of thing all the time you might consider installing XFCE's File manager, Thunar. It has all sorts of advanced capabilities ;)

---

### Post by forrestcupp on 2012-03-25
> **Morbius1 said:**
> I will be the first to admit that this is a goofy thing to do if all you want to do is create one custom association but if you do this sort of thing all the time you might consider installing XFCE's File manager, Thunar. It has all sorts of advanced capabilities ;)

Thank you for that suggestion. I haven't used Thunar for a long time. I might have to check it out again.

---

