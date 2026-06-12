---
title: "Perl debugger and history / readline"
date: 2006-10-28
forum: Programming Talk
---

### Post by Lard!!! on 2006-10-28
Hello!

I have a problem with the PERL debugger. It seems as if the history function is not properly set up. When I start "perl -d someprogram.pl" and I try to recall the last command by using the "up" arrow key I get a "^[[A". 
I remember that I tried to figure out what's going on when I had Ubuntu 6.6 installed but I was not able to solve the problem. 
Now I've installed Ubuntu 6.10 and I'm very happy with it but for this stupid problem. 
Does anybody know a solution for that?

Thank you!
Lard!!!

---

### Post by ggathrig on 2006-11-01
I have the very same question.  Anyone have an answer?  Thanks.

---

### Post by Lard!!! on 2006-11-01
I found the solution. One has to install the Package "libterm-readline-gnu-perl"

Have fun!

---

### Post by ggathrig on 2006-11-01
That worked.  Thanks!
GG

---

### Post by fbicknel on 2012-04-27
Any way to get vi readline functionality?  libterm-readline-gnu-perl is great with arrow keys (better than nothing), but having vi functions available is very productive.

---

### Post by fbicknel on 2012-04-27
[http://packages.debian.org/sid/libterm-readline-zoid-perl](http://packages.debian.org/sid/libterm-readline-zoid-perl)

Thought that was it, but it doesn't seem to work.  Didn't break anything, but didn't make the debugger work as I was hoping.

---

