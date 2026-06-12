---
title: "arguments in for loop"
date: 2014-01-08
forum: Programming Talk
---

### Post by cedricmaes92 on 2014-01-08
hy guys 

i'm having a little problem in a for loop i can't seem to solve. i want to count different types of videofiles (avi, mvk, mp4, etc) in a map and write the number of each type to the file "aantal". 
i'm going to change the writing to a file to something usefull later on but i figure i'd get this working first.
 So far i have this small code.

```

#!/bin/bash -xv

cd /media/sf_Downloads/testmap
for i in *.avi *.mkv *.mp4
do 
 find -P "${i##*.}" | wc -l >>/home/cedric/aantal
done

```

i know the fault is somewhere in ```
"${i##*.}"
``` but i don't know why or how it works
This is what it get's me 
```

+ for i in '*.avi' mkv '*.mp4'
+ wc -l
+ find -P avi
find: ‘avi’: Bestand of map bestaat niet
+ for i in '*.avi' mkv '*.mp4'
+ wc -l
+ find -P mkv
find: ‘mkv’: Bestand of map bestaat niet
+ for i in '*.avi' mkv '*.mp4'
+ wc -l
+ find -P mp4
find: ‘mp4’: Bestand of map bestaat niet

```

I want it to find any avi-, mp4-, mkv-files regardless of the name (i.e. "Man Of Tai Chi (2013).mkv" or "Burn Notice - The Fall of Sam Axe (2011).mkv"  ") but it doesn't do that for now.
any help please?
other methods of doing something like this are also welcome 

thanks in advance,

Cedric

---

### Post by QIII on 2014-01-08
Moved to Programming Talk.

---

### Post by sisco311 on 2014-01-08
Check out BashFAQ 004 (link in my signature).

---

### Post by Habitual on 2014-01-08
Try an array:

```
Source=(*.avi *.mkv *.mp4)
for i in ${Source[@]} ; do <stuff here>  ; done
```

---

### Post by Vaphell on 2014-01-08
```
#!/bin/bash

dir=.
exts=( avi mkv mp4 mov )  # array of relevant extensions

# associative array of counters, count[X] = number_of_X
declare -A count

# construct the regex matching desired file types
printf -v rgx "%s|" "${exts[@]}"
rgx=".*[.](${rgx%?})"

# loop through the output of find supplied with the prepared regex
while read -rd $'\0' f
do
  ext=${f##*.}                         # get file extension
  ext=${ext,,}                         # normalize ext to lowercase
  count[$ext]=$(( ${count[$ext]}+1 ))  # add one to the counter
done < <( find "$dir" -regextype posix-extended -iregex "$rgx" -type f -print0 )

# print the key/value pairs present in the count array
for k in ${!count[@]}; do echo "$k: ${count[$k]}"; done
```

```
$ cd test
$ ls
test2.avi  test2.mp4  test.mkv  test.mp4
test2.MKV  test.AVI   test.Mov  videos.sh
$ ./videos.sh 
mkv: 2
mp4: 2
mov: 1
avi: 2
```
redirecting to file inside the script is not necessary. You can redirect the script itself wherever you want, which gives you way more flexibility
```
./script
./script | some | commands
./script > file
```

---

### Post by ofnuts on 2014-01-09
```

for ext in avi mp4 mkv
do
          echo $ext:$(find . -name "*.$ext" | wc -l) >> /home/cedric/aantal
done

```

or am I missing something?

---

### Post by sisco311 on 2014-01-09
> **ofnuts said:**
> ```

for ext in avi mp4 mkv
do
          echo $ext:$(find . -name "*.$ext" | wc -l) >> /home/cedric/aantal
done

```

or am I missing something?

```

[sisco@acme tmp]$ mkdir foo
[sisco@acme foo]$ cd foo
[sisco@acme foo]$ > "this is an avi file.avi"
[sisco@acme foo]$ > "this is another one.AVI"
[sisco@acme foo]$ ls -al
total 40
drwxr-xr-x  2 sisco users  4096 Jan  9 11:29 .
drwxr-xr-x 11 sisco users 36864 Jan  8 13:53 ..
-rw-r--r--  1 sisco users     0 Jan  9 10:51 this is an avi file.avi
-rw-r--r--  1 sisco users     0 Jan  9 10:51 this is another one.AVI
[sisco@acme foo]$ find ./ -name "*.avi" | wc -l
1
[sisco@acme foo]$ > "and now for
> something
> completely
> different.avi"

[sisco@acme foo]$ ls -al
total 40
drwxr-xr-x  2 sisco users  4096 Jan  9 11:26 .
drwxr-xr-x 11 sisco users 36864 Jan  8 13:53 ..
-rw-r--r--  1 sisco users     0 Jan  9 11:26 and now for?something?completely?different.avi
-rw-r--r--  1 sisco users     0 Jan  9 10:51 this is an avi file.avi
-rw-r--r--  1 sisco users     0 Jan  9 10:51 this is another one.AVI
[sisco@acme foo]$ find ./ -name "*.avi" | wc -l
5

```

---

### Post by ofnuts on 2014-01-09
```

for ext in avi mp4 mkv
do
          echo $ext:$(find . -iname "*.$ext" -print0 | tr -d '\n' | tr '\0' '\n' | wc -l) >> /home/cedric/aantal
done

```

---

### Post by Vaphell on 2014-01-09
names are not important so it's better to replace them with something predictable to avoid the whitespace issues. You can simply use something like -printf "x" | wc -c
```
for ext in avi mp4 mkv
do
    echo $ext:$( find . -iname "*.$ext" -printf "x" | wc -c )
done > /home/cedric/aantal
```

that said, running find n times is a bit wasteful. I tried to do this in one go, by creating universal regex for find and then counting extensions

---

### Post by cedricmaes92 on 2014-01-09
hy guys 

thanks a lot with these examples. i will definitly try them out and try to understand how they work.

kind regards

Cedric

---

### Post by ofnuts on 2014-01-09
Much cleverness in the "-printf x | wc -c".

In practice the consecutive calls to "find" aren't that bad, because the first one puts the whole file structure in the filesystem cache, so the second one runs much faster. On my photo archives (laptop with Core I5 and 7200pm disk):

```

time find . -type f -iname '*.JPG' -printf x | wc -c
5409

real    0m1.162s
user    0m0.016s
sys     0m0.064s
>>>time find . -type f -iname '*.CR2' -printf x | wc -c
450

real    0m0.019s
user    0m0.000s
sys     0m0.016s

```

So the first find takes around one second, but the second one takes under 20ms... (and this remain true for further calls)

---

### Post by Vaphell on 2014-01-09
unsurprisingly i got the *-printf x | wc -c* trick from some thread where sisco schooled yet another noob :D

true, it's not a problem with few hundred files, but I wouldn't want to scan my system spanning 3 harddrives 4x though, i doubt i got that much memory to spare ;-)
I tend to choose somewhat academic solutions that don't risk brutal overheads in nasty corner cases and there is some innate ugliness in redundancy :-)

---

### Post by ofnuts on 2014-01-09
We are only scanning one directory with videos here... Unless these are for Vine there can't be that many on a consumer hard disk...

---

