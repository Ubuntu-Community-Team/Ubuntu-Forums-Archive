---
title: "[SOLVED] SED: how to read from stdin and write the result to a file"
date: 2007-11-27
forum: Programming Talk
---

### Post by everthonvaladao on 2007-11-27
hi guys, 

i`m trying to write a script to collect RTTs from a given site, but i`m having some trouble to write the result to a file... :(

i`ve tried sed and awk, but i think the problem is something about pipes and streams, or maybe something about the 1st line...

```

ping www.google.com | sed -e 's/\(.*time=\)\([0-9]*\)\(.*\)/\2/'

```

ok, this prints to stdout the results i want, but when i try:

```

ping www.google.com | sed -e 's/\(.*time=\)\([0-9]*\)\(.*\)/\2/'** > rtt.txt**

```

the result file is empty!!! 

i test some other script:

```

ping www.google.com | grep time=

```

ok, this prints to stdout, but:

```

ping www.google.com | grep time=** > out.txt**

```

retunrs a empty file too... so i think that i`m doing some stupid thing with streams and pipes, but i`m new to shell programming, and i`ll be very grateful if you could help me to solve it... ;)

---

### Post by athomson on 2007-11-27
Hi,

Easy solution :-)

First, you should probably set a count.
Second, set the redirect to append, otherwise it will get the last entry which is often empty from a control-c as you break the ping

```
 ping www.google.com [COLOR="Red"]-c[/COLOR] 10 | sed -e 's/\(.*time=\)\([0-9]*\)\(.*\)/\2/' [COLOR="Red"]>>[/COLOR] rtt.txt
```

If you want to see what is going on do this:

```
 ping www.google.com -c 10 | sed -e 's/\(.*time=\)\([0-9]*\)\(.*\)/\2/' | tee -a rtt.txt
```

Andy

---

