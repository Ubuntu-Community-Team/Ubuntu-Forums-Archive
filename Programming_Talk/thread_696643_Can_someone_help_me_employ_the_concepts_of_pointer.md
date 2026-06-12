---
title: "Can someone help me employ the concepts of pointers in C++?"
date: 2008-02-14
forum: Programming Talk
---

### Post by ogwilson on 2008-02-14
Beginner programmer here. I just got to the chapter about Pointers in my book. While I kind of get the idea of them (they point to some address of another variable in memory), I generally like to employ learned concepts (even simple ones) in some form or another into a simple program.
 
You may be thinking "Shouldn't your coursebook have exercises?"
 
It does, but my coursebook is so convoluted. They expect you to have perfect knowledge of the subject after your first time through the chapter, and I don't have time to read through a 70 page chapter 1-2 more times for the sake of understanding their convoluted nature in writing.
 
Anyway, I was wondering, could someone please come up with a semi-practical exercise for a beginner program to employ some basic concepts of pointers which may or may not include the manipulation of a 1 dimensional array?

---

### Post by LaRoza on 2008-02-14
Pointers cause of a lot of trouble for people just learning C (and C++).

If this is your first language, you might save yourself some time in the long run to start with a different language, like Python (here we go again...)

A pointer is a variable, that holds a memory address. (Read that again)

I am not a C++ programmer that much, and prefer C. Pointers in C++ are not that common, as compared to C as far as I can tell.

This might help: [http://www.cplusplus.com/doc/tutorial/pointers.html](http://www.cplusplus.com/doc/tutorial/pointers.html)

Writing a linked list class is usually a good exercise for learning the use of pointers.

---

### Post by Zugzwang on 2008-02-14
There is a nice book on C++ called "Thinking in C++" by Bruce Eckel. It has lots of information & examples on pointers. He also doesn't assume *too* much knowledge about the respective previous chapters. You can download a free copy at:

[http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html]("http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html")

Try Volume 1. Have a look at that and tell us if that was sufficient.

---

### Post by ogwilson on 2008-02-14
Thanks to both of you for the resources.
 
Well, I'm learning C++ at Uni right now, so I kinda have no choice but to learn it (although learning Python on the side is attractive).
 
Also, it's the weird structure of my book. My book considers Linked Lists as an advanced topic, and thus its shoved into the very last chapter of the book.
 
Thus far, I've learned Variables, Input and Output statements, stream formatting, basic arrays, functions/prototypes/with paramters, basic classes, minimal exception handling, iterative repetition, control statements, and a few little more basic things.
 
Well, I'm going to try and find a tutorial on linked lists so I can see what you're talking about. And I will download the free book.

---

### Post by amingv on 2008-02-14
While you're at it, I like the explanation on these pages, too:

[http://cplusplus.com/doc/tutorial/pointers.html](http://cplusplus.com/doc/tutorial/pointers.html)

[http://xkcd.com/371/](http://xkcd.com/371/) (for fun :))

---

### Post by LaRoza on 2008-02-14
> **amingv said:**
> 
[http://xkcd.com/371/](http://xkcd.com/371/) (for fun :))

Also a favourite of mine: [http://xkcd.com/138/](http://xkcd.com/138/)

(And I already posted the other link in my first post)

---

### Post by Zwack on 2008-02-14
Strange... Pointers are usually not used in C++, for a linked list it's better to use STL and iterators...  

Any decent C reference will teach you what you need to know about pointers in C++... 

Z.

---

### Post by LaRoza on 2008-02-14
> **Zwack said:**
> Strange... Pointers are usually not used in C++, for a linked list it's better to use STL and iterators...  

Any decent C reference will teach you what you need to know about pointers in C++... 

Z.

Yes, but learning about them is essential. And C references are not good for C++, ironically, because of C++ references.

---

### Post by johnnyb1726 on 2008-02-14
> **Zwack said:**
> Strange... Pointers are usually not used in C++, for a linked list it's better to use STL and iterators...  

Any decent C reference will teach you what you need to know about pointers in C++...

Z.

A lot of times they do not let you use the STL in a class especially if it is your first class in C++ or a class in data structures.

--cheers

---

### Post by CptPicard on 2008-02-14
> **ogwilson said:**
> While I kind of get the idea of them (they point to some address of another variable in memory)

Just to nitpick on terminology: "pointing to" is generally understood in C/C++ to mean being a pointer to something. A pointer *is* the address of some other variable, thus "points" to that other variable. What you are saying is something like being a pointer to pointer ;)

---

### Post by Wybiral on 2008-02-14
> **CptPicard said:**
> Just to nitpick on terminology: "pointing to" is generally understood in C/C++ to mean being a pointer to something. A pointer *is* the address of some other variable, thus "points" to that other variable. What you are saying is something like being a pointer to pointer ;)

Just to nitpick ever further, pointers have nothing to do with variables. It's all about the memory. A pointer can also point to a dynamically allocated chunk of memory without any variables having access to it (just the pointer). In fact, I often think of variables (labels) themselves as "pointers" in C and C++ since they are essentially just an alias for the address in the stack (I guess they're more like references in that case, or "address aliases"). Wait until the pointers to pointers to pointers come into play and you get into multi-star dereferencing :)

EDIT:

This is why you shouldn't learn C or C++ until you REALLY understand what's going on behind the scenes.

---

### Post by pmasiar on 2008-02-14
Now without nitpicking: for beginners, not for C++ language lawyers :-)

