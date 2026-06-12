---
title: "Why do indexes of arrays start with zero?"
date: 2009-09-26
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2009-09-26
Hi,

I was wondering why indexes of arrays in C based languages and some other popular languages like Ruby or Python start with zero instead of one.

I also saw some other languages whose indexes start with one and didn't see any problem with that approach. Actually, I frequently see that starting indexes by zero causes "off-by-one" errors which leads to bugs in software.

Also, starting with one sounds more familiar to human thinking since we don't use zero as a counting number, instead we use it to symbol absence of an item.

So, is there an advantage of starting the indexes with zero or is it because of historical reasons?

---

### Post by dwhitney67 on 2009-09-26
Starting array indices with a zero was not arbitrarily chosen.

The first location of an array is addressed by the pointer to the array.  Subsequent locations in the array are indicated by an offset from that pointer.

Here's some C code to explain the offsets a little better:
```

int array[3];

int* parray = &array;

int val0 = *(parray + 0);   // 1st element (note the +0 is not required)
int val1 = *(parray + 1);   // 2nd element
int val2 = *(parray + 2);   // 3rd element

```
As for the start index being zero-based vs. the one-based, yes, this may cause confusion for some, but once you stick to programming languages such as C, C++, Java, C#, Python, and others, you get the hang of it.

---

### Post by CptPicard on 2009-09-26
Well, there is first of all the technical reason that in C, the array variable itself is just a pointer to the first element of the array... so doing pointer arithmetic is much more logical when first element is index 0, next is +1 and so on.

More stuff here:

[http://www.c2.com/cgi/wiki?WhyNumberingShouldStartAtZero](http://www.c2.com/cgi/wiki?WhyNumberingShouldStartAtZero)

---

### Post by ZuLuuuuuu on 2009-09-26
> **dwhitney67 said:**
> Starting array indices with a zero was not arbitrarily chosen.

The first location of an array is addressed by the pointer to the array.  Subsequent locations in the array are indicated by an offset from that pointer.

Here's some C code to explain the offsets a little better:
```

int array[3];

int* parray = &array;

int val0 = *(parray + 0);   // 1st element (note the +0 is not required)
int val1 = *(parray + 1);   // 2nd element
int val2 = *(parray + 2);   // 3rd element

```
As for the start index being zero-based vs. the one-based, yes, this may cause confusion for some, but once you stick to programming languages such as C, C++, Java, C#, Python, and others, you get the hang of it.

This is more like a choice, they could have said: "Array indexes start by 1, but array name alone points to the first item so you have to add 0 if you want to reach the first item by using pointer arithmetic." so the pointer arithmetic still holds while we can use the regular one based indexes.

Though, maybe this keeps the compiler simpler, because when the compiler sees array[a_number] it can convert it to *(array + a_number) directly and use the same semantics instead of seperately writing two semantics for the two usages. And at the time C appeared, writing a compiler was much more difficult I guess...

But most of the languages like Java, C#, Python etc. don't even have pointers, as far as I know.

> **CptPicard said:**
> [http://www.c2.com/cgi/wiki?WhyNumberingShouldStartAtZero](http://www.c2.com/cgi/wiki?WhyNumberingShouldStartAtZero)

Thanks, I'll read it as soon as possible.

---

### Post by credobyte on 2009-09-26
[B][COLOR=RoyalBlue][COLOR=Green]0 1 2 3 4 5 6 7 8 9[/COLOR]
[COLOR=Red]1 2 3 4 5 6 7 8 9 0[/COLOR]

[/COLOR][/B]Not related to C++ or any other language, however, makes more sense than talking about pointers and whatnot :p

---

### Post by nvteighen on 2009-09-26
I think this is less related to programming than to maths... Mathematical notation usually starts from zero, e.g. in subindices. That may have been transferred into programming very easily.

Of course, pointer arithmetics may have a lot of influence in this too, being C taken as the model for a lot of programming practices, even in languages totally unrelated to it.

---

### Post by TheBuzzSaw on 2009-09-26
> **ZuLuuuuuu said:**
> This is more like a choice, they could have said: "Array indexes start by 1, but array name alone points to the first item so you have to add 0 if you want to reach the first item by using pointer arithmetic." so the pointer arithmetic still holds while we can use the regular one based indexes.
I understand your frustration, but I strongly disagree with this assessment. Why would they have the math behave one way and have the access index do it another way? You need to understand that an array variable is nothing more than a constant pointer.
```
int stuff[7]; // a const int pointing to the first element of 7 integers
const int* stuff; // same data type just without the 7 allocated integers
```
The array access syntax of [n] *is* pointer arithmetic.

---

### Post by napsy on 2009-09-26
> **CptPicard said:**
> Well, there is first of all the technical reason that in C, the array variable itself is just a pointer to the first element of the array...

Not true. Arrays are arrays that can, in some situations, descent into pointers (ie. as function arguments). They don't point to the first element but are a part of that storage. Arrays may seem like pointers but the way the program access memory with a pointer and with an array is different.

---

### Post by CptPicard on 2009-09-26
@napsy, true... there is no actual "pointer variable" involved, I was being too inaccurate there. For the compiler the array name is a label for the address of the beginning of the array though, so it can "realize" an actual pointer from that at will. Better? :)

Then there is also to be considered that the array syntax vs. pointer arithmetic exchangeability works both ways... one can take a pointer and index from there....

---

### Post by jpkotta on 2009-09-26
I do a fair about of Octave/Matlab programming, and their arrays are 1-indexed.  Besides being different from most languages I use, I really hate 1-indexed arrays when I'm doing modulo arithmetic on the index.  If you want to make your array N-periodic, you usually do something like
```
for i in 0 to 2N-1:
    y += x[i%N]*f(i)

```
If it's 1-indexed, it would be
```

for i in 0 to 2N-1:
    y += x[(i%N)+1]*f(i)

```
This kind of thing arises quite a bit in signal processing code.  On the flipside, I never find myself wishing for 1-indexing in other languages.

---

### Post by tom66 on 2009-09-26
Because arrays kind of translate like this:

```

 item_value = array[item_pos];
 item_value = *(array_address + (sizeof(type_of_array_element) * item_pos));

```

(remember, C automatically translates +1 into the correct offset for the data size)

---

### Post by TheBuzzSaw on 2009-09-26
> **napsy said:**
> Not true. Arrays are arrays that can, in some situations, descent into pointers (ie. as function arguments). They don't point to the first element but are a part of that storage. Arrays may seem like pointers but the way the program access memory with a pointer and with an array is different.

... Riiiight. You sure about that?

```
#include <iostream>
#include <sstream>
using namespace std;

int main(const int argc, const char** argv)
{
    int* z;
    z = new int;
    *z = 7;
    cout << z << endl;
    cout << *z << endl;
    cout << z[0] << endl;
    return 0;
}
```

Lemme know how that turns out. ;)

