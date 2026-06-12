---
title: "Bash script challenge: remove characters up to a specific word"
date: 2009-02-13
forum: Programming Talk
---

### Post by NinjitsuStylee on 2009-02-13
Hi there folks,

I'm sure I could post this in some other forum instead of here, but golly you guys are just too smart for me to go anywhere else. ;)

Imagine I have a file that looks like this:

```


1) Fruit: apple
2) Fruit: pear
3) ...Fruit: banana
4)     Fruit: orange
5) Fruit: apple
6) xx123Fruit: banana
    7) Fruit: apple


```What I would like to do is format the file (and output to another file) so that it looks like this:

```

Fruit: pear
Fruit: orange

```
So basically, strip all characters from the beginning of each line before the word "Fruit" and also totally obliterate both pairs of duplicates in the file.  Using pipes is a-ok.

I know this will probably involve awk/sed and maybe even uniq but I'm still pretty green at using these utilities (and regexp, for that matter).

Thoughts?

---

### Post by geirha on 2009-02-13
There are many ways to achieve that. Here's one using grep and sort
```
grep -o 'Fruit:.*' file.txt | sort -u
```

---

### Post by NinjitsuStylee on 2009-02-17
This is close, but it produces the output:

```

Fruit: apple
Fruit: banana
Fruit: orange
Fruit: pear

```

This only removes one of the dupes, and I want to get rid of all of the dupes, so that the output should only be:

```
[FONT=monospace]
Fruit: pear
Fruit: orange
[/FONT]
```


Anyone else want to take a shot? :)

---

### Post by Martin Witte on 2009-02-17
> **NinjitsuStylee said:**
> This is close, but it produces the output:

```

Fruit: apple
Fruit: banana
Fruit: orange
Fruit: pear

```

This only removes one of the dupes, and I want to get rid of all of the dupes, so that the output should only be:

```
[FONT=monospace]
Fruit: pear
Fruit: orange
[/FONT]
```


Anyone else want to take a shot? :)

:confused:
```
martin@toshibap200:~$ cat testfile
1) Fruit: apple
2) Fruit: pear
3) ...Fruit: banana
4)     Fruit: orange
5) Fruit: apple
6) xx123Fruit: banana
    7) Fruit: apple
martin@toshibap200:~$ grep -o 'Fruit:.*' testfile | sort -u
Fruit: apple
Fruit: banana
Fruit: orange
Fruit: pear
martin@toshibap200:~$ 


```

---

### Post by Yuzem on 2009-02-17
```
sed -e '/pear\|orange/!d' -e 's/.*F/F/' file.txt
```

---

### Post by stylishpants on 2009-02-17
Oh, so if fruit A has any duplicates, then don't include fruit A in the output at all.

How about this:

```

bob@cob:/tmp$ cat data.txt 
1) Fruit: apple
2) Fruit: pear
3) ...Fruit: banana
4)     Fruit: orange
5) Fruit: apple
6) xx123Fruit: banana
    7) Fruit: apple
8. Fruit: StarFruit

bob@cob:/tmp$ grep -o 'Fruit:.*' data.txt | sort | uniq -c  | sed -nre 's/^\s*1\s*//; T; p'
Fruit: orange
Fruit: pear
Fruit: StarFruit

```

EDIT: Turns out that uniq has the -u flag, which shows only the non-duplicated lines, so sed doesn't need to do it:
```

bob@cob:/tmp$ grep -o 'Fruit:.*' data.txt | sort | uniq -u
Fruit: orange
Fruit: pear
Fruit: StarFruit


```

---

### Post by Yuzem on 2009-02-17
> **stylishpants said:**
> Oh, so if fruit A has any duplicates, then don't include fruit A in the output at all.

```
sed -e '/pear\|orange/!d' -e 's/.*F/F/' file.txt | sort -u
```

Maybe I didn't understand the concept correctly... :(

---

