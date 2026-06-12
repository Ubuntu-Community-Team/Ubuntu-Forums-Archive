---
title: "use of grep [p]attern"
date: 2013-10-14
forum: Programming Talk
---

### Post by vasa1 on 2013-10-14
[FONT=Courier New]**ps aux | grep xfce**[/FONT] gives:
[FONT=Courier New][B]vasa1   1656  0.0  0.2 234672  9036 ?        Ssl  14:14   0:00 xfce4-power-manager
vasa1   1668  0.0  0.0   6348  2296 ?        S    14:14   0:00 /usr/lib/i386-linux-gnu/xfce4/xfconf/xfconfd
vasa1   3723  0.0  0.0   5652   836 pts/1    S+   17:06   0:00 grep --color=auto xfce[/B][/FONT]

But [FONT=Courier New]**ps aux | grep [x]fce**[/FONT] gives only the first two lines and excludes the unwanted line with "**grep --color=auto xfce**":
[FONT=Courier New][B]
vasa1   1656  0.0  0.2 234672  9036 ?        Ssl  14:14   0:00 xfce4-power-manager
vasa1   1668  0.0  0.0   6348  2296 ?        S    14:14   0:00 /usr/lib/i386-linux-gnu/xfce4/xfconf/xfconfd[/B][/FONT]

Now, if I save the first (three-line) output to a file, **xfce.txt**, and run:
[FONT=Courier New]**grep xfce xfce.txt**[/FONT] or
[FONT=Courier New]**grep [x]fce xfce.txt**[/FONT] or
[FONT=Courier New]**cat xfce.txt | grep xfce**[/FONT] or
[FONT=Courier New]**cat xfce.txt | grep [x]fce**[/FONT]

I get the same results: all three lines. So why does **grep [p]attern** behave differently?

---

### Post by steeldriver on 2013-10-14
When you use 

```
ps aux | grep [x]fce
```

the grep command appears in the ps list with a literal [x] i.e.

```
vasa1  3723 0.0 0.0 5652 836 pts/1 S+ 17:06 0:00 grep --color=auto -v **[x]fce**
```

which doesn't match the *regex* [x]fce. In contrast, when you run grep against the *file*, the grep line is just

```
vasa1 3723 0.0 0.0 5652 836 pts/1 S+ 17:06 0:00 grep --color=auto **xfce**
```

which does match the [x]fce regex

---

### Post by Vaphell on 2013-10-14
no, you can't save these 3 lines. Grep line should be different because when you test with *grep [x]fce* you should have exactly that in the input as well, not previous *grep xfce*
[x]fce will match your 'grep xfce' in file, but wouldn't match 'grep [x]fce' that should be there

```
$ test=[COLOR="#0000FF"]xfce[/COLOR]
$ echo -e "${test//[\[\]]}\ngrep $test"
[COLOR="#0000FF"]xfce[/COLOR]
grep [COLOR="#0000FF"]xfce[/COLOR]
$ echo -e "${test//[\[\]]}\ngrep $test" | grep "$test"
[COLOR="#0000FF"]xfce[/COLOR]
grep [COLOR="#0000FF"]xfce[/COLOR]

$ test=[COLOR="#0000FF"][x]fce[/COLOR]
$ echo -e "${test//[\[\]]}\ngrep $test"
[COLOR="#0000FF"]xfce[/COLOR]
grep [x[COLOR="#FF0000"]][/COLOR]fce     <- this thing on the input side won't get matched by the regex
$ echo -e "${test//[\[\]]}\ngrep $test" | grep "$test"
[COLOR="#0000FF"]xfce[/COLOR]
```

x]fce (5 chars) is not matched by [x]fce regex describing 4 chars

---

### Post by vasa1 on 2013-10-14
I'm really sorry but I'm still not getting it.

The way I see it: 
in **ps aux | grep xfce**, I'm asking grep to return all lines with the string **xfce** in them; that's all, no other requirement.
in **ps aux | grep [x]fce**, I'm asking grep to return all lines with the string **fce**, preceded by "x". So the results *should* be the same and *should* include the line with "grep --color=auto xfce". I can't get the reasoning behind the exclusion of the line with "grep --color=auto xfce".

I even tried **ps aux | grep x[fce]**, which found all lines with "x" followed by "f" or "c" or "e". So I got a few more lines like:
vasa1   1680  0.0  0.4 268164 17456 ?        Sl   14:14   0:02 **xf**desktop
vasa1   1736  0.0  0.0  15860  2684 ?        Sl   14:14   0:00 /usr/lib/i386-linux-gnu/libmenu-cache2/libe**xe**c/menu-cached
vasa1   2554  0.0  0.0  55000  3704 ?        Sl   14:53   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.3 /org/gtk/gvfs/e**xe**c_spaw/0
but still no line with "grep --color=auto xfce".

---

### Post by Vaphell on 2013-10-14
long story short: learn to regex :D

[...] is not there to break the flow of the string just for kicks, but with no meaning otherwise, it's a thing that describes character classes
[x] = 1 'x',
[fce] = 1 ('f' or 'c' or 'e')
[0-9] = 1 digit
[a-z] = 1 lowercase ascii char

[x]fce = 1 char from the set of ('x') + 'fce' = 4 chars
x[fce] = 'x' + 1 char from the set of ( 'f', 'c', 'e' ) = 2 chars.

---