---

### Post by ve4cib on 2009-09-27
As has already been illustrated the zero-based array indices using in C (and probably in Fortran before that) are essentially short-hand for pointer math.  Instead of manually inserting the pointer arithmetic they simply created a shortcut to offset a pointer.

As C and C++ gained popularity other languages started copying them.  To make life easier for programmers already familiar with C or C++ other languages use much of the same syntax.  Java, Perl, Python, etc... all use very C-style syntax for most operators.  This includes array indices.  You're correct in saying that it would be easy to change the compiler to use one-based indices, but why bother?  If you're trying to attract C-programmers to your newfangled language you might as well make their life easier by keeping the syntax close to what they know and minimizing useless cosmetic changes so that they can focus on the exciting major changes in your language.  Advertising Java as being "Fully Object-oriented" is much more likely to appeal to people than advertising it as "being free of pesky zero-based array indices."

These days the standard of zero-based indices is exactly that; a standard that almost every language adheres to.  VB and Matlab are the only notable exceptions I can think of (though VB allows you to set arbitrary indices; if you want your array to start at 13 you can do that).

Yes, if you're a beginner programmer the zero-based indices take a while to get used to.  But once you get used to them (and you're pretty much obliged to, or find a different line of work) they're easy.

---

### Post by TheStatsMan on 2009-09-27
> **ve4cib said:**
> As has already been illustrated the zero-based array indices using in C (and probably in Fortran before that) are essentially short-hand for pointer math. 

Fortran uses 1 based arrays.

---

### Post by Marflus on 2009-09-27
If it bothers you a lot, write a little function for yourself to use when you use arrays so you don't have to start at 0. 

I've never been bothered by it though - it took me a little while to get used to, sure, but 0 seems the logical starting point to me now.

---

### Post by Habbit on 2009-09-27
> **TheStatsMan said:**
> Fortran uses 1 based arrays.

In Fortran, as in VB, you can declare your arrays to use whatever indexing you like, but the default is 1-based:```
integer :: numsone(7)    ! Equivalent to numsone(1:7)
integer :: numszero(0:6) ! Now zero-based
```

---

### Post by napsy on 2009-09-27
> **TheBuzzSaw said:**
> ... Riiiight. You sure about that?

```
#include <iostream>
#include <sstream>
using namespace std;

int main(const int argc, const char** argv)
{
    int* z;
    z = new int;
    *z = 7;
    cout << z << endl;
    cout << *z << endl;
    cout << z[0] << endl;
    return 0;
}
```

Lemme know how that turns out. ;)

And your point was?

---

### Post by TheBuzzSaw on 2009-09-27
> **napsy said:**
> And your point was?
My point is that your statement was wrong. Pointers have virtually no association with any kind of "array data type". All a pointer does is point to the first element in memory. You said that the way pointers access memory is different from the way arrays access memory, and that is simply untrue.

---

### Post by napsy on 2009-09-27
> **TheBuzzSaw said:**
> My point is that your statement was wrong. Pointers have virtually no association with any kind of "array data type". All a pointer does is point to the first element in memory. You said that the way pointers access memory is different from the way arrays access memory, and that is simply untrue.

Wrong. Let's see an example:

[PHP]
#include <stdlib.h>

