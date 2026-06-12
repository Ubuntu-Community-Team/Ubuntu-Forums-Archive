---
title: "[SOLVED] How do I open RAR files?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by keiichidono on 2008-07-15
I don't know of a program that unzips RAR archives in Linux that is easy to use and good. I've installed 7zip from Add/Remove and it doesn't do anything/work. I've heard about unrar but it's command-line only and I'm not messing with that. Does anyone have any suggestions, please?

---

### Post by appi2012 on 2008-07-15
Does archive manager not work? Try double clicking them, or selecting Open With ... Archive Manager

---

### Post by mikewhatever on 2008-07-15
Search for 'unrar' package in synaptic and install it.

---

### Post by keiichidono on 2008-07-15
Archive manager doesn't work with .rar's. Also, i heard that unrar was CLI only so i want something with a GUI or that is at least easy to use.

---

### Post by Pro-reason on 2008-07-15
> **CalvinB said:**
> I don't know of a program that unzips RAR archives in Linux that is easy to use and good. I've installed 7zip from Add/Remove and it doesn't do anything/work. I've heard about unrar but it's command-line only and I'm not messing with that. Does anyone have any suggestions, please?

Installing backends such as gzip, bzip2, rar, unrar, 7za and lzop, etc., allows two things: (1) it allows you to extract things on the command line; (2) it allows front-ends such as file-roller and Ark to extract them with a graphical interface.

I personally install all such utilities as soon as I install a new Linux distro.  I don't want to be unable to uncompress any given archive.

---

### Post by RKCole on 2008-07-15
It appears as if [PeaZip]("http://peazip.sourceforge.net/index.html") supports extraction of RAR files.  It seems as though they have a DEB package on the download page.

Hopefully this will be of some help to you.

Take care.

---

### Post by Vadi on 2008-07-15
Click [here]("apt:rar") to install rar support. After that, you'll be able to double-click, right-click, and do anything you like with them, just like other archives!

---

### Post by cariboo on 2008-07-15
I've got unrar installed and file-roller opens rar archives with no problem. Don't be afraid of command line programs, as most of the time at least you know it is working, sometimes with a gui you never know if it is working properly or not. To find out how a command line program works, in a terminal type:

```
man <appliction>
```

This will tell you more then you need to know about the particular application. In the above example <application> is the app you want to know about.

Jim

---

### Post by mikewhatever on 2008-07-15
> **CalvinB said:**
> Archive manager doesn't work with .rar's. Also, i heard that unrar was CLI only so i want something with a GUI or that is at least easy to use.

Unrar package enables the default gnome archive program, File Roller, to view and unpack rar archives using it's standard GUI. Couldn't be simpler then that.

---

### Post by ByteJuggler on 2008-07-15
> **Pro-reason said:**
> Installing backends such as gzip, bzip2, rar, unrar, 7za and lzop, etc., allows two things: (1) it allows you to extract things on the command line; (2) it allows front-ends such as file-roller and Ark to extract them with a graphical interface.

I personally install all such utilities as soon as I install a new Linux distro.  I don't want to be unable to uncompress any given archive.

Just in case the above isn't obvious enough:  Installing "unrar" will enable the GUI to extract rar files too.  Just install the package and you're done!

---

### Post by keiichidono on 2008-07-15
Ok, thanks for the help guys. I installed unrar (non free version) and i also installed rar support using the link above. It now works, thanks! I would l ike to note for anyone viewing this looking for help, Comix is also good for peeking into .rar files. EDIT: It seems the RAR thing is shareware, I'm gonna uninstall it and see what happens. EDIT: It seems to be WinRAR for Linux, so instead of calling it LinRAR RAR labs called it RAR. I'm pretty sure it will keep working after 40 days but i don't want this on my computer so i'll see how unrar does by itself.

---

