---
title: "nedd script: delete files older than $TIMEVAR"
date: 2008-06-04
forum: Programming Talk
---

### Post by jo.angel on 2008-06-04
Hello out there!

Ok, Ok, I admit it...
I am not a skilled shell scripting dude ...

Can anyone of you give me a line for a shell script to delete all files in a given directory ($DIR) older than x days ($TIMEVAR)?

That'll be so nice!
Cheers in advance,

jo.angel

---

### Post by geirha on 2008-06-04
```

find "$DIR" -type f -mtime +$TIMEVAR -ls

```
If the files that command lists looks right (for deletion), replace «-ls» with «-delete» to do the actual delete, and of course prepend with sudo if you need root privileges.

---

### Post by jo.angel on 2008-06-04
Looking good!

And very elegant as well!

Thanks a lot, mate...

---