int main()
{
    int *a;
    int b[2];

    a = malloc(sizeof(int) * 2);
    *a = 4;
    *(++a) = 2;
    b[1] = 3;
    b[0] = 7;

    return 0;
}
[/PHP]

copiled with:

gcc ptr.c -o ptr

and now make gdb disassemble main. We get:

> Dump of assembler code for function main:
0x00000000004004c4 <main+0>:	push   %rbp
0x00000000004004c5 <main+1>:	mov    %rsp,%rbp
0x00000000004004c8 <main+4>:	sub    $0x10,%rsp
0x00000000004004cc <main+8>:	mov    $0x8,%edi
0x00000000004004d1 <main+13>:	callq  0x4003c0 <malloc@plt>
0x00000000004004d6 <main+18>:	mov    %rax,-0x8(%rbp)
0x00000000004004da <main+22>:	mov    -0x8(%rbp),%rax
[COLOR="navy"]0x00000000004004de <main+26>:	movl   $0x4,(%rax)[/COLOR]
0x00000000004004e4 <main+32>:	addq   $0x4,-0x8(%rbp)
0x00000000004004e9 <main+37>:	mov    -0x8(%rbp),%rax
[COLOR="Navy"]0x00000000004004ed <main+41>:	movl   $0x2,(%rax)[/COLOR]
[COLOR="Red"]0x00000000004004f3 <main+47>:	movl   $0x3,-0xc(%rbp)
0x00000000004004fa <main+54>:	movl   $0x7,-0x10(%rbp)[/COLOR]
0x0000000000400501 <main+61>:	mov    $0x0,%eax
0x0000000000400506 <main+66>:	leaveq 
0x0000000000400507 <main+67>:	retq   


Now pay close attention to the blue and red lines. The blue ones associate values using pointers. The red ones using arrays. Are they the same?

So do you now agreee that memory access is different in pointers and arrays?

btw. using brackets (a[0] = 4 equals *a = 4) gives the same assembly output.

---

### Post by TheBuzzSaw on 2009-09-27
The assembly does exactly what your arithmetic did in your code. Again, the only difference is that an actual array is a **const** pointer where you have to use [n] arithmetic to access other elements. In your example, you actually moved the pointer location using ++a, so a[0] now points to where a[1] used to point. Obviously, you cannot do that with b because it is constant. The assembly reflects that. This has nothing to do with your previous statement.

```
0x00000000004004f3 <main+47>: movl $0x3,**-0xc(%rbp)**
0x00000000004004fa <main+54>: movl $0x7,**-0x10(%rbp)**
```

See those offsets? That is exactly what your code is saying.

---

### Post by johnl on 2009-09-27
1) you allocated the array on the stack, and the pointer on the heap.
2) you used an increment-and-dereference on the pointer and a direct indexing on the array.

Different operations result in different (unoptimized) instructions.  This is not a reflection on any inherent difference between pointers and arrays.


An array is a high-level construct that is based on pointers.  Assembly has no concept of 'arrays', just operations on blocks of memory.

---

### Post by TheBuzzSaw on 2009-09-27
> **napsy said:**
> Arrays may seem like pointers but **the way the program access memory with a pointer and with an array is different.**
This is wrong. A standard pointer has *more options* than a standard array, but they both operate under the same basic principle: it is a pointer variable that points to the first element in the array (whether it was dynamically allocated or not). They both can access elements using a[n] form. The pointer has the added option of moving itself to point to another location. However, if you access an element using a[n] whether it is a pointer or an array, the assembly is the same.

The only difference is, yes, one is on the stack and the other on the heap.

> **johnl said:**
> An array is a high-level construct that is based on pointers.  Assembly has no concept of 'arrays', just operations on blocks of memory.

Doesn't this contradict what you were saying earlier? Arrays are not special.

---

### Post by Zugzwang on 2009-09-27
> **napsy said:**
> Now pay close attention to the blue and red lines. The blue ones associate values using pointers. The red ones using arrays. Are they the same?


No. But the array is on the stack whereas the memory the pointer points to is not. So the compiler produces different code.

EDIT: Looks like I'm too slow. ;-)

---

### Post by napsy on 2009-09-27
So if arrays and pointers are equal, the following code should produce the same assembly output:

[PHP]#include <stdlib.h>

int main()
{
    int *a;
    int b[2];

    a = malloc(sizeof(int) * 2);
    a[1] = 5;
    b[1] = 5;

    return 0;
}
[/PHP]

Let's see the output:

> (gdb) disassemble 
Dump of assembler code for function main:
0x00000000004004c4 <main+0>:	push   %rbp
0x00000000004004c5 <main+1>:	mov    %rsp,%rbp
0x00000000004004c8 <main+4>:	sub    $0x10,%rsp
0x00000000004004cc <main+8>:	mov    $0x8,%edi
0x00000000004004d1 <main+13>:	callq  0x4003c0 <malloc@plt>
0x00000000004004d6 <main+18>:	mov    %rax,-0x8(%rbp)
0x00000000004004da <main+22>:	mov    -0x8(%rbp),%rax
0x00000000004004de <main+26>:	add    $0x4,%rax
[COLOR="Red"]0x00000000004004e2 <main+30>:	movl   $0x5,(%rax)[/COLOR]
[COLOR="DarkSlateBlue"]0x00000000004004e8 <main+36>:	movl   $0x5,-0xc(%rbp)[/COLOR]
0x00000000004004ef <main+43>:	mov    $0x0,%eax
0x00000000004004f4 <main+48>:	leaveq 
0x00000000004004f5 <main+49>:	retq

