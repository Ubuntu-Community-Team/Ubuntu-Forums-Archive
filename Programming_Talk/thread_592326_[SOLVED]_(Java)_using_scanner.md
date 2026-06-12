---
title: "[SOLVED] (Java) using scanner"
date: 2007-10-26
forum: Programming Talk
---

### Post by Balazs_noob on 2007-10-26
hi guys i have a problem with Scanner in Java ...
the problem is that i need to read  a date
with dots as delimiters ( like 2007.10.10.)
the date is in strDate and it is correct i checked with the eclipse debugger

i tried 
> 
        Scanner s = new Scanner(strDate);
        s.useDelimiter(".");
        
        System.out.println(s.nextInt());
        System.out.println(s.nextInt());
        System.out.println(s.nextInt());
which didn't worked, i tried with other delimiters like = and stuff and it worked great, but i need to use dot
any help is appriciated

p.s : i tried \. because it is a special character at Patterns,so i thought i can escape it with this  but it didn't worked

---

### Post by Ramses de Norre on 2007-10-26
You need to specify the delimiter like this:
```
s.useDelimiter("\\.");
```
This is a bit stupid, it's because you need to pass "\." to the regex engine, but if you type "\." in a string literal you say to the compiler to escape the "." character and pass that escaped value to the regex engine, which isn't what you want.
So to pass "\." to the regex engine you need to escape the first backslash.

---

### Post by Balazs_noob on 2007-10-26
:popcorn: it worked ;)
 thanks for the solution and explanation too :)

---

