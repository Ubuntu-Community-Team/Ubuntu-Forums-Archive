---
title: "Issue with having icon for a python program"
date: 2009-04-24
forum: Programming Talk
---

### Post by Pollox on 2009-04-24
I have a python program I've worked on with a group, and I'm trying to create a .deb package for it.  The program consists of two .py files and an icon files.  To run the program I run one .py file, which uses the other two files.  I was successful in creating the .deb file (thanks to the guide on here) but when I try to include a shortcut in the gnome menu for the program that executes:
python "/opt/treelink/TreeLink.py"
The program will start with the error message:
Can't load image from file 'treelink_icon.ico': file does not exist.
but otherwise runs normally (except for the lack of an icon)

The icon is implemented like this in the code (using wxpython):
iconFile = "treelink_icon.ico"
icon = wx.Icon(iconFile, wx.BITMAP_TYPE_ICO)

This is the same error I get if I am in terminal, and not in the current working directory of the program files, and then attempt to execute the program by providing the path the file (i.e. python /path/to/file/file.py ).

How can I fix this error?  Is it simply a matter of putting the icon file in the right directory (right now everything gets put in a folder in the /opt directory upon install)?  Or is it some change I need to make to the code (in which case I would preferably like to make this change in a way that keeps it cross-platform).

---

### Post by ajackson on 2009-04-24
The quick and dirty way (assuming the icon and py file are in the same directory or the icon file is in a directory off that directory) is to use
```
os.path.dirname(__file__)
```
To return the directory that you py file is in and then append the icon file name using os.path.join

---

### Post by unutbu on 2009-04-24
Building on ajackson's suggestion, perhaps:
[PHP]os.chdir(os.path.dirname(__file__))[/PHP]

---

### Post by Pollox on 2009-04-24
Thanks.  I went with the join option and it worked well (although the chdir trick is also a neat idea).

---

