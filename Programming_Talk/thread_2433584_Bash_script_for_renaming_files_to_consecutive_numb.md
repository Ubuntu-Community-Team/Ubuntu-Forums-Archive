---
title: "Bash script for renaming files to consecutive numbers in multiple directories"
date: 2019-12-21
forum: Programming Talk
---

### Post by lilipop on 2019-12-21
hello,
i have a problem very similar to this dude:
[https://stackoverflow.com/questions/22880570/bash-script-for-renaming-files-to-consecutive-numbers-in-multiple-directories](https://stackoverflow.com/questions/22880570/bash-script-for-renaming-files-to-consecutive-numbers-in-multiple-directories)

but my problem is slightly different
the extensions of my files are not all jpg. i have various file types and i want to keep that extensions.
so, i have changed the code to this:
```

#!/bin/bash
for dir in $(find -type d \( ! -name '.*' \)) 
do 
  i=1; 
  ext=
  for file in $(find "$dir" -name '*.*')
  do 
     ext="${i#*.}"
     a=$(printf "%02d" $i)
     new=${file%/*}
     echo "mv $file $new/$a.$ext"
     let i=i+1
  done 
done

```

got some inspiration from here too: [https://ubuntuforums.org/showthread.php?t=1355021](https://ubuntuforums.org/showthread.php?t=1355021)


so, the input would be like this:
```

Folder1
 -> AD01
   -> DSC123.jpg
   -> DSC124.php
 -> AD02
   -> DSC234.png
   -> DSC1455.exe
 -> AD03
  ->...
 -> AD04
  ->...
 ->...
Folder2
 ->...
...
and the output would be like this
Fo1
 -> Pg1
   -> Fo1_Pg1_1.jpg
   -> Fo1_Pg1_2.php
 -> Pg2
   -> Fo1_Pg2_1.png
   -> Fo1_Pg2_2.exe
 -> Pg3
  ->...
 -> Pg4
  ->...
 ->...
Fo2
 ->...
...



```

thanks

---

### Post by TheFu on 2019-12-22
I would break this down into 2 separate steps and make a script for each that generates a script with lots of **mv** and **rename** lines.

*.* is an MS-Dos thing because extensions are treated differently in that OS.  Unix doesn't care.  * is the same.  File globbing is a subset of the regex language.

If I had to do something like this every day for 500 directories and 20000 files, I wouldn't use bash.  I'd use perl.

---

