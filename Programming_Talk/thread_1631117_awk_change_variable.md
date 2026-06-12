---
title: "awk change variable"
date: 2010-11-26
forum: Programming Talk
---

### Post by wanna_try on 2010-11-26
Hi.
How to change string variable in awk?
for example, I parse with awk script text file named some_name_with_extension.txt

I want to print only some_name in my script

```
....
varCompName = FILENAME
print varCompName
```

How to put not all symbols from FILENAME to variable?
thank you
This make my day

In windows I used some of next 
```
%my_var:~0,-2%
```

would extract all but the last 2 characters of the my_var variable.

---

### Post by Arndt on 2010-11-26
> **wanna_try said:**
> Hi.
How to change string variable in awk?
for example, I parse with awk script text file named some_name_with_extension.txt

I want to print only some_name in my script

```
....
varCompName = FILENAME
print varCompName
```

How to put not all symbols from FILENAME to variable?
thank you
This make my day

In windows I used some of next 
```
%my_var:~0,-2%
```

would extract all but the last 2 characters of the my_var variable.

Doing "man awk" and searching for "substr" brought up this text:

```
       substr(s, i [, n])      Returns  the at most n-character substring of s
                               starting at i.  If n is omitted, the rest of  s
                               is used.
```

---