---

### Post by napsy on 2009-09-27
C doesn't know 'the stack'. Where automatic variables are stored is implementation dependent.

---

### Post by TheBuzzSaw on 2009-09-27
OK. I see what you're saying with that. The compiler has the pointer move instead of using static math. That part I never knew.

I am just pointing out that, fundamentally, they are the same data structure.

EDIT -- However, I did notice that when you use any form of optimization, it *does* in fact make them the same. It stops moving the pointer around and uses the same math as the array.

```
40051e:	c7 40 04 05 00 00 00 	movl   $0x5,0x4(%rax)
```

---

### Post by napsy on 2009-09-27
> **TheBuzzSaw said:**
> OK. I see what you're saying with that. The compiler has the pointer move instead of using static math. That part I never knew.

I am just pointing out that, fundamentally, they are the same data structure.

No they're not. You cannot re-assign an array. Thus:

[PHP]
int a[1], b[1];

b = a;
[/PHP]

is not a valid code.

but with pointers you can do:

[PHP]
int a[1], *b;

b = &a[0];
b = a;
[/PHP]

Arrays happen to descent into pointers. Example:

[PHP]
void foo(int *a)
{
    *a = 3;
}

main()
{
int array[32];

foo(array);
}
[/PHP]

THe array will descent into a pointer when used as an argoument to a function call.

---

### Post by TheBuzzSaw on 2009-09-27
> **napsy said:**
> No they're not. You cannot re-assign an array. Thus:

[PHP]
int a[1], b[1];

b = a;
[/PHP]

is not a valid code.

but with pointers you can do:

[PHP]
int a[1] *b;

b = &a[0];
b = a;
[/PHP]
I already addressed that. An array is nothing more than a **const type***. So of course you cannot move it around. However, it is not special at all. If I want to pass an array in a function, it only needs to take a pointer of that type. That is not a "special exception" or anything of the sort.

```
#include <iostream>
using namespace std;

int main()
{
    int a[7];
    cout << a << endl;
    return 0;
}
```

The output? **0x7fff94746b30**

The array does not "descend into a pointer" at all. It **is** a pointer. That's all it is. Even your assembly examples confirm this.

---

### Post by napsy on 2009-09-27
Optimizations sometimes break "the rules" in order to get more speed. The fact stays that arrays != pointers, even in memory access.

If you optimize

[PHP]
main() { int a, b, c }
[/PHP]

your assembly would look like
> 
(gdb) disassemble 
Dump of assembler code for function main:
0x0000000000400480 <main+0>:	xor    %eax,%eax
0x0000000000400482 <main+2>:	retq  


instead of
> Dump of assembler code for function main:
0x0000000000400474 <main+0>:	push   %rbp
0x0000000000400475 <main+1>:	mov    %rsp,%rbp
0x0000000000400478 <main+4>:	sub    $0x18,%rsp
0x000000000040047c <main+8>:	mov    $0x0,%eax
0x0000000000400481 <main+13>:	leaveq 
0x0000000000400482 <main+14>:	retq 

with no optimizations.

---

### Post by CptPicard on 2009-09-27
Regardless of implementation details, the value semantics of pointers and arrays are interchangeable... it's the assignment difference where it becomes obvious that an array is essentially a compile-time constant pointer and not an explicit address storage location. I'm getting the feeling you guys are brewing a storm in a teacup here ;)

---

### Post by TheBuzzSaw on 2009-09-27
> **napsy said:**
> Optimizations sometimes break "the rules" in order to get more speed. The fact stays that arrays != pointers, even in memory access.

I understand that. However, you demonstrated that the compiler chooses to treat the two slightly differently in that on one, it moves the pointer, and in the other, it uses addition to find the location. That says nothing about how they are stored in memory. I just completed Computer Architecture this past summer semester where we saw many demonstrations on the matter. An array is a const pointer. How is it not?

Still, I would argue that compiling without the optimization is not "the rule".

> **CptPicard said:**
> Regardless of implementation details, the value semantics of pointers and arrays are interchangeable... it's the assignment difference where it becomes obvious that an array is essentially a compile-time constant pointer and not an explicit address storage location. I'm getting the feeling you guys are brewing a storm in a teacup here ;)

This doesn't help. Frankly, I am very interested in this discussion as napsy is a rare individual in that he is very educated on the matter. We're not throwing dirt at each other. We're clarifying this situation. Do not mistake vigorous back-and-forth as "fighting". It really bothers me when people try to "break up" a non-existent fight.

---

### Post by napsy on 2009-09-27
> **TheBuzzSaw said:**
> I understand that. However, you demonstrated that the compiler chooses to treat the two slightly differently in that on one, it moves the pointer, and in the other, it uses addition to find the location. That says nothing about how they are stored in memory. I just completed Computer Architecture this past summer semester where we saw many demonstrations on the matter. An array is a const pointer. How is it not?


