---
title: "using awk to separate differently numbered lines"
date: 2009-03-05
forum: Programming Talk
---

### Post by onytz on 2009-03-05
Hello all,
I have a file where each line is a number that may or may not be the same number as the one on the preceding or following line. I'd like to insert an '\n' in between lines whose numbers are not the same, and leave off where the preceding or following numbers are the same. I'd like to use mawk.

```
$ cat f1
01
01
01
02
02
03
```

If I run:

```
$ mawk '{if ($1 != prev) {print '\n';prev=$1;print} else {print}}' f1

01
01
01

02
02

03

```


and I want:

```
mawk '*script*'f1
01
01
01

02
02

03
```

That is: the spacing is a bit off. If you see what I'm after, can you suggest some working code? It would help me see how my logic and grasp of mawk are wrong, incomplete, or both...
Thanks!

---

### Post by lloyd_b on 2009-03-05
If you mean you want to suppress that newline on the first line:
```
mawk '{if ($1 != prev) {if (prev != "") {print '\n'};prev=$1;print} else {print}}' f1
```
Basically, what's hitting you is that "prev" is initially undefined, so the "($1 != prev)" test will always be true on the first line (unless the first line of the file happens to be blank, that is).

So just adding a trap to suppress printing the newline if "prev" is blank should do the trick.

Lloyd B.

---

### Post by onytz on 2009-03-05
Yes, I did want to supress the newline on the first line. And your code did the trick! Thanks for the explanation. Now, to digest it...

---

### Post by ghostdog74 on 2009-03-05
```

# awk '$1!=c{print "\n"}{c=$1}$1==c' file


01
01
01


02
02


03


```

---

