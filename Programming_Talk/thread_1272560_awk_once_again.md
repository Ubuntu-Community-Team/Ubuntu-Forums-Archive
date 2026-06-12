---
title: "awk once again"
date: 2009-09-22
forum: Programming Talk
---

### Post by abraxas334 on 2009-09-22
I really should try understanding manuals better ....
anyway my problem is this:
I want to print from 1000 files like this file.*.dat the last line into a single file i.e. the new files ends up with 1000 last lines of the 1000 file.*.dat.

I got as far as printing it from one file

[PHP]
awk 'END{print}' file.1.dat > newFile
[/PHP]

however 

[PHP]
awk 'END{print}' file.*.dat > newFile 
[/PHP]
also produces just one line in the new file! Any ideas please?

Thank you

---

### Post by falconindy on 2009-09-22
You'll need to create a loop. Provided all 1000 files are in the same directory, and it's your pwd:
```
for f in `ls *.dat`; do
    awk 'END{print}' $f >> /path/to/newFile
done
```

Hmm, I might also be wrong about awk not accepting wildcards... Use '>>' instead of '>'.

---

### Post by geirha on 2009-09-22
Not sure how to do that with awk, but with GNU tail, you can do:
```
tail -q -n 1 file.*.dat > newFile
```

@falconindy. Don't loop over the output of ls, it breaks for files with spaces and special characters, and is also completely unnecessary. And second, remember to [COLOR="Red"]quote[/COLOR] parameter expansions for the same reason (preserve spaces and special characters in filenames)

```
for f in *.dat; do awk 'END{print}' [COLOR="Red"]"[/COLOR]$f[COLOR="Red"]"[/COLOR]; done > newFile
```

---

### Post by abraxas334 on 2009-09-22
> **geirha said:**
> Not sure how to do that with awk, but with GNU tail, you can do:
```
tail -q -n 1 file.*.dat > newFile
```

[/COLOR]$f[COLOR="Red"]"[/COLOR]; done > newFile[/code]

Thanks that was great :) it worked really well! 
Another one to write down and try to remember!

---

### Post by falconindy on 2009-09-22
> **geirha said:**
> Not sure how to do that with awk, but with GNU tail, you can do:
```
tail -q -n 1 file.*.dat > newFile
```

@falconindy. Don't loop over the output of ls, it breaks for files with spaces and special characters, and is also completely unnecessary. And second, remember to [COLOR="Red"]quote[/COLOR] parameter expansions for the same reason (preserve spaces and special characters in filenames)

```
for f in *.dat; do awk 'END{print}' [COLOR="Red"]"[/COLOR]$f[COLOR="Red"]"[/COLOR]; done > newFile
```
Mmm, good point. Tail is a much better solution. Thanks.

---