Let's see how arrays and pointers access memory:

int array[4];
int *pointer = malloc(sizeof(int) * 4);
int num;

If you want to read a value from an array and assign it to num, then the following happens:

num = array[3] 
(go to three places forward in the current location and assigne the value to num)

num = pointer[3]
(add three * sizeof(int) to address the pointer has, move to that location and read tha value. Then assign it to num)

---

### Post by TheBuzzSaw on 2009-09-27
> **napsy said:**
> Let's see how arrays and pointers access memory:

int array[4];
int *pointer = malloc(sizeof(int) * 4);
int num;

If you want to read a value from an array and assign it to num, then the following happens:

num = array[3] 
(go to three places forward in the current location and assigne the value to num)

num = pointer[3]
(add three * sizeof(int) to address the pointer has, move to that location and read tha value. Then assign it to num)
Will you please read my posts? I already digressed that they behave slightly different at a non-optimized level. However, they are both stored in the same fashion: the pointer holds the first element, and you have to offset (whether it be by moving or math) to reach the desired element.

---

### Post by napsy on 2009-09-27
Ok I agree that maybe with optimizations memory access could be the same. But it is wrong to propagate the belief that pointers and arrays are the same. Arrays have different properties. Be that where memory is stored or how the assignment operator is working on them. This can be misleading if you program on a non-standard platform.

---

### Post by CptPicard on 2009-09-27
> **TheBuzzSaw said:**
> We're clarifying this situation. Do not mistake vigorous back-and-forth as "fighting". It really bothers me when people try to "break up" a non-existent fight.

What I am saying is that IMO the matter is not even particularly interesting, as the compiler does what it wants to behind the scenes as long as the programming language's semantics are not violated, and the array vs. pointer *semantic* issue is also rather simple -- as evaluated values they are for most purposes the same (the types are not the same however), but an array is not a storage location for an address.

Trust me, I was around here when we were very much "clarifying situations" much more vocally than what I see here today, I wouldn't make the mistake you're describing :)

---

### Post by napsy on 2009-09-27
> **CptPicard said:**
> What I am saying is that IMO the matter is not even particularly interesting, as the compiler does what it wants to behind the scenes as long as the programming language's semantics are not violated, and the array vs. pointer *semantic* issue is also rather simple -- as evaluated values they are for most purposes the same (the types are not the same however), but an array is not a storage location for an address.

Trust me, I was around here when we were very much "clarifying situations" much more vocally than what I see here today, I wouldn't make the mistake you're describing :)

The thing that bothered me was to tell statements such as "arrays are pointers" and discarding the important details to someone who's learning to program. It matters weather or not the compiler optimizes out the difference. A good programmer should know that.

---

### Post by TheBuzzSaw on 2009-09-27
> **napsy said:**
> Ok I agree that maybe with optimizations memory access could be the same. But it is wrong to propagate the belief that pointers and arrays are the same. Arrays have different properties. Be that where memory is stored or how the assignment operator is working on them. This can be misleading if you program on a non-standard platform.
Hey, I agree with ya there. I'll be sure to make the distinction in the future. Thanks for clarifying.
> **CptPicard said:**
> What I am saying is that IMO the matter is not even particularly interesting, as the compiler does what it wants to behind the scenes as long as the programming language's semantics are not violated, and the array vs. pointer *semantic* issue is also rather simple -- as evaluated values they are for most purposes the same (the types are not the same however), but an array is not a storage location for an address.

Trust me, I was around here when we were very much "clarifying situations" much more vocally than what I see here today, I wouldn't make the mistake you're describing :)
Is our discussion not allowed to proceed simply because you do not find it interesting? By all means, leave the thread if it bores you. I was very interested in this discussion! I learned something. Yes, to the average programmer, this level of detail is likely irrelevant, but I am not the average programmer, and I wanted to talk about it. I understand what you're trying to do, but it is just gunkin' up the works... :-/

+1 to what napsy said

---

### Post by napsy on 2009-09-27
> **CptPicard said:**
> ... but an array is not a storage location for an address.

I agree here. Arrays don't store an address to a block of memory.

That's why

[PHP]
int *a = malloc(30);
int b[30];
...
sizeof(a) != sizeof(b)
[/PHP]

If someone is more interested, there's a nice article about it here: [http://www.iso-9899.info/wiki/Why_arrays_arent_pointers](http://www.iso-9899.info/wiki/Why_arrays_arent_pointers)

---

### Post by CptPicard on 2009-09-27
> **napsy said:**
> The thing that bothered me was to tell statements such as "arrays are pointers" and discarding the important details to someone who's learning to program.

Considering the context of the OP's question -- why pointer-arithmetic and indexing work the way they do -- the point that needs clarification, and will give the important insight, is exactly the fact that the values of arrays and pointers are exchangeable exactly because the compiler will allow you to use the array name as a label for the address of the first element, which is when it is equivalent to it being a pointer to it, and conversely, because indexing will work on a pointer as if there were an array starting from the pointed-to element. 

