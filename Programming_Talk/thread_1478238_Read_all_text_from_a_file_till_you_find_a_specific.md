---
title: "Read all text from a file till you find a specific word Unix Scripting"
date: 2010-05-09
forum: Programming Talk
---

### Post by hakermania on 2010-05-09
I have a file wich look like this:
**blablablablabla@gmail.com:78632485796238756293847564447:blablablablabla**
well, what I want is to read [email]blablablablabla@gmail.com[/email] and nothing else. How can I do this? All this is one the same line and the name (blablablablabla) is not stable (so I cannot use **username=`expr substr $INPUT 5 8` **becauz the username is not always the same! )
I imagine that I should use something that reads the file till .com or .fr or any other extension like .ru, .gr, .it etc............. Hope it isn't too difficult!

---

### Post by soltanis on 2010-05-09
If the file is always delimited by ":" like that, then you can use this awk program.

```

awk 'BEGIN{IFS=":"} $1 ~ /\.[[:alnum:]]{1,5}/ { print $1 }' [file]

```

Maybe. I never did have much luck with awk regexps.

---

### Post by Portmanteaufu on 2010-05-09
You could also do:
```

grep -Po '[\w\.]+@[\w.]+\.[\w]+' filename.txt

```

That'll spit out all the e-mail addresses in the file. You could also put a ^ at the beginning of the pattern (right in front of the first '[' ) to make it only print e-mail addresses appearing at the beginning of a line.

---

### Post by raf_kig on 2010-05-09
If the delimiter is always a colon you can just use cut:

```
cut -d: -f1 /path/to/the/file
```

Regards,

raf

---

