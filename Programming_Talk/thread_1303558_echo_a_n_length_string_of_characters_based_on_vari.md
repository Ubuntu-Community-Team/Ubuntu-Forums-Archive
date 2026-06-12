---
title: "echo a n length string of characters based on variable value"
date: 2009-10-28
forum: Programming Talk
---

### Post by kakotako on 2009-10-28
I am writing a bash script that will take quick measurements and visualize them on screen in a form of a scrolling histogram.

Everything works well except that the below excerpt prints "|" characters one by one instead of all at once. This looks cool but is of no consequence for my measurements and just adds latency to the measurement taking.

```
while [ "$i" -le "$MaxValue" ]
 do
  echo -n "|"
  i=`expr $i + 1`
done
```

I would match rather get rid of the WHILE loop and use ECHO alone if there was a way to make echo print a $MaxValue length of "|" characters in a single statement.

If that's impossible I was thinking using if/then statements, one for each $MaxValue from 1 to 80. I tested it and it works fast but it doesn't seem very elegant.

Thanks all. I am a bash script beginner so be easy on me.

---

### Post by ghostdog74 on 2009-10-28
maybe i don't understand your problem, but you can use printf instead of echo

---

### Post by Arndt on 2009-10-28
> **kakotako said:**
> I am writing a bash script that will take quick measurements and visualize them on screen in a form of a scrolling histogram.

Everything works well except that the below excerpt prints "|" characters one by one instead of all at once. This looks cool but is of no consequence for my measurements and just adds latency to the measurement taking.

```
while [ "$i" -le "$MaxValue" ]
 do
  echo -n "|"
  i=`expr $i + 1`
done
```

I would match rather get rid of the WHILE loop and use ECHO alone if there was a way to make echo print a $MaxValue length of "|" characters in a single statement.

If that's impossible I was thinking using if/then statements, one for each $MaxValue from 1 to 80. I tested it and it works fast but it doesn't seem very elegant.

Thanks all. I am a bash script beginner so be easy on me.

You can construct the string in a loop, and then output it:

```
i=0
s=""

while [ $i -le 10 ]
do
    s="|$s"
    i=`expr $i + 1`
done

echo $s
```

---

### Post by geirha on 2009-10-28
```
printf "%.s|" {1..10}
```

BTW, expr is a command used in ancient shells to do arithmetics. POSIX shells, including bash, has special syntax for it.
```
a=2 b=3; echo $((a+b))
```

If you want to learn bash-scripting properly, read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by kakotako on 2009-10-29
> **geirha said:**
> ```
printf "%.s|" {1..10}
```


This works but I could not figure out how to use a variable in place of "10" in {1..10}. I looked around and found this:

```
length=40
printf -v line '%*s' "$length"
echo ${line// /-}

```

which runs faster some 30% than what I had before. I still prefer your single line solution if I could get it to work. Thanks for the excelent link too.

---

### Post by geirha on 2009-10-29
Well, you could make a function ...
```

repeat() { # $1 - string to repeat, $2 - number
  (($# == 2)) || return   # number of arguments is two, else return
  local i
  for ((i=0; i < $2; i++)); do
    printf '%s' "$1"
  done
}

$ repeat ha 10
hahahahahahahahahaha

```

---

### Post by kakotako on 2009-10-29
Thanks Geirha. I am humbled by your scripting skills. I slightly modified your suggestion using a function and my script now runs 33% faster than before.

---

