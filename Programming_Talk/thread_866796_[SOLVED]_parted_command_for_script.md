---
title: "[SOLVED] parted command for script"
date: 2008-07-22
forum: Programming Talk
---

### Post by KB1LQC on 2008-07-22
I cannot figure out the command (shell script) for parted to automatically allocate the largest amount of space available on a drive.  I currently have

```
parted /dev/${i} --script mkpart primary 0 -1
```

but its giving me an error.

I used to have

```
parted /dev/${i} --script mkpart primary 0 -0
```

Which actually worked for some reason, the largest partition was made but it outputs an error message so I want to fix that.  Any suggestions?

---

### Post by KB1LQC on 2008-07-22
I think I just figured it out:
```

parted /dev/${i} --script mkpart primary 0 -- -1
```

If someone could let me know if this is indeed the correct way to go about this that would be awesome and I will mark the thread as solved.

---

### Post by unutbu on 2008-07-22
```
parted /dev/${i} --script mkpart primary 0 -- -1
```
Yes, this works. I didn't know -1 could be used to specify the end of the disk -- thank you!

I believe the reason why 
```

parted /dev/${i} --script mkpart primary 0 -1

``` did not work is because '-1' is interpreted as an option (flag) sent to parted instead of as a number. '--' tells the shell the rest of the line is not an option.

This also works, and perhaps looks a little nicer:
```

parted /dev/${i} --script -- mkpart primary 0 -1
```

---

### Post by KB1LQC on 2008-07-30
Thank you!

---

