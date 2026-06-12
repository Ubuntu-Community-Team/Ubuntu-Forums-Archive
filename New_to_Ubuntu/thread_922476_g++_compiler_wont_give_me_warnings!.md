---
title: "g++ compiler wont give me warnings!"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by jyar727 on 2008-09-17
Hi, I compile a couple of programs using

g++ -Werror -Wall -m32 etc.
however I noticed that I dont get warnings on some things.

For example:
double a = 2.0;
int y;
y=a;

This wont show up as a warning, but compiling on redhat would give me a warning... I just wanna be able to get these kinds of warnings on my own system other than having to compile on school computers to check. 

suggestions? 

thanks

---

### Post by ggaaron on 2008-09-17
Have you checked what versions of gcc are this? Probably you are just using different ones and this makes the difference.

---

### Post by jyar727 on 2008-09-17
hmm alright. I guess g++ 4.2 doesnt check if u set an int to a double? i'll see what version the school one is... if i can...

---

### Post by ggaaron on 2008-09-18
I tried gcc 4.3 and it didn't warn me either, quite strange=/

---

### Post by jyar727 on 2008-09-18
*sigh* I guess i'll be compiling somewhere else :-(. Thanks for the input!

---

