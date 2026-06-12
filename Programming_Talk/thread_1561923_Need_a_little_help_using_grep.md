---
title: "Need a little help using grep"
date: 2010-08-26
forum: Programming Talk
---

### Post by |Enraiha on 2010-08-26
I'm trying to use grep to filter a command output. What I need to do is search for lines matching certain patterns and print out a specific number of lines after it. I can get it working properly searching for one pattern;
[I]
command[/I] | grep -A NUM [I]pattern1

[/I]but I need to do this for two patterns and have a different number of trailing lines for the second pattern. I've tried this but it doesn't work:redface:

command | grep -A NUM pattern1|grep -A NUM pattern2

Does anyone know how I can achieve this?

Thanks.:)

---

### Post by bcz on 2010-08-26
What the pipe symbol ('|') does is direct the output to another program, so we look for the second string in the lines containing the first string, which is probably not what you want.

Replace the pipe symbol with a ';' and you will run both greps, but you need to specify an input source

Rgds BillC

---

### Post by |Enraiha on 2010-08-26
I tried;

command | grep -A NUM pattern1 ; grep -A NUM pattern2

and the first grep displays its output but the terminal just hangs on  the second one (requires Ctrl + c). What do you mean by "specify an input source"?

---

### Post by Toz on 2010-08-26
How about:

command | grep -A NUM pattern1 && command | grep -A NUM pattern2

May not be the most efficient, but will work.

/ToZ

---

### Post by |Enraiha on 2010-08-27
Thanks for your help guys:D
I've managed to write a script that outputs what I needed.

VAR1=$(*command*)

echo "$VAR1" | grep -A [I]x pattern1
[/I]echo "$VAR1" | grep -A *y pattern2*

---

### Post by DaithiF on 2010-08-27
Hi,
you can combine multiple patterns in a single search.

either 
```
grep -A 'pattern1\|pattern2' somefile

```or
```
grep -EA 'pattern1|pattern2' somefile
```

---

