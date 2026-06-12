---
title: "lvalue required error???"
date: 2011-01-27
forum: Programming Talk
---

### Post by Praveen30 on 2011-01-27
#include<stdio.h>

void main()
{
   char arr[8]="rhombus";
   int i;
   for(i=0;i<=7;i++)
   printf("\n%d",*arr);
   arr++;                   //lvalue required here//
}

i am getting an error..LVALUE required...i want to know deeply what is this lvalue...why it comes??how it comes?? 

i can run this programme by putting *(arr+i) in place of *arr..and omitting arr++..but this is not my point of concern....

---

### Post by dileepm on 2011-01-27
Can u try changing your code to

> #include<stdio.h>

void main()
{
char arr[7]="rhombus";
int i;
for(i=0;i<7;i++)
printf("\n%d",arr[i]);
i++;
}

---

### Post by MadCow108 on 2011-01-27
an lvalue is a reference to an object where something can be stored in. e.g. a piece of memory.
They can be modifiable or not.

an array is no modifiable lvalue you can't assign a different memory location to it after initialization.
you can use a pointer to the beginning of the array to do what you wanted:
```

int ar[]={1,2,3};
int * p = ar; // implicit conversion of array to pointer
for (int i=0; i< 3; i++) {
  printf("%d\n",*p);
  p++; // can be assigned to
}
// or
for (int * p = ar; p < ar + 3; p++)
  printf("%d\n",*p);

```

---

### Post by Praveen30 on 2011-01-27
> **MadCow108 said:**
> an lvalue is a reference to an object where something can be stored in. e.g. a piece of memory.
They can be modifiable or not.

an array is no modifiable lvalue you can't assign a different memory location to it after initialization.
you can use a pointer to the beginning of the array to do what you wanted:
```

int ar[]={1,2,3};
int * p = ar; // implicit conversion of array to pointer
for (int i=0; i< 3; i++) {
  printf("%d\n",*p);
  p++; // can be assigned to
}
// or
for (int * p = ar; p < ar + 3; p++)
  printf("%d\n",*p);

```

ok fine, but can you tell me what are the different possibilities where  lvalue error can come???

---

### Post by Tony Flury on 2011-01-27
> **Praveen30 said:**
> ok fine, but can you tell me what are the different possibilities where  lvalue error can come???

@Praveen30 - MadCow108 did already explain it "an lvalue is a reference to an object where something can be stored in. e.g. a piece of memory. They can be modifiable or not."

In other words - an Lvalue is any object/variable that can appear on the left hand side of an assignment - hence LValue (Left Value).

given the declarations you have - you could not do :
```

arr = 3 ;

```
for instance as you can't change the value of arr - It is not a valid lvalue.

You could do 
```

arr[0] = 3 ;

```

---

### Post by MadCow108 on 2011-01-27
another example for the lvalue error is:
```

1 = 3;

>lvalue required as left operand of assignment

```
a number is nothing where something can be stored, it is no lvalue. (in C at least, I think there are languages which allow this [fortran?] ).

---

### Post by Praveen30 on 2011-01-27
> **MadCow108 said:**
> another example for the lvalue error is:
```

1 = 3;

>lvalue required as left operand of assignment

```a number is nothing where something can be stored, it is no lvalue. (in C at least, I think there are languages which allow this [fortran?] ).

thanks!!!!!

---

### Post by psusi on 2011-01-27
Actually if something can not be modified then by definition, it is NOT an lvalue.  Things that can be modified can be used as either rvalue or lvalue, but immutable objects can only be used as rvalues.

---

### Post by Praveen30 on 2011-01-27
> **psusi said:**
> Actually if something can not be modified then by definition, it is NOT an lvalue.  Things that can be modified can be used as either rvalue or lvalue, but immutable objects can only be used as rvalues.

thanks for clarifying this!!!!

---

### Post by trent.josephsen on 2011-01-27
C99 6.3.2.1 says (formatting in the original):

