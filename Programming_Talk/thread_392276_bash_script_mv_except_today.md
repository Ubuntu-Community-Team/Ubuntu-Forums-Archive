---
title: "bash script mv except today"
date: 2007-03-24
forum: Programming Talk
---

### Post by tocleora on 2007-03-24
I have a script that moves files to a backup drive every night.  If it doesn't run however, I want to run it manually, however during the day there are new files I don't want moved, so I thought I could just build in to the script to only mv files that aren't for today.  I could either do it mv ones that the file creation date isn't today, or the file names are like pl-YYYYMM so if there's anyway I could mv based on that... Any help would be appreciated!

---

### Post by monkeyking on 2007-03-24
I haven't really thought it through,
but you can extract the modified date from the file with a small proggy like
```

ls -l | awk '{print $6}'

```

And from this you can compare with todays date.

---

### Post by Mr. C. on 2007-03-24
Use:

find ... -mtime +1 

to find files modified 1 or more days ago.

MrC

---

