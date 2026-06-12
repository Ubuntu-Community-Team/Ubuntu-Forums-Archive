---
title: "Auto compress and upload"
date: 2007-09-25
forum: Programming Talk
---

### Post by Feel-Ya on 2007-09-25
Hello!
I'm new to linux and I'm an owner of Counter-Strike public server.
The server runs okay and it is recording game replays, and for Half-Life it's demos.
They are stored in one directory, but I need them to be compressed (each demo in seperate archive) and after, uploaded to the webserver.

Could anyone tell me how to do this, or it would be much better if you could provide me with this kind of script, where I just have to change the directories. 
Thanks in advance!

---

### Post by Feel-Ya on 2007-09-30
Umm.... BUMP?

---

### Post by cwaldbieser on 2007-09-30
> **Feel-Ya said:**
> Umm.... BUMP?

I think you need to provide more information.  For example, how are you manually doing the compress and upload at this time?

---

### Post by Feel-Ya on 2007-09-30
Well.... I just take the demo file, compress it with *.zip and then just move to webpage folder.

---

### Post by cwaldbieser on 2007-09-30
> **Feel-Ya said:**
> Well.... I just take the demo file, compress it with *.zip and then just move to webpage folder.

Well, if you are simply compressing and moving the files to another directory on the same server, why not something like:
```

ZIPFILE=/path/to/destination/archive
SOURCEFILES="file1 file2 file3 etc."
zip "$ZIPFILE" $SOURCEFILES

```

---

