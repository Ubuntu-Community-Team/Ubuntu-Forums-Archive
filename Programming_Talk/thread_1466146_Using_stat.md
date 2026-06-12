---
title: "Using stat?"
date: 2010-04-30
forum: Programming Talk
---

### Post by indarkness on 2010-04-30
Hi, I have a little question. 
I need to know the size of a directory, and the number of element that it has got. 
I've proved with stat which shows the size of the dir,but that function shows me more what i need, and i've thoutgh to use "cut" to delete the colums i don't need.
To show the number of elements in te directory, how can i do? I know i cojos use "ls",but i only want the number of element not a list of them. 
Thanks

---

### Post by lostinxlation on 2010-04-30
ls <dir> | wc -l

---

### Post by Ibidem on 2010-04-30
Maybe
ls |wc -w
(number of "words" in output of ls)
or 
ls -l -A|head -n 1
(I think that's files & folders added up)

---

### Post by soltanis on 2010-04-30
Try du.

```

du | awk '{ acc += $1 } END { print acc / 1024 "M" }'

```

---

### Post by dragos2 on 2010-04-30
Or simpler:
```

du -ch

```

---

