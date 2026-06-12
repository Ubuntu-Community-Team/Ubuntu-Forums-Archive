---
title: "bash renaming files"
date: 2012-07-19
forum: Programming Talk
---

### Post by abraxas334 on 2012-07-19
Hi
I have the following problem I am not sure how to solve elegantly.
I have a directory with  203 files named foo_*.xvg for the * substitute numbers from 0 to 302
Now evidently the numbering isn't correct. I want files called foo0.xvg to foo302.xvg
It doesn't matter which file has which number. How do I solve this with a simple bash script?
Thanks for any help.

---

### Post by Lars Noodén on 2012-07-19
Probably [rename](http://linux.die.net/man/1/rename) would be the place to start.  It is quite good with patterns.  You can find a few HowTos, tutorials and other examples of using it around on the net.

---

### Post by codemaniac on 2012-07-19
> **abraxas334 said:**
> Hi
I have the following problem I am not sure how to solve elegantly.
I have a directory with  203 files named foo_*.xvg for the * substitute numbers from 0 to 302
Now evidently the numbering isn't correct. I want files called foo0.xvg to foo302.xvg
It doesn't matter which file has which number. How do I solve this with a simple bash script?
Thanks for any help.

```
#!/bin/bash
j=0
for i in "*.xvg"
do
        mv $i foo_"$j".xvg
        ((j++))
done
```

---

### Post by ajgreeny on 2012-07-19
So it looks as if you just want the underscore removed from the file names, is that correct?

If so navigate to the folder and run command ```
rename 's/_//g' *
```

Simple!

---

### Post by abraxas334 on 2012-07-19
The mv you suggest assumes that foo_"$j".xvg is a directory. 

The error I get is that the target is not a directory...

---

### Post by abraxas334 on 2012-07-19
> **ajgreeny said:**
> So it looks as if you just want the underscore removed from the file names, is that correct?

If so navigate to the folder and run command ```
rename 's/_//g' *
```

Simple!

No not quite, I want the numbering to be continuous, at the moment there is a random gap in the numbering somewhere, as in it goes from say 0 to 50 and then starts again at 150. the underscore I don't care that much about.

---

### Post by abraxas334 on 2012-07-19
Ok i guess i sloved it myself:
```


#!/bin/bash

arr=(foo*.dat)  # * is list of all file and dir names

n=${#arr[@]}
echo "number of files and dirs "$n

echo ${arr[0]}
echo ${arr[1]}
j=0

for i in "${arr[@]}"
do
        echo $i
        mv ${i} foo${j}.xvg
        ((j++))
done


```

---

