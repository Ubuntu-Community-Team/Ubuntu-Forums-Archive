---
title: "getline function behaviour"
date: 2005-11-25
forum: Programming Talk
---

### Post by bhupeshrawal on 2005-11-25
Hi,

    I was using ubuntu older version and i was able to compile my program. Now i installed Ubuntu-5.10. Initially i did apt-get install build-essential and solved the compilation problem. 

But now i encounter that my program in not behaving properly. In my application a child process reads a line from file using getline function as follows:

read = getline ( &line, &len, Filename] );

it got failed here. There was no compilation or linking error. I tried "man getline" but was not there on my system. Please help me out what i am missing.

thanks

---

### Post by Roptaty on 2005-11-25
You might want to install manpages-dev and glibc-doc. :)

---

