---
title: "understanding some code"
date: 2013-04-24
forum: Programming Talk
---

### Post by spiritech on 2013-04-24
i was looking through some old posts to try and find alternatives to renaming files during a while loop and found this old post by vaphell

```
ext="mp4"
while read -r var 
do     
      echo "normal: $var"     
      echo "new ext: ${var%.???}.$ext"     
      echo "new ext(2): ${var%.[a-zA-Z][a-zA-Z][a-zA-Z0-9]}.$ext" 
done < input
```

i didnt read into it much back when it was posted as i didnt have much experience with bash. i have tested it today and found it is a much cleaner way of renaming files during a for - or while - loop. instaed of my sulotion of using a pipe then sed command.  i understand most of whats going on in the code. 

echo "normal: $var" outputs the unaltered input
echo "new ext: ${var%.???}.$ext" ouputs the input with a new extension.

i assume that using the {} enters the variable into a bash substitution, the "." means a dot and the ??? means any 3 digits. i also assume that the % defines last occurance or from end of line non-greedy the same kind of function $ has in sed. 

i would like to understand things further. how can i use defferent matching criteria i.e. any. all or first occurance etc? does it support this kind of matching? is there a tutorial covering this subject?

spiritech

---

### Post by schragge on 2013-04-24
[Bash info manual: Shell Parameter Expansion](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)
[BBG: Transformation of variables](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_03.html#sect_10_03_03)
[ABS: Parameter Substitution](http://tldp.org/LDP/abs/html/parameter-substitution.html)

---