> It matters weather or not the compiler optimizes out the difference. A good programmer should know that.

For me it is not a compiler-optimization, but a language-definition matter. In addition, people who need to ask the OP's question are not "good programmers" yet...

---

### Post by napsy on 2009-09-27
> **CptPicard said:**
> 
For me it is not a compiler-optimization, but a language-definition matter. In addition, people who need to ask the OP's question are not "good programmers" yet...

I agree that it's the language definition that says arrays are not equal to pointers. Sometimes they can behave as pointers but in this discussion we learned that there might be difference how the program accesses the memory with an array and a pointer.

An array is still different because the storage size is known and pointer arithmetic for arrays is different.

By "good programmers" I meant in order for the C/C++ students to become good programmers and master the language, they should know such details.

---

### Post by ZuLuuuuuu on 2009-09-27
> **CptPicard said:**
> Considering the context of the OP's question -- why pointer-arithmetic and indexing work the way they do --

...

In addition, people who need to ask the OP's question are not "good programmers" yet...

My question wasn't that. I sense people thought that I don't know about pointer arithmetic which is untrue. Please be careful before making assumptions about how well a person knows about programming and read the first post again. I got the answer from the first posts so don't much care how the topic leads...

---

### Post by CptPicard on 2009-09-27
> **ZuLuuuuuu said:**
> I sense people thought that I don't know about pointer arithmetic which is untrue.

Actually, I know that. :) The underlying point of the question, which is often asked, is however the issue at hand... and at that point it becomes irrelevant what you actually know, it's not what is being talked about :)

---

### Post by Reiger on 2009-09-27
First, this is a matter which has implications in some languages but not others. For instance, in Java it is little but conventions since all you'll ever do is pass around pointers anyway*.

Second arrays do not mean a pointer to a block of memory. It is, literally, an array of values -- where they actually are is arbitrary: in this respect behaving actually much more the same as Haskell tuples (using indexing instead of pattern matching to access specific elements), or perhaps better yet a JavaScript property list. Again, that in C or C++ array access can be _thought_ of as pointer access for simplification of the thing doesn't translate (well) into other languages.

Then we haven't descended into the concept of associative arrays... 

As Cpt. Picard says; an array is little more than a label for a collection of things, whatever those things might be (and they need not necessarily be all of the same kind of thing either).

*Yes I know the matter is a little different with primitive types and certain calling conventions.

---

### Post by A_Fiachra on 2009-09-28
As a mathematician -- I would have to go with Dijkstra.

The natural numbers start at 0.  So far, no one has come up with a convincing argument to index anything using something other than the natural numbers except "I don't like it!"

Ironically Fortran got away with 1 based indexing -- but, then again, Fortran wasn't built by mathematicians, it was built by engineers.

(insert snarky comment about engineers here)

After all, accessing the 0th row, 0th column element of a matrix as M[1,1] is simply [bad and wrong]("http://catb.org/jargon/html/B/Bad-and-Wrong.html").

---

### Post by Arndt on 2009-09-28
> **A_Fiachra said:**
> As a mathematician -- I would have to go with Dijkstra.

The natural numbers start at 0.  So far, no one has come up with a convincing argument to index anything using something other than the natural numbers except "I don't like it!"

Ironically Fortran got away with 1 based indexing -- but, then again, Fortran wasn't built by mathematicians, it was built by engineers.

(insert snarky comment about engineers here)

After all, accessing the 0th row, 0th column element of a matrix as M[1,1] is simply [bad and wrong]("http://catb.org/jargon/html/B/Bad-and-Wrong.html").

As it happens, though, matrices in math are indexed like that, usually.

---

### Post by TheBuzzSaw on 2009-09-28
On the flip side, I am very unimpressed with mathematicians implementation of float/double. :P

---

### Post by jpkotta on 2009-09-28
> **A_Fiachra said:**
> As a mathematician -- I would have to go with Dijkstra.

The natural numbers start at 0.  So far, no one has come up with a convincing argument to index anything using something other than the natural numbers except "I don't like it!"

Ironically Fortran got away with 1 based indexing -- but, then again, Fortran wasn't built by mathematicians, it was built by engineers.

(insert snarky comment about engineers here)

After all, accessing the 0th row, 0th column element of a matrix as M[1,1] is simply [bad and wrong]("http://catb.org/jargon/html/B/Bad-and-Wrong.html").

I'm an engineer, and I dislike 1-indexing.  Also, I was under the impression that the natural numbers could include or exclude 0 depending on what kind of mathematician you were talking to.  But as in computer languages, most of them use 0-indexing.  Finally, Fortran most certainly was designed by mathematicians (look up John Backus).

> **Arndt said:**
> As it happens, though, matrices in math are indexed like that, usually.

I don't know about that.  Most of the math I see is 0-indexed.  It usually ends up being simpler, as I tried to explain (poorly) in my first post.

---

### Post by Can+~ on 2009-09-28
> **TheBuzzSaw said:**
> On the flip side, I am very unimpressed with mathematicians implementation of float/double. :P

