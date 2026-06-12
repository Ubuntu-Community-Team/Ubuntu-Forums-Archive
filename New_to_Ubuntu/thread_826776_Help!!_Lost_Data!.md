---
title: "Help!! Lost Data!"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by TheDilettante on 2008-06-12
So, I am using Hardy, have been since it was released.  All was well until yesterday, when one of my most important files suddenly disappeared.

The problem is as follows: on a separate partition from any of my OS's I keep my music, downloads and documents.  I keep them in the folders labeled Music, Downloads and Documents, all on the same level of the file system (all are children of the parent directory /mine).  Yesterday I was working on one word document in Open Office.  When I finished I shut the computer down, and later rebooted to discover that Documents, previously a folder containing all of my resumes, thesis work and manuals, was no longer a folder but rather the new name for the one document I had been working on earlier in the day.  When I went to the CLI and asked "file Documents" it told me it was an MS Word file.  I booted into Vista and tried to open the Documents folder, but Vista told me the folder was corrupted (it wouldn't even let me delete the folder).  Interestingly enough, the other folders, Music and Downloads, are all ok... for now.  I am worried though, that whatever has happened, may happen again or spread to the other folders in /mine, and delete all of my music, which would cost a lot to replace.

I'm asking for help - where are my files?!  Please help!

---

### Post by kesman on 2008-06-12
How big is this file? Can you take a copy of it? If you can, place a copy of the file somewhere else and OPERATE WITH THE COPY UNTIL YOU FIGURE SOMETHING OUT!

First, try opening this "file" with nano text editor. I think it should print out garbage, since it's actually a directory, somehow turned into a binary file.

While in terminal, run command
```

ls

```
in the directory where the copy of the file is. Depending on your terminal emulator, it should print out files and directories in different colours, at least xterm does this. Maybe you could also try simply accessing the file with command
```

cd directorynamehere

```
of course replacing directoryname with the name of this mysterious file/directory.

Maybe someone else has suggestions too?

---

### Post by TheDilettante on 2008-06-12
cd Documents yielded "Not a directory"...  It's as if the path to my folder now leads to my MS Word file.  But I checked - I'm not dealing with a link at all.  "Documents" is the new name of MS Word file.

---

### Post by Najand on 2008-06-12
By any chance aren't your documents in "Lost&Found" directory at your partition highest directory?
By the way, what filesystem are you using?

---

### Post by melrom on 2008-06-12
> **Najand said:**
> By any chance aren't your documents in "Lost&Found" directory at your partition highest directory?
By the way, what filesystem are you using?

On that note, check 

```

cd /lost+found
ls

```

---

### Post by Najand on 2008-06-12
Well, as far as /mine is a seperate directory, then it is probably
```

cd /mine/lost&found
ls -al

```

---

### Post by TheDilettante on 2008-06-12
re: lost+found - nothing in /mine/lost+found, or /lost+found
re: filesystem - it's just your standard ext3
re: kesman - it's not a folder gone binary.  it's actually one single word document.


I have no idea what has happened.  I don't know where 300 MB disappears to...  Ubuntu doesn't recognize "Documents" as a folder anymore - its icon is now a Word document icon.  In Vista, however, it is recognized as a folder (albeit a corrupted one).  Do you guys suppose that somehow Ubuntu has simply forgotten that the folder exists?  Or do you think that the data itself is gone forever?

---

### Post by TheDilettante on 2008-06-13
Anyone?

---

### Post by _sphinx_ on 2008-06-13
What if the size of the Word Document which is converted from the Document folder. Is it the same as the Document folder?

---

### Post by TheDilettante on 2008-06-13
The file is 107 kb, which is definitely not the same size as the missing folder.

---