Variable is a "pretty" name for address in memory. Pointer is kind of "alias". 
So pointer can "point" at memory of different variables, or in arrays, point where different  elements "live".

Multi-level pointer point to other pointers, so your brain can get exercise :-)

You may consider reading couple C++ books in parallel, often different parts are better explained in different books - and reading explanation in different words beats reading the same explanation for N+1 time. Sticky FAQ has the links.

And yes, certainly consider learning Python (see wiki in my sig). Everything is simpler, computer works much harder for you - with C++, you work for computer :-) Also, learning programming in different languages will let you to see what problems are inherent to programming task and what is just syntax difficulties of language you used to code it.

---

### Post by Wybiral on 2008-02-14
And for a good round of "wtf?", try to guess why the first one of these snippets breaks, while the other two work just fine...

Segfault...
```

#include <stdio.h>

int main(int argc, char *argv[])
{
    char *str = "Hello world\n";
    str[0] = 'X';
    printf(str);
}

```

Works...
```

#include <stdio.h>

int main(int argc, char *argv[])
{
    char str[] = "Hello world\n";
    str[0] = 'X';
    printf(str);
}

```

Works...
```

#include <stdio.h>

int main(int argc, char *argv[])
{
    char str[] = "Hello world\n";
    char *str2 = str;
    str2[0] = 'X';
    printf(str2);
}

```

---

### Post by Lster on 2008-02-14
Wow. I remember having _huge_ problems understanding pointers. I seem to remember even posting a thread wondering why something, like that code Wybiral posted, segfaulted. :)

---

### Post by aks44 on 2008-02-14
> **Wybiral said:**
> And for a good round of "wtf?", try to guess why the first one of these snippets breaks, while the other two work just fine...

TBH I'm not wondering why the first snippet segfaults, but why **g++** even compiles it without whining (it should definitely flag the error :shock:)...


EDIT:
@Wybiral: according to the g++ manpage, this shouldn't happen... can this be considered a bug (I'm using 4.1.2)? (I won't tell more for now, so that other people can have fun solving your riddle ;))

---

### Post by Wybiral on 2008-02-14
> **aks44 said:**
> TBH I'm not wondering why the first snippet segfaults, but why **g++** even compiles it without whining (it should definitely flag the error :shock:)...

Indeed, it doesn't even throw a warning with "-Wall" on. But even if it did catch the error, my point was that the new programmer has to understand quite a bit of baggage just to get why the first one is different. Understanding the subtle differences between s*r*n* l*t*r*l*, character pointers, and character arrays and such. I'll take my dynamic, strong-typed languages any day :p

---

### Post by aks44 on 2008-02-14
> **Wybiral said:**
> I'll take my dynamic, strong-typed languages any day :p
As far as I'm concerned, I guess I'll have to settle for the [Comeau C++ compiler]("http://www.comeaucomputing.com/")... ;)

---