I second that.

---

### Post by TheStatsMan on 2009-09-28
In mathematics the standard index for the first element of a matrix is [1,1]. Off the top of my head I cannot remember ever seeing otherwise(I am not saying it never is, but it is surely rare). Fortran (and matlab both start with 1) are probably the most widely used languages in linear algebra by applied mathematicians and computer scientists that work in that area. Fortran was designed by a team of people, of which the leader (and possibly others in the group) was a mathematician.

More to the point surely this is hardly an issue to get so excited about. I code in languages that start in one and some that start in zero. It is hardly a problem, it is only slight annoyance when for instance one calls a Fortran routine from C++.

---

### Post by A_Fiachra on 2009-09-29
Evidently I forgot my basic linear algebra and stand corrected, matrices are 1-indexed.  :oops:

However, Backus wasn't a mathematician in the sense of Von Neumann, Goldstine or Minsky, he had a master's degree, not a doctorate.  He did win a Turing award .. no slouch! 

Formally, the natural numbers include 0, and a lot of mathematical constructs speak of a 0th element.  There is a joke among math grad students that a real math book has a chapter 0.

Perl uses 0-based arrays (by default) but uses $1 as a place holder for the first grouped match in a string -- little inconsistent?

Python's re package use re.match,group(0) to represent a string that matched a regex and re.match.group(1) for the first actual group (if any).  BUt in python you can always do
```

m = re.match(r"(?P<first_name>\w+) (?P<last_name>\w+)", "Malcom Reynolds")
m.groupdict()

{'first_name': 'Malcom', 'last_name': 'Reynolds'}


```
That's the nice thing about associative arrays -- no explicit order!!

---

### Post by A_Fiachra on 2009-09-29
> **Can+~ said:**
> I second that.


Wait -- don't you remember the Pentium FDIV bug? That chip was designed by electrical engineers!  :-p

---

### Post by TheStatsMan on 2009-09-29
> **A_Fiachra said:**
> 

However, Backus wasn't a mathematician in the sense of Von Neumann, Goldstine or Minsky, he had a master's degree, not a doctorate.  He did win a Turing award .. no slouch! 



Having a master's degree and not a doctorate, does not mean that he wasn't a mathematician. I know a statistician that is currently appointed as a professor in two different universities, has published in many of the top statistical journals (including JRSSB, which is the top), yet he only has a master's degree. I know plenty of people with PhD's that have never worked on anything that could be regarded as decent. Is this fellow not a statistician, because he can't be bothered stringing together a bunch of his papers and turning it into a thesis so he can obtain a piece of paper and a title. 

FWIW I have a PhD.

---

### Post by nvteighen on 2009-09-29
> **TheStatsMan said:**
> Having a master's degree and not a doctorate, does not mean that he wasn't a mathematician. I know a statistician that is currently appointed as a professor in two different universities, has published in many of the top statistical journals (including JRSSB, which is the top), yet he only has a master's degree. I know plenty of people with PhD's that have never worked on anything that could be regarded as decent. Is this fellow not a statistician, because he can't be bothered stringing together a bunch of his papers and turning it into a thesis so he can obtain a piece of paper and a title. 

FWIW I have a PhD.

+1

And Aristotles hadn't any PhD :)

---

### Post by lisati on 2009-09-29
Ay ay ay what a thread!
> **ZuLuuuuuu said:**
> Hi,

I was wondering why indexes of arrays in C based languages and some other popular languages like Ruby or Python start with zero instead of one.


Short answer: because it makes the translation of the reference to an element of an array to a real address marginally easier for the compiler.

---

### Post by gnepets on 2009-09-29
Hi,

The answer to 'Why do arrays start at zero?' is rather simple

**Answer**: It is a memory location offset, so the first position in an array is
memoryLocation [offset]

**NOTE:** that when you say memoryLocation [1] it is (+1 * length of  char), (+1 * length of int), (+1 * length of long), (+1 * length of struct)





I am not sure if the answer was given yet, long thread is hard to read.

---

### Post by ZuLuuuuuu on 2009-09-29
By the way, thanks all for your answers (thanks button still not around :\ )...

---

### Post by A_Fiachra on 2009-09-29
> **TheStatsMan said:**
> Having a master's degree and not a doctorate, does not mean that he wasn't a mathematician. I know a statistician that is currently appointed as a professor in two different universities, has published in many of the top statistical journals (including JRSSB, which is the top), yet he only has a master's degree. I know plenty of people with PhD's that have never worked on anything that could be regarded as decent. Is this fellow not a statistician, because he can't be bothered stringing together a bunch of his papers and turning it into a thesis so he can obtain a piece of paper and a title. 

FWIW I have a PhD.

Point taken.  Hey, Ramanujan was self-taught.

---

### Post by Reiger on 2009-09-29
> **A_Fiachra said:**
> Perl uses 0-based arrays (by default) but uses $1 as a place holder for the first grouped match in a string -- little inconsistent?
Not really: $0 or the first match is the entire matching string. That's sort of a regexp convention with which Perl has more or less shaped other regexp conventions in other languages (if they do not simply copy Perl).

