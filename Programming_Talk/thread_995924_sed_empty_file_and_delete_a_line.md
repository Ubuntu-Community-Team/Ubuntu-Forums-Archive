---
title: "sed: empty file and delete a line"
date: 2008-11-28
forum: Programming Talk
---

### Post by PryGuy on 2008-11-28
Good day, people!
Silly question, I know, but I'm all mixed up
I have a file with a single line, I have to replace the line with my own line and I do not care what the line is, I mean it can be anything. Pretty simple thing but it got me confused... :(

EDIT: sudo cat "text" >> file says 'permission denied' :(

---

### Post by geirha on 2008-11-28
```
sudo echo "text" >> *file*
``` does seem logical, but the « >> file »-part is handled by the shell, which is running as your user. Only echo gets run as root.

To append a line of text as root to a file, you can use tee
```
echo "text" | sudo tee -a *file*
```

If you want to overwrite the file so it only contains your new line, use tee without the -a option.
```
echo "text" | sudo tee *file*
```

---

### Post by PryGuy on 2008-11-28
I know this, it says "Permission denied" though I make it with sudo :(

---

### Post by geirha on 2008-11-28
> **PryGuy said:**
> I know this, it says "Permission denied" though I make it with sudo :(

I didn't make my point clear enough. ```
sudo echo "text" >> *file*
``` will NOT work, because the text is appended to the file by the shell, not by the echo command, and the shell is still being run as your user, thus you will not be able to append to the file unless you have write-permission to it.

In other words use tee as described above, or run a shell as root to do it:
```
sudo bash -c 'echo "text" >> *file*'
```

---

### Post by ghostdog74 on 2008-11-28
if you want to replace the line, use > instead of >>

---

### Post by PryGuy on 2008-11-29
Got it now, thanks!

---