### Post by Zwack on 2008-02-14
Pointers work the same way in C and C++... (Or C with classes if you're old enough) And they are not usually recommended in C++.

C++ has enough other ways of handling things that I can understand that.  

I understand that the STL is a more advanced topic but it removes the need for implementing your own Linked Lists with pointers.

It sounds to me like this book is written by one of the old school, first you learn C then you learn C++ types... 

So, changing the subject of this thread slightly (as I'm more of a C programmer than a C++ programmer, although Professionally it's the other way around)...

What is different about pointers in C and C++?

Z.

---

### Post by amingv on 2008-02-14
> **LaRoza said:**
> Also a favourite of mine: [http://xkcd.com/138/](http://xkcd.com/138/)

(And I already posted the other link in my first post)

You're right, I didn't notice.

Guess I just wanted an excuse to post the xkcd link...:-\"

---

### Post by LittleLORDevil on 2008-02-14
As corny as this video is this is what my class showed:

[http://www.youtube.com/watch?v=6pmWojisM_E](http://www.youtube.com/watch?v=6pmWojisM_E)

It was pretty helpful IMO

---

### Post by aks44 on 2008-02-14
> **Zwack said:**
> What is different about pointers in C and C++?

In C++, "naked" pointers should usually not be used but for passing parameters in very specific cases.

1. For passing objects as parameters, preferably use references (the aliased object lives longer than the callee, no change of ownership).

2. If the parameter is optional, you can (in fact, must) then use a naked pointer (the aliased object still lives longer than the callee, no change of ownership) so that NULL can be used to denote an absent parameter.

3. For lifetime / ownership management, use smart pointers or custom RAII classes (one single pointer per class). This ensures exception safety and avoids memleaks.

---

### Post by Zwack on 2008-02-14
> **aks44 said:**
> In C++, "naked" pointers should usually not be used but for passing parameters in very specific cases.

1. For passing objects as parameters, preferably use references (the aliased object lives longer than the callee, no change of ownership).

2. If the parameter is optional, you can (in fact, must) then use a naked pointer (the aliased object still lives longer than the callee, no change of ownership) so that NULL can be used to denote an absent parameter.

3. For lifetime / ownership management, use smart pointers or custom RAII classes (one single pointer per class). This ensures exception safety and avoids memleaks.

But this doesn't answer the question that I had... I know that they're not usually used and for good reasons, but what is DIFFERENT about them...  As far as I know there is no difference between pointers between C and C++ in implementation the difference is in need for them and whether you should use them.

Z.

---

### Post by aks44 on 2008-02-14
Sorry I misunderstood your question... I thought about "usage" ;)

You're right, technically *_as far as pointers implementation goes_* there is no difference between C and C++.

But again, C++ exceptions alone totally change the way you have to deal with them.

eg. this code is unsafe (memleak):

```
#include <iostream>
int main()
{
  int* p = new int(42);
  std::cout << *p << std::endl;
  delete p;
  return 0;
}
```

... just because **std::cout::operator<<** can throw.

Correct C++ code:
```
#include <iostream>
#include <memory>
int main()
{
  std::auto_ptr<int> p(new int(42));
  std::cout << *p << std::endl;
  return 0;
}
```




More unsafe C++ code:
```
int main()
{
  int* x = new int;
  int* y = new int; // can throw, "x" then gets leaked
  delete y;
  delete x;
  return 0;
}
```

---

### Post by Zwack on 2008-02-14
Thanks...

I guess we can't really answer the original question without knowing exactly what is being taught or what they are trying to achieve...

The example really helped...  It's been a while since I did any C++ programming (about ten years) so it's probably time to go back and learn C++ again.

If it's an older style course/book that starts with C and then teaches C++ afterwards then learning C pointers may be what is needed.  If it's a pure C++ course then learning C pointers is not a good place to go.

Z.

---

### Post by rplantz on 2008-02-15
I find it useful to distinguish between "pointer" and "pointer variable." Consider the declarations:
```

int x;
int *ptr;

```
Both of these declarations allocate a group of several bytes of memory. Each group of bytes is located at an address, which is a number.

The compiler (and linker) will decide what these addresses are, so we can't use these numbers in our programs. The compiler gives the address of where the first group of bytes is located the name "x", and it gives the address of the second group the name "ptr".

What is stored in each of these groups of bytes is also a number.

The compiler expects that the program will only store integers in the first group, x. And it expects that the program will store addresses in the second group, ptr. (I say "expect" because you can use type casting to tell the compiler to allow other actions.)

That is, you can do something like
```

x = 123;
ptr = &x;

```
Most people say that ptr now points to x. But I think it's helpful to remember that ptr is the name of an address in memory where the address of x is stored. (And x is a name of another address.)

I think that the assignment operator in C/C++ (=) is confusing to beginners because they think "equals." It is better to think "gets." Assignment is probably better expressed by something like the Pascal operator (:=).

I've always found drawings to be the most helpful tool for understanding pointers. Draw a box for each pointer variable. Make up some number for the address of the box and put this number just to the left outside the box. Make a table that lists each variable name and shows its corresponding address (the one you made up). Then as you do something like the above code, you can write the (made up) address of x inside the box you have drawn for ptr. Complete the drawing by drawing a line from the inside of the ptr box to outside of the x box, with an arrow pointing to the x box.

You should quickly get the idea and be able to stop using the numbers. You can simply draw the lines with arrows from the inside of one box pointing to the outside of another box. You write your code so as to move the tails of these lines from box to box.

---

### Post by hod139 on 2008-02-15
> **Wybiral said:**
> And for a good round of "wtf?", try to guess why the first one of these snippets breaks, while the other two work just fine...<snip>
This reminds me of an older discussion:
[http://ubuntuforums.org/showthread.php?t=357869](http://ubuntuforums.org/showthread.php?t=357869)

And, the warning you want to enable (mentioned in the linked discussion) is 
```

-Wwrite-strings

```

Compiling your snippet that faults produces:
```

gcc -Wwrite-strings temp.c
temp.c: In function ‘main’:
temp.c:5: warning: initialization discards qualifiers from pointer target type

```

---

### Post by aks44 on 2008-02-15
> **hod139 said:**
> And, the warning you want to enable (mentioned in the linked discussion) is 
```

-Wwrite-strings

```

Thanks, I overlooked it. I'll include that in the "warnings" section of my compiling FAQ. ;)




However, can anyone explain why this apparently contradicts the observed behaviour of g++ (4.1.2)?
[QUOTE=GCC manual]**-fno-const-strings**
Give string constants type char * instead of type const char *. *_By default, G++ uses type const char * as required by the standard._* Even if you use -fno-const-strings, you cannot actually modify the value of a string constant.[/QUOTE]


**IMPORTANT:** while redacting this post I tried it on [Comeau Online]("http://www.comeaucomputing.com/tryitout/"):
```
#include <iostream>
int main()
{
  char* str = "boom?";
  str[0] = 'X'; // to suppress the "variable was declared but never referenced" warning...
                // note: Comeau Online doesn't actually link / run the submitted code
  return 0;
}
```And it doesn't even blink... There's definitely a subtlety here, as Comeau is well known for its standard compliance.


**MORE:** after playing with g++'s **typeid**, here is what I found:
```
#include <iostream>
#include <typeinfo>

int main()
{
  std::cout << "const char* = " << typeid(const char*).name() << "    -- pointer (P) to const (K) char (c)" << std::endl;
  std::cout << "char* = " << typeid(char*).name() << "           -- pointer (P) to char (c)" <<std::endl;
  std::cout << "Const string = " << typeid("Const string").name() << " -- array(A) of 13 (strlen+\\0) chars (c)" << std::endl;
  return 0;
}
``````
$ g++ -o test test.cpp && ./test
const char* = PKc    -- pointer (P) to const (K) char (c)
char* = Pc           -- pointer (P) to char (c)
Const string = A13_c -- array(A) of 13 (strlen+\0) chars (c)
```

Even after years of using C++ that language never ceases to amaze me... ](*,)

IMNSHO, this is one more reason to avoid "naked" (const) char* variables (aka. plain old C strings) altogether... :roll:

---

### Post by talkeetnaweb on 2008-02-15
hey, guess what... when you create an array, it just returns a pointer to the first member of the array. And every time you increment (add one) the pointer, it points to the next member. Here's a program I wrote in my C class.


#include <stdio.h>
//#include <stdlib.h>
//#include <string.h>

/*                                       Jok Bondurant */
/*                                       C language class */
/*                                       11/9/93,  */


/* This is a program to SHOW ARRAY ARITHMETIC. */
/* */



main()
{
int a[] = {0,2,4,6,8},
*q = a + 3;




printf("%d \n%d\n",*q,*(q+1));

return(0);
    /*   */
}


And guess what, a string is just an array of characters and the variable associated with it is just a pointer to the first character. So try creating a program that makes a string and prints it, then increments it and prints it again. 

I found a link that might help, but try writing and running a simple program first. BTW, strings know they got to the end when they find a null character. If you increment beyond that point and print it, you might print off into space.


[http://www.augustcouncil.com/~tgibson/tutorial/ptr.html](http://www.augustcouncil.com/~tgibson/tutorial/ptr.html)

C language sure was a lot of fun for me.


Jok

---

### Post by aks44 on 2008-02-15
> **talkeetnaweb said:**
> hey, guess what... when you create an array, it just returns a pointer to the first member of the array.
Just nitpicking here, but... an array *decays* to a pointer to its first member (once you *fully* understand the tricky subtleties resulting from that sentence you'll probably be an expert by that time... FWIW even after almost 15 years of C++ I still get caught by that when I dare to go so low level, see previous discussion before it turned wild ;)).


Back to the off topic (I can hardly believe someone actually posted *on*-topic in this thread :p):
> **CptPicard said:**
> In some ways when it comes to the results of the survey... it does seem to me that there *are* individuals that are prominent in the graph, like the Bond Node. The existence of the macro-structure cycle is just beautiful and surprising though :D
IMO the most interesting fact in this graph (as those researchers pointed it out) is that a single relationship can easily connect one to numerous other people "*unlike many adult networks*".

---

### Post by hod139 on 2008-02-16
What happened to this thread?

> **aks44 said:**
> while redacting this post I tried it on [Comeau Online]("http://www.comeaucomputing.com/tryitout/"):
```
#include <iostream>
int main()
{
  char* str = "boom?";
  str[0] = 'X'; // to suppress the "variable was declared but never referenced" warning...
                // note: Comeau Online doesn't actually link / run the submitted code
  return 0;
}
```And it doesn't even blink... There's definitely a subtlety here, as Comeau is well known for its standard compliance.

The code is standard's compliant, so what is the confusion?

The string inside the quotes is a literal, meaning you can't change it.  Just because you are not suppose to do something, doesn't mean C++ won't let you try :)

This line: ```
char* str = "boom?";
```creates a pointer to a literal. This is legal (standard) C++.  

This line: ```
char string[] = "string literal";
```is different than the first line.  This line **copies **the literal onto the stack, thus allowing you to change the values on the copy.

---

### Post by aks44 on 2008-02-16
> **hod139 said:**
> The code is standard's compliant, so what is the confusion?

You're right (I only have C++98 at hand, but Comeau confirms that strict C++03 compliance behaves the same):
> **C++98]**2.13.4 String literals [lex.string]**
1- [...] An ordinary string literal has type &#8220 said:**
>  A wide string literal has type &#8220;array of n const wchar_t&#8221; and has static storage duration


**4.2 Array-to-pointer conversion [conv.array]**
2- A string literal (2.13.4) that is not a wide string literal can be converted to an rvalue of type &#8220;pointer to
char&#8221;; a wide string literal can be converted to an rvalue of type &#8220;pointer to wchar_t&#8221;. [Note: this conversion is deprecated. See Annex D. ] For the purpose of ranking in overload resolution (13.3.3.1.1), this conversion is considered an array-to-pointer conversion followed by a qualification conversion (4.4). [Example: "abc" is converted to &#8220;pointer to const char&#8221; as an array-to-pointer conversion, and then to &#8220;pointer to char&#8221; as a qualification conversion. ]


**D.4 Implicit conversion from const strings [depr.string]**
1- The implicit conversion from const to non-const qualification for string literals (4.2) is deprecated.

I often tend to assimilate "deprecated" to "non-standard", that's where my confusion came from. :oops:

---

