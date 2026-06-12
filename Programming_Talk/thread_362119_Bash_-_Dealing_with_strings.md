---
title: "Bash - Dealing with strings"
date: 2007-02-15
forum: Programming Talk
---

### Post by whistlingtony on 2007-02-15
Hi all,

I have a question! I've been stuck with the task of writing a little script at work. This is a case of "Hey, you know computers, do this." 

I've dorked around with shell scripts before. The basics are not a problem for me, but I've run into something I haven't had to deal with before.

I have a file with a number located on a certain line and always in the same position in that line. I need to read that number, and replace it with a new number. 

I'm using just the BASH shell for this. As I stare at various tutorials, I'm thinking I need to get Perl savvy real quick. 

I"m curious if anyone could point me in the right direction or give me a nice example to get me started? I'm a firm believer that one can do anything with enough patience and a good reference. I just need a little push in the right direction. There seems to be quite a bit of redundancy that I'm running into.

Thanks much!

-Tony

---

### Post by Arndt on 2007-02-15
> **whistlingtony said:**
> 

I have a file with a number located on a certain line and always in the same position in that line. I need to read that number, and replace it with a new number. 

I'm using just the BASH shell for this. As I stare at various tutorials, I'm thinking I need to get Perl savvy real quick. 

I"m curious if anyone could point me in the right direction or give me a nice example to get me started? I'm a firm believer that one can do anything with enough patience and a good reference. I just need a little push in the right direction. There seems to be quite a bit of redundancy that I'm running into.



```
sed -r -i -e '3s/(.{5})[0-9]+/\177/' myfile
```

Assuming your number consists only of digits and is located on line 3 in the file "myfile", with 5 characters before it on the line, the above command replaces it by 77. See the man page for 'sed' to find out exactly what is happening here. Or ask.

No doubt you can do it with Perl too.

---

