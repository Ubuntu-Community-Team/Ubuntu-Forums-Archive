---
title: "[SOLVED] Zipping files into parts"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by adobrakic on 2008-10-30
I want to zip a 700 mb file into 7 parts (.part1, .part2, etc.) and upload it on rapidshare

how would i go about doing this? :)

---

### Post by Rolcol on 2008-10-30
This probably isn't a solution you're looking for but you can use the split command to split a file into any size junks and it will save it with "aa, ab, ac .. ba, bb, bc.. etc" at the end.  You can then combine them by using the cat command.

---

### Post by unutbu on 2008-10-30
```
split --bytes=100m largefile
```
The pieces will be called xaa, xab, xac, ..., xag

To recombine them:
```

cat xaa xab xac xad xae xaf xag > largefile
```

---

### Post by adobrakic on 2008-10-30
would this also work if its not a single 700mb file?

its an album that comes up to be 700mb

---

### Post by Rolcol on 2008-10-30
> **adobrakic said:**
> would this also work if its not a single 700mb file?

its an album that comes up to be 700mb
Well... in that case you could use tar to create an archive of it (single file) and then split it.

---

### Post by unutbu on 2008-10-30
```
tar cf album.tar album/
split --bytes=100m album.tar
```

to recover album:
```
cat xaa xab xac xad xae xaf xag > album.tar
tar xf album.tar
```

---

### Post by aeiah on 2008-10-30
```
rar a -r -v100000*1024 album.rar /path/to/album/ 

```

---

### Post by adobrakic on 2008-10-30
Holy crap this all sounds so confusing. 

> 
Well... in that case you could use tar to create an archive of it (single file) and then split it.


I think this would be my best approach. I've zipped the the file into a .zip and now should I use one of these commands or should i do something else?

---

### Post by Mud.Knee.Havoc on 2008-10-30
Assuming that you want other people to download it and be able to use it without getting horribly frustrated, it will be best to follow aeiah's advice.

---

### Post by aeiah on 2008-10-30
if you're wanting windows users to be able to easily unpack it at the other end then i suggest giving my solution a whirl *nod*

---

### Post by aeiah on 2008-10-30
well that was a little strange

---

### Post by adobrakic on 2008-10-30
it looks like its working, thanks! :D

---

### Post by pirattrev on 2008-10-30
yeah, best stick to rar so that way everyone can open it, seeing as tar.gz is not so popular on windows

---

### Post by adobrakic on 2008-10-30
> **pirattrev said:**
> yeah, best stick to rar so that way everyone can open it, seeing as tar.gz is not so popular on windows

Yeah, that was the main concern I was having:KS

---

### Post by aeiah on 2008-10-30
```
rar a -r -v100000*1024 album.rar /path/to/album/ 

```

no worries. the flags mean as follows:
a for add
-r for recursive (you'd ommit that if you were just adding 1 file or a list of files, not a folder)

-v is the volume size in bytes. 100,000*1024 is more or less 100mb

---

