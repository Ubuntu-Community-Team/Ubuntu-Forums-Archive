---
title: "calculator script"
date: 2012-11-15
forum: Programming Talk
---

### Post by Mia_tech on 2012-11-15
I have a simple script which takes three parameters in the form of

./script.sh 10 * 2

and produces an output, the script works find; however, it doesn't work when using multiplication 10 * 2. I know that * has a special meaning in linux, so how could I get around that. (Basically I'm using case statement for calculations)

---

### Post by pqwoerituytrueiwoq on 2012-11-15
use quotes
```
~$ gcalctool -s "10/3*(7+5-2)"
```

---

### Post by Vaphell on 2012-11-15
if you want to 'disable' special characters use \ or "" or '' (\* "*" '*')

---

### Post by Mia_tech on 2012-11-15
> **Vaphell said:**
> if you want to 'disable' special characters use \ or "" or '' (\* "*" '*')

yeah, I tried that (script.sh 10 \* 2) but I'm getting errors. Also if I use either "" or ' ' it will interpret the parameters as a single parameter right?

---

### Post by Vaphell on 2012-11-15
not if you type them like this:
```
script.sh 10 "*" 2
```
nobody forces you to wrap them all in a single pair of quotes :-)

---

### Post by Mia_tech on 2012-11-15
> **Vaphell said:**
> not if you type them like this:
```
script.sh 10 "*" 2
```
nobody forces you to wrap them all in a single pair of quotes :-)

I think the best way is to pass the arguments like: "10 \* 10", even though is a single param when you pass it to a functions you can still break it down into $1 $2 $3

Thanks

---

