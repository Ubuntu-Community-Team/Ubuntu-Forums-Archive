---
title: "while read and function"
date: 2013-05-04
forum: Programming Talk
---

### Post by spiritech on 2013-05-04
how do i call a function into a while read script. i have a function that renames a file extension.

```
function rename {

 "${f%.*}.$ext" 

}

```

how can i call that function into a while read command

```
while read f; do echo "rename function"; done

```

i am aware i could just put it like

```
while read f; do echo "${f%.*}.$ext"  ; done
```

the actuall function is more complex. so i would like to be able to call it in during the while read command.

spiritech

---

### Post by sisco311 on 2013-05-04
Try something like:
```

rename ()
{
    file="$1"
    ext="$2"
    file="${file%.*}.$ext"
    ...
    echo "$file"
}

e=".whatever"
while read -r f
do
    new=$(rename "$f" "$e")
    mv -- "$f" "$new"
done

```

See:  [http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions)

---

