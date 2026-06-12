---
title: "Problem with script"
date: 2012-05-09
forum: Programming Talk
---

### Post by DiegoTc on 2012-05-09
Hi
I am trying to make a script that tells me if the file "Hello" appears more than 5 times.

I have the script the following way

```


var = ls | grep -c Hello 
if [var >5];then
   echo "It appears more than 5"
else
   echo "It appears less than 5 times"
fi


```
I know that the problem is on the var. But I don't how to assigned the value that grep returns.

---

### Post by Bachstelze on 2012-05-09
```
var=$(ls | grep -c Hello)
```

No spaces!

---

### Post by DiegoTc on 2012-05-09
Solve
Thanks :)

---

### Post by Vaphell on 2012-05-09
```
[var >5]
```

that won't work either
here you need everything separated by spaces ( [ is a command, var is first param, > 2nd, 5 third, ] last )
besides var should be used with $ ($var) and > should be replaced with -gt (greater than)
alternatively if you are using bash you can use
```
if (( var > 5 ))
```
(()) switches to integer mode but it's not too portable to other shells.

---

### Post by sisco311 on 2012-05-09
The output of ls if formated for humans. It will cause bugs in scripts. You should use globs instead:
```

i=0
for _ in *Hello*
do
   #BASH
   ((i++))
   #POSIX
   #i=$((i+1))
done

#BASH
if (( i>5 ))
#POSIX
#if [ $i -gt 5 ]
then
   :
fi

```

---