> An *lvalue* is an expression with an object type or an incomplete type other than **void**; if an lvalue does not designate an object when it is evaluated, the behavior is undefined.  [...] A *modifiable lvalue* is an lvalue that does not have array type, does not have an incomplete type, does not have a const-qualified type, and if it is a structure or union, does not have any member (including, recursively, any member or element of all contained aggregates or unions) with a const-qualified type.

Except when it is the operand of the **sizeof** operator, the unary **&** operator, the **++** operator, the **--** operator, or the left operand of the **.** operator or an assignment operator, an lvalue that does not have array type is converted to the value stored in the designated type (and is no longer an lvalue). [...]

Except when it is the operand of the **sizeof** operator or the unary **&** operator, or is a string literal used to initialize an array, an expression that has the type "array of *type*" is converted to an expression with type "pointer to *type*" that points to the initial element of the array object and is not an lvalue.

In the attempted assignment
```
1 = 3;
```1 is merely a value and does not designate an object; therefore trying to use it as an lvalue results in undefined behavior.  If you were foolish or curious enough to try it, you may expect demons to fly out of your nose.

In the attempted postincrement
```
arr++;
```"arr" is converted to an expression that is *not* an lvalue, according to the third paragraph quoted above.  Since 6.5.2.4p1 requires that the operand of ++ be a modifiable lvalue, that line contains a constraint violation requiring a diagnostic.  When a diagnostic has been issued, then the nasal demons may appear.

So, to be extremely nitpicky:  lvalues may be modifiable or not, but what you have is a non-lvalue by virtue of conversion to pointer, not just an unmodifiable lvalue.  That is why you got a message saying "lvalue required" despite the fact that "arr" is in fact an lvalue.

---

### Post by psusi on 2011-01-27
> **trent.josephsen said:**
> 
In the attempted assignment
```
1 = 3;
```1 is merely a value and does not designate an object; therefore trying to use it as an lvalue results in undefined behavior.  If you were foolish or curious enough to try it, you may expect demons to fly out of your nose.

No, the behavior is quite well defined: the program is malformed and the compiler errors out.

> **trent.josephsen said:**
> So, to be extremely nitpicky:  lvalues may be modifiable or not, but what you have is a non-lvalue by virtue of conversion to pointer, not just an unmodifiable lvalue.  That is why you got a message saying "lvalue required" despite the fact that "arr" is in fact an lvalue.

It does not make sense to say that something is both non modifiable, and can be used as an lvalue.  Either you can use it on the left side of an assignment or you can't.

Arrays are not lvalues.  You seem to be arguing that the array starts out as an lvalue, then implicitly is converted to an rvalue.  For that to be true, there has to be a circumstance where that conversion does not happen and you can use the array as an lvalue.

---

### Post by Arndt on 2011-01-27
> **psusi said:**
> No, the behavior is quite well defined: the program is malformed and the compiler errors out.



It does not make sense to say that something is both non modifiable, and can be used as an lvalue.  Either you can use it on the left side of an assignment or you can't.

Arrays are not lvalues.  You seem to be arguing that the array starts out as an lvalue, then implicitly is converted to an rvalue.  For that to be true, there has to be a circumstance where that conversion does not happen and you can use the array as an lvalue.

Are there not enough clues in the standard text that was quoted?

"An lvalue is an expression with an object type or an incomplete type other than void;"

" A modifiable lvalue is an lvalue that does not have array type"

"Except when it is the operand of the sizeof operator or the unary & operator, or is a string literal used to initialize an array, an expression that has the type "array of type"..."

sizeof is the answer to your question.


Does the phrase "use as an lvalue" occur in the standard at all?

---

### Post by psusi on 2011-01-27
> **Arndt said:**
> 
sizeof is the answer to your question.


sizeof does not require an lvalue.

I guess you can say that it is an lvalue because you can't tell the difference, in the same sense that Schroedinger's cat is both alive and dead, but most people don't like to think that way.  Most people recognize that you can't be both alive and dead, and you aren't both an rvalue and an lvalue, so an array is an rvalue since it can't be used where an lvalue is required.

---

### Post by worksofcraft on 2011-01-27
Sigh - I have this sinking feeling I've posted this link before about [lvalues]("http://en.wikipedia.org/wiki/Value_(computer_science)")

