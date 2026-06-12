---
title: "Advance command for file rename"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by Deepak Jindal on 2012-06-22
Hello all, 

I am trying to rename files from "long file name.mkv" to "long file name - HD.mkv" in terminal. If the statement is true. any suggestions how can I do this?

---

### Post by codemaniac on 2012-06-22
> **Deepak Jindal said:**
> Hello all, 

I am trying to rename files from "long file name.mkv" to "long file name - HD.mkv" in terminal. If the statement is true. any suggestions how can I do this?

On a terminal please do this .

```
mv "long file name.mkv" "long file name - HD.mkv"
```

---

### Post by codemaniac on 2012-06-22
OK i re-read your post and seems like you want to rename files in batch .
I have tried to write up the below .

```
#!/bin/bash


for i in  *.dat
do
        fname=${i%.*}
        renamed="$fname"" - HD.mkv"
        mv $i "$renamed"
done
```

---

### Post by HiImTye on 2012-06-23
```
rename -n 's|.mkv$| - HD.mkv|' *
```once youre comfortable with the output, remove the -n and it will rename the files

---

