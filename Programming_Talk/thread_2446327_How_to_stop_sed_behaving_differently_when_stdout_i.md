---
title: "How to stop sed behaving differently when stdout is not a tty?"
date: 2020-06-28
forum: Programming Talk
---

### Post by &amp;KyT$0P# on 2020-06-28
Xubuntu 18.04.  To illustrate the issue:

First run this in Terminal -
```
bash -c 'for i in $(seq 1 5);do sleep 1;echo "$i";done' | sed 's/^/!!/g'
```

Notice how one line is printed every second.  That's good.

Now run this -
```
bash -c 'for i in $(seq 1 5);do sleep 1;echo "$i";done' | sed 's/^/!!/g' | cat
```

Now it...waits until the end, then suddenly prints everything? :-s

And it's not [FONT=Courier New]cat[/FONT] causing this -
```
bash -c 'for i in $(seq 1 5);do sleep 1;echo "$i";done' | cat
```

This second behavior of [FONT=Courier New]sed[/FONT] is hosing a script I'm trying to write.  How to force the first behavior of [FONT=Courier New]sed[/FONT], i.e. output lines in real time?

---

### Post by &amp;KyT$0P# on 2020-06-28
never mind, I think I found the answer: use [FONT=Courier New]sed -u[/FONT]

From [FONT=Courier New]man sed[/FONT] -
>        -u, --unbuffered

              load minimal amounts of data from the input files and flush the output buffers more often


---

