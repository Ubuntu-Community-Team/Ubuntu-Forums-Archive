---
title: "Move prefix files to folder by bash script"
date: 2013-04-04
forum: Programming Talk
---

### Post by safarin on 2013-04-04
Hi all,
I want to create a script that can help me organize my pictures into some folder. I hope by create this script I can gain new knowledge of using bash shell scripts

Here are the problem:

Files examples
```

2011-12-29_10.37.40.JPG
2011-12-29_10.37.41.JPG
2012-01-02_00.56.59.JPG
2012-01-02_15.52.18.JPG
2012-01-02_15.52.19.JPG
.......
.......

```

What I want to do is to put all files that start from YYYY-MM into the folder name YYYY_MM,
as right now I do it manually by

[PHP]
$ mkdir 2011_12 && mv 2011-12* 2011_12
$ mkdir 2012_01 && mv 2012-01* 2012_01
[/PHP]

As the beginner of bash scripts. I hope, somebody can help me..

Thanks.

---

### Post by sisco311 on 2013-04-04
You can use GNU/find to find the file names:

```

find ./ -maxdepth 1 -regextype posix-extended -iregex '^\./[[:digit:]]{4}-[[:digit:]]{2}-[[:digit:]]{2}_.*.jpg'

```

with its -printf option you can print only the YYYY-MM part of the file names:
```

find ./ -maxdepth 1 -regextype posix-extended -iregex '^\./[[:digit:]]{4}-[[:digit:]]{2}-[[:digit:]]{2}_.*.jpg' -printf '%.9p\n'

```

Now you can pipe the output of find to GNU/sort or GNU/uniq in order to omit the repeated names:
```

find ./ ... | sort -u
```

And finally you can redirect the output of the above pipeline to a while loop. In the loop you can create each directory and move the files:

```

#!/bin/bash

# replace path/to/dir with an actual path
cd path/to/dir || exit 1

while IFS= read -r -d '' dir
do
    mkdir -p "${dir//-/_}"
    mv -b -- "$dir"*.[jJ][pP][gG] "${dir//-/_}"
done < <(find ./ -maxdepth 1 -regextype posix-extended -iregex '^\./[[:digit:]]{4}-[[:digit:]]{2}-[[:digit:]]{2}_.*.jpg' -printf '%.9p\0' | sort -zu)
```

Please test the script before you use it. And keeping a backup of your data is always a good idea. ;)

---

### Post by Vaphell on 2013-04-04
you can easily create all combinations of (years) and (months) 

```
for mth in {2011..2013}-{01..12}
do
  echo "$mth"
  mkdir -p "$mth"
  mv "$mth"*.[jJ][pP][gG] "$mth"
done
```

if you don't want to have tons of potentially empty directories you need to process files individually

```
for f in [0-9][0-9][0-9][0-9]-[0-9][0-9]-*.[jJ][pP][gG]
do
  mkdir -p "${f:0:7}"
  mv "$f" "${f:0:7}"
done
```

---

### Post by papibe on 2013-04-04
EDIT: I continue to be the slowest to reply... as usual.

Hi safarin.

First,  you can cycle through all your images with something like this:
```
#!/bin/bash
for file in *.JPG
do
    echo "$file"
done
```
Note that this would only consider images ending in JPG.

If you also have jpg,  jpeg, and others, you would need to include it in the expression:
```
#!/bin/bash
for f in *.JPG *.jpg *.jpeg
do
    echo "$file"
done
```
Once you are sure you are getting all images in your loop, you can start using parameter substitution to get the directory part out of the filename.

The following expression would get the directory as you wanted:
```
${file%-[0-9][0-9]_*}
```
You can test that by doing:
```
#!/bin/bash
for file in *.JPG
do
    echo "moving $file  -->  ${file%-[0-9][0-9]_*}"
done
```
But the directory does not exist yet. You could create it with the 'mkdir' command, but that would give you an error in subsequent intents to create the same directory. Testing if the directory exists would solve the problem.
```
#!/bin/bash
for file in *.JPG
do
    dir="${file%-[0-9][0-9]_*}"

    if [ ! -d "$dir" ]; then
        echo mkdir "$dir"
    fi

    echo mv -iv "$file"  "${file%-[0-9][0-9]_*}"
done
```
Now, if you feel you are ready to roll, remove both words **echo** on the script to actually create the directories and move the files.

Hope it helps. Let us know how it goes.
Regards.

P.S: If you want to continue exploring study the following alternative skeleton for the cycle:
```
#!/bin/bash
while IFS= read -r -d '' file
do
    echo "$file"
done < <(find . -maxdepth 1 -regex '.*jpg\|.*jpeg' -print0)

```

---

### Post by schragge on 2013-04-04
Perhaps
```

ls -q|sed -nr 's/^([0-9]{4}-[0-9]{2}).*/\1/p'|uniq|xargs -rd\\n -n1 sh -c 'd=${0%-*}_${0#*-};mkdir -p $d&&mv $0* $d'

```

---

### Post by sisco311 on 2013-04-04
On a second thought, you could use printf instead of find:
```

printf '%.9s\0' ./[[:digit:]][[:digit:]][[:digit:]][[:digit:]]-[[:digit:]][[:digit:]]-[[:digit:]][[:digit:]]_*.[jJ][pP][gG] | sort -zu | while IFS= read -r -d '' dir; do echo "$dir"; done
```


> **schragge said:**
> Perhaps
```

ls|sed -nr 's/^([0-9]{4}-[0-9]{2}).*/\1/p'|uniq|xargs -d\\n -n1 sh -c 'mkdir $0 && mv $0-* $0'

```

It might work in this particular case, but parsing ls is considered a bad practice:
[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

---

### Post by safarin on 2013-04-05
Wow! I never thought the solution would be some complicated syntax code...
Thank you guys.. I need extra time to study and experiment what does the codes do, because mostly it seem new to me.

I will update to you guys later... 
Thanks~!!

---

### Post by ofnuts on 2013-04-05
Something that can be read without the help of a whole jar of Aspirin pills:

```

for file in ????-??-??_??.??.??.JPG
do
   dir=${file:0:4}_${file:5:2}
   mkdir -p $dir
   mv $file $dir
done

```

---

