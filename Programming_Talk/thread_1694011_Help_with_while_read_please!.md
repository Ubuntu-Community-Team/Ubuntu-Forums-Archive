---
title: "Help with while read please!"
date: 2011-02-23
forum: Programming Talk
---

### Post by bcooperizcool on 2011-02-23
I have two text files (names and contents).
so my script is:
```
if [[ -f "/Applications/$name/$contents" ]];
then mv "/Applications/$names/$contents" "/Applications/$names/1$contents"; cp "$theme_base/$theme/Folders/$names/$contents" "/Applications/$names/$contents"; echo "Setting up custom $names images";
else echo "No custom images for $names";
fi
done 3< $theme_base/.names.txt 4< $theme_base/.contents.txt
```

Instead of it going through each one for both files, I would need the $names variable to stay the same while it reads through the contents text file, and then go to the next line on the names file and repeat the whole process.  

Thanks!

---

### Post by Vaphell on 2011-02-23
without trying to understand what you are doing exactly i made an example with 2 whiles, 1 inside the other, where list.txt stores the names to open and for each name appropriate file is iterated

```
#!/bin/bash

while read name
do
    while read content
    do
        echo $name: $content
    done < $name.txt
done < list.txt
```

example output:
```
stuff1: some stuff
stuff1: other stuff
stuff2: omg
stuff2: omgomgomg!
```

---

### Post by bcooperizcool on 2011-02-23
THANK YOU SO MUCH!   :D
Its working!  :D

---

