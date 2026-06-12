---
title: "basic bash question"
date: 2010-10-19
forum: Programming Talk
---

### Post by daveli on 2010-10-19
Hi list,

I want to divide the number of lines in a text file by a number. I know how to get the number of lines with wc -l and also how to do simple maths with expr, but is it possible to pipe the output of the first to the second command? I tried with 

$wc -l mytext | expr /2

but of course it did not work

Thanks,

D.

---

### Post by Barrucadu on 2010-10-19
```
expr `wc -l mytext | sed 's: .*::'` / 2
```

---

### Post by ksprasad on 2010-10-19
Hi,
 
 You can do it in this way.
 
 expr `wc -l mytext | cut -d " " -f1` / 2
 
regards,
ksprasad

---

### Post by geirha on 2010-10-20
Don't use expr in bash, it's pointless. Bash can do everything expr can, and better.

```
echo "$(( $(wc -l < mytext) / 2 ))"
```

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by ghostdog74 on 2010-10-20
Bash is useless when it comes to floating points, if your number of lines is odd, that is.

you should really learn how to use awk instead

```

awk 'END{print NR/2}' file

```

that's it.

---

