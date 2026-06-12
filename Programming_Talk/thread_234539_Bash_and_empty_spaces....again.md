---
title: "Bash and empty spaces....again"
date: 2006-08-11
forum: Programming Talk
---

### Post by gasparov on 2006-08-11
Hi,
   I'm learning bash and these empty spaces in filenames make me crazy,I'm not even able to do simple things.
For example I'd like to make a script that list files older than a week in a directory,it would be really simple for me as well if I had no empty spaces.
```
#! /bin/sh
for file in $(find /Downloadz/Donkey/amule -mtime +7);do
echo mv ${file}
done

```

so if I "close" the variable
```

#! /bin/sh
for file in "$(find /Downloadz/Donkey/amule -mtime +7)";do
echo "mv $file"
done
```

The problem is that the whole list is taken as the variable,so that "for" is useless.For example if i have three files in the directory i got this output.
mv file 1
file2
file3

instead i want
mv file1
mv file2
mv file2

With the first script I had
mv file
mv 1
mv file2
mv file3

I was thinking about using arrays....

---

### Post by LordHunter317 on 2006-08-11
You shouldn't do that anyway, because unbounded output from find(1) will crash your shell if it's too big.

Pipe the output of find into a loop, like so:```
find <path> -mtime +7 | while read line ; do
    mv "$line" /somewhere/else
done
```

---

### Post by gasparov on 2006-08-11
Thanks a lot,
   so it's for that breaks things,for+whitespaces simply doesn't work.

---

### Post by LordHunter317 on 2006-08-11
Not like that.  There are ways to make it work by changing IFS, but usually I've found that means I need to take another approach.

---

