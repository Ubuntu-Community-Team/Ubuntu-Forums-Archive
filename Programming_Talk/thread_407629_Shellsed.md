---
title: "Shell/sed"
date: 2007-04-12
forum: Programming Talk
---

### Post by surhudm on 2007-04-12
Hi,

I have a file with 120 lines. I would like to add a newline after every 40 lines. Is there any simple command which can do it for me? Can sed or some shell commands do it for me?

I know this is easy in c++/fortran/c but I am looking for something using the shell and commandline.

Thanks in advance.

Surhud

---

### Post by surhudm on 2007-04-12
Hi,

Figured it out.

#/bin/sh
count=40
while [ $count -lt 120 ]
do
    head -n $count $1 | tail -n 40 >>output
    echo " " >> output
    count=`expr $count + 40`
done

Surhud

---

### Post by bashologist on 2007-04-12
This should work
```
sed '0~40G' filename
```

---

### Post by &lt;mawe&gt; on 2007-04-12
Shouldn't it be **1~40** ?

---

### Post by WW on 2007-04-12
Let's try it.  I'll use 5 instead of 40 to keep the output reasonable.
```

$ cat junk.dat
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
$ sed '0~5G' junk.dat
Segmentation fault
$ sed '1~5G' junk.dat
1

2
3
4
5
6

7
8
9
10
11

12
13
14
15
16

17
18
19
20
$ sed '5~5G' junk.dat
1
2
3
4
5

6
7
8
9
10

11
12
13
14
15

16
17
18
19
20

$

```
For a blank line after every 40 lines:
```

$ sed '40~40G' filename

```

---

### Post by bashologist on 2007-04-12
0~40 works for me. Idk, maybe it's because I'm using debian.

---

### Post by WW on 2007-04-12
Strange!  My test above was on debian sarge.  I get a segfault when I try 0~40.  Now on my ubuntu computer, 0~40 works fine.  Go figure.

---

### Post by Arndt on 2007-04-13
> **bashologist said:**
> This should work
```
sed '0~40G' filename
```

Interesting:

$ sed '0~40G' /etc/passwd
Segmentation fault

---

### Post by Arndt on 2007-04-13
> **Arndt said:**
> Interesting:

$ sed '0~40G' /etc/passwd
Segmentation fault

Sorry, I hadn't read the remaining posts in the thread.

Now that you got a solution with 'sed', here's one in Perl:
```
perl -pe 'print "\n" if ($. % 5 == 0)' filename
```

---

### Post by surhudm on 2007-04-14
Thanks guys... I just checked these posts now.

Surhud

---

