---
title: "shell script, find frequency of chars in files"
date: 2009-05-22
forum: Programming Talk
---

### Post by monkeyking on 2009-05-22
Hi I got files which contents looks like
```

sdlhf\tas,od@d\n"lsdjf
asd\tasdf\n35rjl:
ads¨]@lih],lkjdskj\t\nasfd
dhfah"#¤5$,\n,lkjg\tjhh74kjregt
.

```
How do I find the frequency of each char?
If they had been space-seped, I would have done something like,
[PHP]
tr " " "\n" <inFile >tmp;
sort tmp |uniq -c
[/PHP]

thanks in advance

---

### Post by unutbu on 2009-05-22
This one comes courtesy of ghostdog74 from sometime, somewhere on the forum:

[PHP]awk 'BEGIN{FS=""}{for(i=1;i<=NF;i++)a[$i]++}END{for(i in a) {print i,a[i]}}' file[/PHP]

---

### Post by monkeyking on 2009-05-22
This looks very reasonable. And will work for the question asked.

But In my concrete case, the situation is abit more complicated,
and I think the solution is quite easy.
The string from which I want to  find the distribution of  the chars.
Is actually not the only field on the line, each field is seperated by tab, and the string is the 3th field.
Can I define a subfieldseperator for a awk statement?

The file is actually something like

```

idname <tab> idnumber <tab> CHARS <endline>

```

I know I could of cause do

```

cut -f3 inFile | awk 'BEGIN{FS=""}{for(i=1;i<=NF;i++)a[$i]++}END{for(i in a) {print i,a[i]}}'

```

But there might be a faster way?

---

### Post by ghostdog74 on 2009-05-22
> **monkeyking said:**
> 
```

idname <tab> idnumber <tab> CHARS <endline>

```

I know I could of cause do

```

cut -f3 inFile | awk 'BEGIN{FS=""}{for(i=1;i<=NF;i++)a[$i]++}END{for(i in a) {print i,a[i]}}'

```

But there might be a faster way?

do everything in awk
```

awk '{ for(o=1;o<=length($3);o++){a[substr($3,o,1)]++ }}END{ for (i in a) print a[i],i}' file

```

---

