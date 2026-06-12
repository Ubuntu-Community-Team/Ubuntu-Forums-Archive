---
title: "[bash] adding shuffle to script"
date: 2013-12-08
forum: Programming Talk
---

### Post by sammyp90 on 2013-12-08
hi, i have a simple script that will play music in a folder however i have been trying to shuffle to order using 'shuf' with no luck.

the current script is ```
#!/bin/bash


for file in $1/*
do
 omxplayer -o local "$file"
done


```
my 100 previous attempts are based on a line of code posted in another thread by steeldriver which is
```
while read -r -d $'\0' file; do echo play "$file"; done < <(shuf -ze *.mp3)
```
any ideas how i will get the functionality of this line of code in the bash script?

---

### Post by papibe on 2013-12-08
Thread closed. Duplicated thread here: [http://ubuntuforums.org/showthread.php?t=2192558&p=12868538](http://ubuntuforums.org/showthread.php?t=2192558&p=12868538)

Please do not post duplicates. Besides diluting the community effort, it is very difficult to provide any consistent help.

Please continue the conversation on the other thread.

Regards.

---

