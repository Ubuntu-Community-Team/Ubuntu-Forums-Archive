---
title: "[SOLVED] help understand a shell script line (tr sed and cat)"
date: 2008-08-12
forum: Programming Talk
---

### Post by king vash on 2008-08-12
```
cat "$@" | { tr '<>"\47 ' '[\n*]' | sed -n -e 's/href=//gI' -e 's/src=//gI' -e '/http:/Ip'
}
```
I know that it takes the input (an html file) and spits out all the urls in it. I know that cat "$@" reads in all the data and that the '[\n*] does adds a bunch of end lines but I do not understand the rest

---

### Post by Alasdair on 2008-08-13
the tr command is replacing any of the characters <,>,",' (\47) or a space with a newline, so for example:
```
> echo "<a href=\"http:://www.google.com\">link<\a>" | tr '<>"\47 ' '[\n*]'

a
href=
http:://www.google.com

link
/a


```

The sed command (look up the sed manual - it's a pretty feature-rich little program) then just filters out the non-urls, giving you your list of urls. You could get rid of the tr bit entirely by using sed to do what it does (an exercise for the reader perhaps ;))

---

### Post by king vash on 2008-08-13
Thanks very much! I understand all but one little thing.
It filters '<' '>' ' ' and \47 what is \47 is that characture code 47? or what


I have a couple of questions about sed. I see that I can use sed s/oldstring/newstring to do what the tr does right now. How do I get it to change the entire string.

```

echo day day day | sed s/day/night/ 

returns

night day day

```

this is most of it I think
```

cat "$@" | sed -e 's:<::' -e 's:>::' -e 's:"::' -e 's: ::' | sed -n -e 's/href=//gI' -e 's/src=//gI' -e '/http:/Ip'

```

---

### Post by ghostdog74 on 2008-08-13
> **king vash said:**
> Thanks very much! I understand all but one little thing.
It filters '<' '>' ' ' and \47 what is \47 is that characture code 47? or what

[/code]

check the ascii table. Its either a single quote or double quote.

> 
I have a couple of questions about sed. I see that I can use sed s/oldstring/newstring to do what the tr does right now. How do I get it to change the entire string.

use the g modifier
```

echo day day day | sed s/day/night/g
```

---

