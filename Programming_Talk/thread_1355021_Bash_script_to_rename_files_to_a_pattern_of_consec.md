---
title: "Bash script to rename files to a pattern of consecutive numbers"
date: 2009-12-14
forum: Programming Talk
---

### Post by Frogging101 on 2009-12-14
This is the first time I have EVER tried to understand bash, and I am sure it is very easy to do this. I am trying to make a script that will rename a bunch of files to names such as 0001.png, 0002.png, 0003.png and so on. How would I go about doing this?

---

### Post by Rany Albeg on 2009-12-14
Hello Frogging101 , 

It is possible to rename a file with the 'mv' command by executing :

mv oldname newname

while , of curse , oldname and newname are in the same directory.

--

from here you'll just need to run the above command in a loop and it will almost be a solution:

```
new=0
for i in *
do
        mv "$i" "$new"
        ((new++))
done
```

but lets don't forget about the file extension - we will want to contain it as an integral part of the file name.
so lets save the extension of the current file and add it afterwards to the final name.
this is how we will feed the extension variable:

ext="${i#*.}"

lets make the code complete:

```
new=0
ext=

for i in *
do
        ext="${i#*.}"
        mv "$i" "$new.$ext"
        ((new++))
done
```

output example:

```
rany@rany-laptop:~/Desktop/test$ touch file1.jpg file2.bmp file3.csv file4.cpp
rany@rany-laptop:~/Desktop/test$ ls
file1.jpg  file2.bmp  file3.csv  file4.cpp
rany@rany-laptop:~/Desktop/test$ new=0;for i in *;do ext="${i#*.}";mv "$i" "$new.$ext";((new++));done
rany@rany-laptop:~/Desktop/test$ ls
0.jpg  1.bmp  2.csv  3.cpp
rany@rany-laptop:~/Desktop/test$
```

---

### Post by SecretCode on 2009-12-14
And if you need leading zeros, printf will help:

```
#!/bin/bash
i=1
for file in *.jpg
do
        j=$( printf "%04d" "$i" )
        mv "$file" "$j.jpg"
        (( i++ ))
done
```

---

### Post by Rany Albeg on 2009-12-15
> **SecretCode said:**
> And if you need leading zeros, printf will help:

```
#!/bin/bash
i=1
for file in *.jpg
do
        j=$( printf "%04d" "$i" )
        mv "$file" "$j.jpg"
        (( i++ ))
done
```

Thanks for fixing.

Have a nice day.

---

### Post by spupy on 2009-12-15
> **SecretCode said:**
> And if you need leading zeros, printf will help:

```
#!/bin/bash
i=1
for file in *.jpg
do
        j=$( printf "%04d" "$i" )
        mv "$file" "$j.jpg"
        (( i++ ))
done
```

I'm interested, is there a way to pass the pattern for the for-loop (*.jpg in this case) as an argument of the script? Would $@ work?

---

### Post by kaibob on 2009-12-15
Post deleted by kaibob.

---

### Post by ki3456 on 2011-07-13
> **kaibob said:**
> If I understand you correctly, the following script will do what you want. After the script name, you type the extension without an asterisk or dot.      I think the last version of the script will permanently delete some files.  Use with caution.

---

### Post by kaibob on 2011-07-13
> **ki3456 said:**
> I think the last version of the script will permanently delete some files.  Use with caution.
The shell script was mine and was written when I was first learning shell scripts. The script was wrong in two respects, and I have deleted it. Thanks for the heads-up.

---

