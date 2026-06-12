---
title: "X Terminal- Maemo Nokia N900"
date: 2013-02-21
forum: Programming Talk
---

### Post by Holy bible on 2013-02-21
Hi guys. So I got one problem which I cannot solve myself anymore.
I was trying to do programing in my "new" mobile phone Nokia N900 which runs on Maemo 5 (Linux-based).

Firstly I was following guides how to install GCC on it and I was successful because I installed it and you run it as : gcc-4.2 <source code>   or   g++-4.2 <source code>
so I made myself a really noobish program just to try how it works.
I work in C so this was the source:

#include <stdio.h>
int main()
{
 int i;
 for(i=0; i<10; i++)
  printf("Hello, world\n");
return 0;
}

just simple hello world. So and where is the problem. I wrote this source by "nano" which i also installed but just by simple method (Maemo "app store" and just downloaded nano program)
so no intricate methods.
Okey I used nano and wrote this code. I saved it as prog.c
Now as in Ubuntu (I got some beginner skills from programing in ubuntu so this is why im putting question) i used gcc to compile it so

gcc-4.2 prog.c

as in Ubuntu it made for me "a.out".

and now. the problem is clear. When i do ---> ./a.out
it returns me:           /bin/sh: ./a.out: Permission denied    

and I REALLY DON'T KNOW what to do with that problem.
I hope you guys can solve this problem. Thanks a lot in advance ):P

---

### Post by Holy bible on 2013-02-22
Okey :D so now I got it solved. Problem was that I got output - "a.out" saved in MyDocs which is FAT so it won't give you permission :)

SOLVED!

---

