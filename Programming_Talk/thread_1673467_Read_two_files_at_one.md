---
title: "Read two files at one"
date: 2011-01-22
forum: Programming Talk
---

### Post by bcooperizcool on 2011-01-22
Is it possible to read two text file at once?   Like
```

while read foo
do echo"$foo"
done < foo.txt

```
except have it two text files, with two variables?


Thanks!

---

### Post by SeijiSensei on 2011-01-22
If you mean read the contents of file A, then read the contents of file B in that order, try this:

```

cp /path/to/fileA /tmp/bigfile
cat /path/to/fileB >> /tmp/bigfile

```

Now just read /tmp/bigfile which will contain both files concatenated together.

---

### Post by geirha on 2011-01-22
If you mean read one line from file A and one from line B at the same time, then:
```
# BASH
while read -u3 -r lineA && read -u4 -r lineB; do
    echo "<$lineA> <$lineB>"
done 3< fileA 4< fileB

```

It depends a bit on what you actually need this for though, just a simple paste(1) may also be what you need.


See [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) and [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ) for alot of useful information and examples on Bash and POSIX sh scripting.

---

### Post by hakermania on 2011-01-23
The solution is much simpler. To read two or more files at ones use
```
cat file1 file2
```

---

### Post by bcooperizcool on 2011-01-23
Thank you geihrah!  That is exactly what I was looking for! That makes my job a lot easier :D
what does the -u2 and -u4 do though?

---

### Post by geirha on 2011-01-23
> **bcooperizcool said:**
> Thank you geihrah!  That is exactly what I was looking for! That makes my job a lot easier :D
what does the -u2 and -u4 do though?

See the information about read in bash's manual, or with the help builtin:
```
help '\read'
```

(You can type just "help read" too, but then you also get information on readarray and readonly, since they contain the word read.)

---

