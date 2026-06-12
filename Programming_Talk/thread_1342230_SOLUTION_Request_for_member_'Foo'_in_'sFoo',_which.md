---
title: "SOLUTION: Request for member 'Foo' in 'sFoo', which is of non-class type 'sth'"
date: 2009-11-30
forum: Programming Talk
---

### Post by Call My Function on 2009-11-30
I was going to post a question about this, but managed to figure out the solution on my own. Since others might have similar problems, I'll post my solution for anyone who's looking for one.

I'm currently "bullet proofing" a class I've written, and to help me I wrote a small function that displays some info:
[php]void debug()
{
   cout << "0 = F, 1 = T\n";
   cout << "MapC: " << getMapC() << endl;
   cout << "MapR: " << getMapR() << endl;
   cout << "Empty: " << isEmpty() << endl;
   cout << "typeIcons: " << iconsSet() << endl;
   cout << "numIcons: " << numIcons << endl;
}[/php]This is a **public class** function that is inline.

I wrote a program to test my constructors:
[php]#include <iostream>
#include "tw_btmap.h"
using namespace std;

int main()
{
   btMap mappy();

   //CheckMap
   mappy.debug();

   return 0;
}[/php]When I tried to compile, I got this error:
[php]btmtest.cpp: In function ‘int main()’:
btmtest.cpp:10: error: request for member ‘debug’ in ‘mappy’, which is of non-class type ‘btMap()’
[/php]I spent the next hour or so tearing my hair out trying to figure out why it wasn't working. I'd written a THOUSAND functions just like it before and they worked fine. But then I noticed that *none* of my class functions were working anymore -- it's like the class had broken.
I also noticed that my constructors weren't being called anymore... *then* I noticed...
[php]btMap mappy();[/php]First of all, my class has **two** constructors -- a default one, and one that accepts some arguments. Previously I had been testing the latter constructor and had deleted the arguments sent to it -- but I left the **brackets**.
I took the brackets out and, viola, works as happily as a purring kitten.
From what I can tell, the above line calls the *second* constructor -- the one that takes arguments -- but it doesn't create anything. Hence, the errors.

SO, the moral of the story is such:
If you're getting that error for some strange reason, take a look at your object declaration. If you want to use the default constructor, **DO NOT** leave empty brackets on the end.

I hope this helps.

---

### Post by Habbit on 2009-11-30
Actually the problem is not that you are calling some other version of the constructor, but that the line "btMap mappy();" declares a _function_ called mappy that takes no arguments and returns a btMap object. If you want to call the default constructor, either remove the parentheses, or use the assignment syntax "btMap mappy = btMap();" for an explicit call.

---

