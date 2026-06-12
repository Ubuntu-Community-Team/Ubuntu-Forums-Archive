---
title: "Is there any difference between *s++, (*s)++ in C"
date: 2008-08-08
forum: Programming Talk
---

### Post by sharks on 2008-08-08
Is there any diff between *s++,(*s)++ in C

---

### Post by Zugzwang on 2008-08-08
Why don't you just try both statements in an example program?

---

### Post by theuninvitedguest on 2008-08-08
Depends on which of the operators {*,++} is stronger

---

### Post by NovaAesa on 2008-08-08
According to this: [http://www.cppreference.com/operator_precedence.html](http://www.cppreference.com/operator_precedence.html), it seems that they will be very differcent. The post incriment opperator (++) has a higher precidence compared to the dereference operator (*). so:

*s++ will add one to the pointers value, and then that location will be dereferenced.

On the other hand, (*s)++ will dereference and then add one to the object (this will only work if the object is a numeric type or has some type of operator overloading happening).

I would think that you probably want the second one most times rather than not. It's normally a really bad idea to be messing around with directly manipulating pointers. You could get all sorts of unexpected things happening. Unless of course you know what you are delving into, in which case you wouldn't be asking this question :P

---

### Post by kknd on 2008-08-08
NovaAesa is right.

But the *s++ ir very usefull to.

Example: pick the substring after a dot:

[PHP]
const char* s = "Hello.world!";
char* ptr = s;

while(*ptr++ != '.');

printf("%s", ptr);
[/PHP]

---

