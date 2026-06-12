---
title: "Copying files from Win2k to external HDD"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Dark006 on 2008-08-18
I'm having a problem copying files from my friends computer, they are running Win2k. When I run ```
mount
```I can see that /dev/hda1 (their hard drive, on /mnt/hda1) and /dev/sda1 (my external drive, on /mnt/sda1) are both mounted. 

I can get to their documents folder (C:\Documents and Settings\Sharon1\My Documents), but every time I try to copy them to my external drive, it gives an error saying 'omitting My Documents'. This is what I've tried in the C:\Documents and Settings\Sharon1\ ```
cp 'My Documents' /dev/sda1/
```

I've even made a directory (/dev/sda1/Sharons) and pointed it to that but it still doesn't work. I've never done this before so I might be missing a step or something. Anyone have any ideas?

---

### Post by tarps87 on 2008-08-19
Try:
```

cp -r 'My Documents' /dev/sda1/
```
This should copy the whole folder

If you want to find out more on a command type:
```

man <command name>
```

---

