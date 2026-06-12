---
title: "Shell Script Question"
date: 2007-07-31
forum: Programming Talk
---

### Post by DBQ on 2007-07-31
Hey guys.  Do any of know the following:

I have a list of files named such as n1, n2, n3, etc...

I want to write script where the script feeds the files into the program.  Is there a way to have a loop that would append numbers to 'n' and then feed the resulting string into the program?

---

### Post by yabbadabbadont on 2007-07-31
Read up on the 'seq' command.  If you don't need the numbers to be a fixed width, then something like this will work:
```
for i in $(seq 1 100)
do
  echo "n$i" | some-program-that-reads-from-stdin
done
```
That would produce n1, n2, n3, ..., n10, ..., n100.  You could also do this:
```
for i in $(seq -w 1 100)
do
  echo "n$i" | abcdefg
done
```
This time you would get n001, n002, n003, ..., n100.

---

