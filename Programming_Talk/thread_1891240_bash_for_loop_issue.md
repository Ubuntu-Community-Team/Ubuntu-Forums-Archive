---
title: "bash for loop issue"
date: 2011-12-05
forum: Programming Talk
---

### Post by Drenriza on 2011-12-05
i have a text file containing numbers. Each number is separated by a newline.
example
1
2
3
4
600
2310
and so on.

I would like with a for or while loop to count the characters on each line. And only if the line is equal to 5 characters, should that line be printed. But i cant quite get their.

So far i have worked with

```
for i in `cat file`; do echo $i |wc -m; done
```
which print the length in characters of each line. But how can i say

if line == 5, print it. I tried with this, but it docent work.

```
for i in `cat file`
do
if [ "$i |wc -m" == "5" ]
then
echo $i
fi
done
```

So what am i doing wrong here?

Thanks on advance.
Kind regards.

---

### Post by Lars Noodén on 2011-12-05
One thing is that the [test](http://manpages.ubuntu.com/manpages/precise/en/man1/test.1posix.html) to compare numbers is [font=Courier New]-eq[/font] rather than = or ==.

```

for i in $(cat file); do 
  if [ 5 -eq $(echo "$i" |wc -m) ]; then 
    echo $i; 
  fi; 
done

```

See also [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by Drenriza on 2011-12-05
> **Lars Noodén said:**
> One thing is that the [test](http://manpages.ubuntu.com/manpages/precise/en/man1/test.1posix.html) to compare numbers is [font=Courier New]-eq[/font] rather than = or ==.

```

for i in $(cat file); do 
  if [ 5 -eq $(echo "$i" |wc -m) ]; then 
    echo $i; 
  fi; 
done

```

See also [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Thanks for the help and guide.
Kind regards.

---

### Post by Vaphell on 2011-12-05
pure bash
```
while read i; do if [ **${#i}** -eq 5 ]; then echo $i; fi; done < file
```

what about grep '^.....$' or grep -E '^.{5}$'?
or sed -n '/^.....$/p'? :)

---

### Post by Lars Noodén on 2011-12-05
> **Vaphell said:**
> pure bash
```
while read i; do if [ **${#i}** -eq 5 ]; then echo $i; fi; done < file
```

You truly rock.

---

### Post by sisco311 on 2011-12-05
> **Vaphell said:**
> POSIX:
```
while read i; do if [ **${#i}** -eq 5 ]; then echo $i; fi; done < file
```

fixed :)

In bash I'd use: **if (( ${#i} == 5 )); ...**

---

### Post by Drenriza on 2011-12-05
Hi guys.
 
Thanks for all the awesome replies.
>  
what about 
grep '^.....$' 
grep -E '^.{5}$'
sed -n '/^.....$/p'

 
I have no idea what all the '^.....$' and so on does. But if you have any good bash guides, i will read them :p

---

### Post by Lars Noodén on 2011-12-05
> **Drenriza said:**
> I have no idea what all the '^.....$' and so on does. But if you have any good bash guides, i will read them :p

The caret (^) stands for the start of the line.
Each dot stands for separate character.
The dollar sign ($) stands for the end of the line.

So it will match lines that are exactly 5 characters long.

[http://www.zytrax.com/tech/web/regex.htm](http://www.zytrax.com/tech/web/regex.htm)
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)

---

