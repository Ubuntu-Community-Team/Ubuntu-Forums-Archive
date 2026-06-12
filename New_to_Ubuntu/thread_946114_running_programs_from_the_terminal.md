---
title: "running programs from the terminal"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by a_weasel on 2008-10-13
How do i figure out how to run a particular program from the terminal?

For example, i have a .ps file that I can view using document viewer. How would i do this in the terminal?

Also, I can't even find document viewer anywhere in my applications menu (i'm 100% sure i DO have it)...where would i go just to open document viewer?

---

### Post by b0b138 on 2008-10-13
evince /path/to/file.ps  

maybe?

---

### Post by OutOfReach on 2008-10-13
Just type in the application name, say if you wanted to launch firefox:
```
firefox
```

---

### Post by RequinB4 on 2008-10-13
As b0b138 mentioned above, you need to run
```

evince ~/path/to/file.ps

```

In this case, your file.ps isn't executable - when you double click on it, you're telling another program (evince = document viewer) to open the file.  The terminal code above does the same things where ~/path/to/ is the directory the file is in.

---

### Post by t0p on 2008-10-13
*evince*  is called "Document Viewer" in Gnome.  No way of knowing that other than by knowing it.  Just like you ain't gonna know "File Manager" in Gnome is really called *nautilus* unless you know it already.  Pretty stupid if you ask me.

I don't know whether it's Gnome or Ubuntu responsible for this idiocy...

But I do know good old Linux can save us from it.  Thanks to the good old command line.  And **apropos**.

```
t0p@xxxx:~$ apropos "document viewer"
evince (1)           - GNOME document viewer
t0p@xxxx:~$  apropos "file manager"
nautilus (1)         - the GNOME File Manager
t0p@xxxx:~$ 


```

---

