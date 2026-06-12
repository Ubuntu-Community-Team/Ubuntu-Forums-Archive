---
title: "script that compares media"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by shortridge11 on 2008-08-14
i have 2 media libraries (all music) and i wanted to make a script that would compare them and fill them both in so they both have the same files.  How would i go around writing it?

---

### Post by cosine352 on 2008-08-14
may be you can try [rsync]("http://www.sanitarium.net/golug/rsync_backups.html")

---

### Post by LowSky on 2008-08-14
[http://www.ubuntugeek.com/conduit-synchronize-your-data-in-easy-way.html](http://www.ubuntugeek.com/conduit-synchronize-your-data-in-easy-way.html)

---

### Post by cariboo on 2008-08-14
You could have a look here:

[http://linux.byexamples.com/archives/143/compare-two-directory-listings/](http://linux.byexamples.com/archives/143/compare-two-directory-listings/)

This looks like what you are looking for.

I just tried the suggestions in the above link and they don't work the way I expected, your best bet is to use the diff command.

```
diff /dir1 /dir2
```

If you want to pipe it to a text file:

```
diff /dir1 /dir2 > differences.txt
```

Jim

---

### Post by shortridge11 on 2008-08-14
thanks, i'm going to try Conduit.

---

### Post by ace007 on 2008-08-14
rsync will work wonderfully here.  In my opinion, there is no better sync tool.

usage: 
```

rsync -ruvt --progress /media/is/here /location/to/receive

```

You can run this so that all the files that dont exist in the second directory that are in the first are created in the second. And then swap the directories and run it again so that the first one now has all the same as the second.

type:
```

man rsync

```
 to find out what the uvrt arguments mean. 

ALSO, you can add the "n" flag as an argument ("uvrtn" replaces "uvrt") to just do a dry run. It will print to the screen what files would be copied, but it wont move a thing.

---

