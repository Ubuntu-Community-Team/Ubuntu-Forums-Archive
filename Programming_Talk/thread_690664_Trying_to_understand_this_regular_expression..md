---
title: "Trying to understand this regular expression."
date: 2008-02-07
forum: Programming Talk
---

### Post by jingo811 on 2008-02-07
I've managed to understand how these work by trial-and-error from a great tutorial on google.  
```
bill@gates:~$ **grep 'Adri[ae].*' /usr/share/dict/words **
Adrian
Adrian's
Adriana
Adriana's
Adriatic
Adrienne
Adrienne's
bill@gates:~$ **grep 'Adri[a|e].*' /usr/share/dict/words **
Adrian
Adrian's
Adriana
Adriana's
Adriatic
Adrienne

```
But I can't figure out how this can be used by trial-and-error. :confused:
Can someone fill in the blanks for me and explain how this can be utilized?
```
'stree[color=red](t|v)[/color]ille'
```

---

### Post by stroyan on 2008-02-07
You need to use a -E option to get grep to handle the '(pattern1|pattern2)' syntax as an extended regular expression.
It will match either of the patterns.
The patterns can have multiple characters.

The 'Adri[a|e].*' pattern that you showed is not doing what you probably think it does.
The '|' character is not special between '[]' brackets.
That pattern will match 'Ad' followed by 'a' or '|' or 'e'.
```
$ grep 'Ad[a|e].*' << END
> Ada
> Adb
> Ade
> Ad|
> END
Ada
Ade
Ad|
$ 
```
(The ending '.*' doesn't really affect the lines that match since '.*' can match nothing and grep is willing to match in the middle of a line.)
If you are trying out patterns to see what they match you could learn a little bit more by adding a '--color=auto' option to color the matched part of each line.

---

### Post by aks44 on 2008-02-07
> **jingo811 said:**
> ```
'stree[color=red](t|v)[/color]ille'
```

As far as I can tell (based on my experience of PCRE, not sure if grep fully conforms to that) that regex matches either:

streetille
or
streeville

No more, no less. Incidentally it captures the v or t so that you can tell which one was matched (again, not sure grep can make use of captures / backreferences).

---

### Post by RIchard James13 on 2008-02-08
I use KregExpeditor because it can take a regex and display what it is. 
For stree(t|v)ille it says

```
           Alternatives
stree           t       ille
                v

```

---

### Post by jingo811 on 2008-02-09
Great advices and great program :)

---

### Post by jingo811 on 2008-02-09
[SIZE="4"]New problem[/SIZE]

I'm going by the table 1 from this website and want to send both standard output and error to a file.  I made it work on Debian yesterday but today at home I can't seem to get the same result on Ubuntu and I don't understand how to correct.  Help?
[http://www.linuxdevcenter.com/pub/a/linux/lpt/13_01.html#doc2ac15b1c13](http://www.linuxdevcenter.com/pub/a/linux/lpt/13_01.html#doc2ac15b1c13)
```
$ **find / -name \*.bash_history 2>&1 errall **
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]

$ **find / -name \*.bash_history errall2 2>&1**
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]


```

---

### Post by ghostdog74 on 2008-02-09
```

find /path -name "file*" &> out


```

---

### Post by jingo811 on 2008-02-09
```
find / -name \*.bash_history 2> /dev/null
find / -name \*.bash_history **&>** errall
```
Tnx :D

---

