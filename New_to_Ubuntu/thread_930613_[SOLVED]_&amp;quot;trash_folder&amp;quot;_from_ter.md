---
title: "[SOLVED] &amp;quot;trash folder&amp;quot; from terminal"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by garyed on 2008-09-26
Is there a way to access the trash files from the terminal instead of the gui?

I ask this because I'd also like to delete files to the trash folder in the terminal for safety reasons. This way a simple script could move unwanted files to trash while working in terminal & they would be easy to recover if I made any mistakes.

---

### Post by cmat on 2008-09-26
Here is a helpful thread related to the topic. Good luck. 

[http://ubuntuforums.org/showthread.php?t=837074](http://ubuntuforums.org/showthread.php?t=837074)

---

### Post by Benic on 2008-09-26
Look in /home/<your home folder>/.local/share/Trash/files.

---

### Post by garyed on 2008-09-26
I've searched my whole drive & the only Trash folder is in my Thunderbird mail folders.
I can't find it under  ~/.local/share/

```
 sudo find / -xdev -iname Trash 
```

---

### Post by Benic on 2008-09-26
The .local folder is hidden, it might explain why you can't find it.

This thread explains different options to see hidden files in the terminal: [http://ubuntuforums.org/showthread.php?t=625183](http://ubuntuforums.org/showthread.php?t=625183)

---

### Post by Benic on 2008-09-26
I tried your command and I found:

/root/.local/share/Trash/ (the root trash file)
/home/bm/share/Trash/

Normally, you should have at least two trash folders, one for root and one for every user.

---

### Post by lian1238 on 2008-09-26
Trash items are stored at the root directory of the place they used to be. For example, if you delete an item from your desktop, it'd be move to "~/.Trash/". But if it's on another drive, it'd be moved to the folder ".Trash-yourname/" in that drive. To get a whole list, look in the file "~/.gnome/gnome-vfs/.trash_entry_cache" and you'll see two columns. The folder in the 2nd column keeps the deleted files from the directory listed in the 1st column. This list excludes "~/.Trash/".

---

### Post by garyed on 2008-09-26
I found mine in ~/.Trash.
The find command searched through hidden folders but I didn't think the folder itself was hidden so I needed to use "./Trash" in the command.
Thanks to all for the help.

---

### Post by styfle on 2008-09-26
I know this is solved but this thread doesn't explain how to delete files using terminal
Can someone please tell me how to do that?

---

### Post by garyed on 2008-09-26
> **styfle said:**
> I know this is solved but this thread doesn't explain how to delete files using terminal
Can someone please tell me how to do that?
This will move the file into the trash bin assuming that is the correct path for the trash folder.

```
 mv filename ~/.Trash 
```

I also wrote a bash script that does it.
I named the script "trash" so all I do is:
```
 trash filename
``` 
That moves the file to Trash instead of plain deleting it.
Here's the script:
** Warning - this script only works on one file at a time 
  Moving more than one file at a time can cause permanant deletion. ***
  
#!/bin/bash
# This is will move files to Trash folder instead of deleting.
 if [ -f $1 ];
then
mv $1 /home/gary/.Trash/
else
echo " $FILE does not exist or the path is incorrect"
fi

---

