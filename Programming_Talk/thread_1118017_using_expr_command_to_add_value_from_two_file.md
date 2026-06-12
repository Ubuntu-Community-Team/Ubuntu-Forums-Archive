---
title: "using expr command to add value from two file"
date: 2009-04-06
forum: Programming Talk
---

### Post by aliahsan81 on 2009-04-06
How to add two number from two different file using expr command ??

---

### Post by Arndt on 2009-04-06
> **aliahsan81 said:**
> How to add two number from two different file using expr command ??

Can you give some more information? Are the numbers in the filenames, or stored inside the files? Give an example.

---

### Post by aliahsan81 on 2009-04-06
Like i have file A and B

Both contain Numaric like

File A

34
45
56
78

File B

34
67
89

I want to add first number number from both file 
34+45=Result in some other file
45+67=Result in some other file

and soo on

---

### Post by aliahsan81 on 2009-04-06
Both file have same number of numeric characters

---

### Post by Arndt on 2009-04-06
> **aliahsan81 said:**
> Both file have same number of numeric characters

Here is a Perl one-liner:

```
$ cat n1
12
34
32
11
$ cat n2
56
677
99
88
$ perl -e 'open(F1,$ARGV[0]); open(F2,$ARGV[1]); while (<F1>) {print $_+<F2>,"\n"}' n1 n2
68
711
131
99

```

If you want to use 'expr', you will need a shell script to read the numbers from the files. Did you try writing such a script?

---

### Post by aliahsan81 on 2009-04-06
Its a small part of script.Actually i am processing access log of apache.I want to process access log from where it last time left.For this i am doing this

tail --bytes filename

which will give length of current access log 

then when next time script run it will again do


tail --bytes filename

after then i have two values i can subtract one from and other then i will go the bytes value 

then i  do 

tail -c number filename | grep mything

this ensure i will only pars that log part  which is new from previous and thus enhancing performance. 

Please can you help me in this i mean adding two value from file.using awk or any other mean.
the above i am using becaue i have many access-log for many domain.so keep trakc of each acclog log size.

---

### Post by ghostdog74 on 2009-04-06
> **aliahsan81 said:**
> Like i have file A and B

Both contain Numaric like

File A

34
45
56
78

File B

34
67
89

I want to add first number number from both file 
34+45=Result in some other file
45+67=Result in some other file

and soo on

```

paste file1 file2| sed 's/[[:blank:]]/+/g'| bc

```

awk:
```

awk 'FNR==NR{_[++d]=$1;next}{_[FNR]+=$1}END{for(i in _) print _[i]}' file1 file2

```

---

### Post by aliahsan81 on 2009-04-07
Thanks you all.This is a great forum.I will use the awk code in my script.

---