I will try to put it in my own words:

[LIST=1]
[*]An lvalue is something that has been allocated memory space at run time. To access it, the computer instructions will use a memory address.

[*]A non-lvalue is something that does not have a designated memory space at run time. The computer will not use a memory address to retrieve it's value and it can't write a new value to it.
[/LIST]
Example of a non-lvalue is in an increment instruction that adds the value "one" to it's destination. It does not need to go fetch that value of "one" from anywhere else in memory as it is part of the actual code that is executing.

WRT to this thread, An array IS an lvalue because it resides at a certain location in memory at run time.
OTOH the **address** of that array is **not** an lvalue: It will be built into the instructions that access the array.
In C the name of an array is synonymous with the address of that array and so it is not an lvalue that you could increment.
If you want to make it into an lvalue then you need to store it in a pointer variable. Said pointer then does have a memory address of it's own at run time...

---

### Post by Arndt on 2011-01-27
> **trent.josephsen said:**
> C99 6.3.2.1 says (formatting in the original):



In the attempted assignment
```
1 = 3;
```1 is merely a value and does not designate an object; therefore trying to use it as an lvalue results in undefined behavior.  If you were foolish or curious enough to try it, you may expect demons to fly out of your nose.

In the attempted postincrement
```
arr++;
```"arr" is converted to an expression that is *not* an lvalue, according to the third paragraph quoted above.  Since 6.5.2.4p1 requires that the operand of ++ be a modifiable lvalue, that line contains a constraint violation requiring a diagnostic.  When a diagnostic has been issued, then the nasal demons may appear.

So, to be extremely nitpicky:  lvalues may be modifiable or not, but what you have is a non-lvalue by virtue of conversion to pointer, not just an unmodifiable lvalue.  That is why you got a message saying "lvalue required" despite the fact that "arr" is in fact an lvalue.

I found this to be somewhat illuminating. I wasn't even aware that the formulation had changed: [http://bytes.com/topic/c/answers/559645-lvalue-modifiable-non-modifiable](http://bytes.com/topic/c/answers/559645-lvalue-modifiable-non-modifiable)

---

### Post by Praveen30 on 2011-01-27
> **worksofcraft said:**
> Sigh - I have this sinking feeling I've posted this link before about [lvalues]("http://en.wikipedia.org/wiki/Value_%28computer_science%29")

I will try to put it in my own words:

[LIST=1]
[*]An lvalue is something that has been allocated memory space at run time. To access it, the computer instructions will use a memory address.
[*]A non-lvalue is something that does not have a designated memory space at run time. The computer will not use a memory address to retrieve it's value and it can't write a new value to it.
[/LIST]
Example of a non-lvalue is in an increment instruction that adds the value "one" to it's destination. It does not need to go fetch that value of "one" from anywhere else in memory as it is part of the actual code that is executing.

WRT to this thread, An array IS an lvalue because it resides at a certain location in memory at run time.
OTOH the **address** of that array is **not** an lvalue: It will be built into the instructions that access the array.
In C the name of an array is synonymous with the address of that array and so it is not an lvalue that you could increment.
If you want to make it into an lvalue then you need to store it in a pointer variable. Said pointer then does have a memory address of it's own at run time...
 nice one, Sir.

---

### Post by psusi on 2011-01-27
You can look at it that way.  Or you can look at it as the elements of the array are lvalues, but the array as a whole is not, and the array as a whole will decay into a pointer to the first element, which is itself not an lvalue, but when you dereference it to get to the first element, that is an lvalue.

---

### Post by trent.josephsen on 2011-01-28
For the record.

[quote=psusi]Actually if something can not be modified then by definition, it is NOT an lvalue.[/quote]

This is one possible definition of "lvalue".  I don't want to imply that this definition is incorrect.  However, in relation to C, it might be misleading to use this definition, because the C Standard uses the term differently (and is defined as I quoted in my previous post).

