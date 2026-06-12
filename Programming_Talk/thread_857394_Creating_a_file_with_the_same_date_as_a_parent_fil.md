---
title: "Creating a file with the same date as a parent file"
date: 2008-07-12
forum: Programming Talk
---

### Post by danielsbrewer on 2008-07-12
Hello,

I am writing a bash script that rotates a movie and I would like to have it that the resulting file has the same date as the original movie file.  I think it should be possible with touch but can't work it out.  Any suggestions would be appreciated.

---

### Post by mike2357 on 2008-07-12
I'm not exactly sure what you want to do, but "cp -p" will copy a file and preserve the timestamp.  If this doesn't help, please post back and give an example.

---

### Post by nvteighen on 2008-07-12
This worked for me:

```

touch --reference=PARENT_FILE --date='0 seconds' TARGET

```

date is used as a relative value, so we need to add 0s to the reference (PARENT_FILE's timestamp).

More information in:
```

info coreutils 'touch invocation'

```

---

### Post by danielsbrewer on 2008-07-12
Thanks for the reply, but that is not really what I want.

So we have a file amd ls -l produces this:

-rwxrwxrwx+ 1 daniel  daniel  2446372 May 28  2004 DSCF0060.AVI

I rotate the file using mencoder like this:
mencoder -ovc lavc -lavcopts vbitrate=9000:vcodec=mpeg4 -ffourcc DX50 -of avi -vf rotate=1 -oac mp3lame -lameopts preset=standard DSCF0060.AVI -o tmp2.avi

Now tmp2.avi has the current date and time.  I would like to alter tmp2.avi such that it has the same date and time as DSCF0060.AVI.

---

### Post by danielsbrewer on 2008-07-12
> **nvteighen said:**
> This worked for me:

```

touch --reference=PARENT_FILE --date='0 seconds' TARGET

```

date is used as a relative value, so we need to add 0s to the reference (PARENT_FILE's timestamp).

More information in:
```

info coreutils 'touch invocation'

```

Thats great thanks.

---