---

### Post by minasmorath on 2009-09-29
you are all making this overly complex, when it's really quite simple.

A computer does it's computations in binary, not in decimal. when you count in binary, you start at 0, because zero in binary is a number, indicitive of the start of the series, and not just a mathematical concept of nothing.

C is compiled to assembly code on the target machine, and then to binary (it's not a big step once it's in assembly).

although we normally translate binary 00000000 as decimal 0, that is simply because in certain areas of computing, such as where mathemeticians are concerned, there has to be a concept of nothing, the same as there is a concept of infinity, even though we only have 32 or 64 bits to represent it.

EDIT: I guess this coencides with the memory location explanation, they are two different answers for the same  problem. (although i was trying to get all the way down to bare concepts with it, and i overthought)

Good day to you all.

Mitch

---

### Post by A_Fiachra on 2009-09-29
> **Reiger said:**
> Not really: $0 or the first match is the entire matching string. That's sort of a regexp convention with which Perl has more or less shaped other regexp conventions in other languages (if they do not simply copy Perl).

hmm?


Isn't $0 the name of the executing program?

---

### Post by Arndt on 2009-09-29
> **minasmorath said:**
> you are all making this overly complex, when it's really quite simple.

A computer does it's computations in binary, not in decimal. when you count in binary, you start at 0, because zero in binary is a number, indicitive of the start of the series, and not just a mathematical concept of nothing.

C is compiled to assembly code on the target machine, and then to binary (it's not a big step once it's in assembly).

although we normally translate binary 00000000 as decimal 0, that is simply because in certain areas of computing, such as where mathemeticians are concerned, there has to be a concept of nothing, the same as there is a concept of infinity, even though we only have 32 or 64 bits to represent it.

EDIT: I guess this coencides with the memory location explanation, they are two different answers for the same  problem. (although i was trying to get all the way down to bare concepts with it, and i overthought)

Good day to you all.

Mitch

(This thread doesn't want to die.) Then you may want to consider the question of why some languages start array indexing with 1.

---

### Post by gnepets on 2009-09-29
> **Arndt said:**
> (This thread doesn't want to die.) Then you may want to consider the question of why some languages start array indexing with 1.

This is simple also :) some one thought
"It might be more convenient for programmers if we made programming more like what they know already"

And so they designed there compilers to use the concept of position 1, 2, 3, ... instead of offset of 0, 1, 2, ...

It is just really just two different systems for doing the same thing, all that you need to do is translate position back to an offset and you are all good.

EDIT: there is no difference speed wise, all done at compile time.

regards,
Stephen.

---

### Post by jpkotta on 2009-10-01
> **TheStatsMan said:**
> In mathematics the standard index for the first element of a matrix is [1,1]. Off the top of my head I cannot remember ever seeing otherwise(I am not saying it never is, but it is surely rare). 

OK, looks like you're right.  I went back and started looking at books and most of the time they use 1-indexing.  But many of my signal processing books use 0-indexing, and in my case, the professor that taught the last linear algebra class I took (it was called signal processing but it was really linear algebra) used 0-indexing almost exclusively.  So again it's all over the place.  

As I read somewhere, let's compromise and start at 1/2.

---

### Post by ZuLuuuuuu on 2009-10-01
> **jpkotta said:**
> OK, looks like you're right.  I went back and started looking at books and most of the time they use 1-indexing.  But many of my signal processing books use 0-indexing, and in my case, the professor that taught the last linear algebra class I took (it was called signal processing but it was really linear algebra) used 0-indexing almost exclusively.  So again it's all over the place.

In signal processing we usually choose 0 to represent a moment in time or a point in space and then, for example, 1 represents, for example, 1 second later or 1 meter right while -1 represents 1 second ago or 1 meter left. Maybe that's why the matrixes are 0 based (although I didn't see yet a matrix notation in our signal processing course), it is actually nothing to do with counting.

But this made me think that there might be cases where you might want an array's index to start with zero. Maybe Eiffel's approach is the best one: There is no number on which array is based (I'm an Eiffel amateur so if this statement is wrong correct me.). You indicate the lower and upper index of an array while creating it. So you can create an array whose first element is at index 1 (which is the usual choice in Eiffel books for everyday problems) or you can create an array whose first element is at index 0 (or even -273 if you want) if it feels natural to the problem (like signal processing example).

---

### Post by coolen on 2009-10-05
Main reason I can think of: memory addressing starts from zero. The address of the very first register in your computer is 0, and the last allowable one is (likely) 2^64 - 1. That's not arbitrary, that's binary.

If you've ever done any assembly, that's important. If you've ever done any programming for microcontrollers, it's also best not to disconnect too much from your underlying knwoledge of the platform.

Remember, C is an old language. It is used to interface directly with hardware, and it doesn't always have the support of a memory manager to obfuscate these things nicely for it. Your code will wind up a lot neater and easier to understand if you don't have to compensate for the fact that your language begins its indexing at 1.

Also, if you're into loops, you can run through 2D arrays row-by-row a lot easier if you have a zero index. Just use a modulus. Easy as pie.

---