array, constant, and object also come to mind as words that have a particular well-defined and specific meaning in the Standard, but are often used in a different sense elsewhere.  (Whether the Standard is in error for co-opting these or any other terms to describe the C language is neither relevant nor topical, and I hope we don't get into that.)

In my first post, I was trying to reconcile the compiler's error message with the Standard.  Reading it with the conventional meaning of "lvalue" results in psusi's interpretation, which is (strictly speaking) incorrect according to the Standard, but as for what is actually going on inside the compiler to detect the error, who knows?  The important part is that the compiler correctly issues a diagnostic (it's a constraint violation, after all).

Aside:
[quote=Arndt]Does the phrase "use as an lvalue" occur in the standard at all?[/quote]
No.  What I meant to say is something like this:
1 either is an lvalue or is not.  If it is, then since it does not designate an object, the behavior is undefined.  If it is not, then the construction violates 6.5.16p2, which says that an assignment operator shall have a modifiable lvalue as its left operand.

Interestingly enough, it seems that it would be OK for a C implementation to allow integer constants to be lvalues (even modifiable lvalues).  I doubt any implementation has taken advantage of this, and I can't think of any practical application that wouldn't be better done some other way, but there you go.

---

### Post by dribeas on 2011-01-28
Arrays are some particular beasts in the language. The rules that apply to the rest of the types do not apply to arrays by design. The first of those rules is about the *pass-by-value* syntax you don't get *pass-by-value* semantics. To make this happen, the language was tweaked so that arrays *decay* into pointers to the first element in most contexts, the decayed pointer is an rvalue. This has generated a big amount of confusion with many people (including book authors) stating that *arrays are pointers* and such.

On the other hand, another quite common misunderstanding is that a given object is an lvalue or rvalue, that is wrong. *Expressions* are lvalues or rvalues, not variables. In general, unless the expression in which is used requires a conversion and as such it produces an rvalue, any identifier for a variable represents an lvalue expression.

Now, the fact that in most use cases the language forces the decay to a pointer to the first element for arrays, and that that the result of the decay is an rvalue expression, does not mean that the identifier of the array is an rvalue expression. For a counter example,  the language requires that the argument to the operator & has to be either the result of a [], unary * operator or an lvalue that is not a bitfield. Now, while this is not the same as a real proof, a simple test that verifies the lvalue-ness of an array can be done with this simple program:

```

int main() {
   int array[10];
   int (*p)[10] = &array;  // this requires array to be an lvalue
}

```

On some of the comments above that say that if it is not modifiable it is not an lvalue, the same goes: lvalue-ness is unrelated to const-ness. Const-ness can be used to create expressions that generate unmodifiable lvalues as for example in:

```

int main() {
   const int constant = 10;
   const int * p = &constant; // same stupid test as above
}

```

Which is a simple proof that you can actually have non modifiable lvalue expressions. 

Another trivial proof for the two things above is a single sentence from the standard quoted above: *A modifiable lvalue is an lvalue that does not have array type* If an lvalue could never be non-modifiable there would not be any need to define what a *modifiable lvalue* is. If an lvalue could not have array type, there would not be any need to state that a *modifiable lvalue* (subset of lvalue) cannot have array type...

Whenever in doubt, read @worksofcraft post above: lvalue-ness of an expression has more to do with the posibility of taking it's address than any other thing

---

### Post by psusi on 2011-01-28
How does that require array to be an lvalue when it is on the right hand side of the assignment, not the left?

And just because they used the word modifiable lvalue does not necessarily mean there is such a thing as a non modifiable lvalue.

---

### Post by worksofcraft on 2011-01-29
> **psusi said:**
> 
And just because they used the word modifiable lvalue does not necessarily mean there is such a thing as a non modifiable lvalue.
OK well you hopefully will agree that a **const** int is non-modifiable?
[php]
// g++ modifiable.cpp
#include <cstdio>
const int nonModifiableLValue = 57005;
int main() {
	return !printf("nonModifiableLValue=%x at %p\n",
		nonModifiableLValue,
		& nonModifiableLValue
	);
}
[/php]

```

$ g++ -Wall modifiable.cpp
$ ./a.out
nonModifiableLValue=dead at 0x40074c


```
Compiles and runs... so it is not modifiable but is it an lvalue?

[php]
// g++ modifiable.cpp
#include <cstdio>
enum { nonModifiableLValue = 57005 };
int main() {
	return !printf("nonModifiableLValue=%x at %p\n",
		nonModifiableLValue,
		& nonModifiableLValue
	);
}
[/php]

```

$ g++ -Wall modifiable.cpp
modifiable.cpp: In function &#8216;int main(int, char**, char**)&#8217;:
modifiable.cpp:7: error: lvalue required as unary &#8216;&&#8217; operand

```

Evidently the enum is NOT an lvalue and so the compiler flatly refuses to take it's address. :shock:

In that case the cost int **must have been** an lvalue and in being **const** it isn't modifiable ;)

---

### Post by worksofcraft on 2011-01-29
p.s.

Just as a trick question... see if you can predict whether the compiler should cope with this one:
[php]
// g++ modifiable.cpp
#include <cstdio>
const int & value(const int &input) { return input; }
#define nonModifiableLValue (value(57005))
int main() {
	return !printf("nonModifiableLValue=%x at %p\n",
		nonModifiableLValue,
		& nonModifiableLValue
	);
}
[/php]
:lolflag:

---

### Post by trent.josephsen on 2011-01-29
In this discussion about C, I fail to see how test programs written in C++ are relevant.  I really, really wish you wouldn't conflate the two with such obstinate regularity.

---

### Post by psusi on 2011-01-30
Having an address does not make something an lvalue.  Being able to use it on the left side of an assignment does.

A function also has an address, but is not an lvalue.

---

### Post by trent.josephsen on 2011-01-30
What makes a function not an lvalue *according to the Standard* is that it does not have object type.  The Standard does not define *lvalue* in terms of assignment statements.

---

### Post by psusi on 2011-01-30
I'm pretty sure that is how the old one defined it.  How does the new one?

---

### Post by trent.josephsen on 2011-01-30
> **psusi said:**
> I'm pretty sure that is how the old one defined it.  How does the new one?
As in my first post.

C99 is pretty easy to come by.  I would be interested to see the text of C89 as it relates to lvalues, if somebody has access to it.

The reference manual in the back of my copy of K&R2 says
> An *object* is a named region of storage; an *lvalue* is an expression referring to an object.
Of course, this isn't the language of C89 itself, but it falls in line with C99.

Google also found [this page](http://www.lysator.liu.se/c/rat/c2.html), which has an interesting comment on 3.2.2.1 (although still without the wording of the Standard).

---

### Post by worksofcraft on 2011-01-30
> **trent.josephsen said:**
> In this discussion about C, I fail to see how test programs written in C++ are relevant.  I really, really wish you wouldn't conflate the two with such obstinate regularity.

Who said it's about C? IMO it is about the concept "lvalue". However specially for you I changed the include file name and the comment style so you can use the C compiler:
[php]
/* gcc modifiable.c */
#include <stdio.h>
enum { nonModifiableLValue = 57005 };
int main(int argc, char *argv[], char *envp[]) {
	return !printf("nonModifiableLValue=%x at %p\n",
		nonModifiableLValue,
		& nonModifiableLValue
	);
}
[/php]

and lo... she still wants an lvalue:
```

$ gcc -Wall -pedantic modifiable.c
modifiable.c: In function &#8216;main&#8217;:
modifiable.c:8: error: lvalue required as unary &#8216;&&#8217; operand

```

I was attempting to show an example of a non-modifiable lvalue and then to confirm that it was indeed considered an lvalue even though, being non modifiable it can't be used on the left hand side of an expression:
[php]
/* gcc modifiable.c */
#include <stdio.h>
const int nonModifiableLValue = 57005;
int main(int argc, char *argv[], char *envp[]) {
	nonModifiableLValue = nonModifiableLValue;
}
[/php]
```

$ gcc -Wall -pedantic modifiable.c
modifiable.c: In function &#8216;main&#8217;:
modifiable.c:5: error: assignment of read-only variable &#8216;nonModifiableLValue&#8217;

```
Perhaps you rather discuss the **symantics of the actual wording** of different versions of official standards, but I'm satisfied I have a **clear mental picture** of what constitutes an lvalue and what doesn't in any language.

---

