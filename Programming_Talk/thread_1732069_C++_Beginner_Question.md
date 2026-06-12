---
title: "C++ Beginner Question"
date: 2011-04-17
forum: Programming Talk
---

### Post by abraxyz on 2011-04-17
```
#include <iostream>
int main()
{
   char buffer[3];
   std::cout << (void *) buffer;
   return 0;
}
```So, the output is something like this:
**0xbfb0d89d**

But, what exactly is that **(void *)**, and how's it different from the address operator **&**?
Looks like a typecast to a pointer of some sort, but I still don't quite get it...
Thanks

---

### Post by MadCow108 on 2011-04-17
its a type cast so the right overloaded << operator is called:
ostream & operator<<(void * str);

without the cast it will call this one:
ostream & operator<<(char * str);
as arrays convert to pointers when passed into functions

these two functions to different things, the former prints the pointer in hexadecimal format the latter prints the char's until it encounters a null terminator (and will do bad stuff when there is none)

&buffer would to the same as the cast in this case

---

### Post by Jonas thomas on 2011-04-17
> **abraxyz said:**
> ```
#include <iostream>
int main()
{
   char buffer[3];
   std::cout << (void *) buffer;
   return 0;
}
```So, the output is something like this:
**0xbfb0d89d**

But, what exactly is that **(void *)**, and how's it different from the address operator **&**?
Looks like a typecast to a pointer of some sort, but I still don't quite get it...
Thanks
Did you intentional leave char buffer[3] uninitiated.

I'm not sure what your experimenting with the (void *)

But I tried this:
> #include <iostream>
using namespace std;
int main()
{
   char buffer[3];
   char buffera[] ={"abc"};

   cout << (void *) buffer<<endl;

   cout << buffera<<endl;
   cout << (void *)buffera<<endl;
   return 0;
}
 
which produces this:
> 
0xbf857ccd
abc
0xbf857cc9



Are you a beginner beginner, or not so beginner trying something Gucci?

---

### Post by abraxyz on 2011-04-17
Thanks for the quick replies.
Not trying anything Gucci so far : )
Was just reading a book when I encountered this, so I wasn't quite sure why the address operator wasn't applied. It was a chapter about placement new operator, by the way, illustrating dynamic memory techniques. I also tried something like **(int *) buffer**, and got pretty much the same result. So, I understand it has to do with the ostream << operator overloading?

> &buffer would to the same as the cast in this case     What would be the case where it wouldn't do the same?

EDIT:

Oh, wait, just tried with the int type:

#include <iostream>
int main()
{
       int n;
       std::cout << (void *) n << std::endl;
       std::cout << &n;

       return 0;
}

[B]0xe77985
0xbfabdb80[/B]

So, I just want to know what is really going on here?

---

### Post by abraxyz on 2011-04-17
OK, replying to myself after the last post, lol...
**n** wasn't initialized, that's why I got those weird looking numbers, but after i initialized **n** variable, **(void *) n** would be the **n** value in hex notation. So, I finally understand the first example when I typecast the address of the first array element to a pointer. Still, doesn't seem like a particularly useful sort of typecast. But then again, I'm only a beginner...

---

### Post by Jonas thomas on 2011-04-17
> **abraxyz said:**
> OK, replying to myself after the last post, lol...
**n** wasn't initialized, that's why I got those weird looking numbers, but after i initialized **n** variable, **(void *) n** would be the **n** value in hex notation. So, I finally understand the first example when I typecast the address of the first array element to a pointer. Still, doesn't seem like a particularly useful sort of typecast. But then again, I'm only a beginner...

Think of a type cast as way of making data look like something else.
I found a bit of a discusion here.  

[http://www.geekinterview.com/question_details/3350]("http://www.geekinterview.com/question_details/3350")
Does this make sense?
Gotta get the kid to bed.. Later

---

### Post by abraxyz on 2011-04-18
Yeah, makes a lot of sense to me now.
Thanks for the help.

---

