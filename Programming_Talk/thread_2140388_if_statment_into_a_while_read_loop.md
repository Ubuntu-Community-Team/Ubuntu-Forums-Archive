---
title: "if statment into a while read loop"
date: 2013-04-29
forum: Programming Talk
---

### Post by spiritech on 2013-04-29
how do i add an if statement into a while read statement?

file contains

```
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
```

```
while read n; do if [[ $n -le 5 ]]
                  then echo "$n"
                  else echo "n is greater than 5"

fi

done < file
```

spiritech

---

### Post by Vaphell on 2013-04-29
where is the problem? the code works just fine.

---

### Post by spiritech on 2013-04-29
yes, sorry. the original code was a little longer and the problem was with an until statement in the if condition. i didnt check the code after i had shortened it down.

---

