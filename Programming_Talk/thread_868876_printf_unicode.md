---
title: "printf unicode"
date: 2008-07-24
forum: Programming Talk
---

### Post by kamel81 on 2008-07-24
executing this command:
printf "\u0041" > /pippo

I found in pippo file \u0041, when I attempt an "A"


executing the command:
printf "\x41" > /pippo

In pippo file I found an "A" (correct!)

Any suggestion?

thanks,
Alex

---

### Post by nvteighen on 2008-07-24
Because hex 0x41 is an 'A' in ASCII (dec 65)... AFAIK, Unicode inherits the same hex codes for the old ASCII characters.

---

### Post by kamel81 on 2008-07-24
ok, but how do I write an "A" with unicode format and printf command?

thanks :)

---

### Post by nvteighen on 2008-07-24
The issue lies in that we actually have two different printf:

1. GNU bash's built-in printf, which doesn't seem to support Unicode.
2. /usr/bin/printf, which is what you want.

But, /usr/bin/printf seem to print characters that are exclusively Unicode? So ASCII characters should be printed with "\x"?
```

ugi@UGI:~$ /usr/bin/printf "\u0041"
/usr/bin/printf: el nombre de carácter universal \u0041 es inválido

```
("Invalid universal character name \u0041"... loosely translated)

This works:
```

ugi@UGI:~$ /usr/bin/printf "\u0141\n"
&#321; 

```

---

