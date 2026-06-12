---
title: "How Do I identfy a Drive in PATH"
date: 2008-07-13
forum: Other OS Talk
---

### Post by carib909 on 2008-07-13
I need to copy some files from one location to another on two separate drives using the terminal as I have to do this with the sudo command. How do I specify a file in a folder on a particular drive?

---

### Post by volkswagner on 2008-07-13
What os are you running?  In Ubuntu drives are listed in /media.

You may also run your file manager as root 

sudo nautilus
or
sudo thunar

if you want a GUI

---

### Post by issih on 2008-07-13
As suggested you can run the file manager as root, although you are meant to use gksudo rather than sudo if you are going to launch a gui application.

If you want to do it from the command line its relatively easy though.

All absolute paths start with /, this is the root of your file system. Every mounter drive, every file and diretory is below this somewhere.

So a typical path would be:

/home/dre/Desktop

That would be the path to my Desktop folder (note that the / acts as a path separator to demarcate directories.

It is worth noting that the terminal has a concept of the current working directory (which is displayed in the prompt line in ubuntu) You can also reference paths relative to that location. So if I launched a terminal (which sets the default location as /home/dre) I could then simply use the path:

Desktop

as it is correct relative to my current location (note the lack of a leading /)

You can also use * and ? as wildcards, * matches anything of any length, and ? allows 1 character of any value.

so e.g.

rub* matches any filenames or directories that start with rub
rub? matches 4 letter filenames or directories starting rub.
*.bin matches any files with the extension bin.

Experimenting with the list command (ls) is a good way to get the hang of this.

Once you are happy you can use the copy command cp, to move files from one place to another, note that by default cp will only move files, and will not drill down into directories to copy them or their contents over. you must use "cp -r" (which stands for recursive) to achieve that.

Hope that helps

---

