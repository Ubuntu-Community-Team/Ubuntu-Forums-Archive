---
title: "I have two and need to get data from that using loop"
date: 2009-04-07
forum: Programming Talk
---

### Post by aliahsan81 on 2009-04-07
Hi all i have two contain some data
like file1

123
345
345

File2
abc
xyz


I want to pass each value from both file to a command in a loop.I try cat with loop but not working because i have two file.And need to pass data from two file one by one to command.I am using bash



like command is this 

ls $file1 $file2
can any one guid me

---

### Post by weresheep on 2009-04-07
Hello,

I'm not sure if I understand what exactly you are asking for but try this...

```
paste file1 file2
```

and see

```
man paste
```

for more information.

-weresheep

---

### Post by aliahsan81 on 2009-04-07
Hi thanks for your quick answer but i know about paste

look my little example


file1

abc
bcd
yhx

file2 
45
67
78

for in file1 file2

file1=get first value from file1
file2=get first value from file2
and soo on ...................
ls $file1 $file2
done
got my point

---

### Post by weresheep on 2009-04-07
Okay,

How about...

```

paste file1 file2 | while read LINE ; do
  f1=$(echo $LINE | awk '{print $1}')
  f2=$(echo $LINE | awk '{print $2}')

  echo "f1 is $f1 and f2 is $f2"

  # Do stuff with $f1 and $f2 here

done

```

-weresheep

---

### Post by aliahsan81 on 2009-04-07
yes thanks

---

### Post by ghostdog74 on 2009-04-07
> **weresheep said:**
> Okay,

How about...

```

paste file1 file2 | while read LINE ; do
  f1=$(echo $LINE | awk '{print $1}')
  f2=$(echo $LINE | awk '{print $2}')

  echo "f1 is $f1 and f2 is $f2"

  # Do stuff with $f1 and $f2 here

done

```

-weresheep

no need awk..
```

# paste file1 file2 | while read a b
> do
> echo $a $b
> done


```

---

