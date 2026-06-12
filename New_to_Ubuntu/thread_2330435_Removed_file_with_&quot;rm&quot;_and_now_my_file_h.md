---
title: "Removed file with &quot;rm&quot; and now my file has &quot;~&quot;"
date: 2016-07-11
forum: New to Ubuntu
---

### Post by eddiefiggie on 2016-07-11
I am learning the command line so bare with me.  (having fun by the way!)

I am trying to determine what the "~" suffix on a file name means.

I created a couple of files with vim...  Messed around with various commands: cat, head, tail, etc....

I then used rm to remove the file:

```
rm -i filename
```

Poof the file was gone...success!!  I used "ls" and confirmed, it was gone (so I thought).

Today I'm messing around again, and with "ls" I saw the file...except it had the tilde "~" appended to it.

What does this mean?

---

### Post by steeldriver on 2016-07-11
At some point you must have edited the file in an editor (such as vi/vim) that saves backup files with the ~ suffix

Then you deleted the original file - but not the backup

---

### Post by oldfred on 2016-07-11
Backups as Steeldriver posted.

 Check for files with tilde
find $HOME -type f -name "*~" -print
This will delete them, but then you have no hidden backups.
find $HOME -type f -name "*~" -print -exec rm {} \;

---

### Post by eddiefiggie on 2016-07-11
Ah ha!  Very helpful thanks!

The journey continues....  ONWARD!

---

