---
title: "using awk with variable $z and 'print' command"
date: 2010-03-20
forum: Programming Talk
---

### Post by felipe1982 on 2010-03-20
I'm using awk for the first time. I have a three-level nested while loop in a script. The inner-most loop increments variable $z. I also call awk, and need to do something like:
```

awk '{ print $'"${z}"' }' somefile

```
It isn't doing what I expect:
```

# lofty expectations
awk '{ print $1 }' somefile
awk '{ print $2 }' somefile
awk '{ print $3 }' somefile
awk '{ print $4 }' somefile
# ...

```How should I change my syntax to achieve what I require?

---

### Post by kaibob on 2010-03-20
The awk command seems to work fine:

> $ cat file
a b c d e
1 2 3 4 5
$
$ for i in {1..3} ; do awk '{ print $'"${i}"' }' file ; done
a
1
b
2
c
3


You may want to use printf rather than print depending on how you want the output formatted. For example,

> $ for i in {1..3} ; do awk '{ printf $'"${i}"' " " }' file ; echo ; done
a 1 
b 2 
c 3

---

### Post by geirha on 2010-03-20
You shouldn't embed variables like that. The proper way is to set an awk variable to the content of the shell variable.

```

$ z=2
$ echo "col1 col2 col3" | awk -v"z=$z" '{print "z:",z; print "$z:",$z;}'
z: 2
$z: col2

```

Doing it that way will relieve you of some surprises in the future, when the variable contains spaces or quotes or similar.

---

### Post by kaibob on 2010-03-21
> **geirha said:**
> You shouldn't embed variables like that. The proper way is to set an awk variable to the content of the shell variable.
The OP appears to have moved on, so perhaps it will be OK if I ask a related question. I frequently use awk one-liners in shell scripts and often use shell variables in the awk commands. So, the above statement was of interest to me. Why does command 2 below work, yet command 3 returns nothing. 

> $ cat file
sentence 1
line 2
sentence 3
line 4

$ # Command 1
$ awk '/sentence/' file
sentence 1
sentence 3

$ # Command 2
$ word=sentence ; awk '/'"$word"'/' file
sentence 1
sentence 3

$ # Command 3
$ word=sentence ; awk -v "w=$word" '/w/' file
$ 

BTW, I looked at both of my awk manuals and spent a fair amount of time googling this. Also, I tried all sorts of quoting and command line variations but couldn't get command 3 to work. Thanks!

---

### Post by geirha on 2010-03-21
You need to use the ~ operator when the regex is in a var, so:
```
awk "-vw=$word" '$0 ~ w'
```

In this particular case though, I'd use $1 == w .

---

### Post by kaibob on 2010-03-21
Thanks geirha. That works great. 

> $ word=sentence ; awk -v "w=$word" '$0 ~ w' file
sentence 1
sentence 3

---

### Post by felipe1982 on 2010-03-22
> **geirha said:**
> You shouldn't embed variables like that. The proper way is to set an awk variable to the content of the shell variable.

```

$ z=2
$ echo "col1 col2 col3" | awk -v"z=$z" '{print "z:",z; print "$z:",$z;}'
z: 2
$z: col2

```

Doing it that way will relieve you of some surprises in the future, when the variable contains spaces or quotes or similar.
Thank you for all of your tips. I will incorporate them into my scripts.

---

