---
title: "MonoDevelop - System.Diagnostics.Process.Start()"
date: 2008-09-10
forum: Programming Talk
---

### Post by pdq on 2008-09-10
I am toying with MonoDevelop.  I tried System.Diagnostics.Process.Start() and gave it a path to a .jpg file.  In a windows environment this would actually open up the image in with the default app that is assigned to .jpg.  

In Ubuntu, nothing happens.  What's the deal?

---

### Post by swegner on 2008-09-10
Windows employs some "magic" to open the default application for known filetypes.  From a command line, you can employ the same magic with

```
start myfile.txt
```

In the above example, notepad will generally be used.

Linux doesn't have the same magic, particularly because it doesn't use filename extensions to determine filetype.  To spawn a process to open a file, specify an appropriate program.  To open a JPEG image for viewing, you might consider "Eye Of GNOME", using the command "eog".

Does this answer your question?

---

### Post by qqqqqqqqq9 on 2008-09-21
Linux doesn't have the same magic, particularly because it doesn't use filename extensions to determine filetype.  

This doesn't seem to be true anymore for eog. After renaming a file from file.jpg to file.png eog states, that this isn't a png-file and refuses to open it.

---

### Post by swegner on 2008-09-21
Hmm, this does seem to be the case with eog, but must happen at the application-level.  This certainly isn't the case for Linux in general:

```
$ file pic.jpg 
pic.jpg: JPEG image data, JFIF standard 1.02
$ cp pic.jpg pic.png
$ file pic.png 
pic.png: JPEG image data, JFIF standard 1.02
```

---

### Post by Greyed on 2008-09-21
Linux does have some of the similar magic.  The problem is that it is up in the DE layer and how they handle the different file types.  Since Mono probably doesn't know (or care) which DE it is operating under (if any) it does not take advantage of those capabilities.

TBH it really is something that should be moved down in the OS to someplace which is application/DE agnostic.

---

