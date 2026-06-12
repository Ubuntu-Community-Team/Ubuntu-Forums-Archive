---
title: "write value relative of the variable in staircase [shell script]"
date: 2016-09-30
forum: Programming Talk
---

### Post by sed_faster on 2016-09-30
hello everyone,

Anybody have idea how can I do this:
```

var=hello
echo $var
h
 e
  l
   l
    o

```

I intend write the value in variable in staircase. I am thinking create a loop where I split the value assigned on variable to each position of the array and after write each position based in index array and for each position I add space more one! This means each times use the loop increase one more space than it he previous loop.

This is the best solution?

---

### Post by TheFu on 2016-09-30
This reads like a homework assignment. Cannot help without you posting code. Why use a loop at all? Modify the string and print it.  Sometimes the simplest answer is the best.

---

### Post by sed_faster on 2016-09-30
More a less!
I haven't started yet build the code, I wanted a mentor before starting.

> 
Sometimes the simplest answer is the best.


I understand, I use loop at all because I am learning shell script and I resolve all with a good loop :)
Are you suggest use a sed or something like?

thanks

---

### Post by steeldriver on 2016-09-30
I'm not saying this is a "good" way to do it, but in pure (bash) shell you could do

```

for ((n=0;n<${#var};n++)); do 
  s=${var:0:$n}
  printf '%s%c\n' "${s//?/ }" "${var:$n:1}"
done

```

FYI perl has some nice [repetition and concatenation operators]("http://perlmaven.com/string-operators") that allow you do so stuff like

```

perl -lne 'print " " x $n++ . $_ for split ""' <<< "$var"

```

---

### Post by Keith_Helms on 2016-10-02
Here's one way:

```
#!/bin/bash

word="hello"
spaces=""
for ((i=0; i<${#word}; i++)); do
   echo "$spaces${word:$i:1}"
   spaces="$spaces "
done
```

---

