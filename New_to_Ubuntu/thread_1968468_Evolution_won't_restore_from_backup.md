---
title: "Evolution won't restore from backup"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-04-29
Hi all

I have upgraded from 11.10 to 12.04 and have installed evolution [3.2.3], as I had in 11.10.
I backed up my mail to a tar.gz file before I upgraded. Now I have upgraded and installed evolution, I went to restore Evolution data, but it won't restore as it says it is an invalid backup file???
I tested the archive:
```

glenn@acer:~/Evolution Backup$ gunzip -t evolution-backup.tar.gz
glenn@acer:~/Evolution Backup$ 

and tested the file inside with:

glenn@acer:~/gunzip -c evolution-backup.tar.gz | tar tf evolution-backup.tar.gz

```
and it came back with no errors?

What can I do about this? anything?

---

### Post by Senior_Buckethead on 2012-04-29
Anyone at all..?

---

### Post by Senior_Buckethead on 2012-04-30
Bump

---

### Post by verymadpip on 2012-04-30
Hi there.

I think you may be able to restore from your tar.gz by extracting it & copying the relevant files (inbox & the like) over by hand, if you see what I mean.

I had a similar issue a while back & if I recall correctly that's how I worked around it.  (I went back to 10.10 from 11.04 for a time & it was the 11.04 backup that wouldn't restore into 10.10)

I've since migrated to Thunderbird

---

### Post by philinux on 2012-04-30
> **Senior_Buckethead said:**
> Hi all

I have upgraded from 11.10 to 12.04 and have installed evolution [3.2.3], as I had in 11.10.
I backed up my mail to a tar.gz file before I upgraded. Now I have upgraded and installed evolution, I went to restore Evolution data, but it won't restore as it says it is an invalid backup file???
I tested the archive:
```

glenn@acer:~/Evolution Backup$ gunzip -t evolution-backup.tar.gz
glenn@acer:~/Evolution Backup$ 

and tested the file inside with:

glenn@acer:~/gunzip -c evolution-backup.tar.gz | tar tf evolution-backup.tar.gz

```

and it came back with no errors?

What can I do about this? anything?

I know this may sound weird but try copying the tar to your Desktop. Then try the restore.

---

### Post by Senior_Buckethead on 2012-05-01
Thanks Philinux,

did as you suggested, Evolution still spitting the dummy saying the evolution-backup.tar.gz file is invalid.
I found an old backup I made a month ago and stored on my Seagate External. It backed up no problems, just loose a month of mail. 
Can't fathom that, an older backup, made by the same program, works, when a new backup, ditto the same, doesn't.

Its almost a problem you'd find with windows.

Glenn.

---

