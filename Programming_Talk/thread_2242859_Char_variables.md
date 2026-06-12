---
title: "Char variables"
date: 2014-09-04
forum: Programming Talk
---

### Post by spacerocket on 2014-09-04
Hello,

If I want to initialize a char variable containing one letter, should I write

char [1]= {c};   or

char c=[1];    or

char c=1;

If I then want to read the users input should it be 

cin>> 'c'; ?

---

### Post by TheFu on 2014-09-04
char c = '1';
Assuming C/C++.

However, there is very little real use of have a single character in most programs these days.  Can't support UTF8/16/32 with those and assuming 7-bit ASCII is dangerous.

Don't know about other languages - which are you trying to use?  That might get you a better answer.

---

### Post by bak&#305;r on 2014-09-05
I suppose this is c++? What are you trying to do? Declare a variable named c or declare another variable whose value is 'c'?

---

### Post by lisati on 2014-09-05
If I have understood the question properly, it's about a variable to hold a single character, in which case it would be defined something like this:
```

     char c;

```
You can then do something like this:
```

     c='A';

```

Reference: [http://www.le.ac.uk/users/rjm1/cotter/page_22.htm](http://www.le.ac.uk/users/rjm1/cotter/page_22.htm)

---

### Post by spacerocket on 2014-09-05
Yes, I actually want to test the user`s input, can I write something like

```


char c;
c='|';

cout<<" To quit the program, enter |";
cin>> "c";

if ('c' == '|' ) { return 0;}

else {}                             // Do nothing


```

---

### Post by sisco311 on 2014-09-05
From the [Posting Guidelines:]("http://ubuntuforums.org/showthread.php?t=2158945")  


> 8.    While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.


Thread closed.

---

