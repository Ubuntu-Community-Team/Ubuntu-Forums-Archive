---
title: "Can't Delete File on USB My Book Drive"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by MrWES on 2008-06-05
I was copying an avi file to my My Book USB drive, and it must have crapped out, now I can't delete the partial file on the USB drive. In nautilus, the file has some sort of weird character in the file name, and from the terminal I get the following error:

```
bill@bill-desktop:/media/My Book/Library/My Movies$ rm -rf Ra&#64209;bo_First_Blood_PartII-001.avi 
rm: cannot lstat `Ra&#64209;bo_First_Blood_PartII-001.avi': Input/output error

```

Any ideas?

Thanks,
Bill

---

### Post by aeiah on 2008-06-05
longshot, but have you tried renaming the file first?

---

### Post by MrWES on 2008-06-05
bill@bill-desktop:/media/My Book/Library/My Movies$ rename Ra&#64209;bo_First_Blood_PartII-001.avi test.avi
Unrecognized character \xEF at (eval 1) line 1.

I had only tried in nautilus, with no luck. Here's the output when I try from the terminal:

bill@bill-desktop:/media/My Book/Library/My Movies$ rename Ra&#64209;bo_First_Blood_PartII-001.avi test.avi
Unrecognized character \xEF at (eval 1) line 1.

---

### Post by sam_delta on 2008-06-05
try

```
rm -f Ra&#64209;bo_First_Blood_*
```


sam

---

### Post by MrWES on 2008-06-05
No luck

```
bill@bill-desktop:/media/My Book/Library/My Movies$ rm -f Ra&#64209;bo_First_Blood_*
rm: cannot remove `Ra&#64209;bo_First_Blood_PartII-001.avi': Input/output error

```

I also noticed the file has NO permissions????

```
?--------- ? ?    ?             ?                ? Ra&#64209;bo_First_Blood_PartII-001
```

---

### Post by walker9010 on 2008-06-05
It may be simpler just to back up the other files on there and reformat the drive

---

### Post by DezSP on 2008-06-05
You could try using unlink, or possibly rm Ra* (move anything that also begins Ra beforehand of course).

---

