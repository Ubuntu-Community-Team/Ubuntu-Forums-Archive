---
title: "md5 hash of a string in shell script"
date: 2007-08-22
forum: Programming Talk
---

### Post by @vijay@ on 2007-08-22
the question is simple 
is it possible to find the md5 hash of a stiring (not of a file) in shell script ;

---

### Post by AlexThomson_NZ on 2007-08-22
Yep, just use md5sum with no options, type your text and press CTRL+D

---

### Post by Mr. C. on 2007-08-22
```
echo "Hello" | md5sum
```

MrC

---

### Post by @vijay@ on 2007-08-23
thanx alot ;:popcorn::popcorn:

---

### Post by pueblo235 on 2007-12-06
Hello, 

I have the same Problem, need to use md5sum for Strings in Shell. But the answer  by Mr. C. is not correctly. Since

> 
~$ echo "Hello" | md5sum 
09f7e02f1290be211da707a266f153b3  -
~$ echo "Hello" >test; md5sum test
09f7e02f1290be211da707a266f153b3  test
Any other suggestion. 

mw

---

### Post by pueblo235 on 2007-12-06
ok, nice trail, but wrong execution.

> 
~$ echo -n 'Hello' | md5sum
8b1a9953c4611296a827abf8c47804d7 


now, I had md5 from a String.


greets
mw

---

### Post by Mr. C. on 2007-12-06
Both md5sums in your prior post are the same, so I think you've proved it does work!

Echo by default prints a newline, and of course that newline is part of the string passed through the filter to md5sum.  You have to know exactly what you are passing; when you are unsure, use od:

```
$ echo "Hello" | od -bc
0000000  110 145 154 154 157 012                                        
           H   e   l   l   o  \n                                        
0000006
```

MrC

---

### Post by moodsey211 on 2009-06-11
Hi guys,

Your answer are very helpful if you just want to print the md5 of the string.  But what if you want to store it in a variable for later use?

Any suggestions how to do this?

Best regards,
moodsey

---

### Post by ad_267 on 2009-06-11
> **moodsey211 said:**
> Hi guys,

Your answer are very helpful if you just want to print the md5 of the string.  But what if you want to store it in a variable for later use?

Any suggestions how to do this?

Best regards,
moodsey

VARNAME=`echo -n "hello" | md5sum | awk '{print $1}'`

---

