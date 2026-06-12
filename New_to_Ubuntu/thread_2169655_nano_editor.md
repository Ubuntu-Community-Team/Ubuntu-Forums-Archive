---
title: "nano editor"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by emerson1979 on 2013-08-22
Hello'
               How do you save and close nano?

Thank You

---

### Post by angry_johnnie on 2013-08-22
ctrl + o to save
ctrl + x to close

---

### Post by nerdtron on 2013-08-22
The commands are listed on the nano interface itself. Look at the lower part of the screen.

---

### Post by deadflowr on 2013-08-22
If you just want to save on close ctrl + x is all you'll need.
when you do that, it's first ask to save the modified file, click y and enter and then it'll ask for a filename.
If you've opened an existing file, then the name should be listed, if so, just click enter, and you'll exit nano.

---

### Post by bapoumba on 2013-08-23
Do not forget to save the original and unmodified file with another name if you are editing config files.

---

### Post by vasa1 on 2013-08-23
> **bapoumba said:**
> Do not forget to save the original and unmodified file with another name if you are editing config files.
That is excellent advice. Also, If you look at /etc/nanorc, you'll see that there's a provision to keep a backup file
```
## Backup files to filename~.
set backup

```
This file uses "#" at the start of a line to comment out options. So, if, in your version of /etc/nanorc, the second line is commented out, open the file (after making a copy of the original with a useful alternate name) using ```
sudo nano /etc/nanorc
```

While saving the original is obviously essential, the backup procedure described above will keep just **a single backup** of subsequent edits.

That's why I prefer to use [gedit as my text editor with the doublesave plugin]("http://askubuntu.com/a/308256/25656"). This way, each and every version of files I modify is saved with a unique timestamp in case I want to go back a few or more versions.

I should mention that most of the files I edit are in my home folder and are not system files.

---

### Post by bapoumba on 2013-08-23
Or open nano with the -B switch
```
-B (--backup)
When saving a file, back up the previous version of it to the current filename suffixed with a ~.
```
If you are doing several edits on the same file, vasa1's method works best (thanks, I did not know that).

If editing config files out of /home, nano should be opened with sudo. You can save the original file to your /home for backup or within the system files. In the later case, files may get written over.

---

