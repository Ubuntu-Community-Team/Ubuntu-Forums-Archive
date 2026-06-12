---
title: "Stupid Shell Scipt problem (regexp related)"
date: 2007-07-29
forum: Programming Talk
---

### Post by tomcheng76 on 2007-07-29
hello, i think i should post it here
i am totally newbie to shell scipt (although i have learnt them b4...)
here is the problem
```

$ cat /usr/local/bin/2jpg
#!/bin/bash
for ext in bmp gif png
do
for file in *.$ext
do
if [ -r $file ]
then
convert "$file" "$file".jpg
fi
done
done
```

it ends up with Picture.bmp.jpg (it is a jpg) which is able to predict 
so, my question is
how to use regexp to remember "Picture" this name ?
i only know using (*) and \1 , but i already forget how to use them
any help would be appreciated,  thanks in advance

---

### Post by PaulFr on 2007-07-29
Would this work ?```
#!/bin/bash

for ext in bmp gif png
do
    for file in *.$ext
    do
        if [ -r $file ]
        then
            base=${file/\.[a-z][a-z][a-z]/}
            convert "$file" "${base}.jpg"
        fi
    done
done
``` Comment: If your directory has sample.bmp and sample.png, then you will have only one sample.jpg.

---

### Post by tomcheng76 on 2007-07-29
it works like a charm
thanks paulFr
how to do auto renaming in case the directory has sample.bmp and sample.png?
also, i want recursive search (subdirectory)
any help would be appreciated

---

### Post by PaulFr on 2007-07-29
```
#!/bin/bash
if test $# -ge 1; then
    cd $1
    echo "Processing $1"
fi
for ext in bmp gif png
do
    for file in *.$ext
    do
        if [ -r $file ]
        then
            base=${file/\.[a-z][a-z][a-z]/}
            new="${base}.jpg"
            idx=0; export idx
            while :
            do
                if [ -f "$new" ]
                then
                    idx=`expr $idx + 1`
                    new="${base}-${idx}.jpg"
                else
                    convert "$file" "$new"
                    break
                fi
            done
        fi
    done
done
exit 0
```This will handle duplicates in a single directory. The easy way to do subdirectories is IMHO:
1. Put the above in a file, say **~/change2jpg**
2. Then go to the top directory where you want to convert the files and run:```
find . -type d -exec ~/change2jpg {} \;
```

---

### Post by tomcheng76 on 2007-07-30
thanks PaulFr!
it works perfectly
i just realized  that i can use find LOL
btw, here is only one question for the scipt
when there is no test for the while loop
i must add a ":" there?

---

### Post by PaulFr on 2007-07-30
The **while : ** is an infinite loop construct (like **while (1) { <do something> }** in the C language).

---

