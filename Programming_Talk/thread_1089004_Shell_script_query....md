---
title: "Shell script query..."
date: 2009-03-06
forum: Programming Talk
---

### Post by spongemonkey on 2009-03-06
Hi guys,
I'm writing a shell script and as part of it I want to be able to get a certain piece of information that ffmpeg outputs when it runs. So I set
```
my_variable="$(ffmpeg -i my_file)"
```
planning to extract what i need later.

To test everything was going as planned I then tried outputting it
```
echo "my_variable"
```
(there are spaces in each of the strings, hence the double quotes, you'll be able to tell me whether I need them or not...)

When the top line executes the output of ffmpeg is printed in the terminal, but nothing outputs after the second line, and indeed nothing has been assigned to the variable.

Any thoughts guys?

Cheers

---

### Post by slavik on 2009-03-06
echo "$my_variable";

also, ffmpeg might be outputting things to stderr, but $() captures stdout.

---

### Post by geirha on 2009-03-06
> **spongemonkey said:**
> 
```
my_variable="$(ffmpeg -i my_file)"
```

That will catch stdout of the ffmpeg command, but ffmpeg is probably sending a lot (or all) of the output to stderr. To catch stderr as well, you'll need to redirect stderr to stdout for that command.
```
my_variable="$(ffmpeg -i my_file 2>&1)"
```

> **spongemonkey said:**
> 
```
echo "my_variable"
```

Is that a typo? It should be ```
echo "$my_variable"
```

---

### Post by spongemonkey on 2009-03-06
Yes ofc, oops, I meant $my_varible. Will give the suggestions a bash (get it lol?... er)

---

### Post by spongemonkey on 2009-03-06
Excellent guys, thanks very much

---

